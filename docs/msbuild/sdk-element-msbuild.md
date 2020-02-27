---
title: Elemento Sdk (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a704744032c5dea70246463a816ba8e1f5c84e8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632472"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)

Fa riferimento a un SDK di progetto MSBuild.

 \<Project> \<Sdk>

## <a name="syntax"></a>Sintassi

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Attributo obbligatorio.<br /><br /> Nome dell'SDK di progetto.|
|`Version`|Attributo facoltativo.<br /><br /> Versione dell'SDK di progetto|

### <a name="child-elements"></a>Elemento figlio

 Nessuno

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |

## <a name="see-also"></a>Vedere anche

- [Procedura: fare riferimento a un SDK di progetto MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
