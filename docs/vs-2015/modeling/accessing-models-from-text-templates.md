---
title: Accesso ai modelli da modelli di testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e9eba4a919f159462080688c64ed765d3c1fec86
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871977"
---
# <a name="accessing-models-from-text-templates"></a>Accesso ai modelli da modelli di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilizzando i modelli di testo, è possibile creare file di report, file di codice sorgente e altri file di testo basati su modelli di linguaggio specifici di dominio. Per informazioni di base sui modelli di testo, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md). I modelli di testo funzioneranno in modalità sperimentale durante il debug del linguaggio DSL e funzioneranno anche in un computer in cui è stato distribuito il linguaggio DSL.

> [!NOTE]
> Quando si crea una soluzione DSL, nel progetto di debug vengono generati file con  **\*estensione TT** del modello di testo di esempio. Quando si modificano i nomi delle classi di dominio, questi modelli non funzioneranno più. Tuttavia, includono le direttive di base necessarie e forniscono esempi che è possibile aggiornare in base al linguaggio DSL.

 Per accedere a un modello da un modello di testo:

- Impostare la proprietà inherit della direttiva template su [ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). Consente di accedere all'archivio.

- Specificare i processori di direttiva per il DSL a cui si vuole accedere. In questo modo vengono caricati gli assembly per il linguaggio DSL, in modo che sia possibile utilizzare le classi, le proprietà e le relazioni di dominio nel codice del modello di testo. Consente inoltre di caricare il file di modello specificato.

  Un `.tt` file simile all'esempio seguente viene creato nel progetto di debug quando si crea una nuova [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione dal modello di linguaggio DSL minimo.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>

```

 Si notino i punti seguenti sul modello:

- Il modello può utilizzare le classi di dominio, le proprietà e le relazioni definite nella definizione DSL.

- Il modello carica il file del modello specificato nella `requires` proprietà.

- Una proprietà in `this` contiene l'elemento radice. Da qui, il codice può passare ad altri elementi del modello. Il nome della proprietà è in genere uguale alla classe di dominio radice del linguaggio DSL. In questo esempio si tratta di `this.ExampleModel`.

- Sebbene la lingua in cui vengono scritti i frammenti di codice sia C#, è possibile generare testo di qualsiasi tipo. In alternativa, è possibile scrivere il codice [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] in aggiungendo la proprietà `language="VB"` alla `template` direttiva.

- Per eseguire il debug del modello `debug="true"` , aggiungere `template` alla direttiva. Se si verifica un'eccezione, il modello [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene aperto in un'altra istanza di. Se si desidera interrompere il debugger in un punto specifico del codice, inserire l'istruzione`System.Diagnostics.Debugger.Break();`

     Per altre informazioni, vedere [debug di un modello di testo T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Informazioni sul processore di direttiva DSL
 Il modello può usare le classi di dominio definite nella definizione DSL. Questa operazione viene apportata da una direttiva che in genere viene visualizzata in prossimità dell'inizio del modello. Nell'esempio precedente, è il seguente.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Il nome della direttiva ( `MyLanguage`in questo esempio) deriva dal nome del linguaggio DSL. Richiama un processore di *direttiva* generato come parte del linguaggio DSL. Il codice sorgente è reperibile in **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Il processore di direttiva DSL esegue due attività principali:

- Inserisce in modo efficace le direttive di importazione e di assembly nel modello che fa riferimento al linguaggio DSL. In questo modo è possibile usare le classi di dominio nel codice del modello.

- Carica il file specificato nel `requires` parametro e imposta una proprietà in `this` che fa riferimento all'elemento radice del modello caricato.

## <a name="validating-the-model-before-running-the-template"></a>Convalida del modello prima dell'esecuzione del modello
 È possibile fare in modo che il modello venga convalidato prima dell'esecuzione del modello.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>

```

 Si noti che:

1. I `filename` parametri `validation` e sono separati da ";" e non devono essere presenti altri separatori o spazi.

2. L'elenco delle categorie di convalida determina i metodi di convalida che verranno eseguiti. Più categorie devono essere separate da "&#124;" e non devono essere presenti altri separatori o spazi.

   Se viene rilevato un errore, questo verrà segnalato nella finestra degli errori e il file dei risultati conterrà un messaggio di errore.

## <a name="Multiple"></a>Accesso a più modelli da un modello di testo

> [!NOTE]
> Questo metodo consente di leggere più modelli nello stesso modello, ma non supporta riferimenti ModelBus. Per leggere i modelli interconnessi dai riferimenti ModelBus, vedere [utilizzo di Visual Studio ModelBus in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Se si desidera accedere a più di un modello dallo stesso modello di testo, è necessario chiamare il processore di direttiva generato una volta per ogni modello. È necessario specificare il nome file di ogni modello nel `requires` parametro. È necessario specificare i nomi che si desidera utilizzare per la classe di dominio radice nel `provides` parametro. È necessario specificare valori diversi per i `provides` parametri in ogni chiamata di direttiva. Si supponga, ad esempio, di avere tre file di modello denominati Library. xyz, School. xyz e work. xyz. Per accedervi dallo stesso modello di testo, è necessario scrivere tre chiamate di direttiva simili a quelle riportate di seguito.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Questo codice di esempio è relativo a un linguaggio basato sul modello di soluzione per la lingua minima.

 Per accedere ai modelli nel modello di testo, è ora possibile scrivere codice simile al codice riportato nell'esempio seguente.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Caricamento dinamico dei modelli
 Per determinare in fase di esecuzione quali modelli caricare, è possibile caricare un file di modello in modo dinamico nel codice del programma, anziché usare la direttiva specifica del linguaggio DSL.

 Tuttavia, una delle funzioni della direttiva specifica del linguaggio DSL consiste nell'importare lo spazio dei nomi DSL, in modo che il codice del modello possa usare le classi di dominio definite in tale DSL. Poiché non si utilizza la direttiva, è necessario aggiungere  **\<> di assembly** e  **\<importare** direttive > per tutti i modelli che è possibile caricare. Questa operazione è semplice se i diversi modelli che è possibile caricare sono tutte istanze dello stesso DSL.

 Per caricare il file, il metodo più efficace consiste nell'utilizzare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus. In uno scenario tipico, il modello di testo utilizzerà una direttiva specifica del linguaggio DSL per caricare il primo modello nel modo consueto. Tale modello conterrebbe riferimenti ModelBus a un altro modello. È possibile utilizzare ModelBus per aprire il modello a cui si fa riferimento e accedere a un particolare elemento. Per altre informazioni, vedere [tramite ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 In uno scenario meno comune, potrebbe essere necessario aprire un file di modello per il quale si dispone solo di un nome di file e che potrebbe non essere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] presente nel progetto corrente. In questo caso, è possibile aprire il file usando la tecnica descritta in [procedura: Aprire un modello da file nel codice](../modeling/how-to-open-a-model-from-file-in-program-code.md)del programma.

## <a name="generating-multiple-files-from-a-template"></a>Generazione di più file da un modello
 Se si desidera generare più file, ad esempio per generare un file separato per ogni elemento di un modello, esistono diversi approcci possibili. Per impostazione predefinita, viene prodotto un solo file da ogni file modello.

### <a name="splitting-a-long-file"></a>Suddivisione di un file lungo
 In questo metodo si usa un modello per generare un singolo file, separato da un delimitatore. Quindi suddividere il file nelle relative parti. Sono disponibili due modelli, uno per generare il singolo file e l'altro per suddividerlo.

 **LoopTemplate. T4** genera il file Long Single. Si noti che l'estensione di file è ". T4", perché non deve essere elaborata direttamente quando si fa clic su **trasforma tutti i modelli**. Questo modello accetta un parametro che specifica la stringa del delimitatore che separa i segmenti:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>

```

 `LoopSplitter.tt``LoopTemplate.t4`richiama, quindi suddivide il file risultante nei segmenti. Si noti che questo modello non deve essere un modello di modellazione, perché non legge il modello.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>

```
