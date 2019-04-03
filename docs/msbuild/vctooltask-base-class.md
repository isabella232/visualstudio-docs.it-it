---
title: Classe VCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 7bdad856a6ea0ec6cca8292bc3095f51c500bcb1
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515256"
---
# <a name="vctooltask-base-class"></a>Classe di base VCToolTask

Molte attività ereditano dalla classe <xref:Microsoft.Build.Utilities.Task> e dalla classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Questa classe aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri della classe di base **VCToolTask**.

|Parametro|Description|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Parametro **Dictionary\<string, ToolSwitch>** facoltativo.|
|**AdditionalOptions**|Parametro **string** facoltativo.|
|**EffectiveWorkingDirectory**|Parametro **string** facoltativo.|
|**EnableErrorListRegex**|Parametro **bool** facoltativo.<br/><br/>Il valore predefinito è `true`.|
|**ErrorListRegex**|Parametro **ITaskItem[]** facoltativo.|
|**ErrorListListExclusion**|Parametro **ITaskItem[]** facoltativo.|
|**GenerateCommandLine**|Parametro **string** facoltativo.<br/><br/>Usare i valori **CommandLineFormat** *formato* [valore predefinito = CommandLineFormat.ForBuildLog] e **EscapeFormat** *formatoEscape* [valore predefinito = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Parametro **string** facoltativo.<br/><br/>Usare i valori **string[]** *opzioniDaRimuovere*, **CommandLineFormat** *formato* [valore predefinito = CommandLineFormat.ForBuildLog] e **formatoEscape** *escapeFormat* [valore predefinito = EscapeFormat.Default].|

## <a name="see-also"></a>Vedere anche

[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)<br/>
[Attività](../msbuild/msbuild-tasks.md)