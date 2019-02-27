---
title: Attività CallTarget | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6594620051675f2c0ce6e06ca098d26e443f624b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617236"
---
# <a name="calltarget-task"></a>attività CallTarget
Richiama le destinazioni specificate nel file di progetto.

## <a name="task-parameters"></a>Parametri dell'attività
 Nella tabella che segue vengono descritti i parametri dell'attività `CallTarget` .


| Parametro | Description |
|---------------------------| - |
| `RunEachTargetSeparately` | Parametro di input `Boolean` facoltativo.<br /><br /> Se `true`, il motore [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] viene chiamato una volta per ogni destinazione. Se `false`, il motore [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] viene chiamato una volta per compilare tutte le destinazioni. Il valore predefinito è `false`. |
| `TargetOutputs` | Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'output di tutte le destinazioni compilate. |
| `Targets` | Parametro `String[]` facoltativo.<br /><br /> Specifica la destinazione o le destinazioni da compilare. |
| `UseResultsCache` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene restituito il risultato memorizzato nella cache, se presente.<br /><br /> **Nota** Se l'attività MSBuild viene eseguita, il relativo output viene memorizzato nella cache in un ambito (ProjectFileName, GlobalProperties)[TargetNames] come elenco di elementi di compilazione. |

## <a name="remarks"></a>Osservazioni
 Se una destinazione specificata in `Targets` ha esito negativo e `RunEachTargetSeparately` è `true`, l'attività continua a compilare le destinazioni rimanenti.

 Per compilare le destinazioni predefinite, usare l'[attività MSBuild](../msbuild/msbuild-task.md) e impostare il parametro `Projects` uguale a `$(MSBuildProjectFile)`.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

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

## <a name="see-also"></a>Vedere anche
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
- [Destinazioni](../msbuild/msbuild-targets.md)