---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20c22e0ea2ef05c108ebe564b186ede2a02f9dfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162419"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene un set di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente. Ogni elemento usato in un progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] deve essere specificato come figlio di un elemento `ItemGroup`.  
  
 \<Project>  
 \<ItemGroup>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo. Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione. Possono esistere zero o più elementi `Item` in un `ItemGroup`.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|[Destinazione](../msbuild/target-element-msbuild.md)|A partire da .NET Framework 3.5, l'elemento `ItemGroup` può essere visualizzato in un elemento `Target`. Per altre informazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra le raccolte di elementi definite dall'utente `Res` e `CodeFiles` in un elemento `ItemGroup`. Ogni elemento nella raccolta di elementi `Res` contiene un elemento [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) figlio definito dall'utente.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementi](../msbuild/msbuild-items.md)   
 [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
