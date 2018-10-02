---
title: Accesso ai modelli da modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6c05befbfa59063956d0df37a7aa57d955503ec5
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860342"
---
# <a name="accessing-models-from-text-templates"></a>Accesso ai modelli da modelli di testo
Usando i modelli di testo, è possibile creare file di report, file di codice sorgente e altri file di testo che si basano sui modelli di linguaggio specifico di dominio. Per informazioni di base sui modelli di testo, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md). I modelli di testo funzioneranno in modalità sperimentale quando si esegue il debug del linguaggio DSL e funzioneranno anche in un computer in cui è stato distribuito il linguaggio DSL.

> [!NOTE]
>  Quando si crea una soluzione DSL, modello di testo di esempio  **\*tt** vengono generati i file nel progetto di debug. Quando si modificano i nomi delle classi di dominio, questi modelli non funzionerà più. Tuttavia, includono le direttive di base che è necessario e vengono forniti esempi che è possibile aggiornare in modo che corrisponda al linguaggio DSL.

 Per accedere a un modello da un modello di testo:

-   Impostare la proprietà di ereditarietà della direttiva del modello per <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Ciò fornisce accesso alla Store.

-   Specificare i processori di direttiva per il linguaggio DSL che si desidera accedere. Ciò consente di caricare gli assembly per il linguaggio DSL in modo che è possibile usare le classi di dominio, le proprietà e relazioni nel codice del modello di testo. Permette inoltre di caricare il file del modello specificato.

 Oggetto `.tt` file simili all'esempio seguente viene creato nel progetto di debug quando si crea una nuova soluzione di Visual Studio dal modello DSL del linguaggio minimo.

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

 Notare gli aspetti seguenti su questo modello:

-   Il modello è possibile usare le classi di dominio, proprietà e relazioni definite nella definizione DSL.

-   Il modello viene caricato il file del modello specificato nella `requires` proprietà.

-   Una proprietà in `this` contiene l'elemento radice. Da qui, il codice può passare agli altri elementi del modello. Il nome della proprietà è in genere quello utilizzato per la classe di dominio di primo livello del linguaggio DSL. In questo esempio si tratta di `this.ExampleModel`.

-   Anche se la lingua in cui vengono scritti i frammenti di codice c#, è possibile generare il testo di qualsiasi tipo. In alternativa, è possibile scrivere il codice [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aggiungendo la proprietà `language="VB"` per il `template` direttiva.

-   Per eseguire il debug del modello, aggiungere `debug="true"` per il `template` direttiva. Il modello verrà aperto in un'altra istanza di Visual Studio se si verifica un'eccezione. Se si desidera interrompere il debugger in un momento specifico nel codice, l'istruzione insert `System.Diagnostics.Debugger.Break();`

     Per altre informazioni, vedere [debug di un modello di testo T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Sul processore di direttiva del DSL
 Il modello può utilizzare le classi di dominio definite nella definizione DSL. Ciò è dovuta a una direttiva che in genere viene visualizzato all'inizio del modello. Nell'esempio precedente, è il seguente.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Il nome della direttiva ( `MyLanguage`, in questo esempio) viene derivato dal nome del linguaggio DSL. Richiama un *processore di direttiva* che viene generato come parte del linguaggio DSL. È possibile trovare il codice sorgente nel **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Il processore di direttiva del DSL esegue due attività principali:

-   Inserisce in modo efficace le direttive di importazione e assembly nel modello che fa riferimento al linguaggio DSL. Ciò consente di usare le classi di dominio nel codice del modello.

-   Carica il file specificato nella `requires` parametro e imposta una proprietà in `this` che fa riferimento all'elemento radice del modello caricato.

## <a name="validating-the-model-before-running-the-template"></a>La convalida del modello prima di eseguire il modello
 È possibile generare il modello da convalidare prima che il modello viene eseguito.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>

```

 Si noti che:

1.  Il `filename` e `validation` parametri sono separati da ";" e non deve essere presente alcun altri separatori o spazi.

2.  L'elenco di categorie di convalida determina quali metodi di convalida verranno eseguiti. Più categorie devono essere separate da "&#124;" e non deve essere presente alcun altri separatori o spazi.

 Se viene rilevato un errore, verrà segnalato nella finestra degli errori e il file di risultati conterrà un messaggio di errore.

## <a name="Multiple"></a> L'accesso a più modelli da un modello di testo

> [!NOTE]
>  Questo metodo consente di leggere più modelli nello stesso modello, ma non supporta riferimenti ModelBus. Per leggere i modelli che sono collegate tra esse tramite riferimenti ModelBus, vedere [tramite ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Se si desidera accedere a più di un modello dallo stesso modello di testo, è necessario chiamare il processore di direttiva generato una sola volta per ogni modello. È necessario specificare il nome del file di ogni modello nella `requires` parametro. È necessario specificare i nomi che si desidera utilizzare per la classe di dominio radice nel `provides` parametro. È necessario specificare valori diversi per il `provides` parametri in ognuna delle chiamate di direttiva. Ad esempio, si supponga di avere tre file modello chiamati Library.xyz School.xyz e Work.xyz. Per accedere ad essi dallo stesso modello di testo, è necessario scrivere tre chiamate simili a quelle seguenti.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  Questo esempio di codice è per una lingua che si basa sul modello di soluzione di linguaggio minimo.

 Per accedere ai modelli nel modello di testo, è ora possibile scrivere codice simile al codice nell'esempio seguente.

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

## <a name="loading-models-dynamically"></a>Caricamento di modelli in modo dinamico
 Se si desidera determinare in fase di esecuzione per caricare i modelli, è possibile caricare un file di modello in modo dinamico nel codice del programma, invece di usare la direttiva di linguaggio specifico di dominio specifico.

 Tuttavia, una delle funzioni della direttiva DSL specifici è importare lo spazio dei nomi di linguaggio specifico di dominio, in modo che il codice del modello può usare le classi di dominio definite in tale linguaggio DSL. Poiché non si usa la direttiva, è necessario aggiungere  **\<assembly >** e  **\<importare >** direttive per tutti i modelli che è possibile caricare. È semplice se i diversi modelli che è possibile caricare sono tutte le istanze del DSL stesso.

 Per caricare il file, il metodo più efficace consiste nell'usare ModelBus di Visual Studio. In uno scenario tipico, il modello di testo userà una direttiva del DSL specifici per caricare il primo modello nel modo consueto. Questo modello contiene un riferimento ModelBus a un altro modello. Per aprire il modello di cui viene fatto riferimento e accedere a un particolare elemento, è possibile usare ModelBus. Per altre informazioni, vedere [tramite ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 In uno scenario meno comune, si potrebbe voler aprire un file di modello per cui si dispone solo un nome di file, e che potrebbero non essere il progetto di Visual Studio corrente. In questo caso, è possibile aprire il file usando la tecnica descritta in [procedura: aprire un modello da File nel codice programma](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Generazione di più file da un modello
 Se si desidera generare un file diversi - ad esempio, per generare un file separato per ogni elemento in un modello, esistono diversi approcci disponibili. Per impostazione predefinita, un solo file viene generato da ogni file di modello.

### <a name="splitting-a-long-file"></a>Suddivisione di un file di lunga durata
 In questo metodo, si usa un modello per generare un singolo file, separato da un delimitatore. Quindi il file suddiviso in sue parti. Esistono due modelli, uno per generare il singolo file e l'altro dividere i dati.

 **LoopTemplate.t4** genera il file singolo lungo. Si noti che l'estensione del file è ".t4", perché non deve essere elaborato direttamente quando fa clic su **Trasforma tutti i modelli**. Questo modello accetta un parametro che specifica la stringa delimitatore che separa i segmenti:

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

 `LoopSplitter.tt` richiama `LoopTemplate.t4`e quindi suddivide il file risultante in segmenti. Si noti che questo modello non deve essere un modello di modellazione, perché non leggere il modello.

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