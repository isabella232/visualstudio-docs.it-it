---
title: Elemento ProjectExtensions (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 94f2d88aa19bf01ebe6f25c7d80772c812abcc59
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632966"
---
# <a name="projectextensions-element-msbuild"></a>Elemento ProjectExtensions (MSBuild)

Consente ai file di progetto MSBuild di contenere informazioni non MSBuild. Qualsiasi elemento all'interno di un elemento `ProjectExtensions` verrà ignorato da MSBuild.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Sintassi

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

 None

### <a name="child-elements"></a>Elemento figlio

 None

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |

## <a name="remarks"></a>Note

 In un progetto MSBuild è possibile utilizzare un solo elemento `ProjectExtensions`.

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

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
