---
title: Attività ResolveNonMSBuildProjectOutput | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7060141f81054bf5daa27cdd09a07639be6e0ae8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608708"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput (attività)
Determina i file di output per riferimenti a progetti non MSBuild.

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveNonMSBuildProjectOutput` .

|Parametro|Description|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa XML che contiene gli output di progetto risolti.|
|`ProjectReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i riferimenti al progetto.|
|`ResolvedOutputPaths`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco dei percorsi di riferimento risolti e conserva gli attributi dei riferimenti al progetto originali.|
|`UnresolvedProjectReferences`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco degli elementi di riferimento del progetto che non sono stati risolti usando l'elenco di output prerisolto.<br /><br /> Poiché Visual Studio prerisolve solo progetti non MSBuild, questo significa che i riferimenti di progetto in questo elenco sono nel formato MSBuild.|

## <a name="remarks"></a>Osservazioni
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)