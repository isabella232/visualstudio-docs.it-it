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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632472"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)

Fa riferimento a un SDK del progetto MSBuild.

 \<Project> \<Sdk>

## <a name="syntax"></a>Sintassi

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Attributo obbligatorio.<br /><br /> Nome dell'SDK di progetto.|
|`Version`|Attributo facoltativo.<br /><br /> Versione dell'SDK di progetto|

### <a name="child-elements"></a>Elementi figlio

 No.

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |

## <a name="see-also"></a>Vedere anche

- [Procedura: Fare riferimento a un SDK di progetto MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Informazioni di riferimento sullo schema del file di progettoProject file schema reference](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
