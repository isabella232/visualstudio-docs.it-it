---
title: Procedure consigliate per MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263149"
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

## <a name="see-also"></a>Vedere anche

- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
