---
title: Creare app Web Razor
description: Fornisce informazioni sul supporto Razor nelle app ASP.NET Core in Visual Studio per Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.topic: how-to
ms.openlocfilehash: 008052c9b78f93b84e650329cd7ebaf6200d21f1
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950524"
---
# <a name="create-razor-web-apps"></a>Creare app Web Razor

Questa guida offre un'introduzione alla creazione della prima app Web Razor. Per istruzioni più dettagliate, vedere [Introduzione a Razor Pages in ASP.NET Core](/aspnet/core/razor-pages/index).

Visual Studio per Mac supporta la modifica Razor, tra cui IntelliSense e l'evidenziazione della sintassi nei file con estensione *cshtml*. Una novità di Visual Studio 2019 per Mac 8.3 + è la possibilità di disporre di IntelliSense in grado di riconoscere il contesto all'interno di un file Razor, in modo da ricevere IntelliSense che corrisponde alla lingua attualmente in corso di modifica all'interno di un documento.

![Modifica Razor in Visual Studio per Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Creazione di un nuovo progetto Razor

1. Nella schermata iniziale selezionare **nuovo** per creare un nuovo progetto:

   ![Nuovo progetto di Visual Studio per Mac](media/razor-new.png)
1. Nella finestra di dialogo **nuovo progetto** passare all' **.NET Core**  >  **App**  >  **applicazione Web** app .NET Core e selezionare **Avanti**:

   ![Modello di progetto Razor](media/razor-new-project1.png)
1. Selezionare il Framework di destinazione di .NET Core (si consiglia la versione 2,2 o successiva) e quindi fare clic su **Avanti**. Scegliere un nome per il progetto e aggiungere il supporto Git, se necessario. Selezionare **Crea** per creare il progetto.

   ![Nome del progetto Razor](media/razor-new-project2.png)

   Visual Studio per Mac apre il progetto nella finestra di layout del codice.
1. Eseguire il progetto senza eseguire il debug usando **comando + opzione + F5**.

   Visual Studio avvia [gheppio](/aspnet/core/fundamentals/servers/kestrel), apre un browser a `https://localhost:5001` e visualizza la prima app Web Razor.

   ![App Web Razor in Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Dettagli del progetto

Le app Web Razor includono i componenti seguenti.

### <a name="pages-folder"></a>Cartella Pages

Questa cartella contiene le pagine Web di un progetto, insieme al code-behind per ogni:
   - Un file con * \* estensione cshtml* per il markup HTML e sintassi Razor.
   - Un file con * \* estensione cshtml.cs* per il code-behind C# per la gestione degli eventi di pagina.

I nomi dei file di supporto iniziano con un carattere di sottolineatura. Ad esempio, il file _Layout.cshtml configura gli elementi dell'interfaccia utente comuni a tutte le pagine. Questo file consente di impostare il menu di navigazione nella parte superiore della pagina e le informazioni sul copyright nella parte inferiore della pagina. Per altre informazioni, vedere [Layout in ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Impostazioni per l'avvio

Il *launchSettings.jsnel* file contiene le impostazioni di IIS, l'URL dell'applicazione e altre impostazioni correlate.

### <a name="app-settings"></a>Impostazioni app

Il *appSettings.jsnel* file contiene i dati di configurazione, ad esempio le stringhe di connessione.

Per ulteriori informazioni sulla configurazione, vedere la pagina relativa alla [configurazione nella Guida di ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Cartella wwwroot

Questa cartella contiene file statici, ad esempio file HTML, JavaScript e CSS. Per altre informazioni, vedere [File statici in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Questo file contiene il punto di ingresso per il programma. Per altre informazioni, vedere [Host Web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Questo file contiene il codice che configura il comportamento dell'app, ad esempio se l'app richiede il consenso per i cookie. Per altre informazioni, vedere [Avvio delle app in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Vedere anche

Per una guida più completa alla creazione di app Web Razor, vedere [Introduzione a Razor Pages in ASP.NET Core](/aspnet/core/razor-pages/index).
