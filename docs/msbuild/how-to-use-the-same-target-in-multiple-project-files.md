---
title: 'Procedura: Usare la stessa destinazione in più file di progetto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bc8f3c95c687244162cb3bd977ca40031cd8f39
ms.sourcegitcommit: ddd99f64a3f86508892a6d61e8a33c88fb911cc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "82255580"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Procedura: Usare la stessa destinazione in più file di progetto

Se sono stati creati più file di progetto MSBuild, è possibile che sia stato rilevato che è necessario usare le stesse attività e le stesse destinazioni in file di progetto diversi. Anziché includere in ogni file di progetto la descrizione completa di tali attività o destinazioni, è possibile salvare una destinazione in un file di progetto separato e importarlo in qualsiasi altro progetto in cui si intende usare la destinazione.

## <a name="use-the-import-element"></a>Usare l'elemento Import

L'elemento `Import` consente di inserire un file di progetto in un altro file di progetto. Il file di progetto da importare deve essere un file di progetto MSBuild valido e contenere XML ben formato. L'attributo `Project` specifica il percorso del file di progetto importato. Per ulteriori informazioni sull' `Import` elemento, vedere [elemento Import (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Per importare un progetto

1. Nel file di progetto di importazione definire tutte le proprietà e gli elementi usati come parametri per le proprietà e gli elementi del progetto importato.

2. Usare l'elemento `Import` per importare il progetto. Ad esempio:

     `<Import Project="MyCommon.targets"/>`

3. Dopo l'elemento `Import`, definire tutte le proprietà e gli elementi che devono eseguire l'override delle definizioni predefinite delle proprietà e degli elementi presenti nel progetto importato.

## <a name="order-of-evaluation"></a>Ordine di valutazione

 Quando MSBuild raggiunge un `Import` elemento, il progetto importato viene inserito in modo efficace nel progetto di importazione in `Import` corrispondenza della posizione dell'elemento. La posizione dell'elemento `Import` può quindi influire sui valori delle proprietà e degli elementi ed è importante conoscere sia le proprietà e gli elementi impostati dal progetto importato, sia le proprietà e gli elementi usati dal progetto.

 Quando si compila il progetto, vengono valutate prima tutte le proprietà e dopo gli elementi. Il codice XML seguente, ad esempio, definisce il file di progetto importato *comune. targets*:

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

 Nel codice XML seguente viene definito *MyApp. proj*, che importa il *comune. targets*:

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

 Poiché il progetto viene importato dopo `Name` che la proprietà è stata definita in *MyApp. proj*, `Name` la definizione di in *comune. targets* sostituisce la definizione in *MyApp. proj*. Se il progetto venisse importato prima di definire la proprietà Name, durante la compilazione verrebbe visualizzato il messaggio seguente:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Usare l'approccio seguente durante l'importazione dei progetti

1. Nel file di progetto definire tutte le proprietà e gli elementi usati come parametri per le proprietà e gli elementi del progetto importato.

2. Importare il progetto.

3. Nel file di progetto definire tutte le proprietà e gli elementi che devono eseguire l'override delle definizioni predefinite delle proprietà e degli elementi presenti nel progetto importato.

## <a name="example"></a>Esempio

 Nell'esempio di codice seguente viene illustrato il file *comune. targets* importato dal secondo esempio di codice. Il file con *estensione targets* valuta le proprietà del progetto di importazione per configurare la compilazione.

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

## <a name="example"></a>Esempio

 Nell'esempio di codice seguente viene importato il file *comune. targets* .

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
