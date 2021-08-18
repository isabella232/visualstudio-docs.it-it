---
title: Trasformazioni di MSBuild | Microsoft Docs
description: Informazioni su come MSBuild le trasformazioni, conversioni uno-a-uno di un elenco di elementi in un altro, per compilare progetti in modo più efficiente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 1428019cad4c057c41721f30c9375a60c3cbc55f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108499"
---
# <a name="msbuild-transforms"></a>Trasformazioni di MSBuild

Una trasformazione è una conversione uno-a-uno di un elenco di elementi in un altro. Oltre a consentire a un progetto di convertire gli elenchi di elementi, una trasformazione consente a una destinazione di identificare un mapping diretto tra gli input e gli output. Questo argomento illustra le trasformazioni e il modo in cui MSBuild per compilare progetti in modo più efficiente.

## <a name="transform-modifiers"></a>Modificatori di comandi

Le trasformazioni non sono arbitrarie, ma sono limitate da una sintassi speciale in cui tutti i modificatori di trasformazione devono essere nel formato %( \<ItemMetaDataName> ). I metadati degli elementi possono essere usati come modificatori della trasformazione. Sono inclusi i metadati noti degli elementi, assegnati a ogni elemento al momento della creazione. Per un elenco di tutti i metadati noti degli elementi, vedere [Metadati noti degli elementi di MSBuild](../msbuild/msbuild-well-known-item-metadata.md).

Nell'esempio seguente un elenco di file con estensione *resx* viene trasformato in un elenco di file con estensione *resources*. Il modificatore di trasformazione %(filename) specifica che ogni file con estensione *resources* ha lo stesso nome del file con estensione *resx* corrispondente.

```xml
@(RESXFile->'%(filename).resources')
```

Se, ad esempio, gli elementi contenuti nell'elenco @(RESXFile) sono *Form1.resx*, *Form2.resx* e *Form3.resx*, gli output nell'elenco trasformato saranno *Form1.resources*, *Form2.resources* e *Form3.resources*.

> [!NOTE]
> Per un elenco di elementi trasformato è possibile specificare un separatore personalizzato, in modo analogo a quanto accade con un elenco di elementi standard. Per separare, ad esempio, un elenco di elementi trasformato usando una virgola (,) anziché il punto e virgola predefinito (;), usare il codice XML seguente: `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Uso di più modificatori

 Un'espressione di trasformazione può contenere più modificatori, che possono essere combinati in qualsiasi ordine e ripetuti. Nell'esempio seguente il nome della directory che contiene il file viene modificato, ma i file mantengono il nome e l'estensione originali.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Se, ad esempio, gli elementi contenuti nell'elenco `RESXFile` sono *Project1\Form1.resx*, *Project1\Form2.resx* e *Project1\Form3.text*, gli output nell'elenco trasformato saranno *Toolset\Form1.resx*, *Toolset\Form2.resx* e *Toolset\Form3.text*.

## <a name="dependency-analysis"></a>analisi delle dipendenze

 Le trasformazioni garantiscono un mapping uno-a-uno tra l'elenco di elementi trasformato e l'elenco di elementi originale. Pertanto, se una destinazione crea output che sono trasformazioni degli input, MSBuild può analizzare i timestamp degli input e degli output e decidere se ignorare, compilare o ricompilare parzialmente una destinazione.

 Nell'[attività Copy](../msbuild/copy-task.md) dell'esempio seguente, ogni file dell'elenco di elementi `BuiltAssemblies` è associato a un file nella cartella di destinazione dell'attività, specificata con una trasformazione nell'attributo `Outputs`. Se viene modificato un file dell'elenco di elementi `BuiltAssemblies`, l'attività `Copy` viene eseguita solo per il file modificato e tutti gli altri file vengono ignorati. Per altre informazioni sull'analisi delle dipendenze e su come usare le trasformazioni, vedere [Procedura: Compilare in modo incrementale](../msbuild/how-to-build-incrementally.md).

```xml
<Target Name="CopyOutputs"
    Inputs="@(BuiltAssemblies)"
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">

    <Copy
        SourceFiles="@(BuiltAssemblies)"
        DestinationFolder="$(OutputPath)"/>

</Target>
```

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

 L'esempio seguente mostra un MSBuild di progetto che usa le trasformazioni. Questo esempio presuppone che nella directory *c:\sub0\sub1\sub2\sub3* sia presente un solo file *xsd* e che la directory di lavoro sia *c:\sub0*.

### <a name="code"></a>Codice

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Schema Include="sub1\**\*.xsd"/>
    </ItemGroup>

    <Target Name="Messages">
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>
        <Message Text="identity: @(Schema->'%(identity)')"/>
        <Message Text="filename: @(Schema->'%(filename)')"/>
        <Message Text="directory: @(Schema->'%(directory)')"/>
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>
        <Message Text="extension: @(Schema->'%(extension)')"/>
    </Target>
</Project>
```

### <a name="comments"></a>Commenti

 Nell'esempio viene prodotto l'output seguente:

```
rootdir: C:\
fullpath: C:\sub0\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\sub0\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: sub0\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>Vedi anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Procedura: Compilare in modo incrementale](../msbuild/how-to-build-incrementally.md)
