---
title: Elemento ParameterGroup | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ef5f386841954aa1017a68ff335a33281f0cc02f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175110"
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
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Parametro](../msbuild/parameter-element.md)|Contiene informazioni su un parametro specifico per un'attività generata da un oggetto `UsingTask``TaskFactory`. Il nome dell'elemento è il nome del parametro.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
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



