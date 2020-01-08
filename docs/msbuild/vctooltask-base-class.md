---
title: Classe VCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591671"
---
# <a name="vctooltask-base-class"></a>Classe di base VCToolTask

Molte attività ereditano dalla classe <xref:Microsoft.Build.Utilities.Task> e dalla classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Questa classe aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri della classe di base **VCToolTask**.

|Parametro|Descrizione|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Parametro **Dictionary\<string, ToolSwitch>** facoltativo.|
|**AdditionalOptions**|Parametro **string** facoltativo.|
|**EffectiveWorkingDirectory**|Parametro **string** facoltativo.|
|**EnableErrorListRegex**|Parametro **bool** facoltativo.<br/><br/>Il valore predefinito è `true`.|
|**ErrorListRegex**|Parametro **ITaskItem[]** facoltativo.|
|**ErrorListListExclusion**|Parametro **ITaskItem[]** facoltativo.|
|**GenerateCommandLine**|Parametro **string** facoltativo.<br/><br/>USA Values **CommandLineFormat** *Format* [default = CommandLineFormat. ForBuildLog] e **EscapeFormat** *EscapeFormat* [default = EscapeFormat. default].|
|**GenerateCommandLineExceptSwitches**|Parametro **string** facoltativo.<br/><br/>USA Values **String []** *switchesToRemove*, **CommandLineFormat** *Format* [default = CommandLineFormat. ForBuildLog] e **EscapeFormat** *EscapeFormat [default* = EscapeFormat. default].|

## <a name="see-also"></a>Vedere anche

[Riferimento alle attività](../msbuild/msbuild-task-reference.md)<br/>
[Attività](../msbuild/msbuild-tasks.md)
