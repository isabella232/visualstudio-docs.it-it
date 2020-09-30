---
title: Presentazione di Visual Studio per Mac
description: Visual Studio per Mac offre un ambiente di sviluppo integrato per creare applicazioni .NET in macOS, inclusi siti Web ASP.NET Core e progetti Xamarin per iOS, Android, Mac e Xamarin.Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: a385e58f73edbcea6eb25b7b2e2728e00f9bcb8d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584009"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Presentazione di Visual Studio 2019 per Mac

Visual Studio per Mac è un _ambiente di sviluppo integrato_ .NET nel Mac che può essere usato per modificare, eseguire il debug, compilare il codice e quindi pubblicare un'app. Oltre a un editor di codice e a un debugger, Visual Studio per Mac include compilatori, strumenti di completamento del codice, finestre di progettazione grafiche e funzionalità di controllo del codice sorgente per semplificare il processo di sviluppo del software.

Visual Studio per Mac supporta molti degli stessi tipi di file della controparte Windows, ad esempio i file con estensione `.csproj`, `.fsproj` o `.sln`, nonché funzionalità quali EditorConfig, rendendo possibile l'uso dell'IDE più adatto alle proprie esigenze.
La creazione, l'apertura e lo sviluppo di app saranno operazioni familiari per chi in precedenza ha usato Visual Studio in Windows. Visual Studio per Mac usa inoltre molti degli strumenti avanzati che rendono la controparte Windows un IDE estremamente potente. La piattaforma di compilazione Roslyn viene usata per il refactoring e per IntelliSense. Il sistema di progetto e il motore di compilazione utilizzano MSBuild e l'editor di origine utilizza la stessa base di Visual Studio in Windows. Vengono usati gli stessi motori di debugger per le app Xamarin e .NET Core e le stesse finestre di progettazione per Xamarin.iOS e Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Attività possibili in Visual Studio per Mac

Visual Studio per Mac supporta i tipi di sviluppo seguenti:

- ASP.NET Core applicazioni Web con C#, F # e supporto per Razor Pages, JavaScript e TypeScript
- Applicazioni console .NET Core con C# o F#
- Giochi Unity multipiattaforma e applicazioni con C#
- Applicazioni Android, iOS, tvOS e watchOS in Xamarin con C# o F# e XAML
- Applicazioni desktop Cocoa in C# o F#

L'articolo illustra varie sezioni di Visual Studio per Mac e presenta alcune delle funzionalità che fanno di questo prodotto un potente strumento per la creazione di queste applicazioni.

## <a name="ide-tour"></a>Presentazione dell'IDE

Visual Studio per Mac è organizzato in sezioni diverse per la gestione di impostazioni e file delle applicazioni, la creazione di codice delle applicazioni e il debug.

## <a name="getting-started"></a>Attività iniziali

Quando si avvia Visual Studio 2019 per Mac per la prima volta, viene visualizzata una finestra di accesso per i nuovi utenti. Accedere con l'account Microsoft per attivare una licenza a pagamento (se disponibile) o connettersi alle sottoscrizioni di Azure. È possibile scegliere di **eseguire questa** operazione in un secondo momento e accedere in un secondo momento tramite la voce **di menu di accesso > di Visual Studio** :

![Effettuare l'accesso con l'account Microsoft.](media/ide-tour-2019-start-signin.png)

Sarà quindi possibile personalizzare l'IDE selezionando i tasti di scelta rapida preferiti: Visual Studio per Mac, Visual Studio, Visual Studio Code o Xcode:

![Selezionare i tasti di scelta rapida Preferiti](media/ide-tour-2019-keyboard-shortcut.png)

Dopo questa configurazione iniziale, viene visualizzata la finestra di _avvio_ quando si apre Visual Studio 2019 per Mac, che mostra un elenco di progetti recenti e i pulsanti per aprire un progetto esistente o crearne uno nuovo:

![Scegliere tra i progetti recenti o crearne uno nuovo](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Soluzioni e progetti

L'immagine seguente mostra Visual Studio per Mac con un'applicazione caricata:

![Visual Studio per Mac con un'applicazione caricata](media/ide-tour-image17.png)

Le sezioni seguenti forniscono una panoramica delle principali aree di Visual Studio per Mac.

## <a name="solution-pad"></a>Riquadro della soluzione

Il riquadro della soluzione organizza i progetti in una soluzione:

![Progetti organizzati nel riquadro della soluzione](media/ide-tour-image18.png)

In questa posizione i file per il codice sorgente, le risorse, l'interfaccia utente e le dipendenze vengono organizzati in progetti specifici della piattaforma.

Per altre informazioni sull'uso di progetti e soluzioni in Visual Studio per Mac, vedere l'articolo [Progetti e soluzioni](./projects-and-solutions.md).

## <a name="assembly-references"></a>Riferimenti ad assembly

I riferimenti ad assembly per ogni progetto sono disponibili nella cartella Riferimenti:

![Cartella Riferimenti nel riquadro della soluzione](media/ide-tour-image19.png)

È possibile aggiungere altri riferimenti usando la finestra di dialogo **Modifica riferimenti**, visualizzata facendo doppio clic sulla cartella Riferimenti oppure scegliendo **Modifica riferimenti** tra le azioni del menu di scelta rapida:

![Finestra di dialogo Modifica riferimenti](media/ide-tour-image20.png)

Per altre informazioni sull'uso dei riferimenti in Visual Studio per Mac, vedere l'articolo [Gestione dei riferimenti in un progetto](./managing-references-in-a-project.md).

## <a name="dependencies--packages"></a>Dipendenze/pacchetti

Tutte le dipendenze esterne usate nell'app vengono archiviate nella cartella dipendenze o pacchetti, a seconda che si tratti di un progetto .NET Core o Novell. iOS/Novell. Android. In genere vengono fornite sotto forma di pacchetto NuGet.

NuGet è il più diffuso strumento di gestione pacchetti per lo sviluppo .NET. Con il supporto di NuGet di Visual Studio è possibile cercare e aggiungere facilmente pacchetti al progetto dell'applicazione.

Per aggiungere una dipendenza all'applicazione, fare clic con il pulsante destro del mouse sulla cartella Dipendenze/Pacchetti e scegliere **Aggiungi pacchetti**:

![Aggiungere un pacchetto NuGet](media/ide-tour-image21.png)

Le informazioni sull'uso di un pacchetto NuGet in un'applicazione sono disponibili nell'articolo [Inserimento di un pacchetto NuGet nel progetto](./nuget-walkthrough.md).

## <a name="source-editor"></a>Editor standard

Indipendentemente da se si sta scrivendo in C#, XAML o JavaScript, l'editor di codice condivide gli stessi componenti di base con Visual Studio in Windows, con un'interfaccia utente completamente nativa.

In questo esempio vengono riportate alcune delle funzionalità seguenti:

* Interfaccia utente (basata su Cocoa) macOS nativa (descrizioni comandi, area dell'editor, ornamenti dei margini, rendering del testo, IntelliSense)
* Filtro del tipo IntelliSense e "Mostra elementi di importazione"
* Supporto per input di testo nativo
* Supporto del linguaggio RTL/BiDi
* Roslyn 3
* Supporto di più punti di inserimento
* A capo automatico
* Interfaccia utente di IntelliSense aggiornata
* Ricerca/sostituzione migliorata
* Supporto per frammenti 
* Selezione di Formatta
* Lampadine inline

Per ulteriori informazioni sull'utilizzo dell'editor di origine in Visual Studio per Mac, vedere la documentazione dell' [editor di origine](./source-editor.md) .

Per tenere le schede visibili in qualsiasi momento, è possibile sfruttare i vantaggi offerti dall'aggiunta. Ciò garantisce che ogni volta che si avvia un progetto, la scheda necessaria sarà sempre visualizzata. Per aggiungere una scheda, passare il puntatore del mouse sulla scheda e fare clic sull'icona del _pin_ :

![Aggiunta di una scheda](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Refactoring

Visual Studio per Mac fornisce due metodi utili per il refactoring del codice: azioni di contesto e analisi dell'origine. Per altre informazioni, vedere l'articolo [Refactoring](./refactoring.md).

## <a name="debugging"></a>Debug

Visual Studio per Mac dispone di debugger che supportano i progetti .NET Core, .NET Framework, Unity e Novell. Visual Studio per Mac usa il debugger di .NET Core e il debugger mono soft, consentendo all'IDE di eseguire il debug di codice gestito in tutte le piattaforme. Per altre informazioni sul debug, vedere l'articolo [Debug](./debugging.md).

Il debugger contiene visualizzatori avanzati per tipi speciali come stringhe, colori, URL, oltre a dimensioni, coordinate e curve di Bézier.

Per altre informazioni sulle visualizzazioni dei dati del debugger, vedere l'articolo [Visualizzazioni dei dati](./data-visualizations.md).

## <a name="version-control"></a>Controllo della versione

Visual Studio per Mac si integra con sistemi di controllo del codice sorgente Subversion e Git. I progetti sottoposti a controllo del codice sorgente sono contrassegnati con un ramo accanto al nome della soluzione:

![Nome del ramo per indicare un progetto sottoposto a controllo del codice sorgente](media/ide-tour-image22.png)

I file con modifiche non sottoposte a commit presentano un'annotazione nelle relative icone nel riquadro della soluzione, come illustrato nell'immagine seguente:

![File con modifiche non sottoposte a commit nel riquadro della soluzione](media/ide-tour-image23.png)

Per altre informazioni sul controllo della versione in Visual Studio, vedere l'articolo [Controllo della versione](./version-control.md).

## <a name="next-steps"></a>Passaggi successivi

- [Installare Visual Studio per Mac](installation.md)
- [Esaminare i carichi di lavoro disponibili](workloads.md)

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Vedi anche

- [IDE di Visual Studio (in Windows)](/visualstudio/ide/visual-studio-ide)