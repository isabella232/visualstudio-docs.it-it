---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8064ce4c13419238ca5877893a731d2ac53afb25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633642"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)

Contiene un set di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente. Ogni elemento utilizzato in un progetto MSBuild deve `ItemGroup` essere specificato come figlio di un elemento.

\<Project> \<ItemGroup>

## <a name="syntax"></a>Sintassi

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo. Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|
|`Label`|Attributo facoltativo. Identifica l'oggetto `ItemGroup`.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione. Possono esistere zero o più elementi `Item` in un `ItemGroup`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |
| [Destinazione](../msbuild/target-element-msbuild.md) | A partire da .NET Framework 3.5, l'elemento `ItemGroup` può essere visualizzato in un elemento `Target`. Per altre informazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Esempio

L'esempio di codice seguente illustra le raccolte di elementi definite dall'utente `Res` e `CodeFiles` in un elemento `ItemGroup`. Ogni elemento nella raccolta di elementi `Res` contiene un elemento [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) figlio definito dall'utente.

```xml
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

- [Informazioni di riferimento sullo schema del file di progettoProject file schema reference](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementi](../msbuild/msbuild-items.md)
- [Elementi di progetto MSBuild comuniCommon MSBuild project items](../msbuild/common-msbuild-project-items.md)
