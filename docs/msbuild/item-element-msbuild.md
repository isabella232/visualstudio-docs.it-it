---
title: Elemento Item (MSBuild) | Microsoft Docs
description: Informazioni su MSBuild l'elemento Item per contenere un elemento definito dall'utente e i relativi metadati. Ogni elemento deve essere figlio di un elemento ItemGroup.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e0ae068ad1137ff83b77839fe09b2baa6cccbefe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108720"
---
# <a name="item-element-msbuild"></a>Elemento Item (MSBuild)

Contiene un elemento definito dall'utente e i relativi metadati. Ogni elemento usato in un progetto MSBuild deve essere specificato come figlio di un `ItemGroup` elemento.

\<Project>\
&nbsp;\<ItemGroup>\
&nbsp;&nbsp;\<Item>

## <a name="syntax"></a>Sintassi

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Specificare i metadati come attributi

In MSBuild 15.1 o versioni successive, un metadato con un nome che non è in conflitto con l'elenco di attributi corrente può essere espresso come un attributo.

Ad esempio, per specificare un elenco di pacchetti NuGet, si userebbe normalmente una sintassi simile alla seguente:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Ora è tuttavia possibile passare il metadato `Version` come un attributo, come illustrato nella sintassi seguente:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Include`|Attributo facoltativo.<br /><br /> Il file o carattere jolly da includere nell'elenco di elementi.|
|`Exclude`|Attributo facoltativo.<br /><br /> Il file o carattere jolly da escludere dall'elenco di elementi.|
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|
|`Remove`|Attributo facoltativo.<br /><br /> Il file o carattere jolly da eliminare dall'elenco di elementi.<br /><br />|
|`KeepDuplicates`|Attributo facoltativo.<br /><br /> Specifica se un elemento deve essere aggiunto al gruppo di destinazione se è un duplicato esatto di un elemento esistente. Se l'elemento di origine e destinazione hanno lo stesso valore `Include`, ma metadati diversi, l'elemento viene aggiunto anche se `KeepDuplicates` è impostato su `false`. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|
|`KeepMetadata`|Attributo facoltativo.<br /><br /> I metadati per gli elementi di origine da aggiungere agli elementi di destinazione. Solo i metadati i cui nomi vengono specificati nell'elenco delimitato da punto e virgola vengono trasferiti da un elemento di origine a un elemento di destinazione. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|
|`RemoveMetadata`|Attributo facoltativo.<br /><br /> I metadati per gli elementi di origine da non trasferire agli elementi di destinazione. Tutti i metadati vengono trasferiti da un elemento di origine a un elemento di destinazione, ad eccezione dei metadati i cui nomi sono contenuti nell'elenco di nomi separati da punto e virgola. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|
|`Update`|Attributo facoltativo. È disponibile solo per i progetti .NET Core in Visual Studio 2017 o versioni successive.<br /><br /> Consente di modificare i metadati di un elemento. in genere usato per eseguire l'override dei metadati predefiniti di elementi specifici dopo che un gruppo di elementi è stato specificato in modo inziale (ad esempio con un carattere jolly).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che non si trova in un `Target`.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Chiave dei metadati di elemento definita dall'utente che contiene il valore dei metadati dell'elemento. Possono esistere zero o più elementi `ItemMetadata` in un elemento.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento di raggruppamento per elementi.|

## <a name="remarks"></a>Commenti

Gli elementi `Item` definiscono gli input nel sistema di compilazione e vengono raggruppati in raccolte di elementi in base ai relativi nomi definiti dall'utente. Queste raccolte di elementi possono essere usate come parametri per le [attività](../msbuild/msbuild-tasks.md), che a loro volta usano i singoli elementi nelle raccolte per eseguire i passaggi del processo di compilazione. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).

L'uso della notazione @( ) consente di espandere una raccolta di elementi di tipo in un elenco di stringhe delimitato da punti e virgola e di passarlo \<myType> \<myType> a un parametro . Se il parametro è di tipo `string`, il valore del parametro è l'elenco di elementi, separati da punti e virgola. Se il parametro è una matrice di stringhe (`string[]`), ogni elemento viene inserito nella matrice in base alla posizione dei punti e virgola. Se il parametro dell'attività è di tipo <xref:Microsoft.Build.Framework.ITaskItem>`[]`, il valore è il contenuto della raccolta di elementi con eventuali metadati associati. Per delimitare ciascun elemento usando un carattere diverso da un punto e virgola, usare la sintassi @(\<myType>, '\<separator>').

Il MSBuild può valutare caratteri jolly come e e caratteri jolly ricorsivi, `*` `?` ad esempio */ \* \* / \* cs*. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).

## <a name="examples"></a>Esempio

Nell'esempio di codice seguente viene illustrato come dichiarare due elementi di tipo `CSFile`. Il secondo elemento dichiarato contiene i metadati con `MyMetadata` impostato su `HelloWorld`.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

L'esempio di codice seguente illustra come usare l'attributo `Update` per modificare i metadati in un file denominato *somefile.cs*, incluso tramite un criterio GLOB. È disponibile solo per i progetti .NET Core in Visual Studio 2017 o versioni successive.

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Vedi anche

- [Elementi](../msbuild/msbuild-items.md)
- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
- [proprietà di MSBuild](../msbuild/msbuild-properties.md)
- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
