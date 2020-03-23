---
title: Batch MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78aeef8ea651aac1fe2a780207474399f4bbcf09
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633434"
---
# <a name="msbuild-batching"></a>Batch MSBuild

MSBuild ha la possibilità di dividere gli elenchi di elementi in diverse categorie, o batch, in base ai metadati dell'elemento ed eseguire una destinazione o un'attività una volta con ogni batch.

## <a name="task-batching"></a>Suddivisione in batch delle attività

Suddividere le attività in batch consente di semplificare i file di progetto, dividendo gli elenchi di elementi in diversi batch che vengono poi passati separatamente in un'attività. Ciò significa che per un file di progetto è necessario dichiarare l'attività e i relativi attributi solo una volta, anche se può essere eseguito più volte.

Si specifica che si desidera che MSBuild per eseguire\<l'invio in batch con un'attività utilizzando la notazione %( ItemMetaDataName>) in uno degli attributi dell'attività. L'esempio seguente suddivide l'elenco di elementi `Example` in batch in base al valore dei metadati degli elementi `Color` e passa ogni batch all'attività `MyTask` separatamente.

> [!NOTE]
> Se non viene fatto riferimento all'elenco di elementi altrove negli attributi dell'attività o il nome dei metadati è ambiguo, è possibile usare la notazione %(\<ItemCollection.ItemMetaDataName>) per qualificare completamente il valore dei metadati degli elementi da usare per la suddivisione in batch.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Per esempi più specifici della suddivisione in batch, vedere [Metadati degli elementi nella suddivisione in batch delle attività](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Suddivisione in batch della destinazione

MSBuild controlla se gli input e gli output di una destinazione sono aggiornati prima di eseguire la destinazione. Se sia gli input che gli output sono aggiornati, la destinazione viene ignorata. Se un'attività all'interno di una destinazione usa l'invio in batch, MSBuild deve determinare se gli input e gli output per ogni batch di elementi sono aggiornati. In caso contrario, la destinazione viene eseguita ogni volta che viene raggiunta.

L'esempio seguente illustra un elemento `Target` che contiene un attributo `Outputs` con la notazione %(\<ItemMetaDataName>). MSBuild dividerà `Example` l'elenco di elementi `Color` in batch in base ai metadati dell'elemento e analizzerà i timestamp dei file di output per ogni batch. Se gli output di un batch non sono aggiornati, la destinazione viene eseguita. In caso contrario, la destinazione viene ignorata.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Per un altro esempio di suddivisione in batch della destinazione, vedere [Metadati degli elementi nell'esecuzione in batch delle destinazioni](../msbuild/item-metadata-in-target-batching.md).

## <a name="property-functions-using-metadata"></a>Funzioni delle proprietà che usano i metadati

La suddivisione in batch può essere controllata usando funzioni delle proprietà che includono i metadati. Ad esempio,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

usa <xref:System.IO.Path.Combine%2A> per combinare un percorso di cartella radice con un percorso di elemento Compile.

Le funzioni delle proprietà possono non apparire all'interno dei valori dei metadati. Ad esempio,

`%(Compile.FullPath.Substring(0,3))`

non è consentito.

Per altre informazioni sulle funzioni delle proprietà, vedere [Funzioni delle proprietà](../msbuild/property-functions.md).

## <a name="see-also"></a>Vedere anche

- [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
