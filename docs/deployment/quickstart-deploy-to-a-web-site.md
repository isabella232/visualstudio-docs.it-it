---
title: Eseguire la pubblicazione in un sito Web
description: Informazioni su come usare lo strumento di pubblicazione per pubblicare app ASP.NET, ASP.NET Core, .NET Core e Python in un sito Web da Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 027350b6a51cae5e7be88643624adc6955de91e4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350699"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Eseguire la pubblicazione un'app Web in un sito Web usando Visual Studio

È possibile usare lo strumento **Pubblica** per la pubblicazione di app ASP.NET, ASP.NET Core, .NET Core e Python in sito Web da Visual Studio. Per Node.js la procedura è supportata, ma l'interfaccia utente è diversa.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Se è necessario pubblicare un'applicazione desktop di Windows in una condivisione file di rete, vedere [Distribuire un'applicazione desktop tramite ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic). Per C++/CLR, vedere [Distribuire un'app nativa tramite ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) oppure per C/C++, vedere [Distribuire un'app nativa tramite un progetto di installazione](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Eseguire la pubblicazione in un sito Web

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica** o usare la voce di menu **Compila** > **Pubblica**.

    ![Il comando pubblica nel menu di scelta rapida del progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "Scegliere Pubblica")

1. Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Selezionare **Nuovo**.

1. Nella finestra **pubblica** scegliere **server Web (IIS)**.

    ![Scegliere la destinazione di pubblicazione](../deployment/media/quickstart-publish-iis.png "Scegliere IIS, FTP e così via.")

1. Scegliere **distribuzione Web** come metodo di distribuzione. La funzionalità Distribuzione Web semplifica la distribuzione di applicazioni Web e siti Web ai server IIS e deve essere installata come applicazione nel server. Usare la [Installazione guidata piattaforma Web](https://www.microsoft.com/web/downloads/platform.aspx) per installarla.

    ![Scegliere il metodo di distribuzione](../deployment/media/quickstart-publish-iis-web-deploy.png "Scegliere IIS, FTP e così via.")

1. Configurare le impostazioni necessarie per il metodo Publish e selezionare **Finish (fine** ). 

    ![Dettagli connessione Distribuzione Web](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Per pubblicare, selezionare **pubblica** nella pagina di riepilogo. La finestra Output mostra i risultati e lo stato della distribuzione.

   Per informazioni sulla risoluzione dei problemi ASP.NET Core in IIS, vedere [risolvere i problemi di ASP.NET Core in app Azure Service e IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione. È anche possibile configurare un profilo di pubblicazione importando le impostazioni di pubblicazione.

> [!div class="nextstepaction"]
> [Importare impostazioni di pubblicazione ed eseguire la distribuzione in IIS](tutorial-import-publish-settings-iis.md)
