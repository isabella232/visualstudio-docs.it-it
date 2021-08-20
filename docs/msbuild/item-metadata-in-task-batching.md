---
title: Metadati degli elementi nella suddivisione in batch delle attività | Microsoft Docs
description: Informazioni su MSBuild i metadati degli elementi nell'invio in batch di attività per dividere gli elenchi di elementi in categorie o batch diversi ed eseguire un'attività una volta con ogni batch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b3afd2b860d56fd78d01cf9509c7e3c75fc9c4e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136885"
---
# <a name="item-metadata-in-task-batching"></a>Metadati degli elementi nella suddivisione in batch delle attività

MSBuild è in grado di dividere gli elenchi di elementi in categorie o batch diversi, in base ai metadati degli elementi, ed eseguire un'attività una volta con ogni batch. Può non essere semplice comprendere esattamente quali elementi vengono passati e a quale batch. Questo argomento descrive gli scenari più comuni relativi alla suddivisione in batch.

- Suddivisione in batch di un elenco di elementi

- Suddivisione in batch di più elenchi di elementi

- Suddivisione in batch di un elemento per volta

- Filtraggio di elenchi di elementi

Per altre informazioni sull'invio in batch con MSBuild, vedere [Invio in batch.](../msbuild/msbuild-batching.md)

## <a name="divide-an-item-list-into-batches"></a>Suddividere in batch un elenco di elementi

La suddivisione in batch consente di dividere un elenco di elementi in vari batch in base ai metadati degli elementi e di passare separatamente ogni batch a un'attività. Questa procedura è utile per compilare assembly satellite.

L'esempio seguente illustra come dividere in batch un elenco di elementi in base ai metadati degli elementi. L'elenco di elementi `ExampColl` viene diviso in tre batch in base ai metadati dell'elemento `Number`. La presenza di `%(ExampColl.Number)` `Text` nell'attributo notifica MSBuild l'invio in batch. L'elenco di elementi `ExampColl` viene diviso in tre batch in base ai metadati dell'elemento `Number` e ogni batch viene passato separatamente all'attività.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>
    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

L'[attività Message](../msbuild/message-task.md) visualizza le informazioni seguenti:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Suddividere in batch più elenchi di elementi

MSBuild possibile dividere più elenchi di elementi in batch in base ai medesimi metadati. Risulta quindi più semplice dividere in batch diversi elenchi di elementi per compilare più assembly. Ad esempio, è possibile avere un elenco di elementi di file con estensione *cs* suddivisi in un batch di applicazioni e un batch di assembly e un elenco di elementi di file di risorse suddivisi in un batch di applicazioni e un batch di assembly. Sarà quindi possibile usare la suddivisione in batch per passare questi elenchi di elementi a un'attività e compilare sia l'applicazione che l'assembly.

> [!NOTE]
> Se un elenco di elementi passato a un'attività non contiene elementi con i metadati di riferimento, ogni elemento incluso nell'elenco viene passato a ogni batch.

L'esempio seguente illustra come dividere più elenchi di elementi in batch in base ai metadati degli elementi. Gli elenchi di elementi `ExampColl` e `ExampColl2` vengono divisi ognuno in tre batch in base ai metadati dell'elemento `Number`. La presenza di `%(Number)` `Text` nell'attributo notifica MSBuild l'invio in batch. Gli elenchi di elementi `ExampColl` e `ExampColl2` vengono divisi in tre batch in base ai metadati dell'elemento `Number` e ogni batch viene passato separatamente all'attività.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>

        <ExampColl2 Include="Item4">
            <Number>1</Number>
        </ExampColl2>
        <ExampColl2 Include="Item5">
            <Number>2</Number>
        </ExampColl2>
        <ExampColl2 Include="Item6">
            <Number>3</Number>
        </ExampColl2>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>
    </Target>

</Project>
```

L'[attività Message](../msbuild/message-task.md) visualizza le informazioni seguenti:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Suddividere in batch di un elemento per volta

È possibile eseguire la suddivisione in batch anche su metadati noti assegnati a ogni elemento al momento della creazione. In questo modo ogni elemento di una raccolta avrà alcuni metadati da usare per la suddivisione in batch. Il `Identity` valore dei metadati è utile per dividere ogni elemento in un elenco di elementi in un batch separato. Per un elenco completo dei metadati degli elementi noti, vedere [Metadati di elementi noti](../msbuild/msbuild-well-known-item-metadata.md).

L'esempio seguente illustra come eseguire in batch un elemento di un elenco per volta. `ExampColl`L'elenco di elementi è suddiviso in sei batch, ognuno dei quali contiene un elemento dell'elenco di elementi. La presenza di `%(Identity)` `Text` nell'attributo notifica MSBuild l'invio in batch.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1"/>
        <ExampColl Include="Item2"/>
        <ExampColl Include="Item3"/>
        <ExampColl Include="Item4"/>
        <ExampColl Include="Item5"/>
        <ExampColl Include="Item6"/>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Identity: '%(Identity)' -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

L'[attività Message](../msbuild/message-task.md) visualizza le informazioni seguenti:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

Non è `Identity` tuttavia garantito che sia univoco. Il relativo valore è il valore finale valutato `Include` dell'attributo. Pertanto, se gli `Include` attributi vengono usati più volte, vengono uniti in batch. Come illustrato nell'esempio seguente, questa tecnica richiede che gli `Include` attributi siano univoci per ogni elemento del gruppo. Per illustrare questo punto, prendere in considerazione il codice seguente:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Item Include="1">
      <M>1</M>
    </Item>
    <Item Include="1">
      <M>2</M>
    </Item>
    <Item Include="2">
      <M>3</M>
    </Item>
  </ItemGroup>

  <Target Name="Batching">
    <Warning Text="@(Item->'%(Identity): %(M)')" Condition=" '%(Identity)' != '' "/>
  </Target>
</Project>
```

L'output mostra che i primi due elementi si trovano nello stesso batch, perché `Include` l'attributo è lo stesso per essi:

```output
test.proj(15,5): warning : 1: 1;1: 2
test.proj(15,5): warning : 2: 3
```

## <a name="filter-item-lists"></a>Filtrare gli elementi di un elenco

È possibile usare la suddivisione in batch per filtrare alcuni elementi da un elenco prima di passarli a un'attività. Ad esempio, l'applicazione di un filtro al valore `Extension` dei metadati di un elemento noto consente di eseguire un'attività solo sui file con una determinata estensione.

L'esempio seguente illustra come dividere in batch un elenco di elementi in base ai metadati degli elementi e come filtrare i batch risultanti nel momento in cui vengono passati a un'attività. L'elenco di elementi `ExampColl` viene diviso in tre batch in base ai metadati dell'elemento `Number`. L'attributo `Condition` dell'attività specifica che verranno passati all'attività esclusivamente i batch con un valore di metadati dell'elemento `Number` pari a `2`.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>

    </ItemGroup>

    <Target Name="Exec">
        <Message
            Text = "Items in ExampColl: @(ExampColl)"
            Condition="'%(Number)'=='2'"/>
    </Target>

</Project>
```

L'[attività Message](../msbuild/message-task.md) visualizza le informazioni seguenti:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Vedi anche

- [Metadati di elementi noti](../msbuild/msbuild-well-known-item-metadata.md)
- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Batch](../msbuild/msbuild-batching.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
