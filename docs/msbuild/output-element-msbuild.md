---
title: Elemento Output (MSBuild) | Microsoft Docs
description: Vedere attributi, elementi e un esempio dell'MSBuild Output, che archivia i valori di output delle attività in elementi e proprietà.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 07449cb310d3f362d32791c20d8e903481e68663
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027656"
---
# <a name="output-element-msbuild"></a>Elemento Output (MSBuild)

Archivia i valori di output dell'attività in elementi e proprietà.

 \<Project> \<Target>
 \<Task>
 \<Output>

## <a name="syntax"></a>Sintassi

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`TaskParameter`|Attributo obbligatorio.<br /><br /> Nome del parametro di output dell'attività.|
|`PropertyName`|È obbligatorio l'attributo `PropertyName` o l'attributo `ItemName`.<br /><br /> Proprietà che riceve il valore del parametro di output dell'attività. Il progetto può quindi fare riferimento alla proprietà con la sintassi $( \<PropertyName> ). Questo nome di proprietà può essere il nome di una nuova proprietà o un nome già definito nel progetto.<br /><br /> Non è possibile usare questo attributo se si usa anche `ItemName`.|
|`ItemName`|È obbligatorio l'attributo `PropertyName` o l'attributo `ItemName`.<br /><br /> Elemento che riceve il valore del parametro di output dell'attività. Il progetto può quindi fare riferimento all'elemento con la sintassi @( \<ItemName> ). Il nome dell'elemento può essere il nome di un nuovo elemento o un nome già definito nel progetto. Quando il nome dell'elemento è un elemento esistente, i valori dei parametri di output vengono aggiunti all'elemento esistente. <br /><br /> Non è possibile usare questo attributo se si usa anche `PropertyName`.|
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementi figlio

 Nessuno.

### <a name="parent-elements"></a>Elementi padre

| Elemento | Descrizione |
| - | - |
| [Attività](../msbuild/task-element-msbuild.md) | Crea ed esegue un'istanza di un'MSBuild attività. |

## <a name="example"></a>Esempio

 L'esempio di codice seguente mostra l'attività `Csc` eseguita all'interno di un elemento `Target`. Gli elementi e le proprietà passati ai parametri dell'attività vengono dichiarati al di fuori dell'ambito di questo esempio. Il valore dal parametro di output `OutputAssembly` viene archiviato nell'elemento `FinalAssemblyName` e il valore del parametro di output `BuildSucceeded` viene archiviato nella proprietà `BuildWorked`. Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md) (Attività).

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Vedi anche

- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
- [Attività](../msbuild/msbuild-tasks.md)
