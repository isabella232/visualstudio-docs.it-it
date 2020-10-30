---
title: Elemento Task di UsingTask (MSBuild) | Microsoft Docs
description: Informazioni sull'elemento Task di UsingTask di MSBuild, che contiene i dati passati a un TaskFactory TaskFactory.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f99452021b0efef1e5df305e984c684f3f446905
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047890"
---
# <a name="task-element-of-usingtask-msbuild"></a>Elemento Task di UsingTask (MSBuild)

Contiene i dati passati a un oggetto `UsingTask` `TaskFactory` . Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<Task>

## <a name="syntax"></a>Sintassi

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Evaluate`|Attributo booleano facoltativo.<br /><br /> Se `true`, MSBuild valuta tutti gli elementi interni ed espande gli elementi e le proprietà prima di passare le informazioni a `TaskFactory` quando viene creata un'istanza dell'attività.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Data|Il testo compreso tra i tag `Task` viene inviato testualmente a `TaskFactory`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fornisce un modo per registrare le attività in MSBuild. Possono esistere zero o più elementi `UsingTask` in un progetto. |

## <a name="example"></a>Esempio

 L'esempio seguente illustra come usare l'elemento `Task` con un attributo `Evaluate`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
