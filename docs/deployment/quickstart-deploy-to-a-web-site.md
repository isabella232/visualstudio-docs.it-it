---
title: Eseguire la pubblicazione in un sito Web
description: Informazioni su come usare lo strumento Pubblica per pubblicare app ASP.NET, ASP.NET Core, .NET Core e Python in un sito Web da Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 825908633e12727d3c792cfa9793486f2d9f005203a8e17646fdbf1b349d7d85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453027"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Eseguire la pubblicazione un'app Web in un sito Web usando Visual Studio

È possibile usare lo strumento **Pubblica** per la pubblicazione di app ASP.NET, ASP.NET Core, .NET Core e Python in sito Web da Visual Studio. Per Node.js la procedura è supportata, ma l'interfaccia utente è diversa.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Se è necessario pubblicare un'applicazione desktop di Windows in una condivisione file di rete, vedere [Distribuire un'applicazione desktop tramite ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic). Per C++/CLR, vedere [Distribuire un'app nativa tramite ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) oppure per C/C++, vedere [Distribuire un'app nativa tramite un progetto di installazione](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Eseguire la pubblicazione in un sito Web

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Comando Pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "Scegliere Pubblica")

1. Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Selezionare **Nuovo**.

1. Nella finestra **Pubblica** scegliere **Server Web (IIS).**

    ![Scegliere la destinazione di pubblicazione](../deployment/media/quickstart-publish-iis.png "Scegliere IIS, FTP e così via.")

1. Scegliere **Distribuzione Web** come metodo di distribuzione. La funzionalità Distribuzione Web semplifica la distribuzione di applicazioni Web e siti Web ai server IIS e deve essere installata come applicazione nel server. Usare la [Installazione guidata piattaforma Web](https://www.microsoft.com/web/downloads/platform.aspx) per installarla.

    ![Scegliere il metodo di distribuzione](../deployment/media/quickstart-publish-iis-web-deploy.png "Scegliere IIS, FTP e così via.")

1. Configurare le impostazioni necessarie per il metodo di pubblicazione e selezionare **Fine.** 

    ![Distribuzione Web dettagli della connessione](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Per pubblicare, **selezionare Pubblica** nella pagina di riepilogo. La finestra Output mostra i risultati e lo stato della distribuzione.

   Per informazioni sulla risoluzione dei ASP.NET Core in IIS, vedere Risolvere i ASP.NET Core [in Servizio app di Azure e IIS.](/aspnet/core/test/troubleshoot-azure-iis)

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione. È anche possibile configurare un profilo di pubblicazione importando le impostazioni di pubblicazione.

> [!div class="nextstepaction"]
> [Importare impostazioni di pubblicazione ed eseguire la distribuzione in IIS](tutorial-import-publish-settings-iis.md)
