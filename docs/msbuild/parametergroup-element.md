---
title: Elemento ParameterGroup | Microsoft Docs
description: Informazioni sull'elemento ParameterGroup di MSBuild, che contiene un elenco facoltativo di parametri presenti nell'attività generata da un oggetto UsingTask TaskFactory.
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
ms.workload:
- multiple
ms.openlocfilehash: 56ff9c63de40f6a352c10f92b937a397c683fc65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905297"
---
# <a name="parametergroup-element"></a>Elemento ParameterGroup

Contiene un elenco facoltativo di parametri che saranno presenti nell'attività generata da un oggetto `UsingTask` `TaskFactory` . Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>

## <a name="syntax"></a>Sintassi

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

 Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Parametro](../msbuild/parameter-element.md)|Contiene informazioni su un parametro specifico per un'attività generata da un oggetto `UsingTask` `TaskFactory` . Il nome dell'elemento è il nome del parametro.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Fornisce un modo per registrare le attività in MSBuild. Possono esistere zero o più elementi `UsingTask` in un progetto. |

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
- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
