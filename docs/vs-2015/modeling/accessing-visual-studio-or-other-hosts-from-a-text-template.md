---
title: Accesso a Visual Studio o altri host da un modello di testo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5bcd1811db000b39f7c9897f1329434af9fe5258
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527312"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Accesso a Visual Studio o altri host da un modello di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [l'accesso a Visual Studio o altri host da un modello di testo](https://docs.microsoft.com/visualstudio/modeling/accessing-visual-studio-or-other-hosts-from-a-text-template).  
  
In un modello di testo, è possibile usare i metodi e proprietà esposte dall'host che esegue il modello, ad esempio [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Si applica ai modelli di testo normale, i modelli di testo non pre-elaborato.  
  
## <a name="obtaining-access-to-the-host"></a>Ottenere l'accesso all'host  
 Impostare `hostspecific="true"` nella `template` direttiva. Consente di utilizzare `this.Host`, che ha tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Questo tipo dispone di membri che è possibile, ad esempio, utilizzare per risolvere i nomi di file e registrazione degli errori.  
  
### <a name="resolving-file-names"></a>Risoluzione dei nomi di File  
 Per trovare il percorso completo di un file relativo al modello di testo, usare questo. Host.ResolvePath().  
  
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
  
### <a name="displaying-error-messages"></a>Visualizzazione dei messaggi di errore  
 In questo esempio Registra i messaggi quando si trasforma il modello. Se l'host è [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vengono aggiunti alla finestra di errore.  
  
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
  
## <a name="using-the-visual-studio-api"></a>Usando l'API di Visual Studio  
 Se si sta eseguendo un modello di testo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile usare `this.Host` per accedere ai servizi forniti da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e tutti i pacchetti o estensioni caricate.  
  
 Impostare hostspecific = "true" ed eseguire il cast `this.Host` a <xref:System.IServiceProvider>.  
  
 Questo esempio mostra come ottenere il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE>, come un servizio:  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>Uso di hostSpecific con ereditarietà modello  
 Specificare `hostspecific="trueFromBase"` se si usa anche il `inherits` attributo, e se si eredita da un modello che specifica `hostspecific="true"`. Ciò consente di evitare un avviso del compilatore all'effetto che la proprietà `Host` è stata dichiarata due volte.



