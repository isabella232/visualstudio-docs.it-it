---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Modello di dati | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 57a6a6aaff1c41a8720f842e20142e3cb1a2e538
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="create-data-model-classes"></a>Creare classi di modelli di dati

Il progetto Unity deve contenere classi di modelli di dati corrispondenti alle tabelle create nel back-end dell'app per dispositivi mobili di Azure.

## <a name="create-the-crashinfo-class"></a>Creare la classe CrashInfo

1. In Unity aggiungere una nuova cartella nella directory **Assets** radice e denominarla **Scripts**. All'interno della nuova cartella Scripts creare un'altra cartella denominata **Data Models**. Questo vale solo per le organizzazioni.

2. All'interno della nuova cartella Data Models creare un nuovo script C# denominato **CrashInfo**.

3. Aprire il nuovo script `CrashInfo`, eliminare eventuale codice del modello, incluse la dichiarazione della classe e le istruzioni using, e aggiungere quanto segue:

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > Perché la procedura dettagliata funzioni correttamente, il nome della classe di modelli di dati deve corrispondere al nome della tabella semplice creata nel back-end dell'app per dispositivi mobili di Azure.

## <a name="create-the-highscoreinfo-class"></a>Creare la classe HighScoreInfo

1. All'interno della cartella Data Models creare un nuovo script C# denominato **HighScoreInfo**.

2. Aprire il nuovo script `HighScoreInfo`, eliminare eventuale codice del modello, incluse la dichiarazione della classe e le istruzioni using, e aggiungere quanto segue:

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>Passaggio successivo

  * [Implementare Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
