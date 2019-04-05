---
title: Metodi di utilità Configurazione di modelli di testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84f5b5de8b28062023d851e38e26930718d599e7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968479"
---
# <a name="text-template-utility-methods"></a>Metodi di utilità per i modelli di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esistono diversi metodi che sono sempre disponibili quando si scrive codice un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modello di testo. Questi metodi sono definiti <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  È anche possibile usare altri metodi e i servizi forniti dall'ambiente host in un normale modello di testo (non pre-elaborato). Ad esempio, è possibile risolvere i percorsi dei file, registrare gli errori e ottenere servizi forniti da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e qualsiasi pacchetto caricato.  Per altre informazioni, vedere [l'accesso a Visual Studio da un modello di testo](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Scrivere metodi  
 È possibile usare la `Write()` e `WriteLine()` metodi per aggiungere un testo in un blocco di codice standard, invece di usare un blocco di codice di espressione. I blocchi di codice seguenti sono funzionalmente equivalenti.  
  
##### <a name="code-block-with-an-expression-block"></a>Blocco di codice con un blocco di espressione  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Blocco di codice usando WriteLine)  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Potrebbe essere utile usare uno di questi metodi di utilità anziché un blocco di espressione all'interno di un blocco di codice lunghi con strutture di controllo annidate.  
  
 Il `Write()` e `WriteLine()` metodi dispongono di due overload, uno che accetta un singolo parametro stringa e uno che accetta una stringa di formato composito oltre a una matrice di oggetti da includere nella stringa di (ad esempio il `Console.WriteLine()` (metodo)). I seguenti due utilizzi di `WriteLine()` sono funzionalmente equivalenti:  
  
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
 È possibile utilizzare i metodi di rientro per formattare l'output del modello di testo. Il <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> classe ha un `CurrentIndent` proprietà stringa che mostra il rientro corrente nel modello di testo e un `indentLengths` campo che rappresenta un elenco dei rientri che sono stati aggiunti. È possibile aggiungere un rientro con il `PushIndent()` metodo e ridurre un rientro con la `PopIndent()` (metodo). Se si desidera rimuovere tutti i rientri, usare il `ClearIndent()` (metodo). Blocco di codice seguente illustra l'uso di questi metodi:  
  
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
  
## <a name="error-and-warning-methods"></a>Errori e i metodi di avviso  
 È possibile usare i metodi di utilità di errore e avviso per aggiungere messaggi al [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] elenco errori. Il codice seguente, ad esempio, aggiungerà un messaggio di errore per l'elenco errori.  
  
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
  
## <a name="access-to-host-and-service-provider"></a>Accesso a Host e Provider di servizi  
 La proprietà `this.Host` può fornire l'accesso alle proprietà esposte dall'host che sta eseguendo il modello. Per utilizzare `this.Host`, è necessario impostare `hostspecific` attributo il `<@template#>` direttiva:  
  
 `<#@template ... hostspecific="true" #>`  
  
 Il tipo di `this.Host` dipende dal tipo di host in cui viene eseguito il modello. In un modello che è in esecuzione nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile eseguire il cast `this.Host` a `IServiceProvider` per accedere ai servizi, ad esempio l'IDE. Ad esempio:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>Usando un diverso set di metodi di utilità  
 Come parte del processo di generazione di testo, il file del modello viene trasformato in una classe, che è sempre denominata `GeneratedTextTransformation`ed eredita da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Se si desidera utilizzare un diverso set di metodi, è possibile scrivere una classe personalizzata e specificarlo nella direttiva del modello. La classe deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Usare il `assembly` direttiva per fare riferimento all'assembly di cui è possibile trovare la classe compilata.
