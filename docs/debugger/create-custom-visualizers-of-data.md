---
title: Creazione di visualizzatori di dati personalizzato | Microsoft Docs
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64f44379c98808cb93fbe51498234a34a695c3d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564724"
---
# <a name="create-custom-data-visualizers"></a>Creazione di visualizzatori dati personalizzati
 Oggetto *visualizer* fa parte di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interfaccia utente del debugger che consente di visualizzare una variabile o un oggetto in modo appropriato al relativo tipo di dati. Ad esempio, un visualizzatore HTML interpreta una stringa HTML e visualizza il risultato come apparirebbe in una finestra del browser. Un visualizzatore di bitmap interpreta una struttura di bitmap e visualizza il grafico da che essa rappresentato. Alcuni visualizzatori consentono di modificare, nonché visualizzare i dati.

 Il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] include sei visualizzatori standard. Il testo, HTML, XML e JSON utilizzati visualizzatori per oggetti stringa. Il Visualizzatore dell'albero di WPF consente di visualizzare le proprietà di una struttura visiva di oggetti WPF. Il Visualizzatore di dataset funziona per gli oggetti DataSet, DataView e DataTable.

I visualizzatori altre potrebbero essere disponibili per il download da Microsoft, terze parti e dalla community. È anche possibile scrivere visualizzatori personalizzati e installarli nel [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugger.

Nel debugger, un visualizzatore è rappresentato da un'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore"). È possibile selezionare l'icona in un **suggerimento dati**, debugger **Watch** finestra, oppure **controllo immediato** nella finestra di dialogo e quindi selezionare il visualizzatore appropriato per l'oggetto corrispondente.

## <a name="write-custom-visualizers"></a>Scrivere visualizzatori personalizzati

 > [!NOTE]
 > Per creare un visualizzatore personalizzato per il codice nativo, vedere la [visualizzatore del Debugger nativo SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) esempio. I visualizzatori personalizzati non sono supportati per le app di 8.x a UWP e Windows.

È possibile scrivere un visualizzatore personalizzato per un oggetto di qualsiasi classe gestita, ad eccezione di <xref:System.Object> e <xref:System.Array>.

L'architettura di un visualizzatore del debugger è definita da due parti:

- Il *lato debugger* viene eseguito all'interno del debugger di Visual Studio e crea e visualizza l'interfaccia utente del visualizzatore.

- Il *lato oggetto del debug* viene eseguito all'interno del processo sottoposto a debug in Visual Studio (l'*oggetto del debug*). L'oggetto dati da visualizzare (ad esempio, un oggetto stringa) è presente nel processo oggetto del debug. Il lato oggetto del debug invia l'oggetto al lato debugger, che lo visualizza nell'interfaccia utente creati.

Il lato debugger riceve l'oggetto dati da un *provider di oggetti* che implementa il <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfaccia. Il lato oggetto del debug invia l'oggetto tramite il *origine dell'oggetto*, che deriva da <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

Il provider di oggetti può inoltre inviare i dati nuovamente all'origine oggetto, che consente di scrivere un visualizzatore che possa modificare i dati. Si esegue l'override di provider di oggetti per comunicare con l'analizzatore di espressioni e l'origine dell'oggetto.

Il lato oggetto del debug e il lato debugger comunicano tra loro attraverso <xref:System.IO.Stream> metodi che serializzano un dati oggetto in un <xref:System.IO.Stream> e la deserializzazione di <xref:System.IO.Stream> nuovamente in un oggetto dati.

È possibile scrivere un visualizzatore per un tipo generico solo se il tipo è un tipo aperto. Questa limitazione è identica a quella prevista quando si usa l'attributo `DebuggerTypeProxy`. Per informazioni dettagliate, vedere [usare l'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Ai visualizzatori personalizzati possono essere associate considerazioni sulla sicurezza. Visualizzare [considerazioni sulla sicurezza del visualizzatore](../debugger/visualizer-security-considerations.md).

La procedura seguente offre una panoramica generale della creazione del visualizzatore. Per istruzioni dettagliate, vedere [procedura dettagliata: Scrivere un visualizzatore in C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) oppure [procedura dettagliata: Scrivere un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Per creare il lato debugger

Per creare l'interfaccia utente del visualizzatore nel lato debugger, si crea una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>ed eseguire l'override di <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodo per visualizzare l'interfaccia. È possibile usare <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> per visualizzare Windows forms, finestre di dialogo e controlli nel Visualizzatore.

1. Usare metodi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> per fornire l'oggetto visualizzato al lato debugger.

1. Creare una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> per visualizzare l'interfaccia. Usare <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metodi per visualizzare Windows forms, finestre di dialogo e controlli nell'interfaccia.

4. Si applicano <xref:System.Diagnostics.DebuggerVisualizerAttribute>, assegnare il visualizzatore per visualizzare (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-debuggee-side"></a>Per creare il lato oggetto del debug

Specificare il codice lato oggetto del debug utilizzando il <xref:System.Diagnostics.DebuggerVisualizerAttribute>.

1. Applicare <xref:System.Diagnostics.DebuggerVisualizerAttribute> per assegnare un visualizzatore (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) e un'origine oggetto (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Se si omette l'origine dell'oggetto, il visualizzatore utilizzerà un'origine predefinita.

1. Per consentire il Visualizzatore di modifica, nonché visualizzare gli oggetti dati, eseguire l'override di `TransferData` oppure `CreateReplacementObject` metodi da <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Scrivere un visualizzatore in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Procedura dettagliata: Scrivere un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Procedura: Testare un visualizzatore ed eseguirne il debug](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Informazioni di riferimento sulle API del visualizzatore](../debugger/visualizer-api-reference.md)
- [Visualizzare i dati nel debugger](../debugger/viewing-data-in-the-debugger.md)