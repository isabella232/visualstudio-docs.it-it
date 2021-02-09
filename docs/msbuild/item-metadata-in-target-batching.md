---
title: Metadati degli elementi nella suddivisione in batch delle destinazioni | Microsoft Docs
description: Informazioni sul modo in cui MSBuild usa i metadati degli elementi nel batch di destinazione per eseguire l'analisi delle dipendenze degli input e degli output di una destinazione di compilazione.
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
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913905"
---
# <a name="item-metadata-in-target-batching"></a>Metadati degli elementi nella suddivisione in batch delle destinazioni

MSBuild è in grado di eseguire l'analisi delle dipendenze per gli input e gli output di una destinazione di compilazione. Se viene stabilito che l'input o output della destinazione sono aggiornati, la destinazione viene ignorata e la compilazione prosegue. Gli elementi `Target` usano gli attributi `Inputs` e `Outputs` per specificare gli elementi da controllare durante l'analisi delle dipendenze.

Se una destinazione contiene un'attività che usa elementi in batch come input o output, l' `Target` elemento della destinazione deve usare la suddivisione in batch negli `Inputs` `Outputs` attributi o per consentire a MSBuild di ignorare i batch di elementi che sono già aggiornati.

## <a name="batch-targets"></a>Destinazioni di batch

L'esempio seguente contiene un elenco di elementi denominato `Res` che viene suddiviso in due batch in base ai metadati dell'elemento `Culture`. Ognuno di questi batch viene passato nell'attività `AL`, che crea un assembly di output per ogni batch. Utilizzando la suddivisione in batch sull' `Outputs` attributo dell' `Target` elemento, MSBuild può determinare se ognuno dei singoli batch è aggiornato prima di eseguire la destinazione. Senza usare la suddivisione in batch della destinazione, entrambi i batch di elementi verrebbero eseguiti dall'attività ogni volta che viene eseguita la destinazione.

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

- [Procedura: eseguire la compilazione incrementale](../msbuild/how-to-build-incrementally.md)
- [Batch](../msbuild/msbuild-batching.md)
- [Elemento target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadati degli elementi nella suddivisione in batch delle attività](../msbuild/item-metadata-in-task-batching.md)
