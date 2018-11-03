---
title: Generazione di file con l'utilità TextTransform in Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6572ef97027466fa97c254664327f2f77b4ea7f2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967080"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generare file con l'utilità TextTransform

TextTransform.exe è uno strumento da riga di comando che è possibile utilizzare per trasformare un modello di testo. Quando si chiama TextTransform.exe, specificare il nome di un file di modello di testo come argomento. TextTransform.exe chiama il motore di trasformazione del testo ed elabora il modello di testo. TextTransform.exe viene in genere chiamato dagli script. Tuttavia, non è in genere necessaria, poiché è possibile eseguire la trasformazione di testo in Visual Studio o nel processo di compilazione.

> [!NOTE]
> Se si desidera eseguire la trasformazione di testo come parte di un processo di compilazione, è consigliabile usare l'attività di trasformazione di testo di MSBuild. Per altre informazioni, vedere [generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md). In un computer in cui è installato Visual Studio, è anche possibile scrivere un'applicazione o estensione di Visual Studio in grado di trasformare i modelli di testo. Per altre informazioni, vedere [elaborazione di modelli di testo tramite un Host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe si trova nella directory seguente:

 **\Programmi file (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

per l'edizione Professional, o

 **\Programmi file (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 per l'edizione Enterprise.

Nelle versioni precedenti di Visual Studio, il file si trova nel percorso seguente:

**\Programmi file (x86) \Common Files\Microsoft Shared\TextTemplating\{versione}**

dove {version} dipende la versione precedente installata.

## <a name="syntax"></a>Sintassi

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametri

|**Argomento**|**Descrizione**|
|-|-|
|`templateName`|Identifica il nome del file del modello che si desidera trasformare.|

|**Opzione**|**Descrizione**|
|-|-|
|**-out** \<nomefile >|Il file in cui viene scritto l'output della trasformazione.|
|**-r** \<assembly>|Un assembly utilizzato per la compilazione e l'esecuzione del modello di testo.|
|**-u** \<namespace>|Uno spazio dei nomi utilizzato per la compilazione del modello.|
|**-I** \<includedirectory>|Una directory che contiene i modelli di testo inclusi nel modello di testo specificato.|
|**-P** \<referencepath>|Una directory per cercare gli assembly specificati all'interno del modello di testo o per l'uso di **- r** opzione.<br /><br /> Ad esempio, per includere gli assembly utilizzati per l'API di Visual Studio, usare<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Il nome, nome completo del tipo e assembly di un processore di direttiva che può essere utilizzato per elaborare direttive personalizzate all'interno del modello di testo.|
|**-un** [processorName]. [ directiveName]. \<parameterName >! \<parameterValue >|Specificare un valore di parametro per un processore di direttiva. Se si specifica solo il nome del parametro e il valore, il parametro sarà disponibile per tutti i processori di direttiva. Se si specifica un processore di direttiva, il parametro è disponibile solo per il processore specificato. Se si specifica un nome di direttiva, il parametro è disponibile solo quando viene elaborata la direttiva specificata.<br /><br /> Per accedere ai valori di parametro da un processore di direttiva o di un modello di testo, usare [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). In un modello di testo, includere `hostspecific` nella direttiva del modello e richiamare il messaggio su `this.Host`. Ad esempio:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Digitare sempre il '!' contrassegnato, anche se si omette il processore facoltativo e nomi di direttiva. Ad esempio:<br /><br /> `-a !!param!value`|
|**-h**|Fornisce la Guida.|

## <a name="related-topics"></a>Argomenti correlati

|Attività|Argomento|
|-|-|
|Generare i file in una soluzione di Visual Studio.|[Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Scrivere processori di direttive per trasformare le origini dati.|[Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)|
|Scrivere un host di modello di testo che consente di richiamare i modelli di testo dalla propria applicazione.|[Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md)|
