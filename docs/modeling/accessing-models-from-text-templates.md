---
title: Accesso ai modelli da modelli di testo
description: Informazioni su come usare modelli di testo per creare file di report, file di codice sorgente e altri file di testo basati su modelli linguistici specifici del dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 451f9963b61d213b8aa95fe83ab68806d6c88bdc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027825"
---
# <a name="access-models-from-text-templates"></a>Accedere ai modelli da modelli di testo

Usando modelli di testo, è possibile creare file di report, file di codice sorgente e altri file di testo basati su modelli linguistici specifici del dominio. Per informazioni di base sui modelli di testo, vedere [Generazione di codice e Modelli di testo T4.](../modeling/code-generation-and-t4-text-templates.md) I modelli di testo funzionano in modalità sperimentale durante il debug del DSL e funzionano anche in un computer in cui è stato distribuito il DSL.

> [!NOTE]
> Quando si crea una soluzione DSL, nel progetto di debug vengono generati file con estensione **\* tt** del modello di testo di esempio. Quando si modificano i nomi delle classi di dominio, questi modelli non funzionano più. Tuttavia, includono le direttive di base necessarie e forniscono esempi che è possibile aggiornare in modo che corrispondano al linguaggio DSL.

 Per accedere a un modello da un modello di testo:

- Impostare la proprietà inherit della direttiva del modello su [Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). In questo modo è possibile accedere a Store.

- Specificare i processori di direttiva per il DSL a cui si vuole accedere. In questo modo vengono caricati gli assembly per il DSL in modo da poterne usare le classi di dominio, le proprietà e le relazioni nel codice del modello di testo. Carica anche il file di modello specificato.

  Un file simile all'esempio seguente viene creato nel progetto debug quando si crea una nuova soluzione Visual Studio dal modello `.tt` linguaggio minimo DSL.

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

 Si notino i punti seguenti su questo modello:

- Il modello può usare le classi di dominio, le proprietà e le relazioni definite nella definizione DSL.

- Il modello carica il file di modello specificato nella `requires` proprietà .

- Una proprietà in `this` contiene l'elemento radice. Da qui, il codice può passare ad altri elementi del modello. Il nome della proprietà è in genere uguale alla classe di dominio radice del DSL. In questo esempio si tratta di `this.ExampleModel`.

- Anche se il linguaggio in cui vengono scritti i frammenti di codice è C#, è possibile generare testo di qualsiasi tipo. In alternativa, è possibile scrivere il codice in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aggiungendo la proprietà alla direttiva `language="VB"` `template` .

- Per eseguire il debug del modello, `debug="true"` aggiungere alla `template` direttiva . Il modello verrà aperto in un'altra istanza Visual Studio se si verifica un'eccezione. Se si vuole interrompere l'esecuzione nel debugger in un punto specifico del codice, inserire l'istruzione `System.Diagnostics.Debugger.Break();`

   Per altre informazioni, vedere [Debug di un modello di testo T4.](../modeling/debugging-a-t4-text-template.md)

## <a name="about-the-dsl-directive-processor"></a>Informazioni sul processore di direttiva DSL
 Il modello può usare le classi di dominio definite nella definizione DSL. Ciò avviene tramite una direttiva che in genere appare vicino all'inizio del modello. Nell'esempio precedente è il seguente.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Il nome della direttiva ( `MyLanguage` , in questo esempio) è derivato dal nome del DSL. Richiama un *processore di* direttiva generato come parte del DSL. È possibile trovare il codice sorgente in **Dsl\GeneratedCode\DirectiveProcessor.cs.**

 Il processore di direttiva DSL esegue due attività principali:

- Inserisce in modo efficace le direttive assembly e import nel modello che fa riferimento al DSL. In questo modo è possibile usare le classi di dominio nel codice del modello.

- Carica il file specificato nel parametro e imposta una proprietà in che fa riferimento all'elemento `requires` `this` radice del modello caricato.

## <a name="validating-the-model-before-running-the-template"></a>Convalida del modello prima dell'esecuzione del modello
 È possibile fare in modo che il modello venga convalidato prima dell'esecuzione del modello.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Si noti che:

1. I parametri e sono separati da ";" e non devono essere presenti `filename` `validation` altri separatori o spazi.

2. L'elenco delle categorie di convalida determina quali metodi di convalida verranno eseguiti. Più categorie devono essere separate da "&#124;" e non devono essere presenti altri separatori o spazi.

   Se viene rilevato un errore, verrà segnalato nella finestra degli errori e il file dei risultati conterrà un messaggio di errore.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> Accesso a più modelli da un modello di testo

> [!NOTE]
> Questo metodo consente di leggere più modelli nello stesso modello, ma non supporta i riferimenti ModelBus. Per leggere i modelli collegati dai riferimenti ModelBus, vedere Uso di [Visual Studio ModelBus in un modello di testo.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 Se si desidera accedere a più di un modello dallo stesso modello di testo, è necessario chiamare il processore di direttiva generato una volta per ogni modello. È necessario specificare il nome file di ogni modello nel `requires` parametro . È necessario specificare i nomi da usare per la classe di dominio radice nel `provides` parametro . È necessario specificare valori diversi per i `provides` parametri in ognuna delle chiamate di direttiva. Si supponga, ad esempio, di avere tre file di modello denominati Library.xyz, School.xyz e Work.xyz. Per accedervi dallo stesso modello di testo, è necessario scrivere tre chiamate di direttiva simili alle seguenti.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Questo codice di esempio è per un linguaggio basato sul modello di soluzione Linguaggio minimo.

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

## <a name="loading-models-dynamically"></a>Caricamento dinamico dei modelli
 Se si desidera determinare in fase di esecuzione quali modelli caricare, è possibile caricare dinamicamente un file di modello nel codice del programma, anziché usare la direttiva specifica del DSL.

 Tuttavia, una delle funzioni della direttiva specifica di DSL è importare lo spazio dei nomi DSL, in modo che il codice del modello possa usare le classi di dominio definite in tale DSL. Poiché non si usa la direttiva , è necessario aggiungere le direttive **\<assembly>** e per tutti i modelli che è possibile **\<import>** caricare. Questo è semplice se i diversi modelli che è possibile caricare sono tutte istanze dello stesso DSL.

 Per caricare il file, il metodo più efficace è l'uso Visual Studio ModelBus. In uno scenario tipico, il modello di testo userà una direttiva specifica di DSL per caricare il primo modello nel modo consueto. Tale modello conterrà riferimenti ModelBus a un altro modello. È possibile usare ModelBus per aprire il modello a cui si fa riferimento e accedere a un particolare elemento. Per altre informazioni, vedere [Uso Visual Studio ModelBus in un modello di testo.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 In uno scenario meno comune, potrebbe essere necessario aprire un file di modello per il quale si dispone solo di un nome file e che potrebbe non essere presente nel progetto Visual Studio corrente. In questo caso, è possibile aprire il file usando la tecnica descritta in [Procedura: Aprire un](../modeling/how-to-open-a-model-from-file-in-program-code.md)modello da file nel codice programma .

## <a name="generating-multiple-files-from-a-template"></a>Generazione di più file da un modello
 Se si desidera generare diversi file, ad esempio per generare un file separato per ogni elemento di un modello, esistono diversi approcci possibili. Per impostazione predefinita, da ogni file modello viene generato un solo file.

### <a name="splitting-a-long-file"></a>Suddivisione di un file lungo
 In questo metodo si usa un modello per generare un singolo file, separato da un delimitatore. Suddividere quindi il file nelle relative parti. Sono disponibili due modelli, uno per generare il singolo file e l'altro per dividerlo.

 **LoopTemplate.t4 genera** il singolo file lungo. Si noti che l'estensione del file è ".t4", perché non deve essere elaborata direttamente quando si fa clic **su Trasforma tutti i modelli**. Questo modello accetta un parametro che specifica la stringa di delimitazione che separa i segmenti:

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

 `LoopSplitter.tt` richiama `LoopTemplate.t4` e quindi suddivide il file risultante in segmenti. Si noti che questo modello non deve essere un modello di modellazione, perché non legge il modello.

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
