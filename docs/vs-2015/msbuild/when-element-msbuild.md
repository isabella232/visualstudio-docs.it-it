---
title: Elemento When (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d74dc4b8b1373e28430a5a0cc8beb7fa725e359
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520268"
---
# <a name="when-element-msbuild"></a>Elemento When (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento When (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/when-element-msbuild).  
  
  
Specifica un blocco di codice selezionabile dall'elemento `Choose`.  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>Sintassi  
  
```  
<When Condition="'StringA'=='StringB'">  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</When>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|Condizione|Attributo obbligatorio.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento facoltativo.<br /><br /> Valuta gli elementi figlio per selezionare una sezione del codice da eseguire. Possono esistere zero o più elementi `Choose` in un elemento `When`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Contiene un set di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente. Possono esistere zero o più elementi `ItemGroup` in un elemento `When`.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Contiene un set di elementi [Property](../msbuild/property-element-msbuild.md) definiti dall'utente. Possono esistere zero o più elementi `PropertyGroup` in un elemento `When`.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Valuta gli elementi figlio per selezionare una sezione del codice da eseguire.|  
  
## <a name="remarks"></a>Note  
 Se l'`Condition` attributo restituisce true, gli elementi figlio `ItemGroup` e `PropertyGroup` dell'elemento `When` vengono eseguiti e tutti gli elementi `When` successivi vengono ignorati.  
  
 Gli elementi `Choose`, `When` e `Otherwise` vengono usati insieme per consentire di selezionare una sezione di codice da eseguire tra diverse alternative. Per altre informazioni, vedere [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md) (Costrutti condizionali).  
  
## <a name="example"></a>Esempio  
 Nel progetto riportato di seguito l'elemento `Choose` viene usato per selezionare il set di valori delle proprietà da impostare negli elementi `When`. Se gli attributi `Condition` di entrambi gli elementi `When` restituiscono `false`, vengono impostati i valori delle proprietà dell'elemento `Otherwise`.  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)   
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)



