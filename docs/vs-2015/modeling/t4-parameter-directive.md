---
title: T4 Direttiva Parameter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e350b353d90143a0805455b29bfe0a14aad25cb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411607"
---
# <a name="t4-parameter-directive"></a>Direttiva parameter T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modello di testo, il `parameter` direttiva dichiara le proprietà nel codice del modello che sono inizializzate da valori passati dal contesto esterno. È possibile impostare questi valori se si scrive codice che richiama trasformazione del testo.  
  
## <a name="using-the-parameter-directive"></a>Utilizzo della direttiva di parametro  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 Il `parameter` direttiva dichiara le proprietà nel codice del modello che sono inizializzate da valori passati dal contesto esterno. È possibile impostare questi valori se si scrive codice che richiama trasformazione del testo. I valori possono essere passati nel `Session` dizionario, o in <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 È possibile dichiarare parametri di qualsiasi tipo utilizzabile in remoto. Vale a dire, il tipo deve essere dichiarato con <xref:System.SerializableAttribute>, o deve derivare da <xref:System.MarshalByRefObject>. In questo modo i valori dei parametri da passare in dominio applicazione in cui viene elaborato il modello.  
  
 Ad esempio, è possibile scrivere un modello di testo con il contenuto seguente:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Passaggio dei valori di parametro a un modello  
 Se si sta scrivendo un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione, ad esempio un comando di menu o un gestore eventi, è possibile elaborare un modello usando il servizio del modello di testo:  
  
```csharp  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## <a name="passing-values-in-the-call-context"></a>Passaggio di valori nel contesto di chiamata  
 In alternativa è possibile passare valori come dati logici in <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Nell'esempio seguente passa i valori usando entrambi i metodi:  
  
```csharp  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Passare valori a un modello di testo (pre-elaborato) in fase di esecuzione  
 Non è in genere necessario usare il `<#@parameter#>` direttiva con modelli di testo (pre-elaborato) in fase di esecuzione. In alternativa, è possibile definire un costruttore aggiuntivo o una proprietà da impostare per il codice generato, tramite cui passare valori di parametri. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Tuttavia, se si desidera utilizzare `<#@parameter>` in un modello in fase di esecuzione, è possibile passare valori a esso utilizzando il dizionario di sessione. Ad esempio, supponiamo di avere creato il file come modello di pre-elaborato chiamato `PreTextTemplate1`. È possibile richiamare il modello nel programma mediante il codice seguente.  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>Recupero di argomenti da TextTemplate.exe  
  
> [!IMPORTANT]
> Il `parameter` direttiva non recupera i valori impostati nella `–a` parametro del `TextTransform.exe` utilità. Per ottenere questi valori, impostare `hostSpecific="true"` nella `template` direttiva e utilizzare `this.Host.ResolveParameterValue("","","argName")`.
