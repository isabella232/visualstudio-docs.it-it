---
title: Costrutti condizionali di MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7997db7fc5c7dd866de8f9d573779ead29e5e9d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518393"
---
# <a name="msbuild-conditional-constructs"></a>Costrutti condizionali di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [costrutti condizionali di MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-conditional-constructs).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] offre un meccanismo per l'elaborazione di tipo either/or con gli elementi [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) e [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## <a name="using-the-choose-element"></a>Uso dell'elemento Choose  
 L'elemento `Choose` contiene una serie di elementi `When` con attributi `Condition` che vengono sottoposti a test in ordine dall'alto verso il basso finché un elemento restituisce `true`. Se più di un elemento `When` restituisce `true`, viene usato solo il primo. Un elemento `Otherwise`, se presente, viene valutato se nessuna condizione per un elemento `When` restituisce `true`.  
  
 Gli elementi `Choose` possono essere usati come elementi figlio degli elementi `Project`, `When` e `Otherwise`. Gli elementi `When` e `Otherwise` possono avere elementi figlio `ItemGroup`, `PropertyGroup` o `Choose`.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa gli elementi `Choose` e `When` per l'elaborazione either/or. Le proprietà e gli elementi per il progetto vengono impostati in base al valore della proprietà `Configuration`.  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)



