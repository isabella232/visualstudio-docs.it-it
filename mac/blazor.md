---
title: Creare app Web Blazor
description: Fornisce informazioni sul supporto Blazor nelle app ASP.NET Core in Visual Studio per Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737586"
---
# <a name="create-blazor-web-apps"></a>Creare app Web Blazor

Questa guida offre un'introduzione alla creazione della prima app Web Blazor. Per indicazioni più approfondite, vedere [Introduzione a ASP.NET Core Blazor](/aspnet/core/blazor/index).

Visual Studio per Mac (a partire dalla versione 8.4) include il supporto per lo sviluppo e la pubblicazione di applicazioni ASP.NET Core Blazor Server. Blazor è un framework per la creazione di un'interfaccia utente Web interattiva sul lato client con .NET, che offre i seguenti vantaggi agli sviluppatori Web:

* scrivere codice in C# invece che in JavaScript.
* Permette di sfruttare l'ecosistema .NET esistente di librerie .NET.
* Permette di condividere la logica dell'app tra server e client.
* Approfitta di . Prestazioni, affidabilità e sicurezza di NET.
* Rimani produttivo con Visual Studio su PC, Linux e macOS.
* basato su un set comune di linguaggi, framework e strumenti che sono stabili, ricchi di funzionalità e facili da usare.

## <a name="creating-a-new-blazor-project"></a>Creazione di un nuovo progetto Blazor

1. Nella **finestra di avvio**, selezionare **Nuovo** per creare un nuovo progetto:

   ![Finestra iniziale di Visual Studio per Mac con l'opzione Nuova selezione evidenziata](media/blazor-new-project.png)
1. Nella finestra di dialogo **Nuovo progetto** selezionare App per server ![ **.NET Core** > **App** > **Blazor** e scegliere **Avanti:** scegliere un modello per la finestra di dialogo del nuovo progetto con il modello Blazor Server App selezionato](media/blazor-project-template.png)

1. Selezionare .NET Core 3.1 come framework di destinazione, quindi scegliere **Avanti**. 
   ![Configurare la nuova finestra di dialogo Blazor Server App visualizzata con Framework di destinazione selezionato per .NET Core 3.1](media/blazor-select-target-framework.png)

1. Scegliere un nome per il progetto e aggiungere il supporto Git, se lo si desidera. Selezionare **Crea** per creare il progetto.
   ![BConfigurare la nuova finestra di dialogo Blazor Server App visualizzata durante l'immissione di Nome progetto](media/blazor-name-project.png)

   Visual Studio per Mac apre il progetto nella finestra Layout codice.
1. Selezionare **Esegui** > **di avvio senza debuggingo** per eseguire l'app.

   Visual Studio avvia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), `https://localhost:5001`apre un browser per e visualizza l'app Web Blazor.

   ![Blazor web app in Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Supporto Blazor in Visual Studio per Mac

Visual Studio per Mac (a partire dalla versione 8.4) include nuove funzionalità che consentono di creare nuovi progetti server Blazor. Inoltre, fornisce il supporto standard che ci si aspetterebbe, ad esempio la compilazione, l'esecuzione e il debug di progetti Blazor. 

Nella procedura dettagliata precedente è stato illustrato come il modello di progetto Blazor Server App consente di creare un nuovo progetto Blazor Server App. Diamo un'occhiata ad alcune delle funzionalità aggiuntive in Visual Studio per Mac per supportare lo sviluppo di progetti server Blazor.

### <a name="editor-support-for-razor-files"></a>Supporto dell'editor per i file *.razor*
Visual Studio per Mac include il supporto per la modifica dei file con estensione razor: la maggior parte dei file che verranno utilizzati durante la creazione di applicazioni Blazor. La versione per Windows e Mac dell'IDE condivide lo stesso editor per i file .razor. Vedrai il supporto completo della colorazione e del completamento per i file .razor, inclusi i completamenti per i componenti Razor dichiarati nel progetto.

![Finestra dell'editor di Visual Studio per Mac che mostra Intellisense per Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Pubblicazione di applicazioni Blazor nel servizio app di AzurePublishing Blazor applications to Azure App Service
È anche possibile pubblicare le applicazioni Blazor direttamente nel servizio app di Azure.You can also publish Blazor applications directly to Azure App Service. Se non si dispone di un account Azure per eseguire l'app Blazor in Azure, è sempre possibile [iscriversi gratuitamente qui](https://azure.microsoft.com/free) che include anche 12 mesi di servizi popolari gratuiti, 200 crediti Azure gratuiti e oltre 25 servizi sempre gratuiti.

![Visual Studio per Mac con esperienza di pubblicazione di Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Dettagli del progetto

Blazor applicazioni web includono alcune directory e file per impostazione predefinita. Come si sta iniziando, qui ci sono i principali che avrete bisogno di avere familiarità con:

### <a name="pages-folder"></a>Cartella Pages

Questa cartella contiene le pagine Web di un progetto, che utilizzano l'estensione del file *.razor.*

### <a name="shared-folder"></a>Cartella condivisa

Questa cartella include componenti condivisi, anche utilizzando l'estensione *.razor.* Si noterà che questo include *MainLayout.razor*, che viene utilizzato per definire il layout comune in tutta l'applicazione. Include anche il componente *NavMenu.razor* condiviso, che viene utilizzato in tutte le pagine. Se stai creando componenti riutilizzabili, andranno nella cartella **Condivisa.**

### <a name="app-settings"></a>Impostazioni app

Il file *appSettings.json* contiene dati di configurazione, ad esempio stringhe di connessione.

Per ulteriori informazioni sulla configurazione, vedere la [Guida Configurazione in ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Cartella wwwroot

Questa cartella contiene file statici, ad esempio file HTML, JavaScript e CSS. Per altre informazioni, vedere [File statici in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Questo file contiene il punto di ingresso per il programma. Per altre informazioni, vedere [Host Web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Questo file contiene il codice che configura il comportamento dell'app, ad esempio se l'app richiede il consenso per i cookie. Per altre informazioni, vedere [Avvio delle app in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Summary
In questa esercitazione è stato illustrato come creare una nuova app Blazor Server in Visual Studio per Mac e sono state fornite informazioni su alcune delle funzionalità offerte da Visual Studio per Mac per creare applicazioni Blazor.

## <a name="see-also"></a>Vedere anche

Per una guida più completa alla creazione di app Web Blazor, vedere [Introduzione a ASP.NET Core Blazor](/aspnet/core/blazor/index).
