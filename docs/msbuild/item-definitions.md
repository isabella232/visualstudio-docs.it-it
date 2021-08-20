---
title: Definizioni degli elementi | Microsoft Docs
description: Informazioni su MSBuild usa ItemGroup e ItemDefinitionGroup per dichiarare i metadati per gli elementi nei file di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f56772bec8d0e4e62a58976b5c084f99c1e6f6e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136898"
---
# <a name="item-definitions"></a>Definizioni degli elementi

MSBuild 2.0 abilita la dichiarazione statica degli elementi nei file di progetto usando [l'elemento ItemGroup.](../msbuild/itemgroup-element-msbuild.md) I metadati possono essere tuttavia aggiunti solo al livello dell'elemento, anche se sono identici per tutti gli elementi. A partire da MSBuild 3.5, un elemento di progetto denominato [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) supera questa limitazione. *ItemDefinitionGroup* consente di definire un set di definizioni degli elementi che aggiungono i valori dei metadati predefiniti a tutti gli elementi del tipo di elemento denominato.

L'elemento *ItemDefinitionGroup* viene visualizzato immediatamente dopo l'elemento [Project](../msbuild/project-element-msbuild.md) nel file di progetto. Le definizioni degli elementi offrono le funzionalità seguenti:

- È possibile definire metadati predefiniti globali per gli elementi all'esterno di una destinazione. In altri termini, gli stessi metadati si applicano a tutti gli elementi del tipo specificato.

- I tipi di elemento possono presentare più definizioni. Quando al tipo vengono aggiunte altre specifiche di metadati, l'ultima ha la precedenza. \(I metadati seguono lo stesso ordine di importazione delle proprietà.\)

- I metadati possono essere additivi. Ad esempio, i valori CDefines vengono accumulati in modo condizionale, a seconda delle proprietà impostate. Ad esempio, `MT;STD_CALL;DEBUG;UNICODE`.

- I metadati possono essere rimossi.

- È possibile usare condizioni per controllare l'inclusione di metadati.

## <a name="item-metadata-default-values"></a>Valori predefiniti dei metadati degli elementi

I metadati degli elementi definiti in un ItemDefinitionGroup sono solo una dichiarazione di metadati predefiniti. I metadati non vengono applicati a meno che non sia definito un elemento che usa un ItemGroup per contenere i valori dei metadati.

> [!NOTE]
> In molti degli esempi riportati in questo argomento viene illustrato un elemento ItemDefinitionGroup, ma la definizione di ItemGroup corrispondente viene omessa per chiarezza.

I metadati definiti in modo esplicito in un ItemGroup hanno la precedenza su quelli presenti in ItemDefinitionGroup. I metadati presenti in ItemDefinitionGroup vengono applicati solo per i metadati non definiti in un ItemGroup. Esempio:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemGroup>
    <i Include="a">
        <o>o1</o>
        <n>n2</n>
    </i>
</ItemGroup>
```

In questo esempio il metadato predefinito "m" viene applicato all'elemento "i" perché non è definito in modo esplicito dall'elemento "i". Al contrario, il metadato predefinito "n" non viene applicato all'elemento "i" perché è già definito dall'elemento "i".

> [!NOTE]
> I nomi di parametri ed elementi XML prevedono la distinzione tra maiuscole e \-minuscole. I metadati degli elementi e i \/nomi di proprietà o elementi non prevedono tale \-distinzione. Di conseguenza, gli elementi ItemDefinitionGroup i cui nomi differiscono solo per l'uso di maiuscole o minuscole devono essere considerati come lo stesso ItemGroup.

## <a name="value-sources"></a>Origini dei valori

I valori per i metadati definiti in un ItemDefinitionGroup possono provenire da molte origini diverse, come indicato di seguito:

- Proprietà PropertyGroup

- Elemento da un ItemDefinitionGroup

- Trasformazione dell'elemento in un elemento ItemDefinitionGroup

- Variabile di ambiente

- Proprietà globale (dalla riga *MSBuild.exe* comando)

- Proprietà riservata

- Metadati noti in un elemento di un ItemDefinitionGroup

- Sezione CDATA \<\!\[CDATA\[anything here is not parsed\]\]\>

> [!NOTE]
> I metadati degli elementi di un ItemGroup non sono utili in una dichiarazione di metadati di un ItemDefinitionGroup perché gli elementi dell'ItemDefinitionGroup vengono elaborati prima di quelli dell'ItemGroup.

## <a name="additive-and-multiple-definitions"></a>Definizioni additive e multiple

Quando si aggiungono definizioni o si usano più ItemDefinitionGroup, tenere presente quanto segue:

- Eventuali altre specifiche dei metadati vengono aggiunte al tipo.

- L'ultima specifica ha la precedenza.

In presenza di più ItemDefinitionGroup, ogni specifica successiva aggiunge i metadati alla definizione precedente. Esempio:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <o>o1</o>
    </i>
</ItemDefinitionGroup>
```

In questo esempio il metadato "o" viene aggiunto a "m" e "n".

È anche possibile aggiungere i valori dei metadati definiti in precedenza. Esempio:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

In questo esempio il valore definito in precedenza per il metadato "m" \(m1\) viene aggiunto al nuovo valore \(m2\), in modo che il valore finale sia "m1;m2".

> [!NOTE]
> Questo può verificarsi anche nello stesso ItemDefinitionGroup.

Quando si esegue l'override dei metadati definiti in precedenza, l'ultima specifica ha la precedenza. Nell'esempio seguente il valore finale del metadato "m" è compreso tra "m1" e "m1a".

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>m1a</m>
    </i>
</ItemDefinitionGroup>
```

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Usare condizioni in un ItemDefinitionGroup

È possibile usare condizioni in un ItemDefinitionGroup per controllare l'inclusione dei metadati. Esempio:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

In questo caso, il metadato predefinito "m1" dell'elemento "i" viene incluso solo se il valore della proprietà "Configuration" è "Debug".

> [!NOTE]
> Nelle condizioni sono supportati solo i riferimenti ai metadati locali.

I riferimenti ai metadati definiti in un ItemDefinitionGroup precedente sono locali per l'elemento, non per il gruppo di definizione. In altre parole, l'ambito dei riferimenti è specifico dell'elemento. Esempio:

```xml
<ItemDefinitionGroup>
    <test>
        <yes>1</yes>
    </test>
    <i>
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>
    </i>
</ItemDefinitionGroup>

```

Nell'esempio precedente l'elemento "i" fa riferimento all'elemento "test" nella condizione. Il valore di questa condizione non sarà mai true perché MSBuild interpreta un riferimento al metadato di un altro elemento in un ItemDefinitionGroup come stringa vuota. Di conseguenza, "m" verrebbe impostato su "m0".

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Nell'esempio precedente "m" verrebbe impostato sul valore "m1" perché la condizione fa riferimento al valore del metadato dell'elemento "i" per l'elemento "yes".

## <a name="override-and-delete-metadata"></a>Eseguire l'override dei metadati ed eliminarli

I metadati definiti in un elemento ItemDefinitionGroup possono essere sottoposti a override in un elemento ItemDefinitionGroup successivo impostando il valore dei metadati su un altro valore. È anche possibile eliminare un elemento dei metadati impostandolo su un valore vuoto. Esempio:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m></m>
    </i>
</ItemDefinitionGroup>
```

L'elemento "i" contiene ancora il metadato "m", ma ora il valore è vuoto.

## <a name="scope-of-metadata"></a>Ambito dei metadati

Gli ItemDefinitionGroup hanno un ambito globale su proprietà definite e globali, ovunque siano definite. Le definizioni dei metadati predefiniti in un ItemDefinitionGroup possono essere autoreferenziali. Ad esempio, di seguito viene usato un riferimento ai metadati semplice:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

È possibile usare anche un riferimento ai metadati qualificato:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Quanto segue, tuttavia, non è valido:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

A partire MSBuild 3.5, ItemGroups può anche essere autoreferenziale. Ad esempio:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Vedere anche

- [Batch](../msbuild/msbuild-batching.md)
