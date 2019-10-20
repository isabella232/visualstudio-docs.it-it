---
title: Esplorazione e aggiornamento di modelli di livello nel codice programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668566"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Esplorare e aggiornare i modelli di livello nel codice del programma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento descrive gli elementi e le relazioni nei modelli di livello, che è possibile esplorare e aggiornare usando codice programma. Per ulteriori informazioni sui diagrammi livello dal punto di vista dell'utente, vedere [diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md) e [diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md).

 Il modello `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` descritto in questo argomento rappresenta un aspetto di un modello <xref:Microsoft.VisualStudio.GraphModel> più generale. Se si sta scrivendo un [comando di menu o un'estensione di movimento](../modeling/add-commands-and-gestures-to-layer-diagrams.md), usare il modello di `Layer`. Se si scrive un' [estensione di convalida dei livelli](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), è più facile usare la `GraphModel`.

## <a name="transactions"></a>Transazioni
 Quando si aggiorna un modello, valutare la possibilità di includere le modifiche in un elemento `ILinkedUndoTransaction`. Ciò consente di raggruppare le modifiche in un'unica transazione. Se non è possibile apportare correttamente una modifica, viene eseguito il rollback dell'intera transazione. Se l'utente annulla una modifica, tutte le modifiche verranno annullate.

 Per altre informazioni, vedere [collegare aggiornamenti di modelli UML tramite transazioni](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Contenuto
 ![ILayer e ILayerModel possono contenere entrambi ILayers.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Layers ([ILayer](/previous-versions/ff644251(v=vs.140))) e il modello di livello ([ILayerModel](/previous-versions/ff643069(v=vs.140))) possono contenere commenti e livelli.

 Un livello (`ILayer`) può essere contenuto in un modello di livello (`ILayerModel`) o annidato in un altro elemento `ILayer`.

 Per creare un commento o un livello, usare i metodi di creazione sul contenitore appropriato.

## <a name="dependency-links"></a>Collegamenti di dipendenza
 Un collegamento di dipendenza è rappresentato da un oggetto e può essere esplorato in entrambe le direzioni:

 ![Un ILayerDependencyLink connette due ILayers.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Per creare un collegamento di dipendenza, chiamare `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Comments
 I commenti possono essere contenuti in livelli o nel modello di livello e possono inoltre essere collegati a qualsiasi elemento livello:

 ![I commenti possono essere collegati a qualsiasi elemento del livello.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Un commento può essere collegato a qualsiasi numero di elementi o a nessun elemento.

 Per ottenere i commenti collegati a un elemento livello, usare:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> La proprietà `Comments` di un elemento `ILayer` ottiene commenti contenuti nell'elemento `ILayer`. Non ottiene i commenti che sono collegati a esso.

 Creare un commento richiamando `CreateComment()` sul contenitore appropriato.

 Creare un collegamento usando `CreateLink()` sul commento.

## <a name="layer-elements"></a>Elementi di livello
 Tutti i tipi di elemento che possono essere contenuti in un modello sono elementi di livello:

 ![Il contenuto del diagramma livello è ILayerElements.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Proprietà
 Ogni `ILayerElement` ha un dizionario di stringhe denominato`Properties`. È possibile usare questo dizionario per collegare informazioni arbitrarie a qualsiasi elemento livello.

## <a name="artifact-references"></a>Riferimenti per elementi
 Un riferimento a artefatto ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))) rappresenta il collegamento tra un livello e un elemento del progetto, ad esempio un file, una classe o una cartella. L'utente crea gli elementi quando crea o aggiunge un livello trascinando elementi da Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti in un diagramma livello. È possibile collegare qualsiasi numero di riferimenti per elementi a un livello.

 Ogni riga di Esplora livello visualizza un riferimento a elementi. Per altre informazioni, vedere [creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md).

 I tipi e i metodi principali interessati dai riferimenti ad artefatti sono i seguenti:

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140)). La proprietà Categorie indica il tipo di artefatto al quale viene fatto riferimento, ad esempio una classe, un file eseguibile o un assembly. Questa proprietà determina le modalità di identificazione dell'elemento di destinazione da parte dell'identificatore.

 [ArtifactReferenceExtensions. CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) crea un riferimento a un elemento da un <xref:EnvDTE.Project> o <xref:EnvDTE.ProjectItem>. Si tratta di un'operazione asincrona, quindi in genere si fornisce un callback che viene chiamato al termine della creazione.

 I riferimenti ad artefatti del livello non devono essere confusi con gli artefatti nei diagrammi dei casi di uso.

## <a name="shapes-and-diagrams"></a>Forme e diagrammi
 Due oggetti vengono usati per rappresentare ogni elemento in un modello di livello: un `ILayerElement` e un [IShape](/previous-versions/ee806673(v=vs.140)). L'oggetto `IShape` rappresenta la posizione e la dimensione della forma sul diagramma. Nei modelli di livello ogni `ILayerElement` ha un `IShape` e ogni `IShape` in un diagramma livello ha un `ILayerElement`. `IShape` è usato anche per i modelli UML, quindi non tutti gli oggetti `IShape` hanno un elemento livello.

 Allo stesso modo, il `ILayerModel` viene visualizzato in un [IDiagram](/previous-versions/ee789658(v=vs.140)).

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

 ![Ogni oggetto ILayerElement è presentato da un oggetto IShape.](../modeling/media/layerapi-shapes.png)

 [IShape](/previous-versions/ee806673(v=vs.140)) e [IDiagram](/previous-versions/ee789658(v=vs.140)) vengono usati anche per visualizzare i modelli UML. Per altre informazioni, vedere [visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>Vedere anche

- [Aggiunta di comandi e movimenti a diagrammi livello](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Aggiungere strumenti di convalida dell'architettura personalizzati a diagrammi livello](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Aggiungere proprietà personalizzate ai diagrammi livello](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)
- [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)
