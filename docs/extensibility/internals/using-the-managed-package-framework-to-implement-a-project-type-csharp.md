---
title: Usando i Framework di pacchetto gestito per un tipo di progetto (c#) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f233e2256fc4baef9ee6ca7f07d3d7b71b68b47
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112305"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso del framework di pacchetto gestito per implementare un tipo di progetto (C#)
Il Framework di pacchetto gestito (MPF) fornisce le classi di c# è possibile usare o ereditare da implementare tipi di progetto personalizzati. MPF implementa molte delle interfacce di che Visual Studio prevede un tipo di progetto per fornire, permettendo all'utente di concentrarsi sull'implementazione delle indicazioni del tipo di progetto.

## <a name="using-the-mpf-project-source-code"></a>Usando il codice sorgente del progetto MPF
 Il Framework di pacchetto gestito per progetti (MPFProj) fornisce classi helper per la creazione e la gestione di nuovo sistema di progetto. A differenza di altre classi in MPF, le classi di progetto non sono inclusi negli assembly forniti con Visual Studio. Al contrario, le classi di progetto vengono fornite come codice sorgente, in [MPF di progetti 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Per aggiungere questo progetto alla soluzione VSPackage, eseguire le operazioni seguenti:

1. Scaricare i file MPFProj *MPFProjectDir*.

2. Nel *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, modificare il blocco seguente:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Creare un progetto di VSPackage.

2. Scaricare il progetto di VSPackage.

3. Modificare il file con estensione csproj VSPackage aggiungendo il blocco seguente prima degli altri `<Import>` blocchi:

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

2. Chiudere e riaprire la soluzione di VSPackage.

3. Riaprire il progetto del pacchetto VSPackage. Si noterà una nuova directory denominata ProjectBase.

4. Aggiungere il seguente riferimento al progetto VSPackage:

     Microsoft.Build.Tasks.4.0

5. Compilare il progetto.

## <a name="hierarchy-classes"></a>Gerarchia classi
 Nella tabella seguente sono riepilogate le classi nel MPFProj che supportano le gerarchie di progetto. Per altre informazioni, vedere [gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Classi di gestione documenti
 Nella tabella seguente elenca le classi in MPF che supportano la gestione dei documenti. Per altre informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Configurazione e le classi di Output
 La tabella seguente elenca le classi di MPF che consentono tipi di progetto supporta più configurazioni, ad esempio il debug e rilascio e raccolte di output del progetto. Per altre informazioni, vedere [opzioni di configurazione Gestione](../../extensibility/internals/managing-configuration-options.md).

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Classi di supporto di automazione
 Nella tabella seguente elenca le classi in MPF che supportano l'automazione in modo che gli utenti del tipo di progetto possono scrivere componenti aggiuntivi.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classi di proprietà
 La tabella seguente elenca le classi di MPF che consentono a tipi di progetto aggiungono le proprietà che gli utenti possono esplorare e modificare in un visualizzatore proprietà.

|Nome di classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|