---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
description: Informazioni sull'MSBuild elemento ItemGroup, che contiene un set di elementi Item definiti dall'utente. Ogni elemento deve essere figlio di un elemento ItemGroup.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 69fc6afd5a6dc7c5c9d51ae5c57afdbfd2c6847f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077257"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)

Contiene un set di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente. Ogni elemento usato in un MSBuild deve essere specificato come figlio di un `ItemGroup` elemento.

\<Project>
\<ItemGroup>

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

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo. Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|
|`Label`|Attributo facoltativo. Identifica l'oggetto `ItemGroup`. |

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione. Possono esistere zero o più elementi `Item` in un `ItemGroup`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un MSBuild di progetto. |
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

In un semplice file di progetto si usa in genere un singolo `ItemGroup` elemento, ma è anche possibile usare più `ItemGroup` elementi. Quando vengono `ItemGroup` usati più elementi, gli elementi vengono combinati in un singolo `ItemGroup` oggetto . Ad esempio, alcuni elementi potrebbero essere inclusi da un elemento `ItemGroup` separato definito in un file importato.

ItemGroups può avere condizioni applicate usando `Condition` l'attributo . In tal caso, gli elementi vengono aggiunti all'elenco di elementi solo se la condizione viene soddisfatta. Vedere [MSBuild condizioni](msbuild-conditions.md)

`Label`L'attributo viene usato in alcuni sistemi di compilazione per controllare i comportamenti di compilazione. È possibile usarlo solo nelle dichiarazioni, come modo per creare script MSBuild più comprensibili o come impostazione di controllo per influire sulle azioni di compilazione.

## <a name="see-also"></a>Vedi anche

- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementi](../msbuild/msbuild-items.md)
- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
