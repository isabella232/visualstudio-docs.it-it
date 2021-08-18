---
title: Elementi MSBuild | Microsoft Docs
description: Informazioni su come usare l MSBuild'attributo Include di ItemGroup per specificare i file da includere in una compilazione.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 520349f829a696e2b34aef262efd01e937ad1998
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077231"
---
# <a name="msbuild-items"></a>Elementi MSBuild

Gli elementi MSBuild, forniti come input al sistema di compilazione, in genere rappresentano file. I file sono specificati nell'attributo `Include`. Gli elementi sono raggruppati in tipi di elemento in base ai nomi degli elementi. I tipi di elementi sono elenchi denominati di elementi che possono essere usati come parametri per le attività. Le attività usano i valori degli elementi per eseguire i passaggi del processo di compilazione.

 Poiché gli elementi vengono denominati in base al tipo di elemento a cui appartengono, i termini "elemento" e "valore dell'elemento" sono interscambiabili.

## <a name="create-items-in-a-project-file"></a>Creare elementi in un file di progetto

 Si dichiarano gli elementi nel file di progetto come elementi figlio di un elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Il nome dell'elemento figlio è il tipo dell'elemento. L'attributo `Include` dell'elemento specifica gli elementi (i file) da includere con tale tipo di elemento. Ad esempio, il codice XML seguente crea un tipo di elemento denominato `Compile` che include due file.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 *L'elemento file2.cs* non sostituisce l'elemento *file1.cs*; il nome del file viene invece aggiunto all'elenco di valori per il tipo `Compile` di elemento.

 Il codice XML seguente crea lo stesso tipo di elemento dichiarando entrambi i file in un solo attributo `Include`. Si noti che i nomi file sono separati da punto e virgola.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

L'attributo è un percorso interpretato in relazione alla cartella del file di `Include` progetto, $(MSBuildProjectPath), anche se l'elemento si trova in un file importato, ad esempio un file con estensione *targets.*

## <a name="create-items-during-execution"></a>Creare elementi durante l'esecuzione

 Agli elementi non compresi in elementi [Target](../msbuild/target-element-msbuild.md) vengono assegnati valori durante la fase di valutazione di una compilazione. Durante la fase di esecuzione successiva, gli elementi possono essere creati o modificati nei modi seguenti:

- Le attività possono creare un elemento. Per creare un elemento, l'elemento [Task](../msbuild/task-element-msbuild.md) deve avere un elemento [Output](../msbuild/output-element-msbuild.md) figlio con un attributo `ItemName`.

- L'attività [CreateItem](../msbuild/createitem-task.md) può creare un elemento. Questo utilizzo è deprecato.

- A partire da .NET Framework 3.5, gli elementi `Target` possono contenere elementi [ItemGroup](../msbuild/itemgroup-element-msbuild.md) che possono contenere elementi Item.

## <a name="reference-items-in-a-project-file"></a>Fare riferimento a elementi in un file di progetto

 Per fare riferimento ai tipi di elemento nel file di progetto viene usata la sintassi @(\<ItemType>). Ad esempio, per fare riferimento al tipo di elemento nell'esempio precedente, si userà `@(Compile)`. Usando questa sintassi, è possibile passare gli elementi alle attività specificando il tipo di elemento come parametro di tale attività. Per altre informazioni, vedere [Procedura: Selezionare i file da compilare.](../msbuild/how-to-select-the-files-to-build.md)

 Per impostazione predefinita, gli elementi di un tipo di elemento vengono separati da punto e virgola (;) quando viene espanso. È possibile usare la sintassi @( , ' ') per \<ItemType> specificare un \<separator> separatore diverso da quello predefinito. Per altre informazioni, [vedere Procedura: Visualizzare un elenco di elementi separati da virgole.](../msbuild/how-to-display-an-item-list-separated-with-commas.md)

## <a name="use-wildcards-to-specify-items"></a>Usare caratteri jolly per specificare gli elementi

È possibile usare i caratteri jolly `**`, `*` e `?` per specificare un gruppo di file come input per una compilazione anziché elencare ogni file separatamente.

- Il carattere jolly `?` corrisponde a un singolo carattere.
- Il carattere jolly `*` corrisponde a zero o più caratteri.
- La sequenza di caratteri jolly `**` corrisponde a un percorso parziale.

Ad esempio, è possibile specificare tutti i file `.cs` nella directory che contiene il file di progetto usando l'elemento seguente nel file di progetto.

```xml
<CSFile Include="*.cs"/>
```

L'elemento seguente seleziona tutti i file `.vb` nell'unità `D:`:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Se si desidera includere caratteri letterali `*` o `?` in un elemento privo di espansione di caratteri jolly, è necessario [aggiungere un carattere di escape ai caratteri jolly](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Per altre informazioni sui caratteri jolly, vedere [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Usare l'attributo Exclude

 Gli elementi Item possono contenere l'attributo `Exclude`, che esclude elementi (file) specifici dal tipo di elemento. L'attributo `Exclude` viene in genere usato con i caratteri jolly. Il codice XML seguente, ad esempio, aggiunge ogni file con estensione *cs* nella directory al tipo di elemento CSFile, ad eccezione del file *DoNotBuild.cs*.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 L'attributo `Exclude` interessa solo gli elementi che vengono aggiunti dall'attributo `Include` nell'elemento item che li contiene entrambi. L'esempio seguente non esclude il file *Form1.cs*, che è stato aggiunto nell'elemento item precedente.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Per altre informazioni, [vedere Procedura: Escludere file dalla compilazione.](../msbuild/how-to-exclude-files-from-the-build.md)

## <a name="item-metadata"></a>Metadati degli elementi

 Gli elementi possono contenere metadati oltre alle informazioni negli attributi `Include` e `Exclude`. Questi metadati possono essere usati dalle attività che richiedono altre informazioni sugli elementi o per dividere in batch le attività e le destinazioni. Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).

 I metadati sono una raccolta di coppie chiave-valore che vengono dichiarate nel file di progetto come elementi figlio di un elemento item. Il nome dell'elemento figlio è il nome dei metadati e il valore dell'elemento figlio è il valore dei metadati.

 I metadati sono associati all'elemento item che li contiene. Ad esempio, il codice XML seguente aggiunge metadati con il valore sia agli elementi `Culture` `Fr` *one.cs* che *two.cs* del tipo di elemento CSFile.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Un elemento può avere zero o più valori di metadati. È possibile modificare i valori dei metadati in qualsiasi momento. Se si impostano i metadati su un valore vuoto, di fatto li si rimuove dalla compilazione.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Fare riferimento ai metadati degli elementi in un file di progetto

 È possibile fare riferimento ai metadati di un elemento nel file di progetto usando la sintassi %(\<ItemMetadataName>). In caso di ambiguità, è possibile qualificare un riferimento usando il nome del tipo di elemento. Ad esempio, è possibile specificare %( \<ItemType.ItemMetaDataName> ). Nell'esempio seguente vengono utilizzati i metadati display per inviare in batch l'attività Message. Per altre informazioni su come usare i metadati di un elemento per la suddivisione in batch, vedere [Metadati degli elementi nella suddivisione in batch delle attività](../msbuild/item-metadata-in-task-batching.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Metadati noti degli elementi

 Quando un elemento viene aggiunto a un tipo di elemento, a tale elemento vengono assegnati alcuni metadati noti. Ad esempio, tutti gli elementi hanno i metadati noti %( ), il cui valore è il \<Filename> nome file dell'elemento (senza l'estensione ). Per altre informazioni, vedere [Metadati noti degli elementi.](../msbuild/msbuild-well-known-item-metadata.md)

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Trasformare i tipi di elemento tramite i metadati

 È possibile trasformare gli elenchi di elementi in nuovi elenchi di elementi usando i metadati. Ad esempio, è possibile trasformare un tipo di elemento con elementi che rappresentano file con estensione cpp in un elenco corrispondente di file `CppFiles` *obj*  usando l'espressione `@(CppFiles -> '%(Filename).obj')` .

 Il codice seguente crea un tipo di elemento `CultureResource` che contiene copie di tutti gli elementi `EmbeddedResource` con i metadati `Culture`. Il valore dei metadati `Culture` diventa il valore dei nuovi metadati `CultureResource.TargetDirectory`.

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 Per altre informazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Definizioni degli elementi

 A partire da .NET Framework 3.5, è possibile aggiungere metadati predefiniti a qualsiasi tipo di elemento usando l'[elemento ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Come i metadati noti, i metadati predefiniti sono associati a tutti gli elementi del tipo di elemento specificato. È possibile eseguire l'override esplicito dei metadati predefiniti nella definizione di un elemento. Ad esempio, il codice XML seguente fornisce `Compile` agli elementi *one.cs* e *three.cs* i metadati `BuildDay` con il valore "Monday". Il codice fornisce all'elemento *two.cs i* metadati `BuildDay` con il valore "Tuesday".

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 Per altre informazioni, vedere [Definizioni degli elementi.](../msbuild/item-definitions.md)

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Attributi per gli elementi in un ItemGroup di una destinazione

 A partire da .NET Framework 3.5, gli elementi `Target` possono contenere elementi [ItemGroup](../msbuild/itemgroup-element-msbuild.md) che possono contenere elementi Item. Gli attributi in questa sezione sono validi quando vengono specificati per un elemento in un `ItemGroup` che si trova in una `Target`.

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Rimuovere l'attributo

 L'attributo `Remove` rimuove elementi (file) specifici dal tipo di elemento. Questo attributo è stato introdotto nella versione .NET Framework 3.5 (solo all'interno delle destinazioni). Sia all'interno che all'esterno delle destinazioni sono supportate a partire MSBuild 15.0.

 Nell'esempio seguente vengono rimossi *.config* file dal tipo di elemento Compile.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> Attributo KeepMetadata

 Un elemento item, se viene generato in una destinazione, può contenere l'attributo `KeepMetadata`. Se questo attributo è specificato, solo i metadati specificati nell'elenco di nomi delimitati da punto e virgola verranno trasferiti dall'elemento di origine a quello di destinazione. Un valore vuoto per questo attributo equivale a non specificarlo. L'attributo `KeepMetadata` è stato introdotto in .NET Framework 4.5.

 L'esempio seguente mostra come usare l'attributo `KeepMetadata`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> Attributo RemoveMetadata

 Un elemento item, se viene generato in una destinazione, può contenere l'attributo `RemoveMetadata`. Se questo attributo è specificato, tutti i metadati vengono trasferiti dall'elemento di origine all'elemento di destinazione, a eccezione dei metadati i cui nomi sono contenuti nell'elenco di nomi separati da punto e virgola. Un valore vuoto per questo attributo equivale a non specificarlo. L'attributo `RemoveMetadata` è stato introdotto in .NET Framework 4.5.

 L'esempio seguente mostra come usare l'attributo `RemoveMetadata`.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Attributo KeepDuplicates

 Un elemento item, se viene generato in una destinazione, può contenere l'attributo `KeepDuplicates`. `KeepDuplicates` è un attributo `Boolean` che specifica se un elemento deve essere aggiunto al gruppo di destinazione se l'elemento è un duplicato esatto di un elemento esistente.

 Se l'elemento di origine e destinazione hanno lo stesso valore Include, ma metadati diversi, l'elemento viene aggiunto anche se `KeepDuplicates` è impostato su `false`. Un valore vuoto per questo attributo equivale a non specificarlo. L'attributo `KeepDuplicates` è stato introdotto in .NET Framework 4.5.

 L'esempio seguente mostra come usare l'attributo `KeepDuplicates`.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>Aggiornamento dei metadati sugli elementi in un ItemGroup all'esterno di una destinazione

I metadati esistenti degli elementi esterni alle destinazioni possono essere aggiornati tramite `Update` l'attributo . Questo attributo non **è disponibile** per gli elementi nelle destinazioni.

```xml
<Project>
    <PropertyGroup>
        <MetadataToUpdate>pencil</MetadataToUpdate>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Color>red</Color>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="notebook">
            <Size>SMALL</Size>
            <Color>YELLOW</Color>
        </Item2>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="$(MetadataToUpdate);stapler;er*r;@(Item2)" Price="10" Material="">
            <Color>RED</Color>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: RED
    Material:
    Price: 10
Item1: pencil
    Size: small
    Color: RED
    Material:
    Price: 10
Item1: eraser
    Size:
    Color: RED
    Material:
    Price: 10
Item1: notebook
    Size: large
    Color: RED
    Material:
    Price: 10
-->
```

:::moniker range=">=vs-2019"
In MSBuild versione 16.6 e successive, l'attributo supporta riferimenti a metadati qualificati per facilitare l'importazione di metadati `Update` da due o più elementi.

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item3 Include="notebook">
            <Size>SMALL</Size>
            <Color>BLUE</Color>
            <Price>20</Price>
        </Item3>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="@(Item2);er*r;@(Item3)" Size="%(Size)" Color="%(Item2.Color)" Price="%(Item3.Price)" Model="2020">
            <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: black
    Material: plastic
    Price:
    Model:
Item1: pencil
    Size: small
    Color: RED
    Material: Premium PLASTIC
    Price:
    Model: 2020
Item1: eraser
    Size: small
    Color:
    Material: gum
    Price:
    Model: 2020
Item1: notebook
    Size: large
    Color:
    Material: paper
    Price: 20
    Model: 2020
-->
```

Osservazioni:
- Metadati non qualificati (%(M)) associati al tipo di elemento da aggiornare ( `Item1` nell'esempio precedente). I metadati qualificati ( `%(Item2.Color)` ) vengono associati all'interno del set di tipi di elemento corrispondenti acquisiti dall'espressione Update.
- Se un elemento corrisponde più volte all'interno e tra più elementi a cui si fa riferimento:
  - L'ultima occorrenza di ogni tipo di elemento a cui si fa riferimento viene acquisita (quindi un elemento acquisito per ogni tipo di elemento).
  - Corrisponde al comportamento dell'invio in batch degli elementi attività nelle destinazioni.
- Dove è possibile inserire riferimenti %():
  - Metadati
  - Condizioni dei metadati
- La corrispondenza dei nomi dei metadati non fa distinzione tra maiuscole e minuscole.
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>Aggiornamento dei metadati sugli elementi in un ItemGroup di una destinazione

I metadati possono essere modificati anche all'interno delle destinazioni, con una sintassi meno espressiva rispetto a `Update` :

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item2 Include="ruler">
            <Color>GREEN</Color>
        </Item2>

    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <!-- Metadata can be expressed either as attributes or as elements -->
            <Item1 Size="GIGANTIC" Color="%(Item2.Color)">
                <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
            </Item1>
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: pencil
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: eraser
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: notebook
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
-->
```

## <a name="see-also"></a>Vedi anche

- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md)
- [Procedura: Escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md)
- [Procedura: Visualizzare un elenco di elementi separati da virgole](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Definizioni degli elementi](../msbuild/item-definitions.md)
- [Batch](../msbuild/msbuild-batching.md)
