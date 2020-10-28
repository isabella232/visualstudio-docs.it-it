---
title: Attività CreateProperty | Microsoft Docs
description: Usare l'attività CreateProperty di MSBuild per popolare le proprietà con i valori passati, consentendo la copia dei valori da una proprietà o una stringa a un'altra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d7dd8d7f5a50998832a8fac6f47bf66e9a6bbe9
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796187"
---
# <a name="createproperty-task"></a>CreateProperty (attività)

Popola le proprietà con i valori passati. In questo modo i valori vengono copiati da una proprietà o una stringa a un'altra.

## <a name="attributes"></a>Attributes

Nella tabella che segue vengono descritti i parametri dell'attività `CreateProperty` .

| Parametro | Descrizione |
|------------------| - |
| `Value` | Parametro di ouput facoltativo `String`.<br /><br /> Specifica il valore da copiare nella nuova proprietà. |
| `ValueSetByTask` | Parametro di ouput facoltativo `String`.<br /><br /> Contiene lo stesso valore del parametro `Value`. Usare questo parametro solo quando si vuole evitare che la proprietà output sia impostata da MSBuild quando ignora la destinazione di inclusione, perché gli output sono aggiornati. |

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

L'esempio seguente usa l'attività `CreateProperty` per creare la proprietà `NewFile` usando la combinazione dei valori della proprietà `SourceFilename` e `SourceFileExtension`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

Dopo l'esecuzione del progetto il valore della proprietà `NewFile` è *Module1.vb* .

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Attività](../msbuild/msbuild-tasks.md)
