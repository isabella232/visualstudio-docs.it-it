---
title: Procedure relative ai modelli di testo
description: Informazioni sulle risposte alle domande comuni riscontrate quando si usano modelli di testo per generare testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50844ce8c6943fcf6b2a0b91c7fd2cfcb6184094
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363185"
---
# <a name="how-to--with-text-templates"></a>Procedure relative ai modelli di testo
I modelli di testo in Visual Studio offrono un modo utile per generare testo di qualsiasi tipo. È possibile usare i modelli di testo per generare testo in fase di esecuzione come parte dell'applicazione e in fase di progettazione per generare parte del codice del progetto. Questo argomento riepiloga le domande più frequenti su "Ricerca per categorie...?" domande.

 In questo argomento vengono proposte alternative diverse risposte precedute da elenchi puntati.

 Per un'introduzione generale ai modelli di testo, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Come si fa...

### <a name="generate-part-of-my-application-code"></a>Genera parte del codice dell'applicazione
 Ho una configurazione o un *modello* in un file o un database. Una o più parti del codice dipendono da tale modello.

- Generare alcuni file di codice dai modelli di testo. Per altre informazioni, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) e [Qual è il modo migliore per iniziare a scrivere un modello?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Genera i file in fase di esecuzione, passando i dati nel modello
 In fase di esecuzione, l'applicazione genera file di testo, ad esempio report, che contengono una combinazione di testo e dati standard. Desidero evitare la scrittura di centinaia di `write` istruzioni.

- Aggiungere un modello di testo di runtime al progetto. Questo modello crea una classe nel codice, che è possibile creare e usare per generare il testo. È possibile passare i dati ad esso nei parametri del costruttore. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Se si desidera generare da modelli disponibili solo in fase di esecuzione, è possibile utilizzare modelli di testo standard. Se si scrive un'estensione di Visual Studio, è possibile richiamare il servizio del modello di testo. Per altre informazioni, vedere [richiamo della trasformazione del testo in un'estensione di Visual](../modeling/invoking-text-transformation-in-a-vs-extension.md)Studio. In altri contesti, è possibile usare il motore del modello di testo. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Utilizzare la \<#@parameter#> direttiva per passare parametri a questi modelli. Per altre informazioni, vedere [direttiva parameter T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Lettura di un altro file di progetto da un modello
 Per leggere un file dallo stesso progetto di Visual Studio del modello:

- Inserire `hostSpecific="true"` nella direttiva `<#@template#>`.

     Nel codice usare `this.Host.ResolvePath(filename)` per ottenere il percorso completo del file.

### <a name="invoke-methods-from-a-template"></a>Richiamare metodi da un modello

Se i metodi sono già presenti, ad esempio, nelle classi .NET:

- Utilizzare la \<#@assembly#> direttiva per caricare l'assembly e utilizzare \<#@import#> per impostare il contesto dello spazio dei nomi. Per altre informazioni, vedere [direttiva import T4](../modeling/t4-import-directive.md).

   Se si utilizza spesso lo stesso set di direttive di assembly e di importazione, è consigliabile scrivere un processore di direttiva. In ogni modello è possibile richiamare il processore di direttiva, che può caricare gli assembly e i file del modello e impostare il contesto dello spazio dei nomi. Per altre informazioni, vedere [creazione di processori di direttive del modello di testo T4 personalizzato](../modeling/creating-custom-t4-text-template-directive-processors.md).

Se si scrivono i metodi manualmente:

- Se si scrive un modello di testo di runtime, scrivere una definizione di classe parziale con lo stesso nome del modello di testo di Runtime. Aggiungere i metodi aggiuntivi in questa classe.

- Scrivere un blocco `<#+ ... #>` di controllo della funzionalità di classe in cui è possibile dichiarare metodi, proprietà e classi private. Quando il modello di testo viene compilato, viene trasformato in una classe. I blocchi di controllo `<#...#>` e il testo standard vengono trasformati in un unico metodo e i blocchi di funzionalità di classe vengono inseriti come membri distinti. Per altre informazioni, vedere [blocchi di controllo del modello di testo](../modeling/text-template-control-blocks.md).

   I metodi definiti come funzionalità di classe possono includere anche blocchi di testo incorporati.

   Si consiglia di inserire le funzionalità di classe in un file separato, che può essere `<#@include#>` inserito in uno o più file di modello.

- Scrivere i metodi in un assembly separato (libreria di classi) e chiamarli dal modello. Utilizzare la `<#@assembly#>` direttiva per caricare l'assembly e `<#@import#>` per impostare il contesto dello spazio dei nomi. Si noti che per ricompilare l'assembly durante il debug, potrebbe essere necessario arrestare e riavviare Visual Studio. Per altre informazioni, vedere [direttive di modello di testo T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generare molti file da uno schema del modello
 Se si generano spesso file da modelli con lo stesso schema di database o XML:

- Prendere in considerazione la scrittura di un processore di direttiva. In questo modo è possibile sostituire più istruzioni assembly e importare istruzioni in ogni modello con una singola direttiva personalizzata. Il processore di direttiva può inoltre caricare e analizzare il file del modello. Per altre informazioni, vedere [creazione di processori di direttive del modello di testo T4 personalizzato](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generare file da un modello complesso

- Provare a creare un linguaggio specifico di dominio (DSL) per rappresentare il modello. In questo modo è molto più semplice scrivere i modelli, perché si usano tipi e proprietà che riflettono i nomi degli elementi nel modello. Non è necessario analizzare il file o spostarsi tra i nodi XML. Ad esempio:

     `foreach (Book book in this.Library) { ... }`

     Per ulteriori informazioni, vedere [Introduzione con Domain-Specific linguaggi](../modeling/getting-started-with-domain-specific-languages.md) e [generazione di codice da un linguaggio di Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Ottenere dati da Visual Studio
 Per usare i servizi forniti in Visual Studio, impostare l' `hostSpecific` attributo e caricare l' `EnvDTE` assembly. Ad esempio:

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

- Per altre informazioni, vedere [generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Domande più generali

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Qual è il modo migliore per iniziare a scrivere un modello di testo?

1. Scrivere un esempio specifico del file generato.

2. Convertirlo in un modello di testo inserendo la `<#@template #>` direttiva e le direttive e il codice necessari per caricare il file o il modello di input.

3. Sostituire progressivamente parti del file con blocchi di codice e di espressione.

### <a name="what-is-a-model"></a>Che cos'è un modello?

- Input letto dal modello. Potrebbe trovarsi in un file o in un database. Potrebbe trattarsi di XML, di un disegno di Visio o di un linguaggio specifico di dominio (DSL) o di un modello UML, oppure potrebbe trattarsi di un testo normale. Potrebbe essere distribuito in diversi file. In genere, più di un modello legge un modello.

     L'implicazione del termine "modello" è che rappresenta un aspetto dell'azienda più direttamente del codice del programma generato o di altri file. Ad esempio, potrebbe rappresentare il piano di una rete di comunicazione che verrà supervisionata dal software generato.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Quali sono i vantaggi dell'utilizzo di modelli di testo?
 In genere, si generano più codice o altri file da un modello. Il modello rappresenta i requisiti più direttamente del codice generato. Omette i dettagli di implementazione e viene scritto in base ai requisiti, anziché al codice. Quando i requisiti cambiano, come in genere, è possibile aggiornare il modello in modo più semplice e affidabile rispetto alle diverse parti del codice programma.

 La generazione del codice è quindi uno strumento prezioso dal punto di vista dei metodi di sviluppo agile.

### <a name="what-best-practices-are-there-for-text-templates"></a>Quali sono le "procedure consigliate" per i modelli di testo?

- Per altre informazioni, vedere [linee guida per la scrittura di modelli di testo T4](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Che cos'è "T4"?

- Un altro nome per le funzionalità del modello di testo di Visual Studio descritte qui. La versione precedente, che non è stata pubblicata, è stata un'abbreviazione per la "trasformazione del modello di testo".
