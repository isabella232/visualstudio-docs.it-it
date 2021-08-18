---
title: Compilazione di più progetti in parallelo con MSBuild | Microsoft Docs
description: Informazioni sulle impostazioni MSBuild che è possibile usare per compilare più progetti più velocemente eseguendoli in parallelo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b6bdbb3efdf836f29307bdf97b21c5a910ef908f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109006"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>Compilare più progetti in parallelo con MSBuild

È possibile utilizzare MSBuild per compilare più progetti più velocemente eseguendoli in parallelo. Per eseguire compilazioni in parallelo, è possibile utilizzare le impostazioni seguenti in un computer multicore o con più processori:

- L'opzione `-maxcpucount` a un prompt dei comandi.

- Il parametro dell'attività <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> in un attività MSBuild.

> [!NOTE]
> L'opzione **-verbosity** (**-v**) in una riga di comando può incidere sulle prestazioni di compilazione, che possono diminuire se il livello di dettaglio delle informazioni del log di compilazione è impostato su dettagliato o diagnostico, utilizzati per la risoluzione dei problemi. Per altre informazioni, vedere [Recuperare log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md) e [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).

## <a name="-maxcpucount-switch"></a>Opzione -maxcpucount

Se si usa l'opzione `-maxcpucount` o l'abbreviazione `-m`, tramite MSBuild è possibile creare il numero specificato di processi *MSBuild.exe* eseguibili in parallelo. Questi processi sono noti anche come "processi di lavoro". Ogni processo di lavoro usa un componente principale o un processore separato, se disponibile, per compilare progetti mentre altri processori eventualmente disponibili ne compilano altri. Ad esempio, se si imposta questa opzione su un valore pari a "4", in MSBuild verranno creati quattro processi di lavoro per compilare il progetto.

Se si include l'opzione `-maxcpucount` senza specificare un valore, in MSBuild verranno utilizzati fino al numero massimo di processori presenti nel computer.

Per altre informazioni su questa opzione, introdotta in MSBuild 3.5, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).

Nell'esempio seguente viene indicato a MSBuild di utilizzare tre processi di lavoro. Se si utilizza questa configurazione, tramite MSBuild sarà possibile compilare tre progetti contemporaneamente.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>Parametro dell'attività BuildInParallel

`BuildInParallel`è un parametro booleano facoltativo in un'MSBuild attività. Quando `BuildInParallel` è impostato su `true` (il valore predefinito è `true`), vengono generati più processi di lavoro per compilare contemporaneamente il maggior numero possibile di progetti. Affinché questo approccio funzioni, è necessario che l'opzione `-maxcpucount` sia impostata su un valore maggiore di 1 e che il sistema sia almeno di tipo dual-core o che disponga di due o più processori.

Di seguito è riportato un esempio, tratto da *microsoft.common.targets*, che descrive come impostare il parametro `BuildInParallel`.

```xml
<PropertyGroup>
    <BuildInParallel Condition="'$(BuildInParallel)' ==
        ''">true</BuildInParallel>
</PropertyGroup>
<MSBuild
    Projects="@(_MSBuildProjectReferenceExistent)"
    Targets="GetTargetPath"
    BuildInParallel="$(BuildInParallel)"
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);
        %(_MSBuildProjectReferenceExistent.SetPlatform)"
    Condition="'@(NonVCProjectReference)'!='' and
        ('$(BuildingSolutionFile)' == 'true' or
        '$(BuildingInsideVisualStudio)' == 'true' or
        '$(BuildProjectReferences)' != 'true') and
        '@(_MSBuildProjectReferenceExistent)' != ''"
    ContinueOnError="!$(BuildingProject)">
    <Output TaskParameter="TargetOutputs"
        ItemName="_ResolvedProjectReferencePaths"/>
</MSBuild>
```

## <a name="see-also"></a>Vedi anche

- [Usare più processori per la compilazione di progetti](../msbuild/using-multiple-processors-to-build-projects.md)
- [Scrivere logger compatibili con più processori](../msbuild/writing-multi-processor-aware-loggers.md)
- [Blog di ottimizzazione del parallelismo di compilazione di C++](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
