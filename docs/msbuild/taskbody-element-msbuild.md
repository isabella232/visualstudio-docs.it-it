---
title: Elemento TaskBody (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5dcddcc0a050698f6e73f12df87316c344da42ec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931239"
---
# <a name="taskbody-element-msbuild"></a>Elemento TaskBody (MSBuild)
Contiene i dati passati a `UsingTask` `TaskFactory`. Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<TaskBody>  

## <a name="syntax"></a>Sintassi  

```xml
<TaskBody Evaluate="true/false" />  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Description|  
|---------------|-----------------|  
|`Evaluate`|Attributo booleano facoltativo.<br /><br /> Se `true`, MSBuild valuta tutti gli elementi interni ed espande gli elementi e le proprietà prima di passare le informazioni a `TaskFactory` quando viene creata un'istanza dell'attività.|  

### <a name="child-elements"></a>Elementi figlio  

|Elemento|Description|  
|-------------|-----------------|  
|Dati|Il testo compreso tra i tag `TaskBody` viene inviato testualmente a `TaskFactory`.|  

### <a name="parent-elements"></a>Elementi padre  

| Elemento | Description |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Consente di registrare attività in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Possono esistere zero o più elementi `UsingTask` in un progetto. |

## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'elemento `TaskBody` con un attributo `Evaluate`.  

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
