---
title: Batch MSBuild | Microsoft Docs
description: Informazioni su MSBuild gli elenchi di elementi in diverse categorie, o batch, in base ai metadati degli elementi ed esegue una destinazione o un'attività una volta con ogni batch.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b9b018871c95cf87fbac226ed768b51bdc69398d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068959"
---
# <a name="msbuild-batching"></a>Batch MSBuild

MSBuild gli elenchi di elementi in diverse categorie, o batch, in base ai metadati degli elementi ed esegue una destinazione o un'attività una sola volta con ogni batch.

## <a name="task-batching"></a>Suddivisione in batch delle attività

Suddividere le attività in batch consente di semplificare i file di progetto, dividendo gli elenchi di elementi in diversi batch che vengono poi passati separatamente in un'attività. Ciò significa che per un file di progetto è necessario dichiarare l'attività e i relativi attributi solo una volta, anche se può essere eseguito più volte.

Si specifica che si vuole MSBuild eseguire l'invio in batch con un'attività usando la `%(ItemMetaDataName)` notazione in uno degli attributi dell'attività. L'esempio seguente suddivide l'elenco di elementi `Example` in batch in base al valore dei metadati degli elementi `Color` e passa ogni batch all'attività `MyTask` separatamente.

> [!NOTE]
> Se non si fa riferimento all'elenco di elementi altrove negli attributi dell'attività o se il nome dei metadati può essere ambiguo, è possibile usare la notazione %(<ItemCollection.ItemMetaDataName>) per qualificare completamente il valore dei metadati dell'elemento da usare per l'invio in batch.

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

MSBuild verifica se gli input e gli output di una destinazione sono aggiornati prima di eseguire la destinazione. Se sia gli input che gli output sono aggiornati, la destinazione viene ignorata. Se un'attività all'interno di una destinazione usa l'invio in batch, MSBuild deve determinare se gli input e gli output per ogni batch di elementi sono aggiornati. In caso contrario, la destinazione viene eseguita ogni volta che viene raggiunto.

Nell'esempio seguente viene `Target` illustrato un elemento che contiene un attributo con la `Outputs` `%(ItemMetadataName)` notazione . MSBuild suddividerà l'elenco di elementi in batch in base ai metadati dell'elemento e analzzerà i timestamp dei file `Example` di output per ogni `Color` batch. Se gli output di un batch non sono aggiornati, la destinazione viene eseguita. In caso contrario, la destinazione viene ignorata.

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

## <a name="item-and-property-mutations"></a>Elementi e proprietà erre

Questa sezione descrive come comprendere gli effetti della modifica delle proprietà e/o dei metadati degli elementi quando si usa l'invio in batch di destinazione o l'invio in batch di attività.

Poiché l'invio in batch di destinazione e l'invio in batch delle attività sono due operazioni MSBuild, è importante comprendere esattamente quale forma di invio in batch MSBuild in ogni caso. Quando la sintassi di invio in batch viene visualizzata in un'attività in una destinazione, ma non in un attributo nella destinazione, MSBuild l'invio in `%(ItemMetadataName)` batch delle attività. L'unico modo per specificare l'invio in batch di destinazione è usare la sintassi batch per un attributo Target, in genere `Outputs` l'attributo .

Con l'invio in batch di destinazione e l'invio in batch delle attività, i batch possono essere considerati per l'esecuzione in modo indipendente. Tutti i batch iniziano con una copia dello stesso stato iniziale dei valori dei metadati della proprietà e dell'elemento. Eventuali modifiche dei valori delle proprietà durante l'esecuzione batch non sono visibili ad altri batch. Si consideri l'esempio seguente:

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

Nella `ItemGroup` destinazione è implicitamente un'attività e, con nell'attributo , viene eseguita l'invio `%(Color)` in batch `Condition` dell'attività. Sono disponibili due batch: uno per il rosso e l'altro per il blu. La proprietà viene impostata solo se i metadati sono blu e l'impostazione influisce solo sul singolo elemento che corrisponde alla condizione quando è stato `%(NeededColorChange)` `%(Color)` eseguito il batch blu. `Message`L'attributo `Text` dell'attività non attiva l'invio in batch, nonostante la sintassi, perché `%(ItemMetadataName)` viene usato all'interno di una trasformazione di elemento.

I batch vengono eseguiti in modo indipendente, ma non in parallelo. Questo fa la differenza quando si accede ai valori dei metadati che cambiano nell'esecuzione in batch. Nel caso in cui si imposta una proprietà in base ad alcuni metadati nell'esecuzione in batch, la proprietà accetta *l'ultimo* valore impostato:

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Dopo l'esecuzione batch, la proprietà mantiene il valore finale di `%(MetadataValue)` .

Anche se i batch vengono eseguiti in modo indipendente, è importante considerare la differenza tra l'invio in batch di destinazione e l'invio in batch delle attività e sapere quale tipo si applica alla situazione specifica. Si consideri l'esempio seguente per comprendere meglio l'importanza di questa distinzione.

Le attività possono essere implicite, anziché esplicite, che possono generare confusione quando si verifica l'invio in batch delle attività con attività implicite. Quando un elemento o viene visualizzato in un oggetto , ogni dichiarazione di proprietà nel gruppo viene trattata in modo implicito come `PropertyGroup` `ItemGroup` `Target` un'attività [CreateProperty](createproperty-task.md) o [CreateItem](createitem-task.md) separata. Ciò significa che il comportamento è diverso quando la destinazione è in batch, rispetto a quando la destinazione non è in batch ,ovvero quando non ha la sintassi `%(ItemMetadataName)` `Outputs` nell'attributo . Quando la destinazione è in batch, viene eseguita una volta per ogni destinazione, ma quando la destinazione non è in batch, gli equivalenti impliciti delle attività o vengono raggruppati in batch usando l'invio in batch delle attività, quindi la destinazione viene eseguita una sola volta e ogni elemento o proprietà del gruppo viene raggruppato separatamente usando l'invio in `ItemGroup` `CreateItem` batch delle `CreateProperty` attività.

L'esempio seguente illustra l'invio in batch di destinazione e l'invio in batch delle attività nel caso in cui i metadati vengono mutati. Si consideri una situazione in cui sono presenti cartelle A e B con alcuni file:

```
A\1.stub
B\2.stub
B\3.stub
```

Esaminare ora l'output di questi due progetti simili.

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

Rimuovere ora `Outputs` l'attributo che ha specificato l'invio in batch di destinazione.

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

Si noti che `Test1` l'intestazione viene stampata una sola volta, ma nell'esempio precedente è stata stampata due volte. Ciò significa che la destinazione non è in batch.  Di conseguenza, l'output è leggermente diverso.

Il motivo è che quando si usa l'invio in batch di destinazione, ogni batch di destinazione esegue tutti gli elementi nella destinazione con la propria copia indipendente di tutte le proprietà e gli elementi, ma quando si omette l'attributo, le singole righe nel gruppo di proprietà vengono considerate come attività distinte e potenzialmente `Outputs` in batch. In questo caso, l'attività viene eseguita in batch (usa la sintassi ), in modo che al momento dell'esecuzione della riga, entrambi i batch della riga sono stati completati e il secondo che ha eseguito ha determinato il valore come illustrato nella `ComponentDir` `%(ItemMetadataName)` seconda `ComponentName` `ComponentDir` riga.

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
