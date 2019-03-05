---
title: Elemento ImportGroup | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3dd0b9fc5ef9441e867d5103bbb722a3628ffc78
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610528"
---
# <a name="importgroup-element"></a>Elemento ImportGroup
Contiene una raccolta di elementi `Import` raggruppati in una condizione facoltativa. Per altre informazioni, vedere [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md).

 \<Project> \<ImportGroup>

## <a name="syntax"></a>Sintassi

```xml
<ImportGroup Condition="'String A' == 'String B'">
    <Import ... />
    <Import ... />
</ImportGroup>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Description|
|---------------|-----------------|
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[Import](../msbuild/import-element-msbuild.md)|Importa il contenuto di un file di progetto in un altro file di progetto.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Description |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |

## <a name="example"></a>Esempio
 L'esempio di codice seguente mostra l'elemento `ImportGroup`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ImportGroup>
        <Import Project="$(Targets1.targets)" />
        <Import Project="$(Targets2.targets)" />
    </ImportGroup>
...
</Project>
```

## <a name="see-also"></a>Vedere anche
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementi](../msbuild/msbuild-items.md)
