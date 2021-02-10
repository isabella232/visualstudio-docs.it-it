---
title: Elemento Sdk (MSBuild) | Microsoft Docs
description: Informazioni su sintassi, attributi ed elementi per l'elemento dell'SDK di MSBuild, che fa riferimento a un SDK di progetto MSBuild.
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
ms.workload:
- multiple
ms.openlocfilehash: cd5f66cc6500a3320e0da962985f5b7fff1e86dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937901"
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

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Attributo obbligatorio.<br /><br /> Nome dell'SDK di progetto.|
|`Version`|Attributo facoltativo.<br /><br /> Versione dell'SDK di progetto|

### <a name="child-elements"></a>Elementi figlio

 Nessuna.

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |

## <a name="see-also"></a>Vedi anche

- [Procedura: Fare riferimento a un SDK di progetto MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
