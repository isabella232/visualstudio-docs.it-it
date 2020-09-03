---
title: Presentazione di Visual Studio per Mac
description: Visual Studio per Mac offre un ambiente di sviluppo integrato per creare applicazioni .NET in macOS, inclusi siti Web ASP.NET Core e progetti Xamarin per iOS, Android, Mac e Xamarin.Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 3d25fced1e9c9dd6431f4056b5b561f476eecb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984978"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Presentazione di Visual Studio 2017 per Mac

> [!NOTE]
> Visual Studio 2019 per Mac è [ora disponibile](installation.md).

Visual Studio per Mac è un _ambiente di sviluppo integrato_ .NET nel Mac che può essere usato per modificare, eseguire il debug, compilare il codice e quindi pubblicare un'app. Oltre alle funzionalità previste, ad esempio un editor e un debugger standard, Visual Studio per Mac include compilatori, strumenti di completamento del codice, finestre di progettazione con interfaccia grafica e controllo del codice sorgente che semplificano il processo di sviluppo del software.

Visual Studio per Mac supporta molti degli stessi tipi di file della controparte Windows, ad esempio i file con estensione `.csproj`, `.fsproj` o `.sln`, nonché funzionalità quali EditorConfig, rendendo possibile l'uso dell'IDE più adatto alle proprie esigenze.
La creazione, l'apertura e lo sviluppo di app saranno operazioni familiari per chi in precedenza ha usato Visual Studio in Windows. Visual Studio per Mac usa inoltre molti degli strumenti avanzati che rendono la controparte Windows un IDE estremamente potente. La piattaforma di compilazione Roslyn viene usata per il refactoring e per IntelliSense. Il sistema del progetto e il motore di compilazione usano MSBuild e l'editor standard supporta i bundle TextMate. Vengono usati gli stessi motori di debugger per le app Xamarin e .NET Core e le stesse finestre di progettazione per Xamarin.iOS e Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Attività possibili in Visual Studio per Mac

Visual Studio per Mac supporta i tipi di sviluppo seguenti:

- Applicazioni Web ASP.NET Core con C#, F# e supporto per Razor Pages, JavaScript e TypeScript
- Applicazioni console .NET Core con C# o F#
- Giochi Unity multipiattaforma e applicazioni con C#
- Applicazioni Android, iOS, tvOS e watchOS in Xamarin con C# o F# e XAML
- Applicazioni desktop Cocoa in C# o F#

L'articolo illustra varie sezioni di Visual Studio per Mac e presenta alcune delle funzionalità che fanno di questo prodotto un potente strumento per la creazione di queste applicazioni.

## <a name="ide-tour"></a>Presentazione dell'IDE

Visual Studio per Mac è organizzato in sezioni diverse per la gestione di impostazioni e file delle applicazioni, la creazione di codice delle applicazioni e il debug.

## <a name="welcome-screen"></a>Schermata iniziale

All'avvio, Visual Studio per Mac visualizza una *schermata iniziale*:

![Schermata iniziale](media/ide-tour-image1.png)

La schermata iniziale contiene le sezioni seguenti:

- **Barra degli strumenti** - Consente l'accesso rapido alla barra di ricerca. Quando viene caricata una soluzione, la barra degli strumenti viene usata per definire le configurazioni dell'app, per eseguire il debug e per visualizzare gli errori.
- **Guida introduttiva** - Consente l'accesso rapido ad argomenti utili per gli sviluppatori, per iniziare a usare Visual Studio per Mac.
- **Soluzioni recenti** - Consente l'accesso rapido alle soluzioni aperte di recente, oltre che fornire comodi pulsanti per aprire o creare progetti.
- **Novità per gli sviluppatori** - Newsfeed che offre aggiornamenti sulle ultime novità per gli sviluppatori Microsoft.

## <a name="solutions-and-projects"></a>Soluzioni e progetti

L'immagine seguente mostra Visual Studio per Mac con un'applicazione caricata:

![Visual Studio per Mac con un'applicazione caricata](media/ide-tour-image17.png)

Le sezioni seguenti forniscono una panoramica delle principali aree di Visual Studio per Mac.

## <a name="solution-pad"></a>Riquadro della soluzione

Il riquadro della soluzione organizza i progetti in una soluzione:

![Progetti organizzati nel riquadro della soluzione](media/ide-tour-image18.png)

In questa posizione i file per il codice sorgente, le risorse, l'interfaccia utente e le dipendenze vengono organizzati in progetti specifici della piattaforma.

Per altre informazioni sull'uso di progetti e soluzioni in Visual Studio per Mac, vedere l'articolo [Progetti e soluzioni](/visualstudio/mac/projects-and-solutions).

## <a name="assembly-references"></a>Riferimenti dell'assembly

I riferimenti ad assembly per ogni progetto sono disponibili nella cartella Riferimenti:

![Cartella Riferimenti nel riquadro della soluzione](media/ide-tour-image19.png)

È possibile aggiungere altri riferimenti usando la finestra di dialogo **Modifica riferimenti**, visualizzata facendo doppio clic sulla cartella Riferimenti oppure scegliendo **Modifica riferimenti** tra le azioni del menu di scelta rapida:

![Finestra di dialogo Modifica riferimenti](media/ide-tour-image20.png)

Per altre informazioni sull'uso dei riferimenti in Visual Studio per Mac, vedere l'articolo [Gestione dei riferimenti in un progetto](/visualstudio/mac/managing-references-in-a-project).

## <a name="dependencies--packages"></a>Dipendenze/pacchetti

Tutte le dipendenze esterne usate nell'app vengono archiviate nella cartella Dipendenze o Pacchetti, a seconda che si stia lavorando a un progetto .NET Core o Xamarin.iOS/Xamarin.Android. In genere vengono fornite sotto forma di pacchetto NuGet.

NuGet è il più diffuso strumento di gestione pacchetti per lo sviluppo .NET. Con il supporto di NuGet di Visual Studio è possibile cercare e aggiungere facilmente pacchetti al progetto dell'applicazione.

Per aggiungere una dipendenza all'applicazione, fare clic con il pulsante destro del mouse sulla cartella Dipendenze/Pacchetti e scegliere **Aggiungi pacchetti**:

![Aggiungere un pacchetto NuGet](media/ide-tour-image21.png)

Le informazioni sull'uso di un pacchetto NuGet in un'applicazione sono disponibili nell'articolo [Inserimento di un pacchetto NuGet nel progetto](/visualstudio/mac/nuget-walkthrough).

## <a name="refactoring"></a>Refactoring

Visual Studio per Mac fornisce due metodi utili per il refactoring del codice: azioni di contesto e analisi dell'origine. Per altre informazioni, vedere l'articolo [Refactoring](/visualstudio/mac/refactoring).

## <a name="debugging"></a>Debug

Visual Studio per Mac ha un debugger nativo che offre supporto per il debug per applicazioni Xamarin.iOS, Xamarin.Mac e Xamarin.Android. Visual Studio per Mac usa Mono Soft Debugger, un debugger implementato nel runtime di Mono, per consentire all'IDE di eseguire il debug di codice gestito in tutte le piattaforme. Per altre informazioni sul debug, vedere l'articolo [Debug](/visualstudio/mac/debugging).

Il debugger contiene visualizzatori avanzati per tipi speciali come stringhe, colori, URL, oltre che dimensioni, coordinate e curve di Bézier.

Per altre informazioni sulle visualizzazioni dei dati del debugger, vedere l'articolo [Visualizzazioni dei dati](/visualstudio/mac/data-visualizations).

## <a name="version-control"></a>Controllo della versione

Visual Studio per Mac si integra con sistemi di controllo del codice sorgente Subversion e Git. I progetti sottoposti a controllo del codice sorgente sono contrassegnati con un ramo accanto al nome della soluzione:

![Nome del ramo per indicare un progetto sottoposto a controllo del codice sorgente](media/ide-tour-image22.png)

I file con modifiche non sottoposte a commit presentano un'annotazione nelle relative icone nel riquadro della soluzione, come illustrato nell'immagine seguente:

![File con modifiche non sottoposte a commit nel riquadro della soluzione](media/ide-tour-image23.png)

Per altre informazioni sul controllo della versione in Visual Studio, vedere l'articolo [Controllo della versione](/visualstudio/mac/version-control).

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Vedere anche

- [IDE di Visual Studio (in Windows)](/visualstudio/ide/visual-studio-ide)
