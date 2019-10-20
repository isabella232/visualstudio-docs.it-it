---
title: Generazione di file con l'utilità TextTransform
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1a12da7c7cae7e862d670b3f62fb801920f34e1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666733"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generare file con l'utilità TextTransform

TextTransform. exe è uno strumento da riga di comando che è possibile utilizzare per trasformare un modello di testo. Quando si chiama TextTransform. exe, è necessario specificare il nome di un file di modello di testo come argomento. TextTransform. exe chiama il motore di trasformazione del testo ed elabora il modello di testo. TextTransform. exe viene in genere chiamato da script. Tuttavia, non è in genere necessario, perché è possibile eseguire la trasformazione del testo in Visual Studio o nel processo di compilazione.

> [!NOTE]
> Se si desidera eseguire la trasformazione del testo come parte di un processo di compilazione, è consigliabile utilizzare l'attività di trasformazione del testo di MSBuild. Per altre informazioni, vedere [generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md). In un computer in cui è installato Visual Studio, è anche possibile scrivere un'applicazione o un'estensione di Visual Studio in grado di trasformare i modelli di testo. Per ulteriori informazioni, vedere [elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform. exe si trova nella directory seguente:

::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

per Professional Edition o

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

per Enterprise Edition.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

per Professional Edition o

**\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

per Enterprise Edition.

Nelle versioni precedenti di Visual Studio, il file si trova nel percorso seguente:

**\Program Files (x86) \File Files\Microsoft Shared\TextTemplating \{version}**

dove {version} dipende da quale versione precedente è installata.

::: moniker-end

## <a name="syntax"></a>Sintassi

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametri

|**Argomento**|**Descrizione**|
|-|-|
|`templateName`|Identifica il nome del file modello che si desidera trasformare.|

|**Opzione**|**Descrizione**|
|-|-|
|**-out** \<filename >|File in cui viene scritto l'output della trasformazione.|
|**-r** \<assembly >|Assembly utilizzato per la compilazione e l'esecuzione del modello di testo.|
|**-u** \<namespace >|Spazio dei nomi utilizzato per la compilazione del modello.|
|**-I** \<includedirectory >|Una directory che contiene i modelli di testo inclusi nel modello di testo specificato.|
|**-P** \<referencepath >|Una directory in cui cercare gli assembly specificati nel modello di testo o per l'uso dell'opzione **-r** .<br /><br /> Per includere ad esempio gli assembly usati per l'API di Visual Studio, usare<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >! \<className >! \<assemblyName&#124;codebase >|Il nome, il nome completo del tipo e l'assembly di un processore di direttiva che può essere utilizzato per elaborare le direttive personalizzate all'interno del modello di testo.|
|**-a** [ProcessorName]! [directiveName]! \<parameterName >! \<parameterValue >|Specificare un valore di parametro per un processore di direttiva. Se si specifica solo il nome e il valore del parametro, il parametro sarà disponibile per tutti i processori di direttiva. Se si specifica un processore di direttiva, il parametro sarà disponibile solo per il processore specificato. Se si specifica un nome di direttiva, il parametro sarà disponibile solo quando la direttiva specificata verrà elaborata.<br /><br /> Per accedere ai valori dei parametri da un processore di direttiva o da un modello di testo, usare [ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). In un modello di testo, includere `hostspecific` nella direttiva template e richiamare il messaggio su `this.Host`. Esempio:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`<br /><br /> Digitare sempre i contrassegni '!', anche se si omettono i nomi facoltativi del processore e della direttiva. Esempio:<br /><br /> `-a !!param!value`|
|**-h**|Fornisce la guida.|

## <a name="related-topics"></a>Argomenti correlati

|Attività|Argomento|
|-|-|
|Genera i file in una soluzione di Visual Studio.|[Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Scrivere processori di direttive per trasformare le origini dati.|[Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)|
|Scrivere un host del modello di testo che consenta di richiamare modelli di testo dalla propria applicazione.|[Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md)|
