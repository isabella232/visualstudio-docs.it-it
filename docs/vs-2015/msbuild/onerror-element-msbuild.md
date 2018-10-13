---
title: Elemento OnError (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f89d21441418ae0b5c267c0fea7e8451115afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228709"
---
# <a name="onerror-element-msbuild"></a>Elemento OnError (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Fa in modo che vengano eseguite una o più destinazioni se l'attributo `ContinueOnError` è `false` per un'attività non riuscita.  
  
 \<Project>  
 \<Target>  
 \<OnError>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Attributo obbligatorio.<br /><br /> Le destinazioni da eseguire se un'attività non riesce. Se si specificano più destinazioni, separarle con punto e virgola. Le destinazioni vengono eseguite nell'ordine specificato.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Destinazione](../msbuild/target-element-msbuild.md)|Elemento contenitore per le attività [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] esegue l'elemento `OnError` se una delle attività dell'elemento `Target` ha esito negativo con l'attributo `ContinueOnError` impostato su `ErrorAndStop` (o `false`). Quando l'attività ha esito negativo, vengono eseguite le destinazioni specificate nell'attributo `ExecuteTargets`. Se la destinazione include più di un elemento `OnError`, gli elementi `OnError` vengono eseguiti in sequenza quando l'attività ha esito negativo.  
  
 Per altre informazioni sull'attributo `ContinueOnError`, vedere [Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md). Per informazioni sulle destinazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Esempio  
 Il codice seguente esegue le attività `TaskOne` e `TaskTwo`. Se `TaskOne` ha esito negativo, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] valuta l'elemento `OnError` ed esegue la destinazione `OtherTarget`.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Destinazioni](../msbuild/msbuild-targets.md)



