---
title: Generazione di file con l'utilità TextTransform
description: Informazioni su come l'utilità TextTransform è uno strumento da riga di comando che è possibile usare per trasformare un modello di testo.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 82a0a5ec91b532e96c795ad65910061b0d5f946e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085611"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generare file con l'utilità TextTransform

TextTransform.exe è uno strumento da riga di comando che è possibile usare per trasformare un modello di testo. Quando si chiama TextTransform.exe, si specifica il nome di un file di modello di testo come argomento. TextTransform.exe chiama il motore di trasformazione del testo ed elabora il modello di testo. TextTransform.exe viene in genere chiamato dagli script. Tuttavia, in genere non è necessario, perché è possibile eseguire la trasformazione del testo in Visual Studio o nel processo di compilazione.

> [!NOTE]
> Se si vuole eseguire la trasformazione del testo come parte di un processo di compilazione, è consigliabile usare l'attività MSBuild trasformazione testo. Per altre informazioni, vedere [Generazione di codice in un processo di compilazione.](../modeling/code-generation-in-a-build-process.md) In un computer in cui Visual Studio è installato, è anche possibile scrivere un'applicazione o un'estensione Visual Studio in grado di trasformare i modelli di testo. Per altre informazioni, vedere [Elaborazione di modelli di testo tramite un host personalizzato.](../modeling/processing-text-templates-by-using-a-custom-host.md)

TextTransform.exe si trova nella directory seguente:

::: moniker range=">=vs-2019"

**\Programmi (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE**

per Professional edition, o

**\Programmi (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

per Enterprise edition.

::: moniker-end

::: moniker range="vs-2017"

**\Programmi (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

per Professional edition, o

**\Programmi (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

per Enterprise edition.

Nelle versioni precedenti di Visual Studio, il file si trova nel percorso seguente:

**\Programmi (x86)\Common Files\Microsoft Shared\TextTemplating \{ versione}**

dove {version} dipende dalla versione precedente installata.

::: moniker-end

## <a name="syntax"></a>Sintassi

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametri

|**Argument**|**Descrizione**|
|-|-|
|`templateName`|Identifica il nome del file modello che si desidera trasformare.|

|**Opzione**|**Descrizione**|
|-|-|
|**-out**\<filename>|File in cui viene scritto l'output della trasformazione.|
|**-r**\<assembly>|Assembly utilizzato per la compilazione e l'esecuzione del modello di testo.|
|**-u**\<namespace>|Spazio dei nomi utilizzato per la compilazione del modello.|
|**-I**\<includedirectory>|Directory che contiene i modelli di testo inclusi nel modello di testo specificato.|
|**-P**\<referencepath>|Directory in cui cercare gli assembly specificati all'interno del modello di testo o per usare **l'opzione -r.**<br /><br /> Ad esempio, per includere gli assembly usati per l'API Visual Studio, usare<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName> \<className> ! !\<assemblyName&#124;codeBase>|Nome, nome completo del tipo e assembly di un processore di direttiva che può essere usato per elaborare direttive personalizzate all'interno del modello di testo.|
|**-a** [processorName]! [directiveName]! \<parameterName> !\<parameterValue>|Specificare un valore di parametro per un processore di direttiva. Se si specificano solo il nome e il valore del parametro, il parametro sarà disponibile per tutti i processori di direttiva. Se si specifica un processore di direttiva, il parametro è disponibile solo per il processore specificato. Se si specifica un nome di direttiva, il parametro è disponibile solo durante l'elaborazione della direttiva specificata.<br /><br /> Per accedere ai valori dei parametri da un processore di direttiva o da un modello di testo, usare [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). In un modello di testo includere `hostspecific` nella direttiva template e richiamare il messaggio su `this.Host` . Ad esempio:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Digitare sempre i contrassegni '!', anche se si omettono i nomi facoltativi del processore e della direttiva. Esempio:<br /><br /> `-a !!param!value`|
|**-h**|Fornisce assistenza.|

## <a name="related-topics"></a>Argomenti correlati

|Attività|Argomento|
|-|-|
|Generare file in una Visual Studio soluzione.|[Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Scrivere processori di direttive per trasformare le origini dati.|[Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)|
|Scrivere un host di modelli di testo che consente di richiamare modelli di testo dalla propria applicazione.|[Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md)|
