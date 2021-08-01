---
title: Creare visualizzatori di dati personalizzati | Microsoft Docs
description: Visual Studio visualizzatori del debugger sono componenti che visualizzano i dati. Informazioni sui sei visualizzatori standard e su come è possibile scrivere o scaricare altri visualizzatori.
ms.custom: SEO-VS-2020
ms.date: 07/29/2021
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
ms.openlocfilehash: d5f2beccbc4004b9b36b7ff1c39b3ad60cc39120
ms.sourcegitcommit: 24dd8fbdf88eca005e9f01328ab57150de37d432
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2021
ms.locfileid: "115014828"
---
# <a name="create-custom-data-visualizers"></a>Creare visualizzatori di dati personalizzati

 Un *visualizzatore* fa parte dell'interfaccia utente del debugger che visualizza una variabile o un oggetto nel modo [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] appropriato per il tipo di dati. Ad esempio, un visualizzatore HTML interpreta una stringa HTML e visualizza il risultato così come verrebbe visualizzato in una finestra del browser. Un visualizzatore bitmap interpreta una struttura bitmap e visualizza l'immagine che rappresenta. Alcuni visualizzatori consentono di modificare e visualizzare i dati.

 Il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] include sei visualizzatori standard. I visualizzatori di testo, HTML, XML e JSON funzionano su oggetti stringa. Il visualizzatore albero WPF visualizza le proprietà di una struttura ad albero visuale di oggetti WPF. Il visualizzatore di set di dati funziona per gli oggetti DataSet, DataView e DataTable.

Altri visualizzatori possono essere disponibili per il download da Microsoft, da terze parti e dalla community. È anche possibile scrivere visualizzatori personalizzati e installarli nel [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugger.

Nel debugger un visualizzatore è rappresentato da un'icona a forma di lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del visualizzatore"). È possibile selezionare l'icona in un **suggerimento** dati, in una finestra espressioni di controllo del **debugger** o in una finestra di dialogo Controllo immediato e quindi selezionare il visualizzatore appropriato per l'oggetto corrispondente. 

## <a name="write-custom-visualizers"></a>Scrivere visualizzatori personalizzati

 > [!NOTE]
 > Per creare un visualizzatore personalizzato per il codice nativo, vedere l'esempio di visualizzatore del debugger nativo [SQLite.](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) I visualizzatori personalizzati non sono supportati per le app UWP e Windows 8.x.

È possibile scrivere un visualizzatore personalizzato per un oggetto di qualsiasi classe gestita, ad eccezione di <xref:System.Object> e <xref:System.Array>.

L'architettura di un visualizzatore del debugger è definita da due parti:

- Il *lato debugger viene* eseguito all'interno Visual Studio debugger e crea e visualizza l'interfaccia utente del visualizzatore. 

  Poiché Visual Studio viene eseguito nel runtime .NET Framework, questo componente deve essere scritto per .NET Framework. Per questo motivo, non è possibile scriverlo per .NET Core.

- Il *lato oggetto del debug* viene eseguito all'interno del processo sottoposto a debug in Visual Studio (l'*oggetto del debug*). L'oggetto dati da visualizzare (ad esempio, un oggetto String) esiste nel processo dell'oggetto del debug. Il lato oggetto del debug invia l'oggetto al lato debugger, che lo visualizza nell'interfaccia utente creata.

  Il runtime per cui si compila questo componente deve corrispondere a quello in cui verrà eseguito il processo dell'oggetto del debug, ovvero .NET Framework o .NET Core.

Il lato debugger riceve l'oggetto dati da un *provider di oggetti* che implementa l'interfaccia <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> . Il lato oggetto del debug invia l'oggetto tramite *l'origine oggetto*, derivata da <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

Il provider di oggetti può anche inviare dati all'origine oggetto, che consente di scrivere un visualizzatore in grado di modificare i dati. Eseguire l'override del provider di oggetti per parlare con l'analizzatore di espressioni e l'origine dell'oggetto.

Il lato oggetto del debug e il lato debugger comunicano tra loro tramite metodi che serializzano un oggetto dati in un oggetto dati e deserializzano l'oggetto <xref:System.IO.Stream> <xref:System.IO.Stream> in un oggetto <xref:System.IO.Stream> dati.

È possibile scrivere un visualizzatore per un tipo generico solo se il tipo è un tipo aperto. Questa limitazione è identica a quella prevista quando si usa l'attributo `DebuggerTypeProxy`. Per informazioni dettagliate, [vedere Usare l'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Ai visualizzatori personalizzati possono essere associate considerazioni sulla sicurezza. Vedere [Considerazioni sulla sicurezza del visualizzatore](../debugger/visualizer-security-considerations.md).

La procedura seguente illustra una panoramica generale della creazione del visualizzatore. Per istruzioni dettagliate, vedere [procedura dettagliata: scrivere un visualizzatore in C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) oppure [procedura dettagliata: scrivere un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Per creare il lato debugger

Per creare l'interfaccia utente del visualizzatore sul lato debugger, creare una classe che eredita da ed eseguire <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> l'override del metodo per visualizzare <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> l'interfaccia. È possibile usare per visualizzare Windows moduli, finestre di <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> dialogo e controlli nel visualizzatore.

1. Usare metodi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> per fornire l'oggetto visualizzato al lato debugger.

1. Creare una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> per visualizzare l'interfaccia. Usare i metodi per visualizzare Windows form, finestre di <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> dialogo e controlli nell'interfaccia.

1. Applicare <xref:System.Diagnostics.DebuggerVisualizerAttribute> , fornendo il visualizzatore da visualizzare ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).

#### <a name="special-debugger-side-considerations-for-net-50"></a>Considerazioni speciali sul lato debugger per .NET 5.0+

I visualizzatori personalizzati trasferiscono i dati tra l'oggetto del debug e i lati *del debugger* tramite la *serializzazione* binaria usando <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> la classe per impostazione predefinita. Tuttavia, questo tipo di serializzazione è in fase di descrizione in .NET 5 e successive a causa di problemi di sicurezza relativi *alle* vulnerabilità infissibili.
Inoltre, è stato contrassegnato come completamente obsoleto in ASP.NET Core 5 e il relativo utilizzo verrà generato come descritto nella documentazione ASP.NET Core [.](/dotnet/core/compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete)
Questa sezione descrive i passaggi da eseguire per assicurarsi che il visualizzatore sia ancora supportato in questo scenario.

- Per motivi di compatibilità, il metodo sottoposto a override nella sezione precedente accetta <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A> ancora un <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> oggetto . Tuttavia, a partire Visual Studio 2019 versione 16.10, è effettivamente di tipo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider2> .
Per questo motivo, eseguire il cast `objectProvider` dell'oggetto all'interfaccia aggiornata.

- Quando si inviano oggetti, ad esempio comandi o dati, al lato oggetto del debug usare il metodo per passarlo a un flusso, determinerà il formato di *serializzazione* migliore da usare in base al runtime del processo dell'oggetto `IVisualizerObjectProvider2.Serialize` del *debug.*
Passare quindi il flusso al `IVisualizerObjectProvider2.TransferData` metodo .

- Se il *componente visualizzatore lato* oggetto del debug deve restituire qualsiasi elemento al *lato debugger,* si trova nell'oggetto <xref:System.IO.Stream> restituito dal metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A> . Usare il `IVisualizerObjectProvider2.GetDeserializableObjectFrom` metodo per ottenere <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> un'istanza di ed elaborarla in base alle esigenze.

Fare riferimento alla sezione Considerazioni sul lato oggetto del debug speciale per [.NET 5.0+](#special-debuggee-side-considerations-for-net-50) per informazioni sulle altre modifiche necessarie sul lato oggetto del debug quando l'uso della *serializzazione* binaria non è supportato.

> [!NOTE]
> Per altre informazioni sul problema, vedere la Guida alla sicurezza [di BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Per creare l'origine dell'oggetto visualizzatore per il lato oggetto del debug

Nel codice lato debugger modificare , fornendo il tipo da visualizzare (origine oggetto lato <xref:System.Diagnostics.DebuggerVisualizerAttribute> oggetto del debug) ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). La `Target` proprietà imposta l'origine dell'oggetto . Se si omette l'origine dell'oggetto, il visualizzatore userà un'origine oggetto predefinita.

::: moniker range=">=vs-2019"
Il codice lato oggetto del debug contiene l'origine dell'oggetto che viene visualizzato. L'oggetto dati può eseguire l'override dei metodi di <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Una DLL lato oggetto del debug è necessaria se si vuole creare un visualizzatore autonomo.
::: moniker-end

Nel codice lato oggetto del debug:

- Per consentire al visualizzatore di modificare gli oggetti dati, l'origine oggetto deve ereditare da ed <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> eseguire l'override dei `TransferData` metodi o `CreateReplacementObject` .

- Se è necessario supportare la multi-destinazione nel visualizzatore, è possibile usare i moniker del framework di destinazione seguenti nel file di progetto sul lato oggetto del debug.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Si tratta degli unici TPM supportati.

#### <a name="special-debuggee-side-considerations-for-net-50"></a>Considerazioni speciali sul lato oggetto del debug per .NET 5.0+

> [!IMPORTANT]
> Potrebbero essere necessari passaggi aggiuntivi per il funzionamento di un visualizzatore a partire da .NET 5.0 a causa di problemi di sicurezza relativi al metodo di serializzazione binaria sottostante usato per impostazione predefinita. Leggere questa [sezione prima](#special-debugger-side-considerations-for-net-50) di continuare.

- Se il visualizzatore implementa il metodo , usare il metodo appena aggiunto <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A> disponibile nella versione più recente di <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetDeserializableObject%2A> `VisualizerObjectSource` . L'oggetto restituito consente di determinare il formato di serializzazione dell'oggetto (binario o JSON) e di deserializzare l'oggetto sottostante in modo che <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> possa essere usato.

- Se il *lato oggetto* del debug restituisce dati sul lato *debugger* come parte della chiamata, serializzare la risposta nel flusso del `TransferData` lato *debugger* tramite il <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A> metodo .

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Scrivere un visualizzatore in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Procedura dettagliata: Scrivere un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Procedura: Testare un visualizzatore ed eseguirne il debug](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Informazioni di riferimento sulle API del visualizzatore](../debugger/visualizer-api-reference.md)
- [Visualizzare i dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
