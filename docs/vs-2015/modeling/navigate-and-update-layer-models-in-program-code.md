---
title: Esplorare e aggiornare i modelli di livello nel codice del programma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 69286377a302fabc900fe4cf9384bb65d094a378
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214935"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Esplorare e aggiornare i modelli di livello nel codice del programma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento descrive gli elementi e le relazioni nei modelli di livello, che è possibile esplorare e aggiornare usando codice programma. Per altre informazioni sui diagrammi livello dal punto di vista dell'utente, vedere [diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md) e [diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md).  
  
 Il modello <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> descritto in questo argomento rappresenta un aspetto di un modello <xref:Microsoft.VisualStudio.GraphModel> più generale. Se si sta scrivendo un [estensione di menu comandi o movimenti](../modeling/add-commands-and-gestures-to-layer-diagrams.md), usare il `Layer` modello. Se si sta scrivendo un [estensione di convalida dei livelli](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), è più facile da usare il `GraphModel`.  
  
## <a name="transactions"></a>Transazioni  
 Quando si aggiorna un modello, valutare la possibilità di includere le modifiche in un elemento `ILinkedUndoTransaction`. Ciò consente di raggruppare le modifiche in un'unica transazione. Se non è possibile apportare correttamente una modifica, viene eseguito il rollback dell'intera transazione. Se l'utente annulla una modifica, tutte le modifiche verranno annullate.  
  
 Per altre informazioni, vedere [aggiornamenti di modelli di collegamento UML tramite transazioni](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Contenuto  
 ![ILayer e ILayerModel possono contenere entrambi oggetti ILayers. ](../modeling/media/layerapi-containment.png "LayerApi_Containment")  
  
 I livelli (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) e il modello di livello (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) possono contenere commenti e livelli.  
  
 Un livello (`ILayer`) può essere contenuto in un modello di livello (`ILayerModel`) o annidato in un altro elemento `ILayer`.  
  
 Per creare un commento o un livello, usare i metodi di creazione sul contenitore appropriato.  
  
## <a name="dependency-links"></a>Collegamenti di dipendenza  
 Un collegamento di dipendenza è rappresentato da un oggetto e può essere esplorato in entrambe le direzioni:  
  
 ![Oggetto ILayerDependencyLink che connette due ILayers. ](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")  
  
 Per creare un collegamento di dipendenza, chiamare `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Commenti  
 I commenti possono essere contenuti in livelli o nel modello di livello e possono inoltre essere collegati a qualsiasi elemento livello:  
  
 ![I commenti possono essere collegati a qualsiasi elemento livello. ](../modeling/media/layerapi-comments.png "LayerApi_Comments")  
  
 Un commento può essere collegato a qualsiasi numero di elementi o a nessun elemento.  
  
 Per ottenere i commenti collegati a un elemento livello, usare:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  La proprietà `Comments` di un elemento `ILayer` ottiene commenti contenuti nell'elemento `ILayer`. Non ottiene i commenti che sono collegati a esso.  
  
 Creare un commento richiamando `CreateComment()` sul contenitore appropriato.  
  
 Creare un collegamento usando `CreateLink()` sul commento.  
  
## <a name="layer-elements"></a>Elementi di livello  
 Tutti i tipi di elemento che possono essere contenuti in un modello sono elementi di livello:  
  
 ![I contenuti del diagramma sono oggetti ILayerElements. ](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Proprietà  
 Ogni `ILayerElement` ha un dizionario di stringhe denominato`Properties`. È possibile usare questo dizionario per collegare informazioni arbitrarie a qualsiasi elemento livello.  
  
## <a name="artifact-references"></a>Riferimenti per elementi  
 Un riferimento per elementi (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) rappresenta il collegamento tra un livello e un elemento di progetto come un file, una classe o una cartella. L'utente crea gli elementi quando crea o aggiunge un livello trascinando elementi da Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti in un diagramma livello. È possibile collegare qualsiasi numero di riferimenti per elementi a un livello.  
  
 Ogni riga di Esplora livello visualizza un riferimento ad artefatti. Per altre informazioni, vedere [creare i diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md).  
  
 I tipi e i metodi principali interessati dai riferimenti ad artefatti sono i seguenti:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. La proprietà Categorie indica il tipo di elemento al quale viene fatto riferimento, ad esempio una classe, un file eseguibile o un assembly. Questa proprietà determina le modalità di identificazione dell'elemento di destinazione da parte dell'identificatore.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> crea un riferimento a elementi da un <xref:EnvDTE.Project> o da un <xref:EnvDTE.ProjectItem>. Si tratta di un'operazione asincrona, quindi in genere si fornisce un callback che viene chiamato al termine della creazione.  
  
 I riferimenti a elementi del livello non devono essere confusi con gli elementi nei diagrammi dei casi di uso.  
  
## <a name="shapes-and-diagrams"></a>Forme e diagrammi  
 Per rappresentare ogni elemento di un modello di livello si usano due oggetti: un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> e un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. L'oggetto `IShape` rappresenta la posizione e la dimensione della forma sul diagramma. Nei modelli di livello ogni `ILayerElement` ha un `IShape` e ogni `IShape` in un diagramma livello ha un `ILayerElement`. `IShape` è usato anche per i modelli UML, quindi non tutti gli oggetti `IShape` hanno un elemento livello.  
  
 Analogamente, <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> è visualizzato in un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.  
  
 Nel codice di un gestore comandi o movimenti personalizzato, è possibile ottenere il diagramma corrente e la selezione corrente di forme dall'importazione `DiagramContext`:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Ogni oggetto ILayerElement è presentato da un oggetto IShape. ](../modeling/media/layerapi-shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> e <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> sono usati anche per visualizzare modelli UML. Per altre informazioni, vedere [visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere comandi e movimenti a diagrammi livelli](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Aggiungere la convalida architettura personalizzati a diagrammi livelli](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Aggiungere proprietà personalizzate ai diagrammi livello](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)   
 [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)



