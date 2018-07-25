---
title: Metadati degli elementi nella suddivisione in batch delle destinazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 486169788ad4533f5d45bf48c979ce3d0f5f7920
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081059"
---
# <a name="item-metadata-in-target-batching"></a>Metadati degli elementi nella suddivisione in batch delle destinazioni
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è in grado di eseguire l'analisi delle dipendenze per gli input e output di una destinazione di compilazione. Se viene stabilito che l'input o output della destinazione sono aggiornati, la destinazione viene ignorata e la compilazione prosegue. Gli elementi `Target` usano gli attributi `Inputs` e `Outputs` per specificare gli elementi da controllare durante l'analisi delle dipendenze.  
  
 Se una destinazione contiene un'attività che usa elementi suddivisi in batch come input o output, l'elemento `Target` della destinazione deve usare la suddivisione in batch negli attributi `Inputs` o `Outputs` per consentire a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di ignorare i batch di elementi che sono già aggiornati.  
  
## <a name="batch-targets"></a>Destinazioni di batch  
 L'esempio seguente contiene un elenco di elementi denominato `Res` che viene suddiviso in due batch in base ai metadati dell'elemento `Culture`. Ognuno di questi batch viene passato nell'attività `AL`, che crea un assembly di output per ogni batch. Usando la suddivisione in batch dell'attributo `Outputs` dell'elemento `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è in grado di determinare se ogni singolo batch è aggiornato prima di eseguire la destinazione. Senza usare la suddivisione in batch della destinazione, entrambi i batch di elementi verrebbero eseguiti dall'attività ogni volta che viene eseguita la destinazione.  
  
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
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Eseguire la compilazione incrementale](../msbuild/how-to-build-incrementally.md)   
 [Suddivisione in batch](../msbuild/msbuild-batching.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadati degli elementi nella suddivisione in batch delle attività](../msbuild/item-metadata-in-task-batching.md)