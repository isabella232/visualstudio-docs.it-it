---
title: Elemento Parameter | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7c4fa5d093952eefc870aded3d3e14a1f5983a7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633005"
---
# <a name="parameter-element"></a>Parameter - elemento

Contiene informazioni su un parametro specifico per un'attività generata da un `UsingTask` `TaskFactory`.  Il nome dell'elemento è il nome del parametro.  Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup> \<Parameter>

## <a name="syntax"></a>Sintassi

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|`ParameterType`|Attributo facoltativo.<br /><br /> Il tipo .NET del parametro, ad esempio, `System.String`.|
|`Output`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro di output per l'attività. Per impostazione predefinita, il valore è `false`.|
|`Required`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro obbligatorio per l'attività. Per impostazione predefinita, il valore è `false`.|

### <a name="child-elements"></a>Elementi figlio

 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene un elenco facoltativo di parametri che saranno presenti nell'attività generata da un `UsingTask` `TaskFactory`.|

## <a name="example"></a>Esempio

 L'esempio seguente illustra come usare l'elemento `Parameter`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
