---
title: Usare Visual Studio per creare un'app Web ASP.NET Core in C#
description: Informazioni dettagliate su come creare un'app web ASP.NET Core in Visual Studio con C#.
ms.custom: mvc
ms.date: 07/20/2018
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
ms.openlocfilehash: a39c042b4a4badd46f7650fe0f2530527c5d537d
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232194"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Web ASP.NET Core

In questa introduzione di 5-10 minuti che spiega come usare Visual Studio viene creata un'app "Hello World" semplice tramite un modello di progetto ASP.NET e il linguaggio di programmazione C#.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa, creare un progetto dell'applicazione Web ASP:NET Core. Il tipo di progetto include fin dall'inizio tutti i file di modello necessari per creare un'app Web.

1. Aprire Visual Studio 2017.

1. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **Visual C#** e scegliere **.NET Core**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**. Denominare il file `HelloWorld` e scegliere **OK**.

   ![Creare un progetto dell'applicazione Web ASP.NET Core per C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro.
   >![Aprire il programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../ide/media/open-visual-studio-installer.png)
   >
   > Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.
   >
   > ![Carico di lavoro ASP.NET nel programma di installazione di Visual Studio](../ide/media/quickstart-aspnet-workload.png)
   >
   >(Potrebbe essere necessario chiudere Visual Studio prima di continuare l'installazione del nuovo carico di lavoro.)

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** verificare che **ASP.NET Core 2.0** venga visualizzato nel menu a discesa in alto. Scegliere quindi **Applicazione Web** e **OK**.

   ![Finestra di dialogo Nuova applicazione Web ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

Dopo pochi istanti, Visual Studio apre il file di progetto.

## <a name="create-the-application"></a>Creare l'applicazione

1. In **Esplora soluzioni** espandere la cartella **Pagine** e quindi scegliere **About.cshtml**.

   ![Scegliere il file About.cshtml in Esplora soluzioni](../ide/media/csharp-aspnet-about-page-html-file.png)

   Questo file corrisponde a una pagina denominata **Informazioni su** nell'app Web.

   ![Pagina di informazioni nell'app Web](../ide/media/csharp-aspnet-about-page.png)

   Nell'editor viene visualizzato il codice HTML per l'area delle "informazioni aggiuntive" della pagina **Informazioni su**.

   ![Codice HTML per l'area delle informazioni aggiuntive nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Modificare il testo "informazioni aggiuntive" in "**Hello World!**".

   ![Modifica del codice HTML predefinito per l'area delle informazioni aggiuntive nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. In **Esplora soluzioni** espandere **About.cshtml** e quindi scegliere **About.cshtml**. (Questo file corrisponde anche alla pagina **Informazioni su** nell'app Web.)

   ![Scegliere il file About.cshtml in Esplora soluzioni](../ide/media/csharp-aspnet-about-page-code-file.png)

   Nell'editor si noterà il codice C# che include il testo per l'area della "descrizione dell'applicazione" della pagina **Informazioni su**.

   ![Codice C# per l'area della descrizione dell'applicazione nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Modificare il testo del messaggio "descrizione dell'applicazione" in "**Qual è il mio messaggio?**".

   ![Modifica del testo del messaggio predefinito per l'area della descrizione dell'applicazione nell'editor di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Premere **CTRL**+**F5** per eseguire l'app e aprirla in un Web browser.

   > [!NOTE]
   > Se viene visualizzato il messaggio di errore **Non è possibile connettersi al server Web 'IIS Express'**, chiudere Visual Studio e quindi aprirlo usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

1. Nella parte superiore della pagina Web scegliere **Informazioni su**.

   ![Selezionare Informazioni su dalla pagina Web](../ide/media/csharp-aspnet-home-page-about.png)

1. Visualizzare il testo aggiornato che è stato aggiunto alla pagina **Informazioni su**.

   ![Visualizzare la pagina Informazioni su aggiornata che include il testo aggiunto](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Chiudere il Web browser.

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE (ambiente di sviluppo integrato) di Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, continuare con le esercitazioni seguenti:

> [!div class="nextstepaction"]
> [Introduzione a C# e ad ASP.NET Core in Visual Studio](tutorial-csharp-aspnet-core.md)
>
> [!div class="nextstepaction"]
> [Introduzione ad ASP.NET Core MVC e Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)

## <a name="see-also"></a>Vedere anche

[Publish your web app to Azure App Service by using Visual Studio](..//deployment/quickstart-deploy-to-azure.md) (Pubblicare l'app Web in Servizio app di Azure con Visual Studio)
