---
title: Generazione di file con l'utilità TextTransform | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 069f7f5ef2c579c10c1ee7c19989c79ce3ad63bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541026"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generazione di file con l'utilità TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [generazione di file con l'utilità di TextTransform](https://docs.microsoft.com/visualstudio/modeling/generating-files-with-the-texttransform-utility).  
  
TextTransform.exe è uno strumento da riga di comando che è possibile utilizzare per trasformare un modello di testo. Quando si chiama TextTransform.exe, specificare il nome di un file di modello di testo come argomento. TextTransform.exe chiama il motore di trasformazione del testo ed elabora il modello di testo. TextTransform.exe viene in genere chiamato dagli script. Tuttavia, non è in genere necessaria, poiché è possibile eseguire la trasformazione di testo in Visual Studio o nel processo di compilazione.  
  
> [!NOTE]
>  Se si desidera eseguire la trasformazione di testo come parte di un processo di compilazione, è consigliabile usare l'attività di trasformazione di testo di MSBuild. Per altre informazioni, vedere [generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md). In un computer nel quale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è installato, è anche possibile scrivere un'applicazione o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione che può trasformare i modelli di testo. Per altre informazioni, vedere [elaborazione di modelli di testo tramite un Host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe si trova nella directory seguente:  
  
 **\Programmi\Common Files\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>Sintassi  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Parametri  
  
|**Argomento**|**Descrizione**|  
|------------------|---------------------|  
|`templateName`|Identifica il nome del file del modello che si desidera trasformare.|  
  
|**Opzione**|**Descrizione**|  
|----------------|---------------------|  
|**-out** \<nomefile >|Il file in cui viene scritto l'output della trasformazione.|  
|**-r** \<assembly>|Un assembly utilizzato per la compilazione e l'esecuzione del modello di testo.|  
|**-u** \<namespace>|Uno spazio dei nomi utilizzato per la compilazione del modello.|  
|**-I** \<includedirectory>|Una directory che contiene i modelli di testo inclusi nel modello di testo specificato.|  
|**-P** \<referencepath>|Una directory per cercare gli assembly specificati all'interno del modello di testo o per l'uso di **- r** opzione.<br /><br /> Ad esempio, per includere gli assembly utilizzati per l'API di Visual Studio, usare<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Il nome, nome completo del tipo e assembly di un processore di direttiva che può essere utilizzato per elaborare direttive personalizzate all'interno del modello di testo.|  
|**-un** [processorName]. [ directiveName]. \<parameterName >! \<parameterValue >|Specificare un valore di parametro per un processore di direttiva. Se si specifica solo il nome del parametro e il valore, il parametro sarà disponibile per tutti i processori di direttiva. Se si specifica un processore di direttiva, il parametro è disponibile solo per il processore specificato. Se si specifica un nome di direttiva, il parametro è disponibile solo quando viene elaborata la direttiva specificata.<br /><br />  In un modello di testo, includere `hostspecific` nella direttiva del modello e richiamare il messaggio su `this.Host`. Ad esempio:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Digitare sempre il '!' contrassegnato, anche se si omette il processore facoltativo e nomi di direttiva. Ad esempio:<br /><br /> `-a !!param!value`|  
|**-h**|Fornisce la Guida.|  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Attività|Argomento|  
|----------|-----------|  
|Generare file in una soluzione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Scrivere processori di direttive per trasformare le origini dati.|[Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)|  
|Scrivere un host di modello di testo che consente di richiamare i modelli di testo dalla propria applicazione.|[Elaborazione di modelli di testo tramite un host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md)|



