---
title: Crea app Web Blazer
description: Fornisce informazioni sul supporto di Blazer nelle app ASP.NET Core in Visual Studio per Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: 978e3676d587bcd54a8e9d0b8b81f5d6c52a92bc
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180279"
---
# <a name="create-blazor-web-apps"></a>Crea app Web Blazer

Questa guida offre un'introduzione alla creazione della prima app Web Blazer. Per istruzioni più dettagliate, vedere [Introduzione a ASP.NET Core Blazer](/aspnet/core/blazor/index).

ASP.NET Core Blazer supporta due diverse opzioni di hosting. Webassembly Blazer server e blazer. Visual Studio per Mac supporta entrambi i modelli di hosting. Visual Studio per Mac 8.4 + supporta il server blazer e Visual Studio per Mac 8.6 + supporta entrambi. Per ulteriori informazioni sui modelli di hosting blazer, vedere la pagina relativa ai [modelli di hosting di ASP.NET Core Blazer ](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). Il supporto per il debug di progetti webassembly Blazer in Visual Studio per Mac verrà rilasciato dopo 8,6.

Che cos'è Blazer? Blazer è un Framework per la creazione di un'interfaccia utente Web interattiva sul lato client con .NET, che offre i vantaggi seguenti agli sviluppatori Web:

* scrivere codice in C# invece che in JavaScript.
* Permette di sfruttare l'ecosistema .NET esistente di librerie .NET.
* Permette di condividere la logica dell'app tra server e client.
* Trarre vantaggio da. Prestazioni, affidabilità e sicurezza di NET.
* È sempre più produttivo con Visual Studio su PC, Linux e macOS.
* basato su un set comune di linguaggi, framework e strumenti che sono stabili, ricchi di funzionalità e facili da usare.

## <a name="creating-a-new-blazor-server-project"></a>Creazione di un nuovo progetto server Blazer

1. Nella **finestra Start**selezionare **nuovo** per creare un nuovo progetto:

   ![Visual Studio per Mac finestra di avvio con la nuova selezione evidenziata](media/blazor-new-project.png)
1. Nella finestra di dialogo **nuovo progetto** selezionare app server di **.NET Core** > **app** > **Blaze** e selezionare **Avanti**: ![ scegliere un modello per la finestra di dialogo nuovo progetto con il modello di app del server Blazer selezionato](media/blazor-project-template.png)

1. Selezionare .NET Core 3,1 come Framework di destinazione, quindi fare clic su **Avanti**. 
   ![Configurare la finestra di dialogo nuova app del server Blazer visualizzata con il Framework di destinazione selezionato per .NET Core 3,1](media/blazor-select-target-framework.png)

1. Scegliere un nome per il progetto e aggiungere il supporto Git, se lo si desidera. Selezionare **Crea** per creare il progetto.
   ![BConfigurare la finestra di dialogo nuova app Server Blazer visualizzata quando si immette il nome del progetto](media/blazor-name-project.png)

   Visual Studio per Mac apre il progetto nella finestra di layout del codice.
1. Selezionare **Esegui**  >  **Avvia senza eseguire debug** per eseguire l'app.

   Visual Studio avvia [gheppio](/aspnet/core/fundamentals/servers/kestrel), apre un browser a `https://localhost:5001` e visualizza l'app Web Blazer.

   ![App Web Blazer in Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Supporto di Blazer in Visual Studio per Mac

Visual Studio per Mac (a partire dalla versione 8,4) include nuove funzionalità che consentono di creare nuovi progetti server blazer. Fornisce inoltre il supporto standard che ci si aspetta, ad esempio la compilazione, l'esecuzione e il debug di progetti blazer. In Visual Studio per Mac 8,6 è stato aggiunto il supporto per la creazione, la compilazione e l'esecuzione di progetti webassembly blazer.

Nella procedura dettagliata precedente è stato illustrato come il modello di progetto di app del server Blazer consente di creare un nuovo progetto di app Server blazer. Verranno ora esaminate alcune delle funzionalità aggiuntive di Visual Studio per Mac per supportare lo sviluppo di progetti blazer.

### <a name="editor-support-for-razor-files"></a>Supporto dell'editor per file con *estensione Razor*
Visual Studio per Mac include il supporto per la modifica dei file con estensione Razor, la maggior parte dei file che verranno usati durante la creazione di applicazioni blazer. La versione Windows e Mac dell'IDE condividono lo stesso editor per i file Razor. Verranno visualizzati il supporto completo per la colorazione e il completamento per i file Razor, inclusi i completamenti per i componenti Razor dichiarati nel progetto.

![Finestra dell'editor Visual Studio per Mac che mostra IntelliSense per blazer](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Pubblicazione di applicazioni Blazer nel servizio app Azure
È anche possibile pubblicare applicazioni Blazer direttamente nel servizio app Azure. Se non si dispone di un account Azure per eseguire l'app Blazer in Azure, è sempre possibile [iscriversi per ottenere un account gratuito](https://azure.microsoft.com/free) , che include anche 12 mesi di servizi diffusi gratuiti, $200 crediti di Azure gratuiti e oltre 25 servizi sempre gratuiti.

![Visual Studio per Mac che illustra l'esperienza di pubblicazione di Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Dettagli del progetto

Per impostazione predefinita, le app Web Blazer includono alcune directory e file. Come si inizia, di seguito sono riportate le informazioni principali che è necessario conoscere:

### <a name="pages-folder"></a>Cartella Pages

Questa cartella contiene le pagine Web di un progetto che usano l'estensione di file *Razor* .

### <a name="shared-folder"></a>Cartella condivisa

Questa cartella include i componenti condivisi, usando anche l'estensione *Razor* . Si noterà che questo include *MainLayout. Razor*, che viene usato per definire il layout comune nell'applicazione. Include anche il componente Shared *NavMenu. Razor* , che viene usato in tutte le pagine. Se si stanno creando componenti riutilizzabili, questi verranno inseriti nella cartella **condivisa** .

### <a name="app-settings"></a>Impostazioni dell'app

Il file *appSettings. JSON* contiene i dati di configurazione, ad esempio le stringhe di connessione.

Per ulteriori informazioni sulla configurazione, vedere la pagina relativa alla [configurazione nella Guida di ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Cartella wwwroot

Questa cartella contiene file statici, ad esempio file HTML, JavaScript e CSS. Per altre informazioni, vedere [File statici in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Questo file contiene il punto di ingresso per il programma. Per altre informazioni, vedere [Host Web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Questo file contiene il codice che configura il comportamento dell'app, ad esempio se l'app richiede il consenso per i cookie. Per altre informazioni, vedere [Avvio delle app in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Summary
In questa esercitazione è stato illustrato come creare una nuova app Server Blazer in Visual Studio per Mac e sono state apprese alcune delle funzionalità offerte da Visual Studio per Mac per facilitare la creazione di applicazioni blazer.

## <a name="see-also"></a>Vedere anche

Per una guida più completa alla creazione di app Web Blazer, vedere [Introduzione a ASP.NET Core Blazer](/aspnet/core/blazor/index).
