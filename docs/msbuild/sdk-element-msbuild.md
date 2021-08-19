---
title: Elemento Sdk (MSBuild) | Microsoft Docs
description: Informazioni su sintassi, attributi ed elementi per l'MSBuild Sdk, che fa riferimento a un SDK MSBuild progetto.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2f4af21014bd749897bf8872fc09c934f1e6ecf9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108356"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)

Fa riferimento a MSBuild SDK del progetto.

 \<Project> \<Sdk>

## <a name="syntax"></a>Sintassi

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Attributo obbligatorio.<br /><br /> Nome dell'SDK di progetto.|
|`Version`|Attributo facoltativo.<br /><br /> Versione dell'SDK di progetto|

### <a name="child-elements"></a>Elementi figlio

 Nessuno.

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un MSBuild di progetto. |

## <a name="see-also"></a>Vedi anche

- [Procedura: Fare riferimento a un SDK di progetto MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
