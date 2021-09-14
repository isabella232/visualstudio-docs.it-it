---
title: Elemento Project (MSBuild) | Microsoft Docs
description: Informazioni sull'MSBuild Project, che è l'elemento radice obbligatorio di un MSBuild di progetto.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ef40e3e42fed7eb9b981defabdd073e4ab9c8c9e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625625"
---
# <a name="project-element-msbuild"></a>Elemento Project (MSBuild)

Elemento radice obbligatorio di un MSBuild di progetto.

## <a name="syntax"></a>Sintassi

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

| Attributo | Descrizione |
|------------------------| - |
| `DefaultTargets` | Attributo facoltativo.<br /><br /> Destinazione o destinazioni predefinite che saranno il punto di ingresso della compilazione se non è stata specificata alcuna destinazione. Per specificare più destinazioni, usare il punto e virgola (;) come delimitatore.<br /><br /> Se non viene specificata alcuna destinazione predefinita nell'attributo o nella riga di comando MSBuild, il motore esegue la prima destinazione nel file di progetto dopo la valutazione degli elementi `DefaultTargets` [Import.](../msbuild/import-element-msbuild.md) |
| `InitialTargets` | Attributo facoltativo.<br /><br /> Destinazione o destinazioni iniziali da eseguire prima delle destinazioni specificate nell'attributo `DefaultTargets` o nella riga di comando. Per specificare più destinazioni, usare il punto e virgola (`;`) come delimitatore. Se più file importati definiscono `InitialTargets`, tutte le destinazioni menzionate verranno eseguite nell'ordine in cui si rilevano le importazioni. |
| `Sdk` | Attributo facoltativo. <br /><br /> Nome e versione facoltativa dell'SDK da usare per creare istruzioni Import implicite che vengono aggiunte al file PROJ. Se non viene specificata alcuna versione, MSBuild tenterà di risolvere una versione predefinita.  Ad esempio, `<Project Sdk="Microsoft.NET.Sdk" />` o `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Attributo facoltativo.<br /><br /> Versione del set di strumenti usato da MSBuild per determinare i valori per $(MSBuildBinPath) e $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Attributo facoltativo.<br /><br /> Nomi di proprietà che non verranno considerati come globali. Questo attributo impedisce a proprietà della riga di comando specifiche di eseguire l'override dei valori delle proprietà impostati in un file di progetto o di destinazioni e di tutte le importazioni successive. Per specificare più proprietà, usare il punto e virgola (;) come delimitatore.<br /><br /> Le proprietà globali in genere eseguono l'override dei valori delle proprietà impostati nel file di progetto o di destinazioni. Se la proprietà è elencata nel valore `TreatAsLocalProperty`, il valore della proprietà globale non esegue l'override dei valori della proprietà impostati in tale file e delle importazioni successive. Per altre informazioni, vedere [Procedura: Compilare gli stessi file di origine con opzioni diverse](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Nota:** per impostare le proprietà globali al prompt dei comandi, usare l'opzione **-property** (o **-p**). È anche possibile impostare o modificare le proprietà globali per i progetti figlio in una compilazione a più progetti usando l'attributo `Properties` dell'attività di MSBuild. Per altre informazioni, vedere MSBuild [attività](../msbuild/msbuild-task.md). |
| `xmlns` | Attributo facoltativo.<br /><br /> Quando specificato, l'attributo `xmlns` deve avere il valore di `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Elementi figlio

| Elemento | Descrizione |
| - | - |
| [Scegliere](../msbuild/choose-element-msbuild.md) | Elemento facoltativo.<br /><br /> Valuta gli elementi figlio per selezionare un set di elementi `ItemGroup` e/o di elementi `PropertyGroup` da valutare. |
| [Importa](../msbuild/import-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente a un file di progetto importare un altro file di progetto. Possono esistere zero o più elementi `Import` in un progetto. |
| [ImportGroup](../msbuild/importgroup-element.md) | Elemento facoltativo.<br /><br /> Contiene una raccolta di elementi `Import` raggruppati in una condizione facoltativa. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Elemento facoltativo.<br /><br /> Elemento di raggruppamento per singoli elementi. Gli elementi vengono specificati usando l'elemento [Item](../msbuild/item-element-msbuild.md). Possono esistere zero o più elementi `ItemGroup` in un progetto. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente di definire un set di definizioni di elementi, ovvero valori di metadati applicati a tutti gli elementi nel progetto per impostazione predefinita. ItemDefinitionGroup ovvia alla necessità di usare le attività`CreateItem` e `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente di rendere persistenti le informazioni non MSBuild in un file MSBuild progetto. Possono esistere zero o un elemento `ProjectExtensions` in un progetto. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Elemento facoltativo.<br /><br /> Elemento di raggruppamento per singole proprietà. Le proprietà vengono specificate usando l'elemento [Property](../msbuild/property-element-msbuild.md). Possono esistere zero o più elementi `PropertyGroup` in un progetto. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Elemento facoltativo.<br /><br /> Fa riferimento a un SDK MSBuild progetto.  Questo elemento può essere usato come alternativa all'attributo Sdk. |
| [Destinazione](../msbuild/target-element-msbuild.md) | Elemento facoltativo.<br /><br /> Contiene un set di attività da MSBuild eseguire in sequenza. Le attività vengono specificate usando l'elemento [Task](../msbuild/task-element-msbuild.md). Possono esistere zero o più elementi `Target` in un progetto. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Elemento facoltativo.<br /><br /> Consente di registrare le attività in MSBuild. Possono esistere zero o più elementi `UsingTask` in un progetto. |

### <a name="parent-elements"></a>Elementi padre

 Nessuno.

## <a name="see-also"></a>Vedi anche

- [Procedura: Specificare quale destinazione compilare per prima](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)
- [Project riferimento allo schema di file](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
