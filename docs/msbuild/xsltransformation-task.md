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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8330cb006143244458c9da0f3e76060275607fa5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777603"
---
# <a name="xsltransformation-task"></a>XslTransformation (attività)
Consente di trasformare un input XML tramite un XSLT o un XSLT compilato e di creare un file o dispositivo di output.

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività `XslTransformation` .

|Parametro|Description|
|---------------|-----------------|
|`OutputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di output per la trasformazione XML.|
|`Parameters`|Parametro `String` facoltativo.<br /><br /> Specifica i parametri per il documento di input XSLT.|
|`XmlContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XML sotto forma di stringa.|
|`XmlInputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file di input XML.|
|`XslCompiledDllPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file XSLT compilato.|
|`XslContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XSLT sotto forma di stringa.|
|`XslInputPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file di input XSLT.|

## <a name="remarks"></a>Osservazioni
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)