---
title: Aprire un modello UML tramite l'API di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5baa2168eeae12f1a85fdce0b2981e267dcd6fbc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083881"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Aprire un modello UML tramite l'API di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È anche possibile aprire modelli e diagrammi nell'interfaccia utente di Visual Studio tramite l'API.  
  
 Se si vuole solo leggere un modello in un codice programma senza renderlo visibile all'utente, è possibile usare i metodi seguenti:  
  
- Il bus di modelli di Visual Studio consente di accedere a modelli ed elementi al loro interno e fornisce un metodo standard per creare collegamenti tra modelli. Per altre informazioni, vedere [integrare i modelli UML con altri modelli e strumenti](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
- È possibile aprire un modello in modalità di sola lettura. Per altre informazioni, vedere [leggere un modello UML nel codice programma](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="Showing"></a> Apertura di modelli e diagrammi in Visual Studio  
 Per aprire un modello nell'interfaccia utente, usare l'API `EnvDTE.DTE` standard di Visual Studio. Sono disponibili due cast utili che è possibile eseguire sugli elementi del progetto di modellazione:  
  
- `EnvDTE.Project` consente l'esecuzione del cast da e verso `IModelingProject`, se il progetto è un progetto di modellazione e se è caricato nell'AppDomain corrente.  
  
- `EnvDTE.ProjectItem` consente l'esecuzione del cast da e verso `IDiagramContext`, se l'elemento è un diagramma UML.  
  
  Per l'esempio seguente, il progetto deve importare i riferimenti indicati di seguito:  
  
- EnvDTE  
  
- Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
- Microsoft.VisualStudio.Modeling.Sdk.[versione]  
  
- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versione]  
  
- Microsoft.VisualStudio.Shell.Immutable.[versione]  
  
- Microsoft.VisualStudio.Uml.Interfaces  
  
- System.ComponentModel.Composition  
  
  Questo esempio apre un modello UML in Visual Studio:  
  
```  
using EnvDTE; // Visual Studio API for loading diagrams  
using   
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;    
   // for ICommandExtension and other handler types  
using Microsoft.VisualStudio.Uml.Classes;   
   // for basic UML types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // for model construction methods  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram   
...  
```  
  
 In un'estensione di Visual Studio è possibile usare questa dichiarazione per ottenere l'accesso al provider del servizio host:  
  
```  
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}  
...  
```  
  
 In un metodo è possibile accedere a un progetto, ad esempio il progetto corrente:  
  
```  
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
IModelingProject modelingProject = project as IModelingProject;  
if (modelingProject == null) return; // not a modeling project  
  
// Access the model's store and contents.  
IModelStore store = modelingProject.Store;  
foreach (IElement element in store.Root.OwnedElements) {...}  
  
// Open all the project's diagrams.  
foreach (ProjectItem item in project.ProjectItems)  
{   
     IDiagramContext modelingItem = item as IDiagramContext;  
     if (modelingItem == null)  
         continue; // not a model diagram  
     IDiagram diagram = modelingItem.CurrentDiagram;  
     if (diagram == null)  
     {  
        // Diagram is closed. Open it.  
        item.Open().Activate();  
        diagram = modelingItem.CurrentDiagram;  
     }  
     // Access the shapes.  
     foreach (IShape<IElement> shape   
               in diagram.GetChildShapes<IElement>())  
     {  
       IElement displayedElement = shape.Element;  
       ...  
     }  
   }  
}   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)
