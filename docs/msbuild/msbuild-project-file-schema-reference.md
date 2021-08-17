---
title: Informazioni di riferimento sullo schema del file di progetto di MSBuild | Microsoft Docs
description: Vedere una tabella che elenca tutti i MSBuild XML Schema con gli attributi disponibili e gli elementi figlio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 49e2b4196ce6ac08177aa9a4b3c7b484de8194c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068878"
---
# <a name="msbuild-project-file-schema-reference"></a>Informazioni di riferimento sullo schema del file di progetto di MSBuild

Fornisce una tabella di tutti gli elementi MSBuild XML Schema con gli attributi disponibili e gli elementi figlio.

 MSBuild i file di progetto per indicare al motore di compilazione cosa compilare e come compilarlo. MSBuild file di progetto sono file XML conformi allo MSBuild XML Schema. In questa sezione viene documentato il file di definizione dello schema XML *(xsd)* per MSBuild.

Il collegamento allo schema in MSBuild file di progetto non è necessario in Visual Studio 2017 e versioni successive. Se presente, deve essere ` http://schemas.microsoft.com/developer/msbuild/2003` indipendentemente dalla versione di Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementi di XML Schema di MSBuild

 Nella tabella seguente sono elencati tutti i MSBuild xml schema e i relativi elementi figlio e attributi.

|Elemento|Elementi figlio|Attributi|
|-------------|--------------------|----------------|
|[Scegliere l'elemento (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Se|--|
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condition<br /><br /> Project|
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Importa|Condition|
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condition<br /><br /> Escludi<br /><br /> Includi<br /><br /> Rimuovi|
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condition|
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condition|
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condition|
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condition<br /><br /> ExecuteTargets|
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Elemento output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condition<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Necessario|
|[Elemento ParameterGroup](../msbuild/parametergroup-element.md)|*Parametro*|--|
|[Project elemento (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importa<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destinazione<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> Sdk<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condition|
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Proprietà*|Condition|
|[Elemento Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nome<br /><br /> Versione|
|[Elemento target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Attività*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condition<br /><br /> DependsOnTargets<br /><br /> Input<br /><br /> KeepDuplicateOutputs<br /><br /> Nome<br /><br /> Output<br /><br /> Restituisce|
|[Elemento Task di Target (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Condition<br /><br /> ContinueOnError<br /><br /> *Parametro*|
|[Elemento Task di UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dati*|Valutazione|
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Attività|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condition<br /><br /> TaskFactory<br /><br /> TaskName|
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condition|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Condizioni](../msbuild/msbuild-conditions.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
