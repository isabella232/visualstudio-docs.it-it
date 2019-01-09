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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e932b5a49559e77b9d7231d969f8ee78e2b4ec6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820280"
---
# <a name="parameter-element"></a>Elemento Parameter
Contiene informazioni su un parametro specifico per un'attività generata da un elemento `UsingTask` `TaskFactory`.  Il nome dell'elemento è il nome del parametro.  Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
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

|Attributo|Description|  
|---------------|-----------------|  
|`ParameterType`|Attributo facoltativo.<br /><br /> Il tipo .NET del parametro, ad esempio, `System.String`.|  
|`Output`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro di output per l'attività. Per impostazione predefinita, il valore è `false`.|  
|`Required`|Attributo booleano facoltativo.<br /><br /> Se `true`, il parametro è un parametro obbligatorio per l'attività. Per impostazione predefinita, il valore è `false`.|  

### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  

### <a name="parent-elements"></a>Elementi padre  

|Elemento|Description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene un elenco facoltativo di parametri che saranno presenti sull'attività generata da un elemento `UsingTask` `TaskFactory`.|  

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
 [Attività](../msbuild/msbuild-tasks.md)   
 [Attività MSBuild](../msbuild/msbuild-task-reference.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
