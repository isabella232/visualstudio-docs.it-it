---
title: 'Procedura: Usare la stessa destinazione in più file di progetto | Microsoft Docs'
description: Informazioni su come salvare una destinazione in un MSBuild di progetto e importarla in qualsiasi altro progetto che deve usare la destinazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 1f9fa6593cfb5e6ef21379b7513be02d943e9c66
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143339"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Procedura: Usare la stessa destinazione in più file di progetto

Se sono stati creati diversi MSBuild di progetto, è possibile che sia necessario usare le stesse attività e le stesse destinazioni in file di progetto diversi. Anziché includere in ogni file di progetto la descrizione completa di tali attività o destinazioni, è possibile salvare una destinazione in un file di progetto separato e importarlo in qualsiasi altro progetto in cui si intende usare la destinazione.

## <a name="use-the-import-element"></a>Usare l'elemento Import

L'elemento `Import` consente di inserire un file di progetto in un altro file di progetto. Il file di progetto da importare deve essere un file di MSBuild file di progetto valido e contenere codice XML ben formato. L'attributo `Project` specifica il percorso del file di progetto importato. Per altre informazioni `Import` sull'elemento , vedere Elemento Import [(MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Per importare un progetto

1. Nel file di progetto di importazione definire tutte le proprietà e gli elementi usati come parametri per le proprietà e gli elementi del progetto importato.

2. Usare l'elemento `Import` per importare il progetto. Esempio:

     `<Import Project="MyCommon.targets"/>`

3. Dopo l'elemento `Import`, definire tutte le proprietà e gli elementi che devono eseguire l'override delle definizioni predefinite delle proprietà e degli elementi presenti nel progetto importato.

## <a name="order-of-evaluation"></a>Ordine di valutazione

 Quando MSBuild raggiunge un elemento, il progetto importato viene inserito in modo efficace nel progetto di importazione `Import` nel percorso `Import` dell'elemento. La posizione dell'elemento `Import` può quindi influire sui valori delle proprietà e degli elementi ed è importante conoscere sia le proprietà e gli elementi impostati dal progetto importato, sia le proprietà e gli elementi usati dal progetto.

 Quando si compila il progetto, vengono valutate prima tutte le proprietà e dopo gli elementi. Ad esempio, il codice XML seguente definisce il file di progetto *importato MyCommon.targets*:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 Il codice XML seguente definisce *MyApp.proj*, che importa *MyCommon.targets*:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Quando si compila il progetto, viene visualizzato il messaggio seguente:

 `Name="MyCommon"`

 Poiché il progetto viene importato dopo che la proprietà è stata definita `Name` in *MyApp.proj,* la definizione di `Name` in *MyCommon.targets* esegue l'override della definizione in *MyApp.proj*. Se il progetto venisse importato prima di definire la proprietà Name, durante la compilazione verrebbe visualizzato il messaggio seguente:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Usare l'approccio seguente durante l'importazione dei progetti

1. Nel file di progetto definire tutte le proprietà e gli elementi usati come parametri per le proprietà e gli elementi del progetto importato.

2. Importare il progetto.

3. Nel file di progetto definire tutte le proprietà e gli elementi che devono eseguire l'override delle definizioni predefinite delle proprietà e degli elementi presenti nel progetto importato.

## <a name="example-1"></a>Esempio 1

 Nell'esempio di codice seguente viene illustrato il file *MyCommon.targets* importato dal secondo esempio di codice. Il file *con estensione targets* valuta le proprietà del progetto di importazione per configurare la compilazione.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Esempio 2

 Nell'esempio di codice seguente viene importato il file *MyCommon.targets.*

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
