---
title: Usare Visual Studio per creare un'app Web ASP.NET Core in C#
description: Informazioni dettagliate su come creare un'app Web Hello World in Visual Studio con C# e ASP.NET Core.
ms.custom: mvc
ms.date: 07/30/2018
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
ms.openlocfilehash: ae4dc5f14db66bee10c8b2e95ea687f71ced2abb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2018
ms.locfileid: "46135605"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Web ASP.NET Core

In questa introduzione di 5-10 minuti che spiega come usare Visual Studio viene creata un'app Web "Hello World" semplice tramite un modello di progetto ASP.NET e il linguaggio di programmazione C#.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa, creare un progetto dell'applicazione Web ASP:NET Core. Ecco come fare.

1. Aprire Visual Studio 2017.

1. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **Visual C#** e scegliere **.NET Core**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**. Denominare il file `HelloWorld` e scegliere **OK**.

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** verificare che **ASP.NET Core 2.0** venga visualizzato nel menu a discesa in alto. Scegliere quindi **Applicazione Web** e **OK**.

  ![Visualizzare il file di immagine animata che illustra come creare un progetto ASP.NET Core C# in Visual Studio](../ide/media/csharp-aspnet-animated-create-project.gif)

  Dopo pochi istanti, Visual Studio apre il file di progetto.

   > [!NOTE]
   > Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro.
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

1. In **Esplora soluzioni** espandere la cartella **Pagine** e quindi scegliere **About.cshtml**.

   Questo file corrisponde a una pagina denominata **Informazioni su** nell'app Web.

   ![Pagina di informazioni nell'app Web](../ide/media/csharp-aspnet-about-page.png)

1. Modificare il testo "informazioni aggiuntive" in "**Hello World!**".

1. In **Esplora soluzioni** espandere **About.cshtml** e quindi scegliere **About.cshtml**.

1. Modificare il testo del messaggio "descrizione dell'applicazione" in "**Qual è il mio messaggio?**".

1. Scegliere **IIS Express** o premere **CTRL**+**F5** per eseguire l'app e aprirla in un Web browser.

  ![Visualizzare il file di immagine animata che illustra come creare ed eseguire un'app Web ASP.NET Core C# in Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Se viene visualizzato il messaggio di errore **Non è possibile connettersi al server Web 'IIS Express'**, chiudere Visual Studio e quindi aprirlo usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

1. Verificare che la pagina **Informazioni su** includa il testo aggiornato.

1. Chiudere il Web browser.

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE (ambiente di sviluppo integrato) di Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Introduzione a C# e ad ASP.NET Core in Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Vedere anche

[Publish your web app to Azure App Service by using Visual Studio](..//deployment/quickstart-deploy-to-azure.md) (Pubblicare l'app Web in Servizio app di Azure con Visual Studio)
