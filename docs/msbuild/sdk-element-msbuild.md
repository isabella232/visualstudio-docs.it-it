---
title: Elemento Sdk (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24392fe34069025209f0e2c02e1231d1cbbe3397
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993274"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)
Fa riferimento a un SDK di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>Sintassi  

```xml  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Description|  
|---------------|-----------------|  
|`Name`|Attributo obbligatorio.<br /><br /> Nome dell'SDK di progetto.|  
|`Version`|Attributo facoltativo.<br /><br /> Versione dell'SDK di progetto|  

### <a name="child-elements"></a>Elementi figlio  
 Nessuno.

### <a name="parent-elements"></a>Elementi padre  

| Elemento | Description |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |

## <a name="see-also"></a>Vedere anche  
 [Procedura: Fare riferimento a un SDK di progetto MSBuild](../msbuild/how-to-use-project-sdk.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
