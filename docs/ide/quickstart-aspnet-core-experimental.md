---
title: Usare Visual Studio per creare un'app Web ASP.NET Core in C#
description: Informazioni dettagliate su come creare un'app Web Hello World in Visual Studio con C# e ASP.NET Core.
ms.custom: mvc
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 8487d09c75ff8880fd6c3fe4af59fa2b494b315e
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684967"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Web ASP.NET Core

In questa introduzione di 5-10 minuti che spiega come usare Visual Studio viene creata un'app Web "Hello World" semplice tramite un modello di progetto ASP.NET e il linguaggio di programmazione C#.

## <a name="before-you-begin"></a>Prima di iniziare

### <a name="install-visual-studio"></a>Installare Visual Studio

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

### <a name="update-visual-studio"></a>Aggiornare Visual Studio

Se Visual Studio è già installato, verificare che si stia usando la versione più recente. Per altre informazioni su come aggiornare l'installazione, vedere la pagina [Aggiornare Visual Studio 2017 alla versione più recente](../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Scegliere il tema (facoltativo)

Questa esercitazione introduttiva include screenshot in cui viene usato il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](quickstart-personalize-the-ide.md).

## <a name="create-a-project"></a>Creare un progetto

Per iniziare, creare un progetto di applicazione Web ASP.NET Core. Ecco come fare.

1. Aprire Visual Studio 2017.

1. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **Visual C#** e scegliere **.NET Core**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**. Denominare il file `HelloWorld` e scegliere **OK**.

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.0** o versione successiva nel menu a discesa in alto e quindi selezionare **Applicazione Web**.

   > [!NOTE]
   > Se **ASP.NET Core 2.0** o versione successiva non è presente nel menu a discesa in alto, verificare che si stia usando la versione più recente di Visual Studio. Per altre informazioni su come aggiornare l'installazione, vedere la pagina [Aggiornare Visual Studio 2017 alla versione più recente](../install/update-visual-studio.md).

   ![Visualizzare il file di immagine animata che illustra come creare un progetto ASP.NET Core C# in Visual Studio](../ide/media/csharp-aspnet-animated-create-project.gif)

   Dopo pochi istanti, Visual Studio apre il file di progetto.

   > [!NOTE]
   > Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro. A seconda delle impostazioni di visualizzazione, potrebbe essere necessario scorrere la pagina per visualizzarla.
   >
   > ![Aprire Programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../ide/media/open-visual-studio-installer.png)
   >
   > Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.
   >
   > ![Carico di lavoro ASP.NET nel programma di installazione di Visual Studio](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Potrebbe essere necessario chiudere Visual Studio prima di continuare l'installazione del nuovo carico di lavoro.)

## <a name="create-and-run-the-app"></a>Creare ed eseguire l'app

In seguito si procederà alla creazione e all'esecuzione dell'app Web "Hello World". Ecco come fare.

1. In Visual Studio, in **Esplora soluzioni** espandere la cartella **Pagine** e quindi scegliere **About.cshtml**.

   ![Scegliere il file About.cshtml in Esplora soluzioni](../ide/media/csharp-aspnet-about-page-html-file.png)

   Questo file corrisponde a una pagina denominata **Informazioni su** nell'app Web, eseguita in un Web browser.

   ![Pagina di informazioni nell'app Web](../ide/media/csharp-aspnet-about-page.png)

1. Nell'editor del codice di Visual Studio modificare il testo "informazioni aggiuntive" in "**Hello World!**".

1. In **Esplora soluzioni** espandere **About.cshtml** e quindi scegliere **About.cshtml**.

1. Modificare il testo del messaggio "descrizione dell'applicazione" in "**Qual è il mio messaggio?**".

1. Scegliere **IIS Express** o premere **CTRL**+**F5** per eseguire l'app e aprirla in un Web browser.

   ![Visualizzare il file di immagine animata che illustra come creare ed eseguire un'app Web ASP.NET Core C# in Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Se viene visualizzato il messaggio di errore **Impossibile connettersi al server Web "IIS Express"** o un messaggio di errore in cui viene indicato un certificato SSL, chiudere Visual Studio. Aprire quindi Visual Studio usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

1. Nel Web browser verificare che la pagina **Informazioni su** includa il testo aggiornato.

1. Chiudere il Web browser.

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE (ambiente di sviluppo integrato) di Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Introduzione a C# e ad ASP.NET Core in Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Vedere anche

[Publish your web app to Azure App Service by using Visual Studio](../deployment/quickstart-deploy-to-azure.md) (Pubblicare l'app Web in Servizio app di Azure con Visual Studio)
