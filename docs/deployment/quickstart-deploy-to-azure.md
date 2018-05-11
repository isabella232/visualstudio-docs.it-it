---
title: Pubblicare in Azure App Service - Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: c5c172ff3ec3033b50815efdb0b4ee293853ab1e
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Pubblicare un'applicazione ASP.NET o ASP.NET Core servizio App di Azure con Visual Studio

È possibile utilizzare il **pubblica** strumento per pubblicare le applicazioni ASP.NET, ASP.NET Core, Python, Node.js e .NET Core servizio App di Azure.

Se si dispone già di un account Azure, è possibile [iscriverti qui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio 2017 installato e il **ASP.NET** e **.NET Framework** carico di lavoro di sviluppo. Per un'applicazione .NET Core, è necessario anche il **.NET Core** carico di lavoro.

    Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

1. In **Visual c#** o **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)**(solo c#) o **applicazione Web di ASP.NET Core**, quindi fare clic su **OK**.

1. Scegliere **MVC** (oppure scegliere **applicazione Web (Model-View-Controller)** per .NET Core), verificare che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK** .

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **compilazione > Compila soluzione** per compilare il progetto.

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

    ![Scegliere Pubblica](../deployment/media/quickstart-publish-aspnet.png "scegliere pubblica")

1. Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, scegliere **servizio App**.

    ![Scegliere servizio App di Azure](../deployment/media/quickstart-publish-azure.png "scegliere servizio App di Azure")

1. Fare clic su **Pubblica**.

    Il **Crea servizio App** viene visualizzata la finestra di dialogo.

    ![Creare servizio App](../deployment/media/quickstart-publish-settings-app-service.png "creare servizio App di Azure")
    
1. Se non è firmato in Visual Studio, eseguire l'accesso e le impostazioni di servizio app predefinite popolano i campi.

    Il profilo delle impostazioni viene visualizzata la finestra di dialogo di pubblicazione.

    ![Scegliere cartella](../deployment/media/quickstart-publish-settings-web.png "scegliere cartella")

    Nella finestra di dialogo, è possibile selezionare la sottoscrizione in uso, selezionare o creare un gruppo di risorse e così via.

1. Scegliere **Crea**.

    Visual Studio distribuisce l'app del servizio App di Azure e carica l'app web nel browser.

    Nel riepilogo del **pubblica** riquadro, viene visualizzato l'URL del sito per il nuovo servizio App di Azure.

## <a name="next-steps"></a>Passaggi successivi

In questa Guida rapida, è stato descritto come utilizzare Visual Studio per creare un profilo di pubblicazione per la distribuzione in Azure. È inoltre possibile configurare una pubblicazione profilo tramite l'importazione di pubblicare le impostazioni di servizio App di Azure.

> [!div class="nextstepaction"]
> [Importazione delle impostazioni di pubblicazione e distribuzione in Azure](tutorial-import-publish-settings-azure.md)
