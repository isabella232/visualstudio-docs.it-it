---
title: Procedure consigliate per MSBuild | Microsoft Docs
description: Informazioni sulle procedure consigliate per la scrittura MSBuild script, ad esempio l'uso degli attributi Condition e il non uso di caratteri jolly.
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
ms.openlocfilehash: c407e93234af7491e99d66d70f667efdc85b5f3790cf7f76408ffa65ee7c9d6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397592"
---
# <a name="msbuild-best-practices"></a>Procedure consigliate per MSBuild

Per la scrittura degli script di MSBuild è consigliabile seguire le indicazioni riportate di seguito:

- I valori di proprietà predefiniti vengono gestiti meglio con l'attributo `Condition` e non dichiarando una proprietà il cui valore predefinito può essere sottoposto a override nella riga di comando. Ad esempio, usare

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- In generale, evitare l'uso di caratteri jolly quando si selezionano gli elementi. Al contrario, specificare i file in modo esplicito. Ciò è dovuto al fatto che nella maggior parte dei tipi di progetto MSBuild espande i caratteri jolly in diversi momenti, ad esempio quando si aggiungono o rimuovono elementi, il che può causare un comportamento imprevisto. Un'eccezione è nei progetti .NET Core SDK, che elaborano correttamente i caratteri jolly.

## <a name="see-also"></a>Vedi anche

- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
