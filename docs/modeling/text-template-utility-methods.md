---
title: Metodi di utilità per i modelli di testo
description: Informazioni sui vari metodi di utilità dei modelli di testo disponibili quando si scrive codice in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 7ee6eff6c47a818eca29673b5aad6905e6f52e28
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637316"
---
# <a name="text-template-utility-methods"></a>Metodi di utilità per i modelli di testo

Esistono diversi metodi che sono sempre disponibili per l'utente quando si scrive codice in un modello Visual Studio testo. Questi metodi sono definiti in <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> È anche possibile usare altri metodi e servizi forniti dall'ambiente host in un modello di testo normale (non pre-elaborato). Ad esempio, è possibile risolvere i percorsi dei file, registrare gli errori e ottenere i servizi forniti da Visual Studio e da qualsiasi pacchetto caricato. Per altre informazioni, vedere [Accesso Visual Studio da un modello di testo.](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))

## <a name="write-methods"></a>Metodi di scrittura

È possibile usare i `Write()` metodi e per aggiungere testo all'interno di un blocco di codice `WriteLine()` standard, anziché usare un blocco di codice di espressione. I due blocchi di codice seguenti sono equivalenti dal punto di vista funzionale.

### <a name="code-block-with-an-expression-block"></a>Blocco di codice con un blocco di espressioni

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Blocco di codice con WriteLine()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Può essere utile usare uno di questi metodi di utilità anziché un blocco di espressioni all'interno di un blocco di codice lungo con strutture di controllo annidate.

I metodi e hanno due overload, uno che accetta un singolo parametro di stringa e uno che accetta una stringa di formato composito più una matrice di oggetti da includere nella stringa `Write()` `WriteLine()` (come il `Console.WriteLine()` metodo ). I due usi seguenti di `WriteLine()` sono equivalenti dal punto di vista funzionale:

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

È possibile usare i metodi di rientro per formattare l'output del modello di testo. La classe ha una proprietà stringa che mostra il rientro corrente nel modello di testo e un campo che è un elenco dei rientri <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> `CurrentIndent` `indentLengths` aggiunti. È possibile aggiungere un rientro con il `PushIndent()` metodo e sottrarre un rientro con il `PopIndent()` metodo . Per rimuovere tutti i rientri, usare il `ClearIndent()` metodo . Il blocco di codice seguente illustra l'uso di questi metodi:

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

## <a name="error-and-warning-methods"></a>Metodi di errore e avviso

È possibile utilizzare i metodi di utilità error e warning per aggiungere messaggi all'elenco Visual Studio errori. Ad esempio, il codice seguente aggiungerà un messaggio di errore all'Elenco errori.

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

## <a name="access-to-host-and-service-provider"></a>Accesso all'host e al provider di servizi

La proprietà `this.Host` può fornire l'accesso alle proprietà esposte dall'host che esegue il modello. Per usare `this.Host` , è necessario impostare `hostspecific` l'attributo nella `<@template#>` direttiva :

`<#@template ... hostspecific="true" #>`

Il tipo di `this.Host` dipende dal tipo di host in cui è in esecuzione il modello. In un modello in esecuzione in Visual Studio, è possibile eseguire il cast a per ottenere l'accesso `this.Host` `IServiceProvider` a servizi come l'IDE. Ad esempio:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Uso di un set diverso di metodi di utilità

Come parte del processo di generazione del testo, il file modello viene trasformato in una classe , che viene sempre denominata `GeneratedTextTransformation` ed eredita da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Se invece si vuole usare un set diverso di metodi, è possibile scrivere una classe personalizzata e specificarla nella direttiva del modello. La classe deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Usare la `assembly` direttiva per fare riferimento all'assembly in cui è possibile trovare la classe compilata.
