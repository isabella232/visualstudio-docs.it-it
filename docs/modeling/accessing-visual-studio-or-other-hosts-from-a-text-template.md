---
title: Accesso a Visual Studio o altri host da un modello di testo
description: Informazioni su come usare metodi e proprietà in un modello di testo esposti dall'host che esegue il modello.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5a812279046bf1b2eb987719762098697ddd8eb1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710206"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Accedere Visual Studio o altri host da un modello di testo

In un modello di testo è possibile usare i metodi e le proprietà esposti dall'host che esegue il modello. Visual Studio è un esempio di host.

> [!NOTE]
> È possibile usare proprietà e metodi host nei modelli di testo normali, ma non nei *modelli di testo pre-elaborato.*

## <a name="obtain-access-to-the-host"></a>Ottenere l'accesso all'host

Per accedere all'host, `hostspecific="true"` impostare nella `template` direttiva . A questo punto è possibile `this.Host` usare , che è di tipo [ITextTemplatingEngineHost.](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) Il [tipo ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) include membri che è possibile usare per risolvere i nomi di file e registrare gli errori, ad esempio.

### <a name="resolve-file-names"></a>Risolvere i nomi di file

Per trovare il percorso completo di un file relativo al modello di testo, usare `this.Host.ResolvePath()` .

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Visualizzare i messaggi di errore

Questo esempio registra i messaggi quando si trasforma il modello. Se l'host è Visual Studio, gli errori vengono aggiunti **all'Elenco errori**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Usare l'API Visual Studio

Se si esegue un modello di testo in Visual Studio, è possibile usare per accedere ai servizi forniti da Visual Studio ed eventuali pacchetti o estensioni `this.Host` caricati.

Impostare hostspecific="true" ed eseguire il cast `this.Host` su <xref:System.IServiceProvider> .

Questo esempio ottiene l'API Visual Studio, <xref:EnvDTE.DTE> , come servizio:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Usare hostSpecific con ereditarietà del modello

Specificare `hostspecific="trueFromBase"` se si usa anche `inherits` l'attributo e se si eredita da un modello che specifica `hostspecific="true"` . In caso contrario, è possibile che venga visualizzato un avviso del compilatore che indica che la proprietà `Host` è stata dichiarata due volte.
