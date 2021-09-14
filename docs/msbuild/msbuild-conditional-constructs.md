---
title: Costrutti condizionali di MSBuild | Microsoft Docs
description: Informazioni su MSBuild un meccanismo per l'elaborazione condizionale con gli elementi Choose, When e Otherwise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c0b371f4aceef5baadd7a00738d885974b88c584
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628464"
---
# <a name="msbuild-conditional-constructs"></a>Costrutti condizionali di MSBuild

MSBuild fornisce un meccanismo per l'elaborazione con gli elementi [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md)e [Otherwise.](../msbuild/otherwise-element-msbuild.md)

## <a name="use-the-choose-element"></a>Usare l'elemento Choose

 L'elemento `Choose` contiene una serie di elementi `When` con attributi `Condition` che vengono sottoposti a test in ordine dall'alto verso il basso finché un elemento restituisce `true`. Se più di un elemento `When` restituisce `true`, viene usato solo il primo. Un elemento `Otherwise`, se presente, viene valutato se nessuna condizione per un elemento `When` restituisce `true`.

 Gli elementi `Choose` possono essere usati come elementi figlio degli elementi `Project`, `When` e `Otherwise`. Gli elementi `When` e `Otherwise` possono avere elementi figlio `ItemGroup`, `PropertyGroup` o `Choose`.

## <a name="example"></a>Esempio

 L'esempio seguente usa gli elementi `Choose` e `When` per l'elaborazione either/or. Le proprietà e gli elementi per il progetto vengono impostati in base al valore della proprietà `Configuration`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
    </Choose>
    <!-- Rest of Project -->
</Project>
```

In questo esempio viene usata una condizione per una costante `DEFINED_CONSTANT` del compilatore. Questi elementi sono inclusi nella `DefinedConstants` proprietà . L'espressione regolare viene usata per trovare la corrispondenza con la costante esatta in un elenco separato da punti e virgola.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>Vedi anche

- [Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)
- [Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
