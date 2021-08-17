---
title: Usare Managed Package Framework per un tipo di progetto (C#)
description: Informazioni su Managed Package Framework, che fornisce classi .NET che è possibile usare o ereditare da per implementare tipi di progetto personalizzati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e05358c2e8ba33048fbeec4af798e77b66755cb9b9a1c5c6867cc20e630f71fe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375598"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso del framework di pacchetto gestito per implementare un tipo di progetto (C#)
Managed Package Framework (MPF) fornisce classi C# che è possibile usare o ereditare da per implementare tipi di progetto personalizzati. MPF implementa molte delle interfacce Visual Studio prevede che un tipo di progetto fornirà, lasciando libero di concentrarsi sull'implementazione delle specifiche del tipo di progetto.

## <a name="using-the-mpf-project-source-code"></a>Uso del codice sorgente Project MPF
 Managed Package Framework for Projects (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. A differenza di altre classi in MPF, le classi di progetto non sono incluse negli assembly forniti con Visual Studio. Le classi di progetto vengono invece fornite come codice sorgente in [MPF for Projects 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Per aggiungere questo progetto alla soluzione VSPackage, eseguire le operazioni seguenti:

1. Scaricare i file MPFProj in *MPFProjectDir*.

2. In *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file modificare il blocco seguente:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Creare un progetto VSPackage.

2. Scaricare il progetto VSPackage.

3. Modificare il file con estensione csproj di VSPackage aggiungendo il blocco seguente prima degli altri `<Import>` blocchi:

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Salvare il progetto.

2. Chiudere e riaprire la soluzione VSPackage.

3. Riaprire il progetto VSPackage. Verrà visualizzata una nuova directory denominata ProjectBase.

4. Aggiungere il riferimento seguente al progetto VSPackage:

     Microsoft.Build.Tasks.4.0

5. Compilare il progetto.

## <a name="hierarchy-classes"></a>Classi di gerarchia
 La tabella seguente riepiloga le classi in MPFProj che supportano le gerarchie di progetto. Per altre informazioni, vedere [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.HierarchyNode`|
|`Microsoft.VisualStudio.Package.ProjectNode`|
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|
|`Microsoft.VisualStudio.Package.FileNode`|
|`Microsoft.VisualStudio.Package.FolderNode`|
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|
|`Microsoft.VisualStudio.Package.ReferenceNode`|
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|
|`Microsoft.VisualStudio.Package.ComReferenceNode`|
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|
|`Microsoft.VisualStudio.Package.BuildDependency`|

## <a name="document-handling-classes"></a>Document-Handling classi
 Nella tabella seguente sono elencate le classi in MPF che supportano la gestione dei documenti. Per altre informazioni, vedere [Apertura e salvataggio di Project elementi](../../extensibility/internals/opening-and-saving-project-items.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Classi di configurazione e output
 Nella tabella seguente sono elencate le classi in MPF che consentono ai tipi di progetto di supportare più configurazioni, ad esempio debug e versione, e raccolte di output del progetto. Per altre informazioni, vedere [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Automation-Support classi
 Nella tabella seguente sono elencate le classi di MPF che supportano l'automazione in modo che gli utenti del tipo di progetto possano scrivere componenti aggiuntivi.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classi Properties
 Nella tabella seguente sono elencate le classi in MPF che consentono ai tipi di progetto di aggiungere proprietà che gli utenti possono esplorare e modificare in un Visualizzatore proprietà.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
