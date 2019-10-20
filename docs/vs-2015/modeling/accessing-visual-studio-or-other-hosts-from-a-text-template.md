---
title: Accesso a Visual Studio 2015 o ad altri host da un modello di testo | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655330"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Accesso a Visual Studio o altri host da un modello di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un modello di testo, è possibile utilizzare i metodi e le proprietà esposti dall'host che esegue il modello, ad esempio [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Si applica ai modelli di testo normali, non ai modelli di testo pre-elaborati.

## <a name="obtaining-access-to-the-host"></a>Ottenere l'accesso all'host

Impostare `hostspecific="true"` nella direttiva `template`. In questo modo è possibile utilizzare `this.Host`, il cui tipo è [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Questo tipo dispone di membri che è possibile usare, ad esempio, per risolvere i nomi di file e registrare gli errori.

### <a name="resolving-file-names"></a>Risoluzione dei nomi di file
 Per trovare il percorso completo di un file relativo al modello di testo, usare questa. Host. ResolvePath ().

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

### <a name="displaying-error-messages"></a>Visualizzazione di messaggi di errore
 Questo esempio registra i messaggi quando si trasforma il modello. Se l'host è [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vengono aggiunti alla finestra di errore.

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

## <a name="using-the-visual-studio-api"></a>Uso dell'API di Visual Studio
 Se si esegue un modello di testo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile usare `this.Host` per accedere ai servizi forniti da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ed eventuali pacchetti o estensioni caricati.

 Impostare hostspecific = "true" ed eseguire il cast `this.Host` <xref:System.IServiceProvider>.

 Questo esempio Mostra come ottenere l'API [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], <xref:EnvDTE.DTE>, come servizio:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Uso di hostSpecific con ereditarietà dei modelli
 Specificare `hostspecific="trueFromBase"` se si usa anche l'attributo `inherits` e se si eredita da un modello che specifica `hostspecific="true"`. In questo modo si evita un avviso del compilatore per l'effetto che la proprietà `Host` è stata dichiarata due volte.
