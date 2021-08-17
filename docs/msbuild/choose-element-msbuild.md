---
title: Elemento Choose (MSBuild) | Microsoft Docs
description: Usare l MSBuild Choose per valutare gli elementi figlio e selezionare un set di elementi ItemGroup o PropertyGroup da valutare.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 8248ad385d3c1af5dde264a9c04c58acbf4f32b7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077725"
---
# <a name="choose-element-msbuild"></a>Elemento Choose (MSBuild)

Valuta gli elementi figlio per selezionare un set di elementi `ItemGroup` e/o di elementi `PropertyGroup` da valutare.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Sintassi

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Altrimenti](../msbuild/otherwise-element-msbuild.md)|Elemento facoltativo.<br /><br /> Specifica gli elementi `PropertyGroup` e `ItemGroup` del blocco di codice da valutare se le condizioni di tutti gli elementi `When` restituiscono `false`. In un elemento `Otherwise` può essere presente al massimo un elemento `Choose` ed è necessario che sia l'ultimo.|
|[Quando](../msbuild/when-element-msbuild.md)|Elemento obbligatorio.<br /><br /> Specifica un blocco di codice selezionabile dall'elemento `Choose`. In un elemento `When` possono essere presenti uno o più elementi `Choose`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Altrimenti](../msbuild/otherwise-element-msbuild.md) | Specifica il blocco di codice da eseguire se le condizioni di tutti gli elementi `When` restituiscono `false`. |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file MSBuild progetto. |
| [Quando](../msbuild/when-element-msbuild.md) | Specifica un blocco di codice selezionabile dall'elemento `Choose`. |

## <a name="remarks"></a>Commenti

 Gli elementi `Choose`, `When` e `Otherwise` vengono usati insieme per consentire di selezionare una sezione di codice da eseguire tra diverse alternative. Per altre informazioni, vedere [Costrutti condizionali di MSBuild](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Esempio

 Nel progetto riportato di seguito l'elemento `Choose` viene usato per selezionare il set di valori delle proprietà da impostare negli elementi `When`. Se gli attributi `Condition` di entrambi gli elementi `When` restituiscono `false`, vengono impostati i valori delle proprietà dell'elemento `Otherwise`.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
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
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
    </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)
- [Project sullo schema del file](../msbuild/msbuild-project-file-schema-reference.md)
