---
title: Procedure relative ai modelli di testo
description: Informazioni sulle risposte alle domande comuni riscontrate quando si usano modelli di testo per generare testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: ab0aa917f79845b7baaad4c65583a5a5a07853f4feec28cab7de9646751aaf3b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429147"
---
# <a name="how-to--with-text-templates"></a>Procedure relative ai modelli di testo
I modelli di testo Visual Studio un modo utile per generare testo di qualsiasi tipo. È possibile usare modelli di testo per generare testo in fase di esecuzione come parte dell'applicazione e in fase di progettazione per generare parte del codice del progetto. Questo argomento riepiloga le domande più frequenti Ricerca per categorie ...?" Domande.

 In questo argomento, più risposte precedute da elenchi puntati sono suggerimenti alternativi.

 Per un'introduzione generale ai modelli di testo, vedere [Generazione di codice e Modelli di testo T4.](../modeling/code-generation-and-t4-text-templates.md)

## <a name="how-to-"></a>Come si fa...

### <a name="generate-part-of-my-application-code"></a>Generare parte del codice dell'applicazione
 È presente una configurazione o *un modello* in un file o in un database. Una o più parti del codice dipendono da tale modello.

- Generare alcuni file di codice da modelli di testo. Per altre informazioni, vedere Generazione di codice in fase di progettazione tramite modelli di testo [T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) e Qual è il modo migliore per iniziare [a scrivere un modello?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generare file in fase di esecuzione, passando i dati nel modello
 In fase di esecuzione, l'applicazione genera file di testo, ad esempio report, che contengono una combinazione di testo e dati standard. Si vuole evitare di scrivere centinaia `write` di istruzioni.

- Aggiungere un modello di testo di runtime al progetto. Questo modello crea una classe nel codice, di cui è possibile creare un'istanza e usarla per generare testo. È possibile passare dati nei parametri del costruttore. Per altre informazioni, vedere Generazione di testo in fase [di esecuzione con modelli di testo T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

- Se si vuole generare da modelli disponibili solo in fase di esecuzione, è possibile usare modelli di testo standard. Se si scrive un'Visual Studio, è possibile richiamare il servizio di creazione modelli di testo. Per altre informazioni, vedere [Richiamo della trasformazione testo in un'estensione di Visual Studio.](../modeling/invoking-text-transformation-in-a-vs-extension.md) In altri contesti è possibile usare il motore di modelli di testo. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Usare la \<#@parameter#> direttiva per passare parametri a questi modelli. Per altre informazioni, vedere [Direttiva del parametro T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Leggere un altro file di progetto da un modello
 Per leggere un file dallo stesso Visual Studio del modello:

- Inserire `hostSpecific="true"` nella direttiva `<#@template#>`.

     Nel codice usare `this.Host.ResolvePath(filename)` per ottenere il percorso completo del file.

### <a name="invoke-methods-from-a-template"></a>Richiamare metodi da un modello

Se i metodi esistono già, ad esempio, nelle classi .NET:

- Usare la direttiva \<#@assembly#> per caricare l'assembly e usare \<#@import#> per impostare il contesto dello spazio dei nomi. Per altre informazioni, vedere [Direttiva import T4.](../modeling/t4-import-directive.md)

   Se si usa spesso lo stesso set di direttive assembly e import, è consigliabile scrivere un processore di direttiva. In ogni modello è possibile richiamare il processore di direttiva, che può caricare gli assembly e i file di modello e impostare il contesto dello spazio dei nomi. Per altre informazioni, vedere [Creazione di processori di direttiva](../modeling/creating-custom-t4-text-template-directive-processors.md)del modello di testo T4 personalizzati .

Se si scrivono i metodi manualmente:

- Se si scrive un modello di testo di runtime, scrivere una definizione di classe parziale con lo stesso nome del modello di testo di runtime. Aggiungere i metodi aggiuntivi in questa classe.

- Scrivere un blocco di controllo della funzionalità di classe `<#+ ... #>` in cui è possibile dichiarare metodi, proprietà e classi private. Quando il modello di testo viene compilato, viene trasformato in una classe . I blocchi di controllo standard e il testo vengono trasformati in un singolo metodo e i blocchi di funzionalità della classe `<#...#>` vengono inseriti come membri separati. Per altre informazioni, vedere [Blocchi di controllo del modello di testo](../modeling/text-template-control-blocks.md).

   I metodi definiti come funzionalità della classe possono anche includere blocchi di testo incorporati.

   Prendere in considerazione l'inserimento delle funzionalità della classe in un file separato che è possibile `<#@include#>` inserire in uno o più file modello.

- Scrivere i metodi in un assembly separato (libreria di classi) e chiamarli dal modello. Usare la direttiva `<#@assembly#>` per caricare l'assembly e `<#@import#>` impostare il contesto dello spazio dei nomi. Si noti che per ricompilare l'assembly durante il debug potrebbe essere necessario arrestare e riavviare Visual Studio. Per altre informazioni, vedere Direttive del modello di [testo T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generare molti file da uno schema del modello
 Se si generano spesso file da modelli con lo stesso schema XML o di database:

- Provare a scrivere un processore di direttiva. In questo modo è possibile sostituire più istruzioni assembly e istruzioni import in ogni modello con una singola direttiva personalizzata. Il processore di direttiva può anche caricare e analizzare il file di modello. Per altre informazioni, vedere [Creazione di processori di direttiva](../modeling/creating-custom-t4-text-template-directive-processors.md)del modello di testo T4 personalizzati .

### <a name="generate-files-from-a-complex-model"></a>Generare file da un modello complesso

- Provare a creare un linguaggio specifico di dominio (DSL) per rappresentare il modello. In questo modo è molto più semplice scrivere i modelli, perché si usano tipi e proprietà che riflettono i nomi degli elementi nel modello. Non è necessario analizzare il file o esplorare i nodi XML. Esempio:

     `foreach (Book book in this.Library) { ... }`

     Per altre informazioni, vedere [Attività iniziali con Domain-Specific e](../modeling/getting-started-with-domain-specific-languages.md) Generazione di codice da un Domain-Specific [linguaggio .](../modeling/generating-code-from-a-domain-specific-language.md)

### <a name="get-data-from-visual-studio"></a>Ottenere dati da Visual Studio
 Per usare i servizi forniti in Visual Studio, impostare `hostSpecific` l'attributo e caricare `EnvDTE` l'assembly. Esempio:

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

### <a name="execute-text-templates-in-the-build-process"></a>Eseguire modelli di testo nel processo di compilazione

- Per altre informazioni, vedere [Generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Domande più generali

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Qual è il modo migliore per iniziare a scrivere un modello di testo?

1. Scrivere un esempio specifico del file generato.

2. Trasformarlo in un modello di testo inserendo la direttiva e le direttive e il codice necessari per caricare il `<#@template #>` file o il modello di input.

3. Sostituire progressivamente parti del file con blocchi di espressioni e di codice.

### <a name="what-is-a-model"></a>Che cos'è un modello?

- Input letto dal modello. Potrebbe essere in un file o in un database. Può trattarsi di XML o di un Visio, di un linguaggio specifico di dominio (DSL) o di un modello UML oppure di testo normale. Potrebbe essere distribuito tra più file. In genere più di un modello legge un modello.

     L'implicazione del termine "modello" è che rappresenta alcuni aspetti dell'azienda più direttamente rispetto al codice del programma generato o ad altri file. Ad esempio, potrebbe rappresentare il piano di una rete di comunicazione che il software generato supervisionerà.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Qual è il vantaggio dell'uso di modelli di testo?
 In genere, si generano più codice o altri file da un modello. Il modello rappresenta i requisiti più direttamente del codice generato. Omette i dettagli di implementazione e viene scritto in termini di requisiti, anziché del codice. Quando i requisiti cambiano, come di solito, è possibile aggiornare il modello in modo più semplice e affidabile rispetto alle diverse parti del codice del programma.

 La generazione di codice è quindi uno strumento utile dal punto di vista dei metodi di sviluppo agile.

### <a name="what-best-practices-are-there-for-text-templates"></a>Quali sono le "procedure consigliate" per i modelli di testo?

- Per altre informazioni, vedere [Linee guida per la scrittura di modelli di testo T4.](../modeling/guidelines-for-writing-t4-text-templates.md)

### <a name="what-is-t4"></a>Che cos'è "T4"?

- Un altro nome per le funzionalità Visual Studio modello di testo descritto qui. La versione precedente, che non è stata pubblicata, era un'abbreviazione di "Trasformazione modello di testo".
