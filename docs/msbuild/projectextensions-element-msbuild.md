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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632966"
---
# <a name="projectextensions-element-msbuild"></a>Elemento ProjectExtensions (MSBuild)

Consente ai file di progetto MSBuild di contenere informazioni non MSBuild. Qualsiasi elemento `ProjectExtensions` all'interno di un elemento verrà ignorato da MSBuild.Anything inside of a element will be ignored by MSBuild.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Sintassi

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

 nessuno

### <a name="child-elements"></a>Elementi figlio

 nessuno

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |

## <a name="remarks"></a>Osservazioni

 In `ProjectExtensions` un progetto MSBuild è possibile utilizzare un solo elemento.

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

- [Informazioni di riferimento sullo schema del file di progettoProject file schema reference](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
