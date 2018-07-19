---
title: Pubblicare in un sito Web
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 036d7549995f79808142c3a0a64e7e5f2075df2c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077503"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Pubblicare un'app Web in un sito web usando Visual Studio

È possibile usare la **pubblica** dello strumento per pubblicare App ASP.NET, ASP.NET Core, .NET Core e Python in un sito Web da Visual Studio. Per Node. js, sono supportati i passaggi, ma l'interfaccia utente è diversa.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Pubblicare in un sito Web

1. In Esplora soluzioni fare clic sul progetto e scegliere **Publish** (o utilizzare il **compilare** > **pubblica** voce di menu).

    ![Il comando Pubblica nel menu di scelta rapida progetto in Esplora soluzioni](../deployment/media/quickstart-publish.png "scegliere pubblica")

1. Se sono stati configurati tutti i profili di pubblicazione, il **pubblica** viene visualizzato il riquadro. Selezionare **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, scegliere **IIS, FTP, e così via**.

    ![Scegliere IIS, FTP e così via](../deployment/media/quickstart-publish-iis-ftp.png "scegliere IIS, FTP e così via.")

1. Selezionare **Pubblica**. Il profilo delle impostazioni viene visualizzata la finestra di dialogo di pubblicazione.

    ![Scegli cartella](../deployment/media/quickstart-publish-settings-web.png "Scegli cartella")

1. Nel **metodo di pubblicazione** campo, scegliere un metodo, ad esempio **distribuzione Web** oppure **FTP**. Le impostazioni che viene visualizzato accanto corrispondono al metodo di pubblicazione. La funzionalità distribuzione Web semplifica la distribuzione di applicazioni Web e siti Web ai server IIS e deve essere installata come un'applicazione nel server. Usare la [instalace Webové platformy](https://www.microsoft.com/web/downloads/platform.aspx) per installarlo.

1. Configurare le impostazioni necessarie per il metodo di pubblicazione e selezionare **convalida connessione**. Se il server o destinazione sia disponibile e le impostazioni siano corrette, un messaggio che indica la connessione viene convalidato e è pronti a pubblicare.

    ![Convalidare la connessione](../deployment/media/quickstart-publish-web-deploy.png "convalidare la connessione")

1. Selezionare **le impostazioni** per configurare altre impostazioni di distribuzione, ad esempio se si desidera distribuire una configurazione Debug o rilascio e quindi selezionare **salvare**. Se sta eseguendo il debug in modalità remota, è necessaria una configurazione di Debug.

1. Per pubblicare, selezionare **pubblica**. La finestra di Output Mostra i risultati e lo stato della distribuzione.

## <a name="next-steps"></a>Passaggi successivi

In questa Guida introduttiva è stato descritto come usare Visual Studio per creare un profilo di pubblicazione. È anche possibile configurare una pubblicazione profilo tramite l'importazione delle impostazioni di pubblicazione.

> [!div class="nextstepaction"]
> [Importare impostazioni di pubblicazione e distribuzione in IIS](tutorial-import-publish-settings-iis.md)
