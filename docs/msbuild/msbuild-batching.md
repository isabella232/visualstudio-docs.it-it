---
title: Batch MSBuild | Microsoft Docs
description: Informazioni su come MSBuild divide gli elenchi di elementi in diverse categorie, o batch, in base ai metadati degli elementi, ed esegue una destinazione o un'attività una volta per ogni batch.
ms.custom: SEO-VS-2020
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d14a979a166f7378c288453530b46b8ec6c98828
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919198"
---
# <a name="msbuild-batching"></a>Batch MSBuild

MSBuild divide gli elenchi di elementi in diverse categorie, o batch, in base ai metadati degli elementi ed esegue una destinazione o un'attività una volta per ogni batch.

## <a name="task-batching"></a>Suddivisione in batch delle attività

Suddividere le attività in batch consente di semplificare i file di progetto, dividendo gli elenchi di elementi in diversi batch che vengono poi passati separatamente in un'attività. Ciò significa che per un file di progetto è necessario dichiarare l'attività e i relativi attributi solo una volta, anche se può essere eseguito più volte.

È necessario specificare che MSBuild esegua l'invio in batch con un'attività usando la `%(ItemMetaDataName)` notazione in uno degli attributi dell'attività. L'esempio seguente suddivide l'elenco di elementi `Example` in batch in base al valore dei metadati degli elementi `Color` e passa ogni batch all'attività `MyTask` separatamente.

> [!NOTE]
> Se non si fa riferimento all'elenco di elementi in un'altra posizione negli attributi dell'attività oppure il nome dei metadati potrebbe essere ambiguo, è possibile usare la notazione%(<ItemCollection. ItemMetaDataName>) per qualificare completamente il valore dei metadati dell'elemento da usare per l'invio in batch.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Per esempi più specifici della suddivisione in batch, vedere [Metadati degli elementi nella suddivisione in batch delle attività](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Suddivisione in batch della destinazione

MSBuild verifica se gli input e gli output di una destinazione sono aggiornati prima di eseguire la destinazione. Se gli input e gli output sono aggiornati, la destinazione viene ignorata. Se un'attività all'interno di una destinazione usa l'invio in batch, MSBuild deve determinare se gli input e gli output per ogni batch di elementi sono aggiornati. In caso contrario, la destinazione viene eseguita ogni volta che viene raggiunta.

Nell'esempio seguente viene illustrato un `Target` elemento che contiene un `Outputs` attributo con la `%(ItemMetadataName)` notazione. MSBuild suddividerà l' `Example` elenco di elementi in batch in base ai `Color` metadati dell'elemento e analizzerà i timestamp dei file di output per ogni batch. Se gli output di un batch non sono aggiornati, la destinazione viene eseguita. In caso contrario, la destinazione viene ignorata.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Per un altro esempio di suddivisione in batch della destinazione, vedere [Metadati degli elementi nell'esecuzione in batch delle destinazioni](../msbuild/item-metadata-in-target-batching.md).

## <a name="item-and-property-mutations"></a>Mutazioni di elementi e proprietà

Questa sezione descrive come comprendere gli effetti della modifica delle proprietà e/o dei metadati degli elementi, quando si usa il batch di destinazione o la suddivisione in batch delle attività.

Poiché il batch di destinazione e l'invio in batch delle attività sono due diverse operazioni di MSBuild, è importante comprendere esattamente quale forma di batch USA MSBuild in ogni caso. Quando la sintassi di invio in batch `%(ItemMetadataName)` viene visualizzata in un'attività in una destinazione, ma non in un attributo della destinazione, MSBuild utilizza la suddivisione in batch delle attività. L'unico modo per specificare la suddivisione in batch di destinazione consiste nell'utilizzare la sintassi batch su un attributo di destinazione, in genere l' `Outputs` attributo.

Con la suddivisione in batch delle attività e l'invio in batch delle attività, è possibile considerare i batch in modo che vengano eseguiti in modo indipendente. Tutti i batch iniziano con una copia dello stesso stato iniziale dei valori dei metadati delle proprietà e degli elementi. Eventuali mutazioni dei valori delle proprietà durante l'esecuzione del batch non sono visibili ad altri batch. Si consideri l'esempio seguente:

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

L'output è il seguente:

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

L'oggetto `ItemGroup` nella destinazione è implicitamente un'attività e con `%(Color)` nell' `Condition` attributo viene eseguita la suddivisione in batch delle attività. Sono disponibili due batch: uno per il rosso e l'altro per il blu. La proprietà `%(NeededColorChange)` viene impostata solo se i `%(Color)` metadati sono blu e l'impostazione influiscono solo sul singolo elemento che corrisponde alla condizione in cui è stato eseguito il batch blu. L' `Message` attributo dell'attività non attiva la suddivisione in `Text` batch, nonostante la `%(ItemMetadataName)` sintassi, perché viene usata all'interno di una trasformazione dell'elemento.

I batch vengono eseguiti in modo indipendente, ma non in parallelo. Ciò fa la differenza quando si accede ai valori dei metadati che cambiano nell'esecuzione batch. Nel caso in cui si imposti una proprietà in base ad alcuni metadati nell'esecuzione batch, la proprietà utilizzerebbe l' *ultimo* valore impostato:

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Dopo l'esecuzione del batch, la proprietà mantiene il valore finale di `%(MetadataValue)` .

Sebbene i batch vengano eseguiti in modo indipendente, è importante prendere in considerazione la differenza tra l'invio in batch di destinazione e l'invio in batch delle attività e determinare quale tipo si applica alla propria situazione. Si consideri l'esempio seguente per comprendere meglio l'importanza di questa distinzione.

Le attività possono essere implicite, anziché esplicite, che possono generare confusione quando si verificano batch di attività con attività implicite. Quando un `PropertyGroup` `ItemGroup` elemento o viene visualizzato in un oggetto `Target` , ogni dichiarazione di proprietà nel gruppo viene trattata in modo implicito come un'attività [CreateProperty](createproperty-task.md) o [CreateItem](createitem-task.md) separata. Questo significa che il comportamento è diverso quando la destinazione è in batch, rispetto a quando la destinazione non è in batch, ovvero quando manca la `%(ItemMetadataName)` sintassi nell' `Outputs` attributo. Quando la destinazione viene eseguita in batch, viene `ItemGroup` eseguita una volta per ogni destinazione, ma quando la destinazione non viene in batch, gli equivalenti impliciti delle `CreateItem` attività o vengono raggruppati in batch utilizzando l'invio in batch delle `CreateProperty` attività, quindi la destinazione viene eseguita solo una volta e ogni elemento o proprietà del gruppo viene in batch separatamente utilizzando la suddivisione in batch delle attività.

Nell'esempio seguente viene illustrato il batch di destinazione e l'invio in batch delle attività nel caso in cui i metadati vengano mutati. Si consideri una situazione in cui sono presenti cartelle A e B con alcuni file:

```
A\1.stub
B\2.stub
B\3.stub
```

A questo punto, esaminare l'output di questi due progetti simili.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

L'output è il seguente:

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

A questo punto `Outputs` , rimuovere l'attributo che ha specificato il batch di destinazione.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

L'output è il seguente:

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

Si noti che l'intestazione `Test1` viene stampata una sola volta, ma nell'esempio precedente è stata stampata due volte. Ciò significa che la destinazione non è in batch.  Di conseguenza, l'output è confusamente diverso.

Il motivo è che quando si usa la suddivisione in batch delle destinazioni, ogni batch di destinazione esegue tutti gli elementi della destinazione con una copia indipendente di tutte le proprietà e gli elementi, ma quando si omette l' `Outputs` attributo le singole righe nel gruppo di proprietà vengono considerate come attività distinte, potenzialmente in batch. In questo caso, l' `ComponentDir` attività viene eseguita in batch (utilizza la `%(ItemMetadataName)` sintassi), in modo che, quando viene `ComponentName` eseguita la riga, entrambi i batch della `ComponentDir` riga siano completati e il secondo che ha determinato il valore come visualizzato nella seconda riga.

## <a name="property-functions-using-metadata"></a>Funzioni delle proprietà che usano i metadati

La suddivisione in batch può essere controllata usando funzioni delle proprietà che includono i metadati. Ad esempio,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

usa <xref:System.IO.Path.Combine%2A> per combinare un percorso di cartella radice con un percorso di elemento Compile.

Le funzioni delle proprietà possono non apparire all'interno dei valori dei metadati. Ad esempio,

`%(Compile.FullPath.Substring(0,3))`

non è consentito.

Per altre informazioni sulle funzioni delle proprietà, vedere [Funzioni delle proprietà](../msbuild/property-functions.md).

## <a name="see-also"></a>Vedi anche

- [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
