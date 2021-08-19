---
title: Attività CallTarget | Microsoft Docs
description: Informazioni su come usare l'MSBuild CallTarget per richiamare le destinazioni specificate all'interno del file di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ceafb3a687d533705d278fb0ca76496f1d27acdf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150612"
---
# <a name="calltarget-task"></a>attività CallTarget

Richiama le destinazioni specificate nel file di progetto.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `CallTarget` .

| Parametro | Descrizione |
|---------------------------| - |
| `RunEachTargetSeparately` | Parametro di input `Boolean` facoltativo.<br /><br /> Se `true` , il motore MSBuild viene chiamato una volta per ogni destinazione. Se `false` , il motore MSBuild viene chiamato una volta per compilare tutte le destinazioni. Il valore predefinito è `false`. |
| `TargetOutputs` | Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'output di tutte le destinazioni compilate. |
| `Targets` | Parametro `String[]` facoltativo.<br /><br /> Specifica la destinazione o le destinazioni da compilare. |
| `UseResultsCache` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene restituito il risultato memorizzato nella cache, se presente.<br /><br /> **Nota** Se l'attività MSBuild viene eseguita, il relativo output viene memorizzato nella cache in un ambito (ProjectFileName, GlobalProperties)[TargetNames] come elenco di elementi di compilazione. |

## <a name="remarks"></a>Commenti

 Se una destinazione specificata in `Targets` ha esito negativo e `RunEachTargetSeparately` è `true`, l'attività continua a compilare le destinazioni rimanenti.

 Per compilare le destinazioni predefinite, usare [l'attività MSBuild](../msbuild/msbuild-task.md) e impostare il parametro `Projects` su `$(MSBuildProjectFile)` .

Quando si usa , MSBuild valuta la destinazione chiamata in un nuovo ambito, anziché nello stesso ambito da cui `CallTarget` viene chiamato. Ciò significa che qualsiasi modifica di elemento e proprietà nella destinazione chiamata non è visibile alla destinazione chiamante.  Per passare informazioni alla destinazione chiamante, usare il `TargetOutputs` parametro di output .

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 L'esempio seguente chiama `TargetA` dall'interno di `CallOtherTargets`.

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
