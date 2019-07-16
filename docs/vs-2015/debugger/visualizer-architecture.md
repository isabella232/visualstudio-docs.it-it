---
title: Architettura del Visualizzatore | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82dd990a44984d2e3cc1c84244fbe07ea519fdfc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189037"
---
# <a name="visualizer-architecture"></a>Architettura del visualizzatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'architettura di un visualizzatore del debugger è definita da due parti:  
  
- Il *lato debugger* viene eseguito all'interno del debugger di Visual Studio. Il codice del lato debugger crea e visualizza l'interfaccia utente del visualizzatore.  
  
- Il *lato oggetto del debug* viene eseguito all'interno del processo sottoposto a debug in Visual Studio (l'*oggetto del debug*).  
  
  Un visualizzatore è un componente del debugger che consente al debugger di *visualizzare* il contenuto di un oggetto dati in modo significativo e comprensibile. Alcuni visualizzatori supportano anche la modifica dell'oggetto dati. Scrivendo visualizzatori personalizzati, è possibile estendere il debugger in modo da gestire i tipi di dati personalizzati.  
  
  L'oggetto dati da visualizzare si trova all'interno del processo del quale si sta eseguendo il debug, ovvero il processo *oggetto del debug*. L'interfaccia utente in cui verranno visualizzati i dati viene creata all'interno del processo del debugger di Visual Studio:  
  
|Processo del debugger|Processo oggetto del debug|  
|----------------------|----------------------|  
|Interfaccia utente del debugger (Suggerimenti dati, Finestra Espressioni di controllo, Controllo immediato)|Oggetto dati da visualizzare|  
  
 Per visualizzare l'oggetto dati all'interno dell'interfaccia del debugger, è necessario del codice per stabilire la comunicazione tra i due processi. Di conseguenza, l'architettura del visualizzatore è costituita da due parti: il codice del *lato debugger* e il codice del *lato oggetto del debug*.  
  
 Il codice del lato debugger crea un'interfaccia utente che può essere richiamata dall'interfaccia del debugger, ad esempio una finestra Suggerimenti dati, Espressioni di controllo o Controllo immediato. L'interfaccia del visualizzatore viene creata utilizzando la classe <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> e l'interfaccia <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>. Come tutte le API dei visualizzatori, DialogDebuggerVisualizer e IDialogVisualizerService si trovano nello spazio dei nomi <xref:Microsoft.VisualStudio.DebuggerVisualizers>.  
  
|Lato debugger|Lato oggetto del debug|  
|-------------------|-------------------|  
|Classe DialogDebuggerVisualizer<br /><br /> Interfaccia IDialogVisualizerService|Oggetto dati|  
  
 L'interfaccia utente ottiene i dati da visualizzare da un provider di oggetti presente sul lato debugger:  
  
|Lato debugger|Lato oggetto del debug|  
|-------------------|-------------------|  
|Classe DialogDebuggerVisualizer<br /><br /> Interfaccia IDialogVisualizerService|Oggetto dati|  
|Provider di oggetti (implementa l'interfaccia <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 Sul lato oggetto del debug è presente un oggetto corrispondente denominato origine oggetto:  
  
|Lato debugger|Lato oggetto del debug|  
|-------------------|-------------------|  
|Classe DialogDebuggerVisualizer<br /><br /> Interfaccia IDialogVisualizerService|Oggetto dati|  
|Provider di oggetti (implementa l'interfaccia <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Origine oggetto (derivata dalla classe <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>).|  
  
 Il provider di oggetti fornisce i dati dell'oggetto da visualizzare nell'interfaccia utente del visualizzatore, ottenendoli dall'origine oggetto. Il provider di oggetti e l'origine oggetto forniscono le API per trasmettere i dati dell'oggetto tra il lato debugger e il lato oggetto del debug.  
  
 Ogni visualizzatore deve ottenere l'oggetto dati da visualizzare. Nella tabella seguente sono indicate le API corrispondenti che il provider di oggetti e l'origine oggetto utilizzano per questo scopo:  
  
|Provider di oggetti|Origine oggetto|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> -oppure-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Si tenga presente che il provider di oggetti può usare il metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> o <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Ciascuna API comporta una chiamata al metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> nell'origine oggetto. Una chiamata a <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> compila una ([IO]<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->), che rappresenta una forma serializzata dell'oggetto che si sta visualizzando.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializza nuovamente i dati nel formato dell'oggetto, che può quindi essere visualizzato nell'interfaccia utente creata con <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> Inserisce i dati come un formato non elaborato <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, che dovrà essere deserializzato. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> funziona chiamando <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> per ottenere l'oggetto serializzato <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, quindi la deserializza i dati. Usare il metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> quando l'oggetto non è serializzabile con .NET e non richiede la serializzazione personalizzata. In tal caso è necessario eseguire anche l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName>.  
  
 Se si sta creando un visualizzatore di sola lettura, è sufficiente una comunicazione unidirezionale con il metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> o <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Se si sta creando un visualizzatore che supporta la modifica di oggetti dati, sono necessarie altre funzionalità. È anche necessario poter inviare un oggetto dati dal provider di oggetti nuovamente all'origine oggetto. Nella tabella seguente sono indicate le API del provider di oggetti e dell'origine oggetto utilizzate per questo scopo:  
  
|Provider di oggetti|Origine oggetto|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> -oppure-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 Si tenga presente che il provider di oggetti può usare due API. I dati vengono sempre inviati dal Provider di oggetti all'origine oggetto come un <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, ma <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> richiede la serializzazione di oggetti in un <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> l'utente corrente.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> Ottiene un oggetto specificato, lo serializza in un <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, quindi chiama <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> per inviare il <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> a <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.  
  
 L'utilizzo di uno dei metodi di sostituzione consente di creare un oggetto dati nuovo nel lato oggetto del debug che sostituisce l'oggetto visualizzato. Se si desidera modificare il contenuto dell'oggetto originale senza sostituirlo, utilizzare uno dei metodi di trasferimento illustrati nella tabella seguente. Queste API trasferiscono contemporaneamente i dati in entrambe le direzioni, senza sostituire l'oggetto visualizzato:  
  
|Provider di oggetti|Origine oggetto|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> -oppure-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)   
 [Procedura dettagliata: Scrittura di un visualizzatore in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Procedura dettagliata: Scrittura di un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Procedura dettagliata: Scrittura di un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Considerazioni sulla sicurezza del visualizzatore](../debugger/visualizer-security-considerations.md)
