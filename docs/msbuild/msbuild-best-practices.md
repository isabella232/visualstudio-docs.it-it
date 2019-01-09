---
title: Procedure consigliate per MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8140a8f2bfa4c80f0f56e3271e17371ccf0ec95c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858267"
---
# <a name="msbuild-best-practices"></a>Procedure consigliate per MSBuild
Per la scrittura degli script di MSBuild è consigliabile seguire le indicazioni riportate di seguito:  
  
-   I valori di proprietà predefiniti vengono gestiti meglio con l'attributo `Condition` e non dichiarando una proprietà il cui valore predefinito può essere sottoposto a override nella riga di comando. Ad esempio, usare  
  
```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```
  
-   Evitare i caratteri jolly quando si selezionano elementi. Al contrario, specificare i file in modo esplicito. Ciò semplifica l'individuazione degli errori che possono verificarsi quando si aggiungono o si eliminano file.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
