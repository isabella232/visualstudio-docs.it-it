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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591671"
---
# <a name="vctooltask-base-class"></a>Classe di base VCToolTask

Molte attività ereditano dalla classe <xref:Microsoft.Build.Utilities.Task> e dalla classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Questa classe aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri della classe di base **VCToolTask**.

|Parametro|Descrizione|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Parametro facoltativo del **dizionario \<string, ToolSwitch> ** .|
|**AdditionalOptions**|Parametro **stringa** facoltativo.|
|**EffectiveWorkingDirectory**|Parametro **stringa** facoltativo.|
|**EnableErrorListRegex**|Parametro **bool** facoltativo.<br/><br/>Il valore predefinito è `true`.|
|**ErrorListRegex**|Parametro **ITaskItem []** facoltativo.|
|**ErrorListListExclusion**|Parametro **ITaskItem []** facoltativo.|
|**GenerateCommandLine**|Parametro **stringa** facoltativo.<br/><br/>Usare i valori **CommandLineFormat** *formato* [valore predefinito = CommandLineFormat.ForBuildLog] e **EscapeFormat** *formatoEscape* [valore predefinito = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Parametro **stringa** facoltativo.<br/><br/>Usare i valori **string[]** *opzioniDaRimuovere*, **CommandLineFormat** *formato* [valore predefinito = CommandLineFormat.ForBuildLog] e **formatoEscape** *escapeFormat* [valore predefinito = EscapeFormat.Default].|

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)<br/>
[Attività](../msbuild/msbuild-tasks.md)
