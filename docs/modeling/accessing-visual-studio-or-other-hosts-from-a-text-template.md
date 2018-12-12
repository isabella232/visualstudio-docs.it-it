---
title: Accesso a Visual Studio o altri host da un modello di testo
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9bb7bce5cb047018540599c9488fa4471dad2d1c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059298"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Accedere a Visual Studio o ad altri host da un modello di testo

In un modello di testo, è possibile usare i metodi e proprietà esposte da host che esegue il modello. Visual Studio è un esempio di un host.

> [!NOTE]
> È possibile usare i metodi di host e le proprietà nei modelli di testo normale, ma non in *pre-elaborato* modelli di testo.

## <a name="obtain-access-to-the-host"></a>Ottenere l'accesso all'host

Per accedere all'host, impostata `hostspecific="true"` nella `template` direttiva. Ora è possibile usare `this.Host`, che ha tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Il <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> tipo dispone di membri che è possibile usare, ad esempio, per risolvere i nomi di file e registrazione degli errori.

### <a name="resolve-file-names"></a>Risolvere i nomi di File

Per trovare il percorso completo di un file relativo al modello di testo, usare `this.Host.ResolvePath()`.

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

In questo esempio Registra i messaggi quando si trasforma il modello. Se l'host si trova Visual Studio, gli errori vengono aggiunti per il **elenco errori**.

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

## <a name="use-the-visual-studio-api"></a>Usare l'API di Visual Studio

Se si sta tentando di eseguire un modello di testo in Visual Studio, è possibile usare `this.Host` per accedere ai servizi forniti da Visual Studio e tutti i pacchetti o le estensioni caricate.

Impostare hostspecific = "true" ed eseguire il cast `this.Host` a <xref:System.IServiceProvider>.

Questo esempio mostra come ottenere l'API di Visual Studio, <xref:EnvDTE.DTE>, come un servizio:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Usare hostSpecific con ereditarietà modello

Specificare `hostspecific="trueFromBase"` se si usa anche il `inherits` attributo, e se si eredita da un modello che specifica `hostspecific="true"`. In caso contrario, si potrebbe ottenere un compilatore che genera l'avviso la proprietà `Host` è stata dichiarata due volte.