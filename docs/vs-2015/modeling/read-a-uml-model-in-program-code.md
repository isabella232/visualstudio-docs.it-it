---
title: Leggere un modello UML nel codice del programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 48d70901a2d616031eeed197b639f3a7bb7336c3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092994"
---
# <a name="read-a-uml-model-in-program-code"></a>Leggere un modello UML nel codice programma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile caricare un modello UML e i relativi diagrammi usando l'API UML.  
  
## <a name="Reading"></a> Lettura di un modello nel codice programma  
 Per accedere al contenuto di un modello senza visualizzarlo in una finestra di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], usare `ModelingProject.LoadReadOnly()`.  
  
 Ad esempio:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 Per leggere le forme in un diagramma è necessario leggere il progetto e quindi il diagramma.  
  
 Ad esempio:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>Metodi alternativi  
 Per molte applicazioni, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus consente di fare riferimento a modelli ed elementi al loro interno, con maggiore efficienza e flessibilità rispetto ai metodi descritti in questo argomento. Fornisce un metodo standard per stabilire collegamenti tra elementi arbitrari, negli stessi modelli o in modelli diversi. Per altre informazioni, vedere [integrare i modelli UML con altri modelli e strumenti](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 È anche possibile aprire modelli e diagrammi nell'interfaccia utente usando l'API di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [aprire un modello UML tramite l'API di Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="Standalone"></a> Applicazioni autonome  
 L'esempio della sezione precedente funziona nelle estensioni di Visual Studio. È possibile leggere un modello in un'applicazione autonoma, ma è necessario aggiungere alcuni riferimenti al progetto[!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  I dettagli relativi alla modalità di lettura di un modello in un'applicazione autonoma potrebbero essere diversi nelle versioni future del prodotto. Alcune funzionalità accessibili nella versione corrente potrebbero non essere più disponibili nelle versioni future.  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Per aggiungere riferimenti per leggere un modello in un'applicazione autonoma.  
  
1. In Esplora soluzioni fare clic sul progetto in cui compila l'applicazione e quindi fare clic su **proprietà**. Nell'editor delle proprietà, nelle **Application** scheda, impostare **Framework di destinazione** alla versione richiesta di .NET Framework.  
  
2. Aggiungere i riferimenti [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] necessari per l'accesso ai modelli UML, in genere:  
  
   - Microsoft.VisualStudio.Uml.Interfaces.dll  
  
   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3. Oltre ai riferimenti elencati nelle sezioni precedenti, aggiungere i riferimenti seguenti al progetto dal **\Programmi\Microsoft Visual Studio [versione] \Common7\IDE\PrivateAssemblies.**:  
  
   - Microsoft.VisualStudio.Uml.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     Per leggere diagrammi nell'applicazione, potrebbero inoltre essere necessari i riferimenti seguenti:  
  
   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)
