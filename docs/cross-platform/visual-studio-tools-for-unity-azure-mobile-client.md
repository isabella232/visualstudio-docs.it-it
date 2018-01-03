---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Client per dispositivi mobili | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 451b4f1f2580a55077bf3fc6a9ad3f16a2afaf0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>Implementare la classe MobileServiceClient di Azure

Al centro di Azure Mobile Client SDK è la classe <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a>, che consente l'accesso al back-end delle app per dispositivi mobili.

## <a name="locate-the-url-of-the-mobile-app-backend"></a>Individuare l'URL di back-end dell'app per dispositivi mobili

Il costruttore di `MobileServiceClient` accetta l'URL dell'app per dispositivi mobili come parametro. Prima di continuare, quindi, è necessario individuare l'URL.

1. Nel portale di Azure fare clic sul pulsante **Servizi app**.

    ![Fare clic su Servizi app](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. Fare clic sulla voce corrispondente all'app per dispositivi mobili.

    ![Fare clic sull'app per dispositivi mobili](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. Copiare l'URL di back-end dell'app per dispositivi mobili.

    ![Copiare l'URL](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>Creare il singleton di MobileServiceClient

Deve esistere una sola istanza di `MobileServiceClient`. La procedura dettagliata, quindi usa una variante del modello singleton.

1. Nella directory **Assets/Scripts** del progetto Unity creare un nuovo script C# denominato **AzureMobileServiceClient**.

2. Aprire lo script `AzureMobileServiceClient` ed eliminare eventuale codice del modello, incluse le istruzioni using e la dichiarazione della classe.

3. Aggiungere il codice seguente:

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > Se IntelliSense non riconosce lo spazio dei nomi Microsoft.WindowsAzure, verificare di aver eseguito tutti i passaggi della sezione [Preparare l'ambiente di sviluppo]().

4. Nel codice precedente sostituire `MOBILE_APP_URL` con l'URL del back-end dell'app per dispositivi mobili.

## <a name="next-step"></a>Passaggio successivo

* [Aggiornare l'archivio di protezione di Mono di Unity](visual-studio-tools-for-unity-azure-security.md)
