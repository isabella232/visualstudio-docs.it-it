---
title: Richiamo della trasformazione del testo in un'estensione VS
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ab846d1d7121d0c36c4187d937330d2ade52eb1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594591"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>Richiama trasformazione testo in un'estensione di Visual Studio

Se si scrive un'estensione di Visual Studio, ad esempio un comando di menu o un [linguaggio specifico di dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), è possibile usare il servizio del modello di testo per trasformare i modelli di testo. Ottenere il servizio [STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) ed eseguirne il cast in [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="get-the-text-templating-service"></a>Ottenere il servizio del modello di testo

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="pass-parameters-to-the-template"></a>Passare parametri al modello

 È possibile passare i parametri nel modello. Nel modello è possibile ottenere i valori dei parametri tramite la direttiva `<#@parameter#>`.

 Per il tipo di un parametro, è necessario utilizzare un tipo serializzabile o di cui può essere effettuato il marshalling. In altri termini, è necessario dichiarare il tipo con <xref:System.SerializableAttribute> oppure deve essere derivata da <xref:System.MarshalByRefObject>. Questa restrizione è necessaria perché il modello di testo viene eseguito in un AppDomain separato. Tutti i tipi incorporati, ad esempio **System. String** e **System. Int32** , sono serializzabili.

 Per passare i valori dei parametri, il codice chiamante può inserire i valori nel dizionario `Session` o in <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Nell'esempio seguente per trasformare un modello di testo breve vengono utilizzati entrambi i metodi:

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>Segnalazione errori e direttiva output

Gli eventuali errori che si verificano durante l'elaborazione verranno visualizzati nella finestra di errore di Visual Studio. Inoltre, è possibile ricevere una notifica degli errori specificando un callback che implementi [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

Se si desidera scrivere la stringa di risultato in un file, è utile conoscere quale estensione di file e codifica sono state specificate nella direttiva `<#@output#>` del modello. Anche queste informazioni verranno passate al callback. Per altre informazioni, vedere [direttiva output T4](../modeling/t4-output-directive.md).

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

Il codice può essere testato con un file modello simile a quello seguente:

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

L'avviso del compilatore verrà visualizzato nella finestra di errore di Visual Studio e verrà generata anche una chiamata a `ErrorCallback`.

## <a name="reference-parameters"></a>Parametri per riferimento

È possibile passare i valori da un modello di testo tramite una classe di parametri derivata da <xref:System.MarshalByRefObject>.

## <a name="related-articles"></a>Articoli correlati

Per generare testo da un modello di testo pre-elaborato: chiamare il metodo `TransformText()` della classe generata. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Per generare testo al di fuori di un'estensione di Visual Studio: definire un host personalizzato. Per altre informazioni, vedere [elaborazione di modelli di testo tramite un Host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md).

Per generare codice sorgente che può essere compilato ed eseguito in un secondo momento, chiamare il metodo [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) di [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).
