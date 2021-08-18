---
title: Creare Blazor app Web
description: Fornisce informazioni sul Blazor supporto per ASP.NET Core app in Visual Studio per Mac.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: c46346299a7b0d7e7ee7244c200e05c6972843658c44ad43d221eb47980a4581
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349868"
---
# <a name="create-blazor-web-apps"></a>Creare Blazor app Web

Questa guida offre un'introduzione alla creazione della prima Blazor app Web. Per indicazioni più dettagliate, vedere [Introduzione Blazor a ASP.NET Core ](/aspnet/core/blazor/index).

BlazorASP.NET Core supporta due diverse opzioni di hosting: Blazor WebAssembly(WASM) o Blazor Server. Visual Studio per Mac supporta entrambi i modelli di hosting. Visual Studio per Mac 8.4+ supporta server e Blazor Visual Studio per Mac 8.6+ supporta entrambi. Per altre informazioni sui modelli Blazor di hosting, vedere [ASP.NET Core di Blazor hosting. ](/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1&preserve-view=true) Il supporto per il debug di progetti in Visual Studio per Mac è disponibile nella versione di anteprima della versione Blazor WebAssembly 8.8 (disponibile tramite il canale di aggiornamento Anteprima nel menu Visual Studio > **Verifica** disponibilità aggiornamenti).

Che cos'è Blazor? Blazor è un framework per la creazione di un'interfaccia utente Web interattiva sul lato client con .NET, che offre i vantaggi seguenti agli sviluppatori Web:

* scrivere codice in C# invece che in JavaScript.
* Permette di sfruttare l'ecosistema .NET esistente di librerie .NET.
* Permette di condividere la logica dell'app tra server e client.
* È possibile trarre vantaggio da . Prestazioni, affidabilità e sicurezza di NET.
* Rimanere produttivi con Visual Studio in PC, Linux e macOS.
* basato su un set comune di linguaggi, framework e strumenti che sono stabili, ricchi di funzionalità e facili da usare.

## <a name="create-a-new-blazor-webassembly-project"></a>Creare un nuovo Blazor WebAssembly progetto
1. Nella finestra **iniziale** selezionare **Nuovo per** creare un nuovo progetto:

   ![Visual Studio per Mac Finestra iniziale con nuova selezione evidenziata](media/blazor-new-project.png)

1. Nella finestra di dialogo New **Project** (Nuovo Project) selezionare .NET Core App (App **.NET Core)** e selezionare Next (Avanti): screenshot della finestra di dialogo New Project (Nuovo Project) con >  > **Blazor WebAssembly**  ![ Blazor WebAssembly App evidenziata nel riquadro App in ASP.NET Core e il pulsante Avanti selezionato.](media/blazor-wasm-project-template.png)

1. Selezionare .NET Core 3.1 come framework di destinazione, quindi selezionare **Avanti.** 
   ![Configurare la nuova finestra di dialogo Blazor WebAssembly App visualizzata con Framework di destinazione selezionato per .NET Core 3.1](media/blazor-wasm-select-target-framework.png)

1. Scegliere un nome per il progetto e aggiungere il supporto Git, se necessario. Selezionare **Crea** per creare il progetto.
    ![Configurare la nuova finestra di dialogo Blazor WebAssembly App visualizzata durante l'immissione Project nome](media/blazor-wasm-name-project.png)

   Visual Studio per Mac apre il progetto nella finestra Layout codice.

1. Selezionare **Esegui Avvia** senza eseguire  >  **debug** per eseguire l'app.

   Visual Studio avvia [Kestrel,](/aspnet/core/fundamentals/servers/kestrel)apre un browser a `https://localhost:5001` e visualizza Blazor l'app Web.

   ![Blazor app Web in Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-blazor-server-project"></a>Creazione di un nuovo Blazor progetto server

1. Nella finestra **iniziale** selezionare **Nuovo per** creare un nuovo progetto:

   ![Visual Studio per Mac Finestra iniziale con nuova selezione evidenziata](media/blazor-new-project.png)
1. Nella finestra di dialogo New **Project** (Nuovo Project) selezionare .NET Core App Server App (App server app **.NET Core)** e selezionare Next (Avanti): screenshot della finestra di dialogo New Project (Nuovo Project) con >  > **Blazor**  ![ Blazor App server evidenziata nel riquadro App in ASP.NET Core e il pulsante Avanti selezionato.](media/blazor-project-template.png)

1. Selezionare .NET Core 3.1 come framework di destinazione, quindi selezionare **Avanti.** 
   ![Configurare la nuova finestra di dialogo Blazor App server visualizzata con Framework di destinazione selezionato per .NET Core 3.1](media/blazor-select-target-framework.png)

1. Scegliere un nome per il progetto e aggiungere il supporto Git, se necessario. Selezionare **Crea** per creare il progetto.
   ![Configurare la nuova finestra di dialogo Blazor App server visualizzata durante l'immissione Project nome](media/blazor-name-project.png)

   Visual Studio per Mac apre il progetto nella finestra Layout codice.
1. Selezionare **Esegui Avvia** senza eseguire  >  **debug** per eseguire l'app.

   Visual Studio avvia [Kestrel,](/aspnet/core/fundamentals/servers/kestrel)apre un browser a `https://localhost:5001` e visualizza Blazor l'app Web.

   ![Blazor app Web in Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>BlazorSupporto in Visual Studio per Mac

Visual Studio per Mac (a partire dalla versione 8.4) include nuove funzionalità che consentono di creare nuovi Blazor progetti server. Fornisce anche il supporto standard che ci si aspetterebbe, ad esempio la compilazione, l'esecuzione e il debug di Blazor progetti. In Visual Studio per Mac stato aggiunto il supporto per la creazione, la compilazione e l'esecuzione di progetti nella Blazor WebAssembly versione 8.6.

Nella procedura dettagliata precedente è stato illustrato come il modello di progetto App server consente Blazor di creare un nuovo progetto app server o Blazor Blazor WebAssembly app. Di seguito sono ora disponibili alcune delle funzionalità aggiuntive di Visual Studio per Mac per supportare lo sviluppo Blazor di progetti.

### <a name="editor-support-for-razor-files"></a>Supporto dell'editor per *i file razor*
Visual Studio per Mac include il supporto per la modifica di file razor, la maggior parte dei file che verranno in uso durante la creazione di Blazor applicazioni. Visual Studio per Mac supporto completo per colorazione e completamento per i file razor, inclusi i completamenti per i componenti Razor dichiarati nel progetto.

![Visual Studio per Mac finestra dell'editor che mostra IntelliSense per Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Pubblicazione Blazor di applicazioni in Servizio app di Azure
È anche possibile Blazor pubblicare applicazioni direttamente in Servizio app di Azure. Se non si ha un account Azure per eseguire l'app in Azure, è sempre possibile iscriversi per ottenere un account gratuito qui che include anche 12 mesi di servizi popolari Blazor gratuiti, $ 200 in crediti Azure gratuiti e oltre 25 servizi sempre gratuiti. [](https://azure.microsoft.com/free)

![Visual Studio per Mac'esperienza di pubblicazione di Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomia del progetto

Blazor Le app Web includono alcune directory e alcuni file per impostazione predefinita. Per iniziare, di seguito sono disponibili le principali con cui è necessario avere familiarità:

### <a name="pages-folder"></a>Cartella Pages

Questa cartella contiene le pagine Web di un progetto, che usano un'estensione di file *razor.*

### <a name="shared-folder"></a>Cartella condivisa

Questa cartella include componenti condivisi, che usano anche *l'estensione razor.* Si noti che questo include *MainLayout.razor,* che viene usato per definire il layout comune nell'applicazione. Include anche il componente *NavMenu.razor* condiviso, che viene usato in tutte le pagine. Se si creano componenti riutilizzabili, questi verranno nella **cartella** Condiviso.

### <a name="app-settings"></a>Impostazioni app

La *appSettings.jsnel* file contiene dati di configurazione, ad esempio stringhe di connessione.

Per altre informazioni sulla configurazione, vedere [configuration in ASP.NET guide](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Cartella wwwroot

Questa cartella contiene file statici, ad esempio file HTML, JavaScript e CSS. Per altre informazioni, vedere [File statici in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Questo file contiene il punto di ingresso per il programma. Per altre informazioni, vedere [Host Web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="blazor-server-app-specific-files"></a>Blazor File specifici dell'app server
#### <a name="app-settings"></a>Impostazioni app

La *appSettings.jsnel* file contiene dati di configurazione, ad esempio stringhe di connessione.

Per altre informazioni sulla configurazione, vedere [configuration in ASP.NET guide](/aspnet/core/fundamentals/configuration/index).

#### <a name="startupcs"></a>Startup.cs

Questo file contiene codice che configura il comportamento dell'app, ad esempio se l'app richiede il consenso per i cookie. Per altre informazioni, vedere [Avvio delle app in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Riepilogo
In questa esercitazione è stato illustrato come creare una nuova app server o un'app in Visual Studio per Mac ed è stata illustrata alcune delle funzionalità offerte da Visual Studio per Mac per facilitare la creazione di Blazor Blazor WebAssembly Blazor applicazioni.

## <a name="see-also"></a>Vedi anche

Per una guida più completa alla creazione Blazor di app Web, vedere [Introduction to ASP.NET Core Blazor ](/aspnet/core/blazor/index).