---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
description: Informazioni sull'MSBuild itemMetadata, che contiene una chiave di metadati dell'elemento definita dall'utente con il valore dei metadati.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: aca05e3711d23e8346770fb45523f98c0c72da38
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143183"
---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)

Contiene una chiave dei metadati di elemento definita dall'utente che contiene il valore dei metadati dell'elemento. Un elemento può avere un numero qualsiasi di coppie chiave-valore dei metadati.

 \<Project> \<ItemGroup>
 \<Item>

## <a name="syntax"></a>Sintassi

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementi figlio

 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Elemento definito dall'utente che definisce gli input per il processo di compilazione.|

## <a name="text-value"></a>Valore di testo

 Il valore di testo è facoltativo.

 Questo testo specifica il valore dei metadati dell'elemento, che può essere testo o XML.

## <a name="example"></a>Esempio

 L'esempio di codice seguente mostra come aggiungere metadati `Culture` con il valore `fr` all'elemento `CSFile`.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Vedi anche

- [Project riferimento allo schema del file](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementi](../msbuild/msbuild-items.md)
