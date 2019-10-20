---
title: Accesso a Visual Studio o altri host da un modello di testo
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652370"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Accedere a Visual Studio o altri host da un modello di testo

In un modello di testo, è possibile utilizzare i metodi e le proprietà esposti dall'host che esegue il modello. Visual Studio è un esempio di host.

> [!NOTE]
> È possibile usare i metodi e le proprietà dell'host nei modelli di testo normali, ma non nei modelli di testo *pre-elaborati* .

## <a name="obtain-access-to-the-host"></a>Ottenere l'accesso all'host

Per accedere all'host, impostare `hostspecific="true"` nella direttiva `template`. A questo punto è possibile usare `this.Host`, il cui tipo è [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Il tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) dispone di membri che è possibile usare per risolvere i nomi di file e registrare gli errori, ad esempio.

### <a name="resolve-file-names"></a>Risolvere i nomi di file

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

### <a name="display-error-messages"></a>Visualizza messaggi di errore

Questo esempio registra i messaggi quando si trasforma il modello. Se l'host è Visual Studio, gli errori vengono aggiunti all' **Elenco errori**.

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

Se si sta eseguendo un modello di testo in Visual Studio, è possibile usare `this.Host` per accedere ai servizi forniti da Visual Studio ed eventuali pacchetti o estensioni caricati.

Impostare hostspecific = "true" ed eseguire il cast `this.Host` <xref:System.IServiceProvider>.

Questo esempio Mostra come ottenere l'API di Visual Studio, <xref:EnvDTE.DTE> come servizio:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Usare hostSpecific con ereditarietà dei modelli

Specificare `hostspecific="trueFromBase"` se si usa anche l'attributo `inherits` e se si eredita da un modello che specifica `hostspecific="true"`. In caso contrario, è possibile che venga visualizzato un avviso del compilatore che indica che la proprietà `Host` è stata dichiarata due volte.