---
title: Elemento ParameterGroup | Microsoft Docs
description: Informazioni sull'MSBuild elemento ParameterGroup, che contiene un elenco facoltativo di parametri presenti nell'attività generata da un elemento UsingTask TaskFactory.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c56eb3b3bfb79bd7896657719157fc6a4bd8e99c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628404"
---
# <a name="parametergroup-element"></a>Elemento ParameterGroup

Contiene un elenco facoltativo di parametri che saranno presenti nell'attività generata da `UsingTask` `TaskFactory` un oggetto . Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>

## <a name="syntax"></a>Sintassi

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Parametro](../msbuild/parameter-element.md)|Contiene informazioni su un parametro specifico per un'attività generata da `UsingTask` `TaskFactory` un oggetto . Il nome dell'elemento è il nome del parametro.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Consente di registrare le attività in MSBuild. Possono esistere zero o più elementi `UsingTask` in un progetto. |

## <a name="example"></a>Esempio

 L'esempio seguente illustra come usare l'elemento `ParameterGroup`.

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
- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
