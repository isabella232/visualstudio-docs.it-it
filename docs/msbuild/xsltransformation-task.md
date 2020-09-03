---
title: Attività XslTransformation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d23799e5ce5bf391915ac459c69c27b990211f0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094542"
---
# <a name="xsltransformation-task"></a>XslTransformation (attività)

Consente di trasformare un input XML tramite un XSLT o un XSLT compilato e di creare un file o dispositivo di output.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `XslTransformation` .

|Parametro|Descrizione|
|---------------|-----------------|
|`OutputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di output per la trasformazione XML.|
|`Parameters`|Parametro `String` facoltativo.<br /><br /> Specifica i parametri per il documento di input XSLT.  Fornire il codice XML non elaborato che include ogni parametro come `<Parameter Name="" Value="" Namespace="" />` .|
|`XmlContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XML sotto forma di stringa.|
|`XmlInputPaths`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica i file di input XML.|
|`XslCompiledDllPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file XSLT compilato.|
|`XslContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XSLT sotto forma di stringa.|
|`XslInputPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file di input XSLT.|

## <a name="remarks"></a>Osservazioni

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene utilizzato un file di trasformazione XSL *Transform. XSLT* per modificare il file XML `$(XmlInputFileName)` . Il codice XML trasformato viene scritto in `$(IntermediateOutputPath)output.xml` . La trasformazione XSL accetta `$(Parameter1)` come parametro di input.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Vedere anche

- [Parametri XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
