---
title: Classe VCToolTask | Microsoft Docs
description: Informazioni su diversi parametri aggiunti dalla classe di base VCToolTask alle attività che ereditano da essa.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e8444755cf0d3e3b5d900f756189f1e0b8128d6b7d6b8d22f940b2b710882cce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397189"
---
# <a name="vctooltask-base-class"></a>Classe di base VCToolTask

Molte attività ereditano dalla classe <xref:Microsoft.Build.Utilities.Task> e dalla classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Questa classe aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri della classe di base **VCToolTask**.

|Parametro|Descrizione|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Parametro **Dictionary \<string, ToolSwitch>** facoltativo.|
|**AdditionalOptions**|Parametro **di stringa** facoltativo.|
|**EffectiveWorkingDirectory**|Parametro **di stringa** facoltativo.|
|**EnableErrorListRegex**|Parametro **bool** facoltativo.<br/><br/>Il valore predefinito è `true`.|
|**ErrorListRegex**|Parametro **ITaskItem[]** facoltativo.|
|**ErrorListListExclusion**|Parametro **ITaskItem[]** facoltativo.|
|**GenerateCommandLine**|Parametro **di stringa** facoltativo.<br/><br/>Usa i **valori CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Parametro **di stringa** facoltativo.<br/><br/>Usa i valori **string[]** *switchesToRemove,* **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)<br/>
[Attività](../msbuild/msbuild-tasks.md)
