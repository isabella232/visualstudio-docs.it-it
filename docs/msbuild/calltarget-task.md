---
title: Attività CallTarget | Microsoft Docs
description: Informazioni su come usare l'attività CallTarget di MSBuild per richiamare le destinazioni specificate all'interno del file di progetto.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efeca838050c9024ad3768b2ac7f73ce7dd06720
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353291"
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

 Se si desidera compilare le destinazioni predefinite, utilizzare l' [attività MSBuild](../msbuild/msbuild-task.md) e impostare il `Projects` parametro su `$(MSBuildProjectFile)` .

Quando `CallTarget` si usa, MSBuild valuta la destinazione chiamata in un nuovo ambito, invece dello stesso ambito da cui viene chiamato. Ciò significa che qualsiasi modifica di elemento e proprietà nella destinazione chiamata non è visibile alla destinazione chiamante.  Per passare informazioni alla destinazione chiamante, usare il `TargetOutputs` parametro output.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

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

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
