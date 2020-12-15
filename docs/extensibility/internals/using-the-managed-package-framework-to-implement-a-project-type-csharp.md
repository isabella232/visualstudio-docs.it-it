---
title: Usare il Framework di pacchetto gestito per un tipo di progetto (C#)
description: Informazioni sul Framework di pacchetto gestito, che fornisce le classi .NET che è possibile usare o ereditare da per implementare tipi di progetto personalizzati.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4b425962ed0f664b8255b6489ac8f0d38be7c13c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487543"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso del framework di pacchetto gestito per implementare un tipo di progetto (C#)
Il Framework di pacchetto gestito (MPF) fornisce le classi C# che è possibile usare o ereditare da per implementare tipi di progetto personalizzati. MPF implementa molte delle interfacce che Visual Studio prevede che un tipo di progetto fornisca, lasciando libero di concentrarsi sull'implementazione dei particolari del tipo di progetto.

## <a name="using-the-mpf-project-source-code"></a>Uso del codice sorgente del progetto MPF
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. A differenza di altre classi in MPF, le classi di progetto non sono incluse negli assembly forniti con Visual Studio. Al contrario, le classi di progetto sono fornite come codice sorgente in [MPF per i progetti 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Per aggiungere questo progetto alla soluzione VSPackage, procedere come segue:

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

3. Modificare il file VSPackage. csproj aggiungendo il blocco seguente prima degli altri `<Import>` blocchi:

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

     Microsoft. Build. Tasks. 4.0

5. Compilare il progetto.

## <a name="hierarchy-classes"></a>Classi Hierarchy
 Nella tabella seguente sono riepilogate le classi in MPFProj che supportano le gerarchie di progetto. Per ulteriori informazioni, vedere [gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Classi Document-Handling
 Nella tabella seguente sono elencate le classi di MPF che supportano la gestione dei documenti. Per ulteriori informazioni, vedere [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Classi di configurazione e output
 Nella tabella seguente sono elencate le classi di MPF che consentono ai tipi di progetto di supportare più configurazioni, ad esempio debug e release, e raccolte di output del progetto. Per ulteriori informazioni, vedere [gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Classi Automation-Support
 Nella tabella seguente sono elencate le classi di MPF che supportano l'automazione, in modo che gli utenti del tipo di progetto possano scrivere componenti aggiuntivi.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classi Properties
 Nella tabella seguente sono elencate le classi di MPF che consentono ai tipi di progetto di aggiungere proprietà che gli utenti possono esplorare e modificare in un visualizzatore proprietà.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
