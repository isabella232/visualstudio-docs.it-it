---
title: Elemento Property (MSBuild) | Microsoft Docs
description: Informazioni sull'MSBuild property, che contiene un nome e un valore di proprietà definiti dall'utente che devono essere specificati come figlio di un elemento PropertyGroup.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 450ac3215b967aced23dcadf99e2f6a049c75cd9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625619"
---
# <a name="property-element-msbuild"></a>Elemento Property (MSBuild)

Contiene un nome un valore della proprietà definiti dall'utente. Ogni proprietà usata in un MSBuild progetto deve essere specificata come figlio di un `PropertyGroup` elemento .

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Sintassi

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
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
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento di raggruppamento per le proprietà.|

## <a name="text-value"></a>Valore di testo

 Il valore di testo è facoltativo.

 Questo testo specifica il valore della proprietà e può contenere codice XML.

## <a name="remarks"></a>Commenti

 I nomi proprietà possono contenere solo caratteri ASCII. Per fare riferimento ai valori delle proprietà nel progetto, si inserisce il nome proprietà tra "`$(`" e "`)`". Ad esempio, `$(builddir)\classes` restituisce *build\classes* se la `builddir` proprietà ha il valore `build` . Per altre informazioni sulle proprietà, vedere MSBuild [proprietà](../msbuild/msbuild-properties.md).

## <a name="example"></a>Esempio

 Il codice seguente imposta la proprietà `Optimization` su `false` e la proprietà `DefaultVersion` su `1.0` se la proprietà `Version` è vuota.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Vedi anche

- [proprietà di MSBuild](../msbuild/msbuild-properties.md)
- [Project sullo schema del file](../msbuild/msbuild-project-file-schema-reference.md)
