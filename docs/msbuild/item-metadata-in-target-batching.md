---
title: Metadati degli elementi nella suddivisione in batch delle destinazioni | Microsoft Docs
description: Informazioni su MSBuild i metadati degli elementi nell'invio in batch di destinazione per eseguire l'analisi delle dipendenze sugli input e gli output di una destinazione di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 10691a013f79f83854f1b942a2d9d1ec1d9cf8c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069061"
---
# <a name="item-metadata-in-target-batching"></a>Metadati degli elementi nella suddivisione in batch delle destinazioni

MSBuild può eseguire l'analisi delle dipendenze sugli input e gli output di una destinazione di compilazione. Se viene stabilito che l'input o output della destinazione sono aggiornati, la destinazione viene ignorata e la compilazione prosegue. Gli elementi `Target` usano gli attributi `Inputs` e `Outputs` per specificare gli elementi da controllare durante l'analisi delle dipendenze.

Se una destinazione contiene un'attività che usa elementi in batch come input o output, l'elemento della destinazione deve usare l'invio in batch nei relativi attributi o per consentire a MSBuild di ignorare batch di elementi già `Target` `Inputs` `Outputs` aggiornati.

## <a name="batch-targets"></a>Destinazioni di batch

L'esempio seguente contiene un elenco di elementi denominato `Res` che viene suddiviso in due batch in base ai metadati dell'elemento `Culture`. Ognuno di questi batch viene passato nell'attività `AL`, che crea un assembly di output per ogni batch. Usando l'invio in batch nell'attributo dell'elemento, MSBuild possibile determinare se ognuno dei singoli batch è aggiornato prima di eseguire `Outputs` `Target` la destinazione. Senza usare la suddivisione in batch della destinazione, entrambi i batch di elementi verrebbero eseguiti dall'attività ogni volta che viene eseguita la destinazione.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Procedura: Compilare in modo incrementale](../msbuild/how-to-build-incrementally.md)
- [Batch](../msbuild/msbuild-batching.md)
- [Elemento target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadati degli elementi nella suddivisione in batch delle attività](../msbuild/item-metadata-in-task-batching.md)
