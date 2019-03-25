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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 4c7cc3490735dbd9ac43cd43555ec673cc3afccd
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070444"
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