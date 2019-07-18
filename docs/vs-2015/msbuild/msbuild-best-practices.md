---
title: Procedure consigliate per MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e597b10913ad495193545ab304b3b324d8f66b41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181111"
---
# <a name="msbuild-best-practices"></a>Procedure consigliate di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la scrittura degli script di MSBuild è consigliabile seguire le indicazioni riportate di seguito:  
  
- I valori di proprietà predefiniti vengono gestiti meglio con l'attributo `Condition` e non dichiarando una proprietà il cui valore predefinito può essere sottoposto a override nella riga di comando. Ad esempio, usare  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
- Evitare i caratteri jolly quando si selezionano elementi. Al contrario, specificare i file in modo esplicito. Ciò semplifica l'individuazione degli errori che possono verificarsi quando si aggiungono o si eliminano file.  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md) (Concetti avanzati)
