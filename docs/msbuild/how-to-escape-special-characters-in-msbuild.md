---
title: 'Procedura: Usare caratteri di escape speciali in MSBuild | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 983e10f26e6fd1d8b4b7ff18c73edd65cb4810f4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634630"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Procedura: Usare caratteri di escape speciali in MSBuild

Alcuni caratteri hanno un significato particolare nei file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tra gli esempi di carattere sono inclusi il punto e virgola (`;`) e l'asterisco (`*`). Per un elenco completo di questi caratteri speciali, vedere [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md).

Per usare questi caratteri speciali come valori letterali in un file di progetto, è necessario specificarli usando la sintassi `%<xx>`, dove `<xx>` rappresenta il valore esadecimale ASCII del carattere.

## <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild

I caratteri speciali sono usati, ad esempio, nell'attributo `Include` degli elenchi di elementi. L'elenco di elementi seguente dichiara ad esempio due elementi: *MyFile.cs* e *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Per dichiarare un elemento che contiene un punto e virgola nel nome, è necessario usare la sintassi `%<xx>` per aggiungere il carattere di escape al punto e virgola e impedire a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di dichiarare due elementi separati. L'elemento seguente, ad esempio, usa il carattere di escape per il punto e virgola e dichiara un solo elemento denominato `MyFile.cs;MyClass.cs`.

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
