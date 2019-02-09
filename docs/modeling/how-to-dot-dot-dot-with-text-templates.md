---
title: Procedure relative ai modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82309eb9288dffb1fca0a3917b764ffb9040ab9d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937179"
---
# <a name="how-to--with-text-templates"></a>Procedure relative ai modelli di testo
Modelli di testo in Visual Studio forniscono un modo utile per la generazione di testo di qualsiasi tipo. È possibile usare i modelli di testo per generare testo in fase di esecuzione come parte dell'applicazione e in fase di progettazione per generare alcuni di codice del progetto. Questo argomento vengono riepilogati più di frequente frequenti "Ricerca per categorie...?" domande.

 In questo argomento, più risposte preceduti da elenchi puntati sono suggerimenti alternativi.

 Per un'introduzione generale ai modelli di testo, leggere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Come si fa...

### <a name="generate-part-of-my-application-code"></a>Generare una parte del codice dell'applicazione
 Dispone di una configurazione o *modello* in un file o un database. Una o più parti del mio codice dipendono da tale modello.

-   Generare alcuni dei file di codice da modelli di testo. Per altre informazioni, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) e [che cos'è il modo migliore per iniziare a scrivere un modello?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generare i file in fase di esecuzione passa il modello di dati
 In fase di esecuzione, l'applicazione genera file di testo, ad esempio report, che contengono una combinazione di testo standard e i dati. Desidera evitare la scrittura di centinaia di `write` istruzioni.

-   Aggiungere un modello di testo di runtime al progetto. Questo modello crea una classe nel codice, che è possibile creare un'istanza e usare per generare testo. È possibile passare i dati nei parametri del costruttore. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

-   Se si desidera generare dai modelli che sono disponibili solo in fase di esecuzione, è possibile usare i modelli di testo standard. Se si sta scrivendo un'estensione di Visual Studio, è possibile richiamare il servizio del modello di testo. Per altre informazioni, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). In altri contesti, è possibile usare il motore del modello di testo. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Usare la \<&@parameter& > direttiva per passare i parametri per questi modelli. Per altre informazioni, vedere [direttiva Parameter T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Leggere un altro file di progetto da un modello
 Per leggere un file dal progetto di Visual Studio stesso come il modello:

-   Inserire `hostSpecific="true"` nella direttiva `<#@template#>`.

     Nel codice, utilizzare `this.Host.ResolvePath(filename)` per ottenere il percorso completo del file.

### <a name="invoke-methods-from-a-template"></a>Richiamare i metodi da un modello
 Se i metodi già esistono, ad esempio, nello standard [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] classi:

- Usare la \<&@assembly& > direttiva per caricare l'assembly e usare \<&@import& > per impostare il contesto dello spazio dei nomi. Per altre informazioni, vedere [direttiva Import T4](../modeling/t4-import-directive.md).

   Se spesso utilizzano lo stesso set di assembly e direttive import, prendere in considerazione la scrittura di un processore di direttiva. In ogni modello, è possibile richiamare il processore di direttiva, che è possibile caricare gli assembly e i file di modello e impostare il contesto dello spazio dei nomi. Per altre informazioni, vedere [creazione di processori direttiva di modelli di Custom T4 testo](../modeling/creating-custom-t4-text-template-directive-processors.md).

  Se si siano scrivendo i metodi familiarità:

- Se si scrive un modello di testo di runtime, scrivere una definizione di classe parziale con lo stesso nome di modello di testo della fase di esecuzione. Aggiungere i metodi aggiuntivi in questa classe.

- Scrivere un blocco di controllo di funzionalità di classe `<#+ ... #>` in cui è possibile dichiarare i metodi, proprietà e classi private. Quando viene compilato il modello di testo, viene trasformato in una classe. I blocchi di controllo standard `<#...#>` e testo vengono trasformati in un singolo metodo, e blocchi della funzionalità di classe vengono inseriti come membri separati. Per altre informazioni, vedere [blocchi di controllo del modello di testo](../modeling/text-template-control-blocks.md).

   Metodi definiti come funzionalità di livello può includere anche i blocchi di testo incorporato.

   È consigliabile inserire le funzionalità di classe in un file separato che è possibile `<#@include#>` in uno o più file di modello.

- Scrivere i metodi in un assembly separato (libreria di classi) e chiamarli in base al modello. Usare la `<#@assembly#>` direttiva per caricare l'assembly e `<#@import#>` per impostare il contesto dello spazio dei nomi. Si noti che per ricompilare l'assembly anche se ne esegue il debug, potrebbe essere necessario arrestare e riavviare Visual Studio. Per altre informazioni, vedere [direttive di modello di testo T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generare molti file da un unico modello schema
 Se spesso possibile generare file da modelli aventi lo stesso schema di database o XML:

-   Prendere in considerazione la scrittura di un processore di direttiva. In questo modo è possibile sostituire più istruzioni di assembly e importare le istruzioni in ogni modello con una singola direttiva personalizzata. Il processore di direttiva possa anche caricare e analizzare il file del modello. Per altre informazioni, vedere [creazione di processori direttiva di modelli di Custom T4 testo](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generare file da un modello complesso

-   È consigliabile creare un linguaggio specifico di dominio (DSL) per rappresentare il modello. Questo rende molto più facile scrivere i modelli, perché si usano tipi e proprietà che riflettono i nomi degli elementi nel modello. Non è necessario analizzare il file o esplorare i nodi XML. Ad esempio:

     `foreach (Book book in this.Library) { ... }`

     Per altre informazioni, vedere [Guida introduttiva a Domain-Specific Language](../modeling/getting-started-with-domain-specific-languages.md) e [generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Ottenere dati da Visual Studio
 Usare i servizi forniti in Visual Studio, dal set il `hostSpecific` attributo e carico il `EnvDTE` assembly. Ad esempio:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>Eseguire i modelli di testo nel processo di compilazione

-   Per altre informazioni, vedere [generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Domande generali

### <a name="starting"></a> Che cos'è il modo migliore per iniziare a scrivere un modello di testo?

1.  Scrivere un esempio specifico del file generato.

2.  Trasformarlo in un modello di testo mediante l'inserimento di `<#@template #>` direttiva e direttive e codice che sono necessari per caricare il file di input o il modello.

3.  Sostituire gradualmente parti del file con espressione e i blocchi di codice.

### <a name="what-is-a-model"></a>Che cos'è un "modello"?

-   L'input letto dal modello. È possibile in un file o in un database. È possibile, XML o un disegno di Visio, o un linguaggio specifico di dominio (DSL) o un modello UML, o potrebbe essere testo normale. Potrebbe essere distribuito in più file. In genere più di un modello legge un modello.

     L'implicazione del termine "modello" è che rappresenta alcuni aspetti del tuo business più direttamente il codice di programma generato o altri file. Ad esempio, potrebbe rappresentare il piano di una rete di comunicazioni che sarà responsabili della supervisione del software generato.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Che cos'è il vantaggio dell'uso di modelli di testo?
 In genere, si genera codice più o altri file da un modello. Il modello rappresenta i requisiti in modo più diretto rispetto al codice generato. Omette dettaglio di implementazione e viene scritto in termini di requisiti, anziché il codice. Quando cambiano i requisiti, come avviene in genere, è possibile aggiornare il modello in modo più semplice e più affidabile rispetto alle diverse parti del codice programma.

 Generazione di codice è quindi uno strumento prezioso dalla prospettiva di metodologia di sviluppo agile.

### <a name="what-best-practices-are-there-for-text-templates"></a>Quali "procedure consigliate" sono disponibili per i modelli di testo?

-   Per altre informazioni, vedere [linee guida per i modelli di testo T4 di scrittura](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Che cos'è "T4"?

-   Un altro nome per le funzionalità di modello di testo di Visual Studio descritte di seguito. La versione precedente, non è stata pubblicata, è un'abbreviazione per "Trasformazione del modello di testo".
