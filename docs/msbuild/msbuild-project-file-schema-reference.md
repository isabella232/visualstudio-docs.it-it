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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263097"
---
# <a name="msbuild-project-file-schema-reference"></a>Informazioni di riferimento sullo schema del file di progetto di MSBuild

Fornisce una tabella di tutti gli elementi dello schema XML MSBuild con gli attributi disponibili e gli elementi figlio.

 MSBuild usa i file di progetto per indicare al motore di compilazione cosa compilare e come compilarlo. I file di progetto MSBuild sono file XML che aderiscono allo schema XML di MSBuild. In questa sezione viene documentato il file di definizione dello schema XML (*con estensione xsd*) per MSBuild.

Il collegamento dello schema in un file di progetto MSBuild non è necessario in Visual Studio 2017 e versioni successive. Se presente, deve ` http://schemas.microsoft.com/developer/msbuild/2003` essere indipendentemente dalla versione di Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementi di XML Schema di MSBuild

 Nella tabella seguente sono elencati tutti gli elementi dello schema XML MSBuild insieme ai relativi elementi e attributi figlio.

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
|[Elemento output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condizione<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Elemento parametro](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Obbligatoria|
|[Elemento ParameterGroup](../msbuild/parametergroup-element.md)|*Parametro*|--|
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importa<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destinazione<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condizione|
|[PropertyGroup (elemento) (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Proprietà*|Condizione|
|[Sdk (elemento) (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nome<br /><br /> Versione|
|[Elemento di destinazione (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Attività*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condizione<br /><br /> DependsOnTargets<br /><br /> Input<br /><br /> KeepDuplicateOutputs<br /><br /> Nome<br /><br /> Output<br /><br /> Valori di codice restituiti|
|[Elemento Task di Target (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Condizione<br /><br /> ContinueOnError<br /><br /> *Parametro*|
|[Elemento Task di UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dati*|Valutazione|
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Attività|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condizione<br /><br /> TaskFactory<br /><br /> TaskName|
|[Quando elemento (MSBuild)When element (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condizione|

## <a name="see-also"></a>Vedere anche

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Condizioni](../msbuild/msbuild-conditions.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
