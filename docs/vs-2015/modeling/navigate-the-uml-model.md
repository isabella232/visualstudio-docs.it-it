---
title: Esplorare il modello UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 827a0f7b79f3973b98710de0fb13565145ffb1e5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300261"
---
# <a name="navigate-the-uml-model"></a>Esplorare il modello UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento introduce i principali tipi di modello UML.  
  
## <a name="the-model-elements-model-and-model-store"></a>Elementi del modello, modello e archivio modelli  
 I tipi definiti nell'assembly **Interfaces** corrispondono ai tipi definiti nel [specifica UML, versione 2.1.2](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).  
  
 I tipi nella specifica UML vengono rappresentati come interfacce in Visual Studio. La lettera "I" viene anteposta al nome di ogni tipo. Ad esempio: <xref:Microsoft.VisualStudio.Uml.Classes.IElement>, <xref:Microsoft.VisualStudio.Uml.Classes.IClass>, <xref:Microsoft.VisualStudio.Uml.Interactions.IInteraction>, <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>.  
  
 Tutti i tipi tranne IElement ereditano le proprietà da uno o più supertipi.  
  
-   Per un riepilogo dei tipi di modelli, vedere [tipi di elemento di modello UML](../modeling/uml-model-element-types.md).  
  
-   Per i dettagli completi dell'API, vedere [riferimento API per l'estendibilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
### <a name="relationships"></a>Relazioni  
 Le proprietà e le relazioni definite nella specifica UML vengono implementate come proprietà .NET.  
  
 La maggior parte delle relazioni è esplorabile in entrambe le direzioni. Una relazione corrisponde a una coppia di proprietà, con una proprietà nel tipo a ogni estremità. Ad esempio, le proprietà `IElement.Owner` e `IElement.OwnedElements` rappresentano due estremità di una relazione. Questa espressione quindi restituirà sempre true:  
  
 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`  
  
 Diverse relazioni, ad esempio IAssociation, sono sempre rappresentate da un oggetto che può disporre di proprietà personalizzate.  
  
 Se si elimina un elemento dal modello, viene automaticamente eliminata qualsiasi relazione di cui fa parte e la proprietà all'altra estremità viene aggiornata.  
  
 Se la specifica UML assegna una molteplicità pari a 0..1 a una proprietà, il valore può essere `null`. Una molteplicità con valore massimo maggiore di 1 indica che la proprietà .NET è di tipo: `IEnumerable<` *tipo*`>`.  
  
 Per altre informazioni sull'attraversamento di relazioni, vedere [esplorare relazioni con l'API UML](../modeling/navigate-relationships-with-the-uml-api.md).  
  
### <a name="the-ownership-tree"></a>Albero di proprietà  
 Un modello contiene un albero di oggetti <xref:Microsoft.VisualStudio.Uml.Classes.IElement>. Ogni elemento dispone delle proprietà `OwnedElements` e `Owner`.  
  
 Nella maggior parte dei casi, alle destinazioni delle proprietà `Owner` e `OwnedElements` viene fatto riferimento anche da altre proprietà con nomi più specifici. Ad esempio, ogni operazione UML è di proprietà di una classe UML. <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> dispone quindi di una proprietà denominata <xref:Microsoft.VisualStudio.Uml.Classes.IOperation.Class%2A> e, in ogni oggetto <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>, `Class == Owner`.  
  
 L'elemento più in alto dell'albero, che non ha un proprietario, è <xref:Microsoft.VisualStudio.Uml.AuxiliaryConstructs.IModel>. IModel è contenuto in <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, in cui è l'oggetto <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore.Root%2A>.  
  
 Ogni elemento del modello viene creato con un proprietario. Per altre informazioni, vedere [creare elementi e relazioni nei modelli UML](../modeling/create-elements-and-relationships-in-uml-models.md).  
  
 ![Diagramma classi: modello, diagramma, forma ed elemento](../modeling/media/uml-mm1.png "UML_MM1")  
  
## <a name="shapes-and-diagrams"></a>Forme e diagrammi  
 Gli elementi nel modello UML possono essere visualizzati nei diagrammi. Diversi tipi di diagrammi possono visualizzare sottotipi diversi di IElement.  
  
 In alcuni casi, un elemento può essere visualizzato in più diagrammi. Ad esempio, un elemento IUseCase può disporre di più IShape, che possono essere visualizzati in un solo diagramma o in diagrammi diversi.  
  
 Le forme vengono disposte in un albero. I bordi dell'albero sono rappresentati dalle proprietà ParentShape e ChildShapes. I diagrammi sono le uniche forme che non dispongono di elementi padre. Le forme sulla superficie di un diagramma sono costituite da parti più piccole. Ad esempio, la forma di una classe ha raggruppamenti per attributi e operazioni.  
  
 Per altre informazioni sulle forme, vedere [visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="access-to-the-model-in-extensions"></a>Accesso al modello nelle estensioni  
 Nelle estensioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] definite come componenti MEF, è possibile dichiarare proprietà che importano informazioni dal contesto in cui l'estensione viene eseguita.  
  
|Tipo di attributo|A cosa consente di accedere|Ulteriori informazioni|  
|--------------------|----------------------------------|----------------------|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> .IDiagramContext<br /><br /> (in Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Il diagramma con stato attivo corrente.|[Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|  
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> .ILinkedUndoContext<br /><br /> (in Microsoft.VisualStudio.Modeling.Sdk.[versione].dll)|Consente di raggruppare le modifiche in transazioni.|[Collegare aggiornamenti di modelli UML tramite transazioni](../modeling/link-uml-model-updates-by-using-transactions.md)|  
|Microsoft.VisualStudio.Shell .SVsServiceProvider<br /><br /> (in Microsoft.VisualStudio.Shell.Immutable.[versione].dll)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] host, da cui è possibile accedere a file, progetti e altri aspetti.|[Aprire un modello UML tramite l'API di Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|  
  
### <a name="to-get-the-context"></a>Per ottenere il contesto  
 Dichiarare una o entrambe le interfacce seguenti all'interno della classe dell'estensione:  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
  
```  
  
 Managed Extensibility Framework (MEF) le assocerà alle definizioni da cui è possibile ottenere il diagramma corrente, l'archivio modelli, l'oggetto radice e così via:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
IClassDiagram classDiagram = diagram as IClassDiagram;  
       // or diagrams of other types  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
### <a name="to-get-the-current-selection"></a>Per ottenere la selezione corrente  
  
```  
// All selected shapes and their elements  
foreach (IShape shape in diagram.SelectedShapes)  
{    
   IDiagram selectedDiagram = shape as IDiagram;  
   if (selectedDiagram != null)  
   { // no shape selected - user right-clicked the diagram  
     ... Context.CurrentDiagram ...  
   }  
   else  
   {  
     IElement selectedElement = shape.Element;  
   ...}  
// All selected shapes that display a specfic type of element  
foreach (IShape<IInterface> in   
   diagram.GetSelectedShapes<IInterface>())   
{...}  
```  
  
## <a name="accessing-another-model-or-diagrams"></a>Accesso a un altro modello o ai diagrammi  
 È possibile:  
  
-   Usare il bus di modelli di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare collegamenti tra elementi in modelli diversi. Per altre informazioni, vedere [integrare i modelli UML con altri modelli e strumenti](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Caricare un progetto di modellazione e i diagrammi in modalità di sola lettura senza renderlo visibile nell'interfaccia utente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [leggere un modello UML nel codice programma](../modeling/read-a-uml-model-in-program-code.md).  
  
-   Aprire un progetto di modellazione e i diagrammi in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e quindi accedere al contenuto. Per altre informazioni, vedere [aprire un modello UML tramite l'API di Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)



