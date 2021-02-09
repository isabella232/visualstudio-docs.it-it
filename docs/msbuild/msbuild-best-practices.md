---
title: Procedure consigliate per MSBuild | Microsoft Docs
description: Informazioni sulle procedure consigliate per la scrittura di script MSBuild, ad esempio l'uso di attributi di condizione e non l'uso di caratteri jolly.
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
ms.workload:
- multiple
ms.openlocfilehash: 83527ac4b7d16d2cb06c797924c18f2567f12350
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919194"
---
# <a name="msbuild-best-practices"></a>Procedure consigliate per MSBuild

Per la scrittura degli script di MSBuild è consigliabile seguire le indicazioni riportate di seguito:

- I valori di proprietà predefiniti vengono gestiti meglio con l'attributo `Condition` e non dichiarando una proprietà il cui valore predefinito può essere sottoposto a override nella riga di comando. Ad esempio, usare

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- In generale, evitare l'uso di caratteri jolly quando si selezionano gli elementi. Al contrario, specificare i file in modo esplicito. Questo perché nella maggior parte dei tipi di progetto, MSBuild espande i caratteri jolly in diversi momenti, ad esempio quando si aggiungono o rimuovono elementi, il che può causare un comportamento imprevisto. Un'eccezione a questo si verifica nei progetti di tipo .NET Core SDK, che consentono di elaborare correttamente i caratteri jolly.

## <a name="see-also"></a>Vedi anche

- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
