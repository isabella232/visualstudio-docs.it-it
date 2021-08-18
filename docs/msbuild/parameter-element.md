---
title: Elemento Parameter | Microsoft Docs
description: Informazioni sull'MSBuild parameter, che contiene informazioni su un parametro specifico per un'attività generata da un oggetto UsingTask TaskFactory.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d408158d203d62c562073d188dc0a5319b964738
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100738"
---
# <a name="parameter-element"></a>Elemento Parameter

Contiene informazioni su un parametro specifico per un'attività generata da `UsingTask` `TaskFactory` un oggetto .  Il nome dell'elemento è il nome del parametro.  Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>
 \<Parameter>

## <a name="syntax"></a>Sintassi

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`ParameterType`|Attributo facoltativo.<br /><br /> Il tipo .NET del parametro, ad esempio, `System.String`.|
|`Output`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro di output per l'attività. Per impostazione predefinita, il valore è `false`.|
|`Required`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro obbligatorio per l'attività. Per impostazione predefinita, il valore è `false`.|

### <a name="child-elements"></a>Elementi figlio

 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene un elenco facoltativo di parametri che saranno presenti nell'attività generata da `UsingTask` `TaskFactory` un oggetto .|

## <a name="example"></a>Esempio

 L'esempio seguente illustra come usare l'elemento `Parameter`.

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
