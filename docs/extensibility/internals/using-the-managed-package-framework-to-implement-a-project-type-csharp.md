---
title: Utilizzo di Framework di pacchetto gestito per un tipo di progetto (c ') Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704113"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso del framework di pacchetto gestito per implementare un tipo di progetto (C#)
Il Framework di pacchetto gestito (MPF) fornisce le classi di C , è possibile utilizzare o ereditare da per implementare i propri tipi di progetto. Il MPF implementa molte delle interfacce che Visual Studio prevede un tipo di progetto da fornire, lasciando libero di concentrarsi sull'implementazione dei particolari del tipo di progetto.

## <a name="using-the-mpf-project-source-code"></a>Utilizzo del codice sorgente del progetto MPF
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di nuovo sistema di progetto. A differenza di altre classi in MPF, le classi di progetto non sono incluse negli assembly forniti con Visual Studio. Al contrario, le classi di progetto vengono fornite come codice sorgente in [MPF per Projects 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Per aggiungere questo progetto alla soluzione VSPackage, eseguire le operazioni seguenti:To add this project to your VSPackage solution, do the following:

1. Scaricare i file MPFProj in *MPFProjectDir*.

2. Nel file *MPFProjectDir,* Dev10, Src, CSharp, ProjectBase del file, modificare il blocco seguente:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Creare un progetto VSPackage.Create a VSPackage project.

2. Scaricare il progetto VSPackage.

3. Modificare il file con estensione csproj VSPackage `<Import>` aggiungendo il blocco seguente prima degli altri blocchi:

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

3. Riaprire il progetto VSPackage. Verrà visualizzata una nuova directory denominata ProjectBase.You should see a new directory named ProjectBase.

4. Aggiungere il riferimento seguente al progetto VSPackage:Add the following reference to the VSPackage project:

     Microsoft.Build.Tasks.4.0

5. Compilare il progetto.

## <a name="hierarchy-classes"></a>Classi gerarchiche
 Nella tabella seguente vengono riepilogate le classi in MPFProj che supportano le gerarchie di progetto. Per ulteriori informazioni, vedere [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Classi di gestione dei documentiDocument-Handling Classes
 Nella tabella seguente sono elencate le classi in MPF che supportano la gestione dei documenti. Per ulteriori informazioni, vedere [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Classi di configurazione e output
 Nella tabella seguente sono elencate le classi in MPF che consentono ai tipi di progetto di supportare più configurazioni, ad esempio debug e rilascio e raccolte di output del progetto. Per ulteriori informazioni, vedere [Gestione delle opzioni](../../extensibility/internals/managing-configuration-options.md)di configurazione .

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Classi di supporto per l'automazione
 Nella tabella seguente sono elencate le classi in MPF che supportano l'automazione in modo che gli utenti del tipo di progetto possano scrivere componenti aggiuntivi.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classi di proprietà
 Nella tabella seguente sono elencate le classi in MPF che consentono ai tipi di progetto di aggiungere proprietà che gli utenti possono esplorare e modificare in un visualizzatore proprietà.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
