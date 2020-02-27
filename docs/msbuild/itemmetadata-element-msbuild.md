---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18e1722fcd6867ca5e8ae52e220ff0a3dd2a3b7f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633616"
---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)

Contiene una chiave dei metadati di elemento definita dall'utente che contiene il valore dei metadati dell'elemento. Un elemento può avere un numero qualsiasi di coppie chiave-valore dei metadati.

 \<Project> \<ItemGroup> \<Item>

## <a name="syntax"></a>Sintassi

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elemento figlio

 Nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento](../msbuild/item-element-msbuild.md)|Elemento definito dall'utente che definisce gli input per il processo di compilazione.|

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

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [Items](../msbuild/msbuild-items.md)
