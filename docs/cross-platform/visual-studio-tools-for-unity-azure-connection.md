---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Connessione | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: f21e320fe9e27f6873b9caed3048a93bfa94a9c4
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-client-connection"></a>Testare la connessione client

Dopo aver creato il singleton AzureMobileServiceClient, è il momento di testare la connessione client.

## <a name="create-the-testclientconnection-script"></a>Creare lo script TestClientConnection

1. Nella cartella **Scripts** (Script) in Unity, creare un nuovo script C# denominato **TestClientConnection**.

2. Aprire lo script in Visual Studio, eliminare eventuale codice di modello e aggiungere quanto segue:

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. Dal menu **GameObject** di Unity scegliere **GameObject > Create Empty** (Crea vuoto) per creare un GameObject vuoto nella scena Unity. Rinominarlo in **TestClientConnection**.

4. **Trascinare** lo script TestClientConnection dalla finestra **Progetto** di Unity al GameObject TestClientConnection nella finestra **Hierarchy** (Gerarchia).

5. Dal menu di Unity scegliere **File > Save Scene as...** (File > Salva scena con nome...). Denominare la scena **Test connessione client** e fare clic su **Salva**.

5. Fare clic sul pulsante **Esegui** in Unity e osservare la finestra della console. Verificare che nessuna delle asserzioni abbia generato un errore.

6. Aprire la tabella semplice CrashInfo nel portale di Azure. La tabella contiene ora una voce con le coordinate **X, Y, Z** corrispondenti a **(1, 2, 3)** e il valore **true** nella colonna **Eliminato**. Ogni volta che si esegue il test, alla tabella viene aggiunta una nuova voce con gli stessi valori ma con un ID univoco.

  ![Voce della tabella semplice](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>Passaggio successivo
* [Importare le risorse del gioco di esempio](visual-studio-tools-for-unity-azure-game-assets.md).
