---
title: Creare visualizzatori dati personalizzati | Microsoft Docs
description: I visualizzatori del debugger di Visual Studio sono componenti che visualizzano i dati. Informazioni sui sei visualizzatori standard e su come è possibile scrivere o scaricare altri utenti.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f3d9a907d0857e918069fc4542d59d87242d609
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865839"
---
# <a name="create-custom-data-visualizers"></a>Creare visualizzatori dati personalizzati

 Un *Visualizzatore* fa parte dell' [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interfaccia utente del debugger che consente di visualizzare una variabile o un oggetto in modo appropriato al relativo tipo di dati. Ad esempio, un visualizzatore HTML interpreta una stringa HTML e visualizza il risultato come verrebbe visualizzato in una finestra del browser. Un visualizzatore bitmap interpreta una struttura bitmap e visualizza l'elemento grafico che rappresenta. Alcuni visualizzatori consentono di modificare e visualizzare i dati.

 Il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] include sei visualizzatori standard. I visualizzatori di testo, HTML, XML e JSON funzionano su oggetti stringa. Il Visualizzatore dell'albero di WPF Visualizza le proprietà di una struttura ad albero visuale di un oggetto WPF. Il Visualizzatore DataSet funziona per gli oggetti DataSet, DataView e DataTable.

È possibile che altri visualizzatori siano disponibili per il download da Microsoft, da terze parti e dalla community. È anche possibile scrivere visualizzatori personalizzati e installarli nel [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugger.

Nel debugger, un visualizzatore è rappresentato da un'icona di lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del Visualizzatore"). È possibile selezionare l'icona in un **DataTip**, nella finestra **espressioni di controllo** del debugger o nella finestra di dialogo controllo **immediato** , quindi selezionare il visualizzatore appropriato per l'oggetto corrispondente.

## <a name="write-custom-visualizers"></a>Scrivere visualizzatori personalizzati

 > [!NOTE]
 > Per creare un visualizzatore personalizzato per il codice nativo, vedere l'esempio del [Visualizzatore nativo del debugger SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) . I visualizzatori personalizzati non sono supportati per le app UWP e Windows 8. x.

È possibile scrivere un visualizzatore personalizzato per un oggetto di qualsiasi classe gestita, ad eccezione di <xref:System.Object> e <xref:System.Array>.

L'architettura di un visualizzatore del debugger è definita da due parti:

- Il *lato debugger* viene eseguito all'interno del debugger di Visual Studio e crea e visualizza l'interfaccia utente del visualizzatore.

- Il *lato oggetto del debug* viene eseguito all'interno del processo sottoposto a debug in Visual Studio (l'*oggetto del debug*). L'oggetto dati da visualizzare, ad esempio un oggetto stringa, esiste nel processo oggetto del debug. Il lato oggetto del debug invia l'oggetto al lato debugger, che lo Visualizza nell'interfaccia utente creata.

Il lato debugger riceve l'oggetto dati da un *provider di oggetti* che implementa l' <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfaccia. Il lato oggetto del debug invia l'oggetto tramite l' *origine dell'oggetto*, derivata da <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

Il provider di oggetti può anche inviare dati all'origine oggetto, che consente di scrivere un visualizzatore in grado di modificare i dati. Si esegue l'override del provider di oggetti per comunicare con l'analizzatore di espressioni e l'origine dell'oggetto.

Il lato del debug e il lato debugger comunicano tra loro tramite <xref:System.IO.Stream> metodi che serializzano un oggetto dati in un oggetto <xref:System.IO.Stream> e deserializzano di <xref:System.IO.Stream> nuovo in un oggetto dati.

È possibile scrivere un visualizzatore per un tipo generico solo se il tipo è un tipo aperto. Questa limitazione è identica a quella prevista quando si usa l'attributo `DebuggerTypeProxy`. Per informazioni dettagliate, vedere [usare l'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Ai visualizzatori personalizzati possono essere associate considerazioni sulla sicurezza. Vedere [considerazioni sulla sicurezza del Visualizzatore](../debugger/visualizer-security-considerations.md).

I passaggi seguenti offrono una panoramica di alto livello della creazione del visualizzatore. Per istruzioni dettagliate, vedere [procedura dettagliata: scrivere un visualizzatore in C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) oppure [procedura dettagliata: scrivere un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Per creare il lato debugger

Per creare l'interfaccia utente del visualizzatore sul lato debugger, creare una classe che erediti da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ed eseguire l'override del <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodo per visualizzare l'interfaccia. È possibile usare <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> per visualizzare Windows Form, finestre di dialogo e controlli nel visualizzatore.

1. Usare metodi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> per fornire l'oggetto visualizzato al lato debugger.

1. Creare una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> per visualizzare l'interfaccia. Usare <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> i metodi per visualizzare Windows Form, finestre di dialogo e controlli nell'interfaccia.

4. Applicare <xref:System.Diagnostics.DebuggerVisualizerAttribute> , assegnando al visualizzatore la visualizzazione ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Per creare l'origine dell'oggetto visualizzatore per il lato oggetto del debug

Nel codice del lato debugger, modificare <xref:System.Diagnostics.DebuggerVisualizerAttribute> , assegnando il tipo da visualizzare (origine oggetto del lato oggetto del debug) ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). La `Target` proprietà imposta l'origine dell'oggetto. Se si omette l'origine oggetto, il Visualizzatore utilizzerà un'origine oggetto predefinita.

::: moniker range=">=vs-2019"
Il codice del lato oggetto del debug contiene l'origine dell'oggetto che viene visualizzata. L'oggetto dati può eseguire l'override dei metodi di <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Una DLL del lato oggetto del debug è necessaria se si vuole creare un visualizzatore autonomo.
::: moniker-end

Nel codice del lato oggetto del debug:

- Per consentire al visualizzatore di modificare gli oggetti dati, l'origine dell'oggetto deve ereditare da <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ed eseguire l'override dei `TransferData` `CreateReplacementObject` metodi o.

- Se è necessario supportare la funzionalità multitargeting nel Visualizzatore, è possibile usare i seguenti moniker del Framework di destinazione (TFM) nel file di progetto lato oggetto del debug.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Questi sono gli unici TFM supportati.

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Scrivere un visualizzatore in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Procedura dettagliata: Scrivere un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Procedura: Testare un visualizzatore ed eseguirne il debug](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Informazioni di riferimento sulle API del visualizzatore](../debugger/visualizer-api-reference.md)
- [Visualizzare i dati nel debugger](../debugger/viewing-data-in-the-debugger.md)