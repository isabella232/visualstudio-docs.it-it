---
title: Elemento ParameterGroup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f4faa9038a5931dec376903f166301f27f00b37
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154793"
---
# <a name="parametergroup-element"></a>Elemento ParameterGroup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene un elenco facoltativo di parametri che saranno presenti sull'attività generata da un oggetto `UsingTask``TaskFactory`. Per altre informazioni, vedere [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ParameterGroup />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[Parametro](../msbuild/parameter-element.md)|Contiene informazioni su un parametro specifico per un'attività generata da un oggetto `UsingTask``TaskFactory`. Il nome dell'elemento è il nome del parametro.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Consente di registrare attività in [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Possono esistere zero o più elementi `UsingTask` in un progetto.|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'elemento `ParameterGroup`.  
  
```  
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
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
