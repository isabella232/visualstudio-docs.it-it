---
title: 'Procedura: Usare caratteri di escape per caratteri speciali in MSBuild | Microsoft Docs'
description: Informazioni su come eseguire l'escape dei caratteri speciali in modo che sia possibile usare questi caratteri come valori letterali nei file di progetto MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 923c517653c42dd0362b398c420c99454ccf4034
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436403"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Procedura: Usare caratteri di escape speciali in MSBuild

Alcuni caratteri hanno un significato particolare nei file di progetto di MSBuild. Tra gli esempi di carattere sono inclusi il punto e virgola (`;`) e l'asterisco (`*`). Per un elenco completo di questi caratteri speciali, vedere [caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md).

Per usare questi caratteri speciali come valori letterali in un file di progetto, è necessario specificarli usando la sintassi `%<xx>`, dove `<xx>` rappresenta il valore esadecimale ASCII del carattere.

## <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild

I caratteri speciali sono usati, ad esempio, nell'attributo `Include` degli elenchi di elementi. L'elenco di elementi seguenti, ad esempio, dichiara due elementi: *MyFile.cs* e *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Se si desidera dichiarare un elemento che contiene un punto e virgola nel nome, è necessario utilizzare la `%<xx>` sintassi per eseguire l'escape del punto e virgola e impedire a MSBuild di dichiarare due elementi distinti. L'elemento seguente, ad esempio, usa il carattere di escape per il punto e virgola e dichiara un solo elemento denominato `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

È anche possibile usare una [funzione di proprietà](../msbuild/property-functions.md) per aggiungere caratteri di escape alle stringhe. Ad esempio, questo equivale all'esempio precedente.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Per usare un carattere speciale di MSBuild come carattere letterale

Usare la notazione `%<xx>` al posto del carattere speciale, dove `<xx>` rappresenta il valore esadecimale del carattere ASCII. Ad esempio, per usare un asterisco (`*`) come carattere letterale, usare il valore `%2A`.

## <a name="see-also"></a>Vedere anche
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Elementi](../msbuild/msbuild-items.md)
