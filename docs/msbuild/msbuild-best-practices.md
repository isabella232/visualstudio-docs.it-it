---
title: Procedure consigliate per MSBuild | Microsoft Docs
description: Informazioni sulle procedure consigliate per la scrittura di MSBuild script, ad esempio l'uso degli attributi Condition e l'uso di caratteri jolly.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b96ed3b0e2ece6c8b0cd27c5733c863d4204c513
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115759"
---
# <a name="msbuild-best-practices"></a>Procedure consigliate per MSBuild

Per la scrittura degli script di MSBuild è consigliabile seguire le indicazioni riportate di seguito:

- I valori di proprietà predefiniti vengono gestiti meglio con l'attributo `Condition` e non dichiarando una proprietà il cui valore predefinito può essere sottoposto a override nella riga di comando. Ad esempio, usare

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- In generale, evitare l'uso di caratteri jolly quando si selezionano gli elementi. Al contrario, specificare i file in modo esplicito. Ciò è dovuto al fatto che nella maggior parte dei MSBuild i caratteri jolly vengono espansi in diversi momenti, ad esempio quando si aggiungono o rimuovono elementi, il che può causare un comportamento imprevisto. Un'eccezione è nei progetti .NET Core SDK in stile, che elaborano correttamente i caratteri jolly.

## <a name="see-also"></a>Vedi anche

- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
