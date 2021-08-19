---
title: 'Procedura: Eseguire la compilazione incrementale | Microsoft Docs'
description: Informazioni su come usare MSBuild compilazione incrementale, in modo che i componenti compilati in precedenza che sono ancora aggiornati non siano ricompilati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 41e4ae9e1c174f95c36c05c50d3d7e88e2bd369f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085078"
---
# <a name="how-to-build-incrementally"></a>Procedura: Eseguire la compilazione incrementale

Quando si compila un progetto di grandi dimensioni, è importante che i componenti compilati precedentemente e ancora aggiornati non vengano ricompilati. Se vengono ricompilate tutte le destinazioni, ogni compilazione impiegherà molto tempo. Per abilitare compilazioni incrementali (compilazioni in cui vengono ricompilate solo le destinazioni che non sono state compilate prima o destinazioni non aggiornate), il Microsoft Build Engine (MSBuild) può confrontare i timestamp dei file di input con i timestamp dei file di output e determinare se ignorare, compilare o ricompilare parzialmente una destinazione. Per questa operazione di confronto, è necessario un mapping uno a uno tra input e output. È possibile usare le trasformazioni per consentire alle destinazioni di identificare tale mapping diretto. Per altre informazioni sulle trasformazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Specifica di input e output

Una destinazione può essere compilata in modo incrementale se gli input e gli output sono specificati nel file di progetto.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Per specificare input e output per una destinazione

- Usare gli attributi `Inputs` e `Outputs` dell'elemento `Target`. Esempio:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild possibile confrontare i timestamp dei file di input con i timestamp dei file di output e determinare se ignorare, compilare o ricompilare parzialmente una destinazione. Nell'esempio seguente, se un file nell'elenco di elementi è più recente del filehello.exe, MSBuild eseguirà la destinazione; in caso contrario, `@(CSFile)` verrà ignorato: 

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Quando gli input e gli output sono specificati in una destinazione, ogni output può essere mappato solo a un input oppure potrebbe non esserci alcun mapping diretto tra gli output e gli input. Nell'attività [Csc](../msbuild/csc-task.md)precedente, ad esempio, l'output, *hello.exe*, non può essere mappato a un singolo input, perché dipende da tutti.

> [!NOTE]
> Una destinazione in cui non esiste alcun mapping diretto tra gli input e gli output verrà sempre compilata più spesso di una destinazione in cui ogni output può essere mappato a un solo input perché MSBuild non è in grado di determinare quali output devono essere ricompilati se alcuni degli input sono stati modificati.

Le attività in cui è possibile identificare un mapping diretto tra output e input, ad esempio l'[attività LC](../msbuild/lc-task.md), sono più adatte per le compilazioni incrementali, a differenza delle attività [Csc](../msbuild/csc-task.md) e [Vbc](../msbuild/vbc-task.md), che producono un assembly di output da un numero di input.

## <a name="example"></a>Esempio

Nell'esempio seguente viene usato un progetto che compila file della Guida per un ipotetico sistema di Guida. Il progetto converte i file di origine con estensione *txt* in file con estensione *content* intermedi, che vengono quindi combinati con i file di metadati XML per generare il file con estensione *help* finale usato dal sistema della Guida. Il progetto usa le attività ipotetiche seguenti:

- `GenerateContentFiles`: converte file *txt* in file *content*.

- `BuildHelp`: combina i file *content* e i file di metadati XML per compilare il file *help* finale.

Il progetto usa trasformazioni per creare un mapping uno a uno tra input e output nell'attività `GenerateContentFiles`. Per altre informazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md). L'elemento `Output` è impostato per usare automaticamente gli output dall'attività `GenerateContentFiles` come input per l'attività `BuildHelp`.

Questo file di progetto contiene le destinazioni `Convert` e `Build`. Le attività `GenerateContentFiles` e `BuildHelp` vengono inserite rispettivamente nelle destinazioni `Convert` e `Build` in modo che ogni destinazione possa essere compilata in modo incrementale. Tramite l'elemento `Output`, gli output dell'attività `GenerateContentFiles` vengono inseriti nell'elenco di elementi `ContentFile` dove possono essere usati come input per l'attività `BuildHelp`. L'uso dell'elemento `Output` in questo modo offre automaticamente gli output da un'attività come input per un'altra attività in modo che non sia necessario elencare manualmente i singoli elementi o elenchi di elementi in ogni attività.

> [!NOTE]
> Sebbene la destinazione `GenerateContentFiles` possa essere compilata in modo incrementale, tutti gli output di tale destinazione sono sempre necessari come input per la destinazione `BuildHelp`. MSBuild fornisce automaticamente tutti gli output da una destinazione come input per un'altra destinazione quando si usa `Output` l'elemento .

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
    </ItemGroup>

    <Target Name = "Convert"
        Inputs="@(TXTFile)"
        Outputs="@(TXTFile->'%(Filename).content')">

        <GenerateContentFiles
            Sources = "@(TXTFile)">
            <Output TaskParameter = "OutputContentFiles"
                ItemName = "ContentFiles"/>
        </GenerateContentFiles>
    </Target>

    <Target Name = "Build" DependsOnTargets = "Convert"
        Inputs="@(ContentFiles);@(XMLFiles)"
        Outputs="$(MSBuildProjectName).help">

        <BuildHelp
            ContentFiles = "@(ContentFiles)"
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Server di destinazione](../msbuild/msbuild-targets.md)
- [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Trasformazioni](../msbuild/msbuild-transforms.md)
- [Csc (attività)](../msbuild/csc-task.md)
- [Vbc (attività)](../msbuild/vbc-task.md)
