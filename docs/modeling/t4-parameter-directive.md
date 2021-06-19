---
title: Direttiva parameter T4
description: Si noti che in Visual Studio la direttiva parameter dichiara le proprietà nel codice del modello inizializzate dai valori passati dal contesto esterno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386098"
---
# <a name="t4-parameter-directive"></a>Direttiva parameter T4

In un Visual Studio di testo, la direttiva dichiara le proprietà nel codice del modello inizializzate dai valori `parameter` passati dal contesto esterno. È possibile impostare questi valori se si scrive codice che richiama la trasformazione del testo.

## <a name="using-the-parameter-directive"></a>Uso della direttiva Parameter

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 La `parameter` direttiva dichiara le proprietà nel codice del modello inizializzate dai valori passati dal contesto esterno. È possibile impostare questi valori se si scrive codice che richiama la trasformazione del testo. I valori possono essere passati nel `Session` dizionario o in <xref:System.Runtime.Remoting.Messaging.CallContext> .

 È possibile dichiarare parametri di qualsiasi tipo utilizzabile in remoto. Ciò significa che il tipo deve essere dichiarato con <xref:System.SerializableAttribute> oppure deve derivare da <xref:System.MarshalByRefObject> . In questo modo i valori dei parametri possono essere passati nell'AppDomain in cui viene elaborato il modello.

 Ad esempio, è possibile scrivere un modello di testo con il contenuto seguente:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Passaggio dei valori dei parametri a un modello
 Se si scrive un'estensione Visual Studio, ad esempio un comando di menu o un gestore eventi, è possibile elaborare un modello usando il servizio di creazione di modelli di testo:

```csharp
// Get a service provider - how you do this depends on the context:
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
 In alternativa, è possibile passare valori come dati logici in <xref:System.Runtime.Remoting.Messaging.CallContext> .

 L'esempio seguente passa i valori usando entrambi i metodi:

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Passaggio di valori a un Run-Time di testo (pre-elaborato)
 In genere non è necessario usare la direttiva con modelli di testo `<#@parameter#>` di run-time (pre-elaborati). È invece possibile definire un costruttore aggiuntivo o una proprietà impostabile per il codice generato, tramite il quale si passano i valori dei parametri. Per altre informazioni, vedere [Generazione di testo di run-time con modelli di testo T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

 Tuttavia, se si vuole usare in un modello di run-time, è possibile passarvi i valori `<#@parameter>` usando il dizionario Session. Si supponga, ad esempio, di aver creato il file come modello pre-elaborato denominato `PreTextTemplate1` . È possibile richiamare il modello nel programma usando il codice seguente.

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
> La `parameter` direttiva non recupera i valori impostati nel parametro `-a` `TextTransform.exe` dell'utilità . Per ottenere tali valori, `hostSpecific="true"` impostare nella direttiva e usare `template` `this.Host.ResolveParameterValue("","","argName")` .
