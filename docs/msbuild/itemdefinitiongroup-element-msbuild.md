---
title: Elemento ItemDefinitionGroup (MSBuild) | Microsoft Docs
description: Informazioni su MSBuild usa l'elemento ItemDefinitionGroup per definire un set di definizioni di elementi e valori di metadati applicati a tutti gli elementi nel progetto.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 3eeea6faf2456dadb1083658d8403a7d2501aa0e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093756"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Elemento ItemDefinitionGroup (MSBuild)

L'elemento `ItemDefinitionGroup` consente di definire un set di definizioni di elementi, ovvero valori di metadati applicati a tutti gli elementi nel progetto per impostazione predefinita. ItemDefinitionGroup ovvia alla necessità di usare l'[attività CreateItem](../msbuild/createitem-task.md) e l'[attività CreateProperty](../msbuild/createproperty-task.md). Per altre informazioni, vedere [Definizioni degli elementi.](../msbuild/item-definitions.md)

\<Project>
\<ItemDefinitionGroup>

## <a name="syntax"></a>Sintassi

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo. Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione. Possono esistere zero o più elementi `Item` in un `ItemDefinitionGroup`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file MSBuild progetto. |

## <a name="example"></a>Esempio

L'esempio di codice seguente definisce due elementi di metadati, m e n, in un ItemDefinitionGroup. In questo esempio il metadato predefinito "m" viene applicato all'elemento "i" perché non è definito in modo esplicito dall'elemento "i". Al contrario, il metadato predefinito "n" non viene applicato all'elemento "i" perché è già definito dall'elemento "i".

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Project riferimento allo schema del file](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementi](../msbuild/msbuild-items.md)
