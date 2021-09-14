---
title: Elemento ProjectExtensions (MSBuild) | Microsoft Docs
description: Informazioni sull'elemento MSBuildProjectExtensions, che consente MSBuild file di progetto di contenere informazioni non MSBuild progetto.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0fbf7760af7275172bc57ce0aac097e70182b4f5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625620"
---
# <a name="projectextensions-element-msbuild"></a>Elemento ProjectExtensions (MSBuild)

Consente MSBuild file di progetto di contenere informazioni non MSBuild progetto. Qualsiasi elemento `ProjectExtensions` all'interno di un elemento verrà ignorato da MSBuild.

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
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un MSBuild di progetto. |

## <a name="remarks"></a>Commenti

 In un `ProjectExtensions` progetto MSBuild un solo elemento.

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

- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
