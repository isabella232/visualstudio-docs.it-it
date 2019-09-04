---
title: Razor
description: Informazioni sul supporto Razor in app ASP.NET Core in Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: a66a31d2c63fcb0e2adc4554c49a76c727f9a288
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107902"
---
# <a name="razor"></a>Razor

Visual Studio per Mac supporta la modifica Razor, tra cui IntelliSense e l'evidenziazione della sintassi nei file con estensione *cshtml*.

![Modifica Razor in Visual Studio per Mac](media/razor-editor.png)

Questa guida fornisce un'introduzione alla creazione della prima app Web Razor. Per una guida più dettagliata, vedere [Razor Pages nella documentazione di .NET Core](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Creazione di un nuovo progetto Razor

* Nella schermata iniziale selezionare **Nuovo** per creare un nuovo progetto:

![Nuovo progetto di Visual Studio per Mac](media/razor-new.png)

* Nella finestra di dialogo Nuovo progetto, passare a **.NET Core** > **App** > **Applicazione Web** e selezionare il pulsante **Avanti**:

![Modello di progetto Razor](media/razor-new-project1.png)

* Selezionare il framework di destinazione di .NET Core necessario (si consiglia la versione 2.2 o successiva) e selezionare **Avanti**.  Scegliere un nome per il progetto e, se necessario, aggiungere il supporto di Git. Selezionare **Crea** per creare il progetto.

![Nome del progetto Razor](media/razor-new-project2.png)

Visual Studio per Mac aprirà il progetto nel layout del codice.

* Eseguire il progetto senza il debug con **Comando-Opzione-F5**.

Visual Studio avvierà [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) e un browser all'indirizzo `https://localhost:5001` e visualizzerà la prima app Web Razor:

![App Web Razor in Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Dettagli del progetto

Le app Web Razor sono generalmente costituite dai componenti seguenti:

### <a name="pages-folder"></a>Cartella Pages

La cartella Pages all'interno del progetto è la posizione in cui si trovano le pagine Web, oltre al code-behind per ognuna:
* Un file con estensione *cshtml* per il markup HTML e la sintassi Razor.
* Un file con estensione *cshtml.cs* per il code-behind C# per la gestione degli eventi della pagina.

I nomi dei file di supporto iniziano con un carattere di sottolineatura. Ad esempio, il file _Layout.cshtml configura gli elementi dell'interfaccia utente comuni a tutte le pagine. Questo file imposta il menu di navigazione nella parte superiore della pagina e le informazioni sul copyright in fondo alla pagina. Per altre informazioni, vedere [Layout in ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Impostazioni di avvio

Il file *launchSettings.json* contiene le impostazioni di IIS, l'URL dell'applicazione e altre impostazioni correlate.

### <a name="app-settings"></a>Impostazioni app

Il file *appSettings.json* contiene i dati di configurazione, ad esempio le stringhe di connessione.

Per altre informazioni sulla configurazione, vedere la [guida alla configurazione in ASP.NET](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Cartella wwwroot

Contiene i file statici, ad esempio i file HTML, i file JavaScript e i file CSS. Per altre informazioni, vedere [File statici in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Contiene il punto di ingresso per il programma. Per altre informazioni, vedere [Host Web ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Contiene codice che configura il comportamento dell'app, ad esempio se richiede il consenso per i cookie. Per altre informazioni, vedere [Avvio delle app in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Vedere anche

Per una guida più completa sulla creazione di app Web Razor, vedere [Introduzione a Razor Pages in ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
