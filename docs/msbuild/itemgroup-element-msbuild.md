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
ms.openlocfilehash: a62b4df06d1c180a6a6d62b0231dce1136fb8059
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288975"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)

Contiene un set di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente. Ogni elemento usato in un progetto MSBuild deve essere specificato come figlio di un `ItemGroup` elemento.

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

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo. Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|
|`Label`|Attributo facoltativo. Identifica l'oggetto `ItemGroup`. |

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione. Possono esistere zero o più elementi `Item` in un `ItemGroup`.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |
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

In un file di progetto semplice, in genere si usa un singolo `ItemGroup` elemento, ma è anche possibile usare più `ItemGroup` elementi. Quando `ItemGroup` vengono usati più elementi, gli elementi vengono combinati in un unico oggetto `ItemGroup` . Alcuni elementi, ad esempio, possono essere inclusi in un `ItemGroup` elemento separato definito in un file importato.

Per ItemGroup è possibile applicare condizioni usando l' `Condition` attributo. In tal caso, gli elementi vengono aggiunti all'elenco di elementi solo se la condizione è soddisfatta. Vedere [le condizioni di MSBuild](msbuild-conditions.md)

L' `Label` attributo viene usato in alcuni sistemi di compilazione come metodo per controllare i comportamenti di compilazione. È possibile usarlo solo nelle dichiarazioni, in modo da creare script MSBuild più comprensibili o come impostazioni di controllo per influire sulle azioni di compilazione.

## <a name="see-also"></a>Vedere anche

- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementi](../msbuild/msbuild-items.md)
- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
