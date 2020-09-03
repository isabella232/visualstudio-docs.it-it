---
title: Metodi di utilità per i modelli di testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c38b15a3b819ce561c098c3b9810ee6884e526b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658528"
---
# <a name="text-template-utility-methods"></a>Metodi di utilità per i modelli di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esistono diversi metodi che sono sempre disponibili quando si scrive il codice in un modello di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] testo. Questi metodi sono definiti in <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> È anche possibile usare altri metodi e servizi forniti dall'ambiente host in un modello di testo normale (non pre-elaborato). Ad esempio, è possibile risolvere i percorsi di file, registrare gli errori e ottenere i servizi forniti da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e tutti i pacchetti caricati.  Per altre informazioni, vedere [accesso a Visual Studio da un modello di testo](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Metodi Write
 È possibile utilizzare i `Write()` `WriteLine()` metodi e per aggiungere testo all'interno di un blocco di codice standard, anziché utilizzare un blocco di codice di espressione. I due blocchi di codice seguenti sono funzionalmente equivalenti.

##### <a name="code-block-with-an-expression-block"></a>Blocco di codice con un blocco Expression

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

##### <a name="code-block-using-writeline"></a>Blocco di codice con WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

 Potrebbe essere utile usare uno di questi metodi di utilità anziché un blocco di espressione all'interno di un blocco di codice lungo con strutture di controllo annidate.

 I `Write()` `WriteLine()` metodi e hanno due overload, uno che accetta un solo parametro di stringa e uno che accetta una stringa di formato composita più una matrice di oggetti da includere nella stringa (come il `Console.WriteLine()` metodo). I due utilizzi seguenti di `WriteLine()` sono funzionalmente equivalenti:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Metodi di rientro
 È possibile utilizzare i metodi di rientro per formattare l'output del modello di testo. La <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> classe dispone di una `CurrentIndent` proprietà di stringa che mostra il rientro corrente nel modello di testo e un `indentLengths` campo che è un elenco dei rientri che sono stati aggiunti. È possibile aggiungere un rientro con il `PushIndent()` metodo e sottrarre un rientro con il `PopIndent()` metodo. Se si desidera rimuovere tutti i rientri, utilizzare il `ClearIndent()` metodo. Il blocco di codice seguente illustra l'uso di questi metodi:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

 Questo blocco di codice produce l'output seguente:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Metodi di errore e di avviso
 È possibile utilizzare i metodi di utilità Error e Warning per aggiungere messaggi al [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Elenco errori. Il codice seguente, ad esempio, aggiungerà un messaggio di errore al Elenco errori.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Accesso a host e provider di servizi
 La proprietà `this.Host` può fornire l'accesso alle proprietà esposte dall'host che esegue il modello. Per utilizzare `this.Host` , è necessario impostare `hostspecific` l'attributo nella `<@template#>` direttiva:

 `<#@template ... hostspecific="true" #>`

 Il tipo di `this.Host` dipende dal tipo di host in cui è in esecuzione il modello. In un modello in cui è in esecuzione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , è possibile eseguire il cast `this.Host` a per `IServiceProvider` ottenere l'accesso ai servizi, ad esempio l'IDE. Ad esempio:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Uso di un set diverso di metodi di utilità
 Come parte del processo di generazione del testo, il file modello viene trasformato in una classe, che è sempre denominata `GeneratedTextTransformation` ed eredita da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Se invece si vuole usare un diverso set di metodi, è possibile scrivere una classe personalizzata e specificarla nella direttiva template. La classe deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

 Utilizzare la `assembly` direttiva per fare riferimento all'assembly in cui è possibile trovare la classe compilata.
