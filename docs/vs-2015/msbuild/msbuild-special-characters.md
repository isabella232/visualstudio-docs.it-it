---
title: Caratteri speciali di MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c9ce1697f370ec1beec8ce12faceb15825fbe5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256451"
---
# <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] riserva alcuni caratteri per usi speciali in contesti specifici. L'escape di tali caratteri è necessario solo se devono essere usati letteralmente nel contesto in cui sono riservati. Ad esempio, un asterisco ha un significato speciale solo negli attributi `Include` e `Exclude` di una definizione di elemento e nelle chiamate a `CreateItem`. Se un asterisco deve apparire come asterisco in uno di questi contesti, è necessario eseguirne l'escape. In ogni altro contesto, è sufficiente digitare l'asterisco nel punto in cui deve essere visualizzato.  
  
 Per eseguire l'escape di un carattere speciale, usare la sintassi %*xx*, dove *xx* rappresenta il valore esadecimale ASCII del carattere. Per altre informazioni, vedere [Procedura: Usare caratteri di escape speciali in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Caratteri speciali  
 Nella tabella seguente sono elencati i caratteri speciali di [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]:  
  
|**Carattere**|**ASCII**|**Utilizzo riservato**|  
|-------------------|---------------|------------------------|  
|%|%25|Riferimento ai metadati|  
|$|%24|Riferimento alle proprietà|  
|@|%40|Riferimento a elenchi di elementi|  
|'|%27|Condizioni e altre espressioni|  
|;|%3B|Separatore di elenco|  
|?|%3F|Carattere jolly per i nomi di file negli attributi `Include` e `Exclude`|  
|*|%2A|Carattere jolly per l'uso nei nomi di file negli attributi `Include` e `Exclude`|  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)   
 [Elementi](../msbuild/msbuild-items.md)



