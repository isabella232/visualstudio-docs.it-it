---
title: Pubblicare un sito Web - Visual Studio | Documenti Microsoft
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
- multiple
ms.openlocfilehash: 6fa914b1b6b353d4e15bd8293f1fc141dd0ae371
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Pubblicare un'app web o un'applicazione .NET Core in un sito web tramite lo strumento di pubblicazione di Visual Studio

È possibile utilizzare il **pubblica** strumento per la pubblicazione di applicazioni ASP.NET in un sito Web.

Questa procedura si applica a ASP.NET, ASP.NET di base, .NET Core e Python App in Visual Studio. Per Node.js, sono supportati i passaggi, ma l'interfaccia utente è diverso.

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

## <a name="publish-to-a-web-site"></a>Pubblicare un sito web

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

    ![Scegliere Pubblica](../deployment/media/quickstart-publish-aspnet.png "scegliere pubblica")

1. Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, scegliere **IIS, FTP, e così via**.

    ![Scegliere IIS, FTP e così via](../deployment/media/quickstart-publish-iis-ftp.png "scegliere IIS, FTP e così via.")

1. Fare clic su **Pubblica**.

    Il profilo delle impostazioni viene visualizzata la finestra di dialogo di pubblicazione.

    ![Scegliere cartella](../deployment/media/quickstart-publish-settings-web.png "scegliere cartella")

1. Nel **metodo di pubblicazione** campo, scegliere un metodo, ad esempio **distribuzione Web** o **FTP**.

    Le impostazioni visualizzate accanto corrispondono al metodo di pubblicazione. La funzionalità distribuzione Web semplifica la distribuzione di applicazioni Web e siti Web ai server IIS e deve essere installata come un'applicazione nel server. Usare la [installazione guidata piattaforma Web](https://www.microsoft.com/web/downloads/platform.aspx) per installarlo.

1. Configurare le impostazioni necessarie per il metodo di pubblicazione e fare clic su **convalida connessione**.

    Se il server o destinazione sia disponibile e le impostazioni siano corrette, si verrà visualizzato un messaggio che indica la connessione viene convalidato e si è pronti per la pubblicazione.

    ![Convalidare la connessione a](../deployment/media/quickstart-publish-web-deploy.png "convalidare la connessione a")

1. Se si desidera configurare altre impostazioni di distribuzione, fare clic su **impostazioni**.

    È possibile configurare opzioni, ad esempio se distribuire una configurazione di Debug o Release e quindi fare clic su **salvare**. Se si esegue il debug in modalità remota, è necessario una configurazione di Debug.

1. Per pubblicare, fare clic su **pubblica**.

    La finestra di Output Mostra i risultati e l'avanzamento della distribuzione.

## <a name="next-steps"></a>Passaggi successivi

In questa Guida rapida, è stato descritto come utilizzare Visual Studio per creare un profilo di pubblicazione. È inoltre possibile configurare una pubblicazione profilo tramite l'importazione delle impostazioni di pubblicazione.

> [!div class="nextstepaction"]
> [Importazione delle impostazioni di pubblicazione e distribuire in IIS](tutorial-import-publish-settings-iis.md)
