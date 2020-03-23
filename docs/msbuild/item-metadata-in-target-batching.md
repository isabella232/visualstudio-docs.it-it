---
title: Metadati degli elementi nella suddivisione in batch delle destinazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633668"
---
# <a name="item-metadata-in-target-batching"></a>Metadati degli elementi nella suddivisione in batch delle destinazioni

MSBuild è in grado di eseguire l'analisi delle dipendenze sugli input e gli output di una destinazione di compilazione. Se viene stabilito che l'input o output della destinazione sono aggiornati, la destinazione viene ignorata e la compilazione prosegue. Gli elementi `Target` usano gli attributi `Inputs` e `Outputs` per specificare gli elementi da controllare durante l'analisi delle dipendenze.

Se una destinazione contiene un'attività che usa elementi in `Target` batch come input o output, l'elemento della destinazione deve usare l'invio in batch nei attributi `Inputs` o `Outputs` per consentire a MSBuild di ignorare i batch di elementi già aggiornati.

## <a name="batch-targets"></a>Destinazioni di batch

L'esempio seguente contiene un elenco di elementi denominato `Res` che viene suddiviso in due batch in base ai metadati dell'elemento `Culture`. Ognuno di questi batch viene passato nell'attività `AL`, che crea un assembly di output per ogni batch. Utilizzando l'invio `Outputs` in batch `Target` sull'attributo dell'elemento, MSBuild può determinare se ognuno dei singoli batch è aggiornato prima di eseguire la destinazione. Senza usare la suddivisione in batch della destinazione, entrambi i batch di elementi verrebbero eseguiti dall'attività ogni volta che viene eseguita la destinazione.

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

## <a name="see-also"></a>Vedere anche

- [Procedura: compilare in modo incrementaleHow to: Build incrementally](../msbuild/how-to-build-incrementally.md)
- [Batch](../msbuild/msbuild-batching.md)
- [Elemento di destinazione (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadati dell'elemento nell'invio in batch di attività](../msbuild/item-metadata-in-task-batching.md)
