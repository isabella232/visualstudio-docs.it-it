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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d29c236b89172ab6dc456be97016b98f2cae19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094558"
---
# <a name="calltarget-task"></a>attività CallTarget

Richiama le destinazioni specificate nel file di progetto.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `CallTarget` .

| Parametro | Descrizione |
|---------------------------| - |
| `RunEachTargetSeparately` | Parametro di input `Boolean` facoltativo.<br /><br /> Se `true`, il motore MSBuild viene chiamato una volta per ogni destinazione. Se `false`, il motore MSBuild viene chiamato una volta per compilare tutte le destinazioni. Il valore predefinito è `false`. |
| `TargetOutputs` | Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'output di tutte le destinazioni compilate. |
| `Targets` | Parametro `String[]` facoltativo.<br /><br /> Specifica la destinazione o le destinazioni da compilare. |
| `UseResultsCache` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene restituito il risultato memorizzato nella cache, se presente.<br /><br /> **Nota** Se l'attività MSBuild viene eseguita, il relativo output viene memorizzato nella cache in un ambito (ProjectFileName, GlobalProperties)[TargetNames] come elenco di elementi di compilazione. |

## <a name="remarks"></a>Osservazioni

 Se una destinazione specificata in `Targets` ha esito negativo e `RunEachTargetSeparately` è `true`, l'attività continua a compilare le destinazioni rimanenti.

 Se si desidera compilare le destinazioni predefinite, `Projects` utilizzare l'attività [MSBuild](../msbuild/msbuild-task.md) e impostare il parametro su . `$(MSBuildProjectFile)`

Quando `CallTarget`si utilizza , MSBuild valuta la destinazione chiamata in un nuovo ambito, anziché nello stesso ambito da cui viene chiamata. Ciò significa che qualsiasi elemento e le modifiche alle proprietà nella destinazione chiamata non sono visibili alla destinazione chiamante.  Per passare informazioni alla destinazione `TargetOutputs` chiamante, usare il parametro di output.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [TaskExtension base class](../msbuild/taskextension-base-class.md).

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

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
