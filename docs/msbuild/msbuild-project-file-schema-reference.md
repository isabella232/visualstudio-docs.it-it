---
title: Informazioni di riferimento sullo schema del file di progetto di MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 824a6f562638edb04854431c437289f2741c46d9
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263097"
---
# <a name="msbuild-project-file-schema-reference"></a>Informazioni di riferimento sullo schema del file di progetto di MSBuild

Fornisce una tabella di tutti gli elementi di XML Schema di MSBuild con i relativi attributi ed elementi figlio disponibili.

 MSBuild utilizza i file di progetto per indicare al motore di compilazione cosa compilare e come compilarlo. I file di progetto MSBuild sono file XML che rispettano il XML Schema MSBuild. Questa sezione illustra il file di definizione XML Schema (*xsd*) per MSBuild.

Il collegamento allo schema in un file di progetto MSBuild non è necessario in Visual Studio 2017 e versioni successive. Se presente, deve essere ` http://schemas.microsoft.com/developer/msbuild/2003` indipendentemente dalla versione di Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementi di XML Schema di MSBuild

 Nella tabella seguente sono elencati tutti gli elementi di MSBuild XML Schema insieme ai relativi attributi e elementi figlio.

|Elemento|Elementi figlio|Attributes|
|-------------|--------------------|----------------|
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Se|--|
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condizione<br /><br /> Project|
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Importa|Condizione|
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condizione<br /><br /> Escludi<br /><br /> Includi<br /><br /> Rimuovere|
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Elemento*|Condizione|
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Elemento*|Condizione|
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Elemento*|Condizione|
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condizione<br /><br /> ExecuteTargets|
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Elemento Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condizione<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Obbligatoria|
|[Elemento ParameterGroup](../msbuild/parametergroup-element.md)|*Parametro*|--|
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importa<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destinazione<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condizione|
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Proprietà*|Condizione|
|[Elemento Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nome<br /><br /> Versione|
|[Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Attività*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condizione<br /><br /> DependsOnTargets<br /><br /> Input<br /><br /> KeepDuplicateOutputs<br /><br /> Nome<br /><br /> Output<br /><br /> Valori di codice restituiti|
|[Elemento Task di target (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Condizione<br /><br /> ContinueOnError<br /><br /> *Parametro*|
|[Elemento Task di UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dati*|Valutazione|
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Attività|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condizione<br /><br /> TaskFactory<br /><br /> TaskName|
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condizione|

## <a name="see-also"></a>Vedere anche

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Condizioni](../msbuild/msbuild-conditions.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
