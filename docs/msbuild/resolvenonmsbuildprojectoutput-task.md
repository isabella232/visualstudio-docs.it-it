---
title: Attività ResolveNonMSBuildProjectOutput | Microsoft Docs
description: Informazioni su MSBuild usa l'attività ResolveNonMSBuildProjectOutput per determinare i file di output per i riferimenti non MSBuild progetto.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: de57cbcd1b1ad59f3edfce47f09bf88a8e9ea94e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100621"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput (attività)

Determina i file di output per riferimenti a progetti non MSBuild.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveNonMSBuildProjectOutput` .

|Parametro|Descrizione|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa XML che contiene gli output di progetto risolti.|
|`ProjectReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i riferimenti al progetto.|
|`ResolvedOutputPaths`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco dei percorsi di riferimento risolti e conserva gli attributi dei riferimenti al progetto originali.|
|`UnresolvedProjectReferences`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco degli elementi di riferimento del progetto che non sono stati risolti usando l'elenco di output prerisolto.<br /><br /> Poiché Visual Studio prerisolve solo progetti non MSBuild, questo significa che i riferimenti di progetto in questo elenco sono nel formato MSBuild.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)