---
title: Elemento ProjectExtensions (MSBuild) | Microsoft Docs
description: Informazioni sull'elemento MSBuildProjectExtensions, che consente ai file di progetto MSBuild di contenere informazioni non di MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74f01f9e6a82d89ca99455f160bda1e9b7e24345
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048838"
---
# <a name="projectextensions-element-msbuild"></a>Elemento ProjectExtensions (MSBuild)

Consente ai file di progetto MSBuild di contenere informazioni non MSBuild. Qualsiasi elemento all'interno di un `ProjectExtensions` elemento verrà ignorato da MSBuild.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Sintassi

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

 Nessuno

### <a name="child-elements"></a>Elementi figlio

 Nessuno

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |

## <a name="remarks"></a>Commenti

 `ProjectExtensions`È possibile utilizzare un solo elemento in un progetto MSBuild.

## <a name="example"></a>Esempio

 L'esempio di codice seguente illustra l'archiviazione di informazioni provenienti dall'ambiente di sviluppo integrato in un elemento `ProjectExtensions`.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>Vedi anche

- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
