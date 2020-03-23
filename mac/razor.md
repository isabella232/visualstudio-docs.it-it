---
title: Creare app Web Razor
description: Fornisce informazioni sul supporto Razor nelle app ASP.NET Core in Visual Studio per Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715883"
---
# <a name="create-razor-web-apps"></a>Creare app Web Razor

Questa guida offre un'introduzione alla creazione della prima app Web Razor. Per indicazioni più approfondite, vedere [Introduzione alle pagine Razor in ASP.NET Core](/aspnet/core/razor-pages/index).

Visual Studio per Mac supporta la modifica Razor, tra cui IntelliSense e l'evidenziazione della sintassi nei file con estensione *cshtml*. Una novità di Visual Studio 2019 per Mac 8.3 è la possibilità di avere IntelliSense sensibile al contesto all'interno di un file Razor, in modo da ricevere IntelliSense che corrisponde al linguaggio attualmente in uso all'interno di un documento.

![Modifica Razor in Visual Studio per Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Creazione di un nuovo progetto Razor

1. Nella schermata iniziale, selezionare **Nuovo** per creare un nuovo progetto:

   ![Nuovo progetto di Visual Studio per Mac](media/razor-new.png)
1. Nella finestra di dialogo **Nuovo progetto** passare a**Applicazione Web** applicazioni di **.NET Core** > **App** > e selezionare **Avanti:**

   ![Modello di progetto Razor](media/razor-new-project1.png)
1. Selezionare il framework di destinazione di .NET Core (è consigliabile versione 2.2 o successiva) e quindi selezionare **Avanti**. Scegliere un nome per il progetto e aggiungere il supporto Git, se necessario. Selezionare **Crea** per creare il progetto.

   ![Nome del progetto Razor](media/razor-new-project2.png)

   Visual Studio per Mac apre il progetto nella finestra Layout codice.
1. Eseguire il progetto senza eseguire il debug utilizzando **Comando , Opzione , F5**.

   Visual Studio avvia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), `https://localhost:5001`apre un browser per e visualizza la prima app Web Razor.

   ![App Web Razor in Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Dettagli del progetto

Le app Web Razor includono i componenti seguenti.

### <a name="pages-folder"></a>Cartella Pages

Questa cartella contiene le pagine Web di un progetto, insieme al code-behind per ogni:
   - Un file * \*con estensione cshtml* per il markup HTML e la sintassi Razor.
   - Un file * \*con estensione cshtml.cs* per il code-behind di C, per la gestione degli eventi di pagina.

I nomi dei file di supporto iniziano con un carattere di sottolineatura. Ad esempio, il file _Layout.cshtml configura gli elementi dell'interfaccia utente comuni a tutte le pagine. Questo file imposta il menu di navigazione nella parte superiore della pagina e l'avviso di copyright nella parte inferiore. Per altre informazioni, vedere [Layout in ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Impostazioni di avvio

Il file *launchSettings.json* contiene le impostazioni di IIS, l'URL dell'applicazione e altre impostazioni correlate.

### <a name="app-settings"></a>Impostazioni app

Il file *appSettings.json* contiene dati di configurazione, ad esempio stringhe di connessione.

Per ulteriori informazioni sulla configurazione, vedere la [Guida Configurazione in ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Cartella wwwroot

Questa cartella contiene file statici, ad esempio file HTML, JavaScript e CSS. Per altre informazioni, vedere [File statici in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Questo file contiene il punto di ingresso per il programma. Per altre informazioni, vedere [Host Web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Questo file contiene il codice che configura il comportamento dell'app, ad esempio se l'app richiede il consenso per i cookie. Per altre informazioni, vedere [Avvio delle app in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Vedere anche

Per una guida più completa alla creazione di app Web Razor, vedere [Introduzione alle pagine Razor in ASP.NET Core](/aspnet/core/razor-pages/index).
