---
title: Utilizzo del Framework di pacchetto gestito per implementare un tipo diC#progetto () | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 066695c6d94603d0a0474243ed05dece4cc0bd1f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300373"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso del framework di pacchetto gestito per implementare un tipo di progetto (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il Framework di pacchetto gestito (MPF) C# fornisce le classi che è possibile utilizzare o ereditare da per implementare tipi di progetto personalizzati. MPF implementa molte delle interfacce che Visual Studio prevede che un tipo di progetto fornisca, lasciando libero di concentrarsi sull'implementazione dei particolari del tipo di progetto.  
  
## <a name="using-the-mpf-project-source-code"></a>Uso del codice sorgente del progetto MPF  
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce classi helper per la creazione e la gestione di un nuovo sistema di progetto. A differenza di altre classi in MPF, le classi di progetto non sono incluse negli assembly forniti con Visual Studio. Al contrario, le classi di progetto sono fornite come codice sorgente in [MPF per i progetti 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
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
  
     Microsoft.Build.Tasks.4.0  
  
5. Compilazione del progetto.  
  
## <a name="hierarchy-classes"></a>Classi Hierarchy  
 Nella tabella seguente sono riepilogate le classi in MPFProj che supportano le gerarchie di progetto. Per ulteriori informazioni, vedere [gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nome della classe|  
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
  
## <a name="document-handling-classes"></a>Classi di gestione dei documenti  
 Nella tabella seguente sono elencate le classi di MPF che supportano la gestione dei documenti. Per ulteriori informazioni, vedere [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nome della classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Classi di configurazione e output  
 Nella tabella seguente sono elencate le classi di MPF che consentono ai tipi di progetto di supportare più configurazioni, ad esempio debug e release, e raccolte di output del progetto. Per ulteriori informazioni, vedere [gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
|Nome della classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Automation-classi di supporto  
 Nella tabella seguente sono elencate le classi di MPF che supportano l'automazione, in modo che gli utenti del tipo di progetto possano scrivere componenti aggiuntivi.  
  
|Nome della classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Classi Properties  
 Nella tabella seguente sono elencate le classi di MPF che consentono ai tipi di progetto di aggiungere proprietà che gli utenti possono esplorare e modificare in un visualizzatore proprietà.  
  
|Nome della classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
