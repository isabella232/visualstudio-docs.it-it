---
title: 'Procedura: accedere e vincolare la selezione corrente'
description: Informazioni su come determinare l'elemento su cui l'utente ha fatto clic con il pulsante destro del mouse quando si scrive un gestore comandi o movimenti per il linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28d0f99743535965b3cf203d461fac5d0193607c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386605"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Procedura: accedere e vincolare la selezione corrente

Quando si scrive un gestore comandi o movimenti per il linguaggio specifico di dominio, è possibile determinare l'elemento su cui l'utente ha fatto clic con il pulsante destro del mouse. È anche possibile impedire la selezione di alcune forme o campi. Ad esempio, è possibile disporre che quando l'utente fa clic su un elemento Decorator icona, viene invece selezionata la forma che lo contiene. Vincolando la selezione in questo modo si riduce il numero di gestori che è necessario scrivere. Rende anche più semplice per l'utente, che può fare clic in un punto qualsiasi della forma senza dover evitare l'elemento Decorator.

## <a name="access-the-current-selection-from-a-command-handler"></a>Accedere alla selezione corrente da un gestore comandi

La classe del set di comandi per un linguaggio specifico di dominio contiene i gestori di comandi per i comandi personalizzati. La classe , da cui deriva la classe del set di comandi per un linguaggio specifico di dominio, fornisce alcuni membri per accedere <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> alla selezione corrente.

A seconda del comando, il gestore dei comandi potrebbe richiedere la selezione in Progettazione modelli, in Esplora modelli o nella finestra attiva.

### <a name="to-access-selection-information"></a>Per accedere alle informazioni di selezione

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe definisce i membri seguenti che possono essere utilizzati per accedere alla selezione corrente.

    |Membro|Descrizione|
    |-|-|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Restituisce se uno degli elementi selezionati in Progettazione modelli è una forma `true` raggruppamento; in caso contrario, `false` .|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Restituisce `true` se il diagramma è selezionato in Progettazione modelli; in caso contrario, `false` .|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Restituisce `true` se viene selezionato esattamente un elemento in Progettazione modelli; in caso contrario, `false` .|
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Restituisce `true` se nella finestra attiva è selezionato esattamente un elemento; in caso contrario, `false` .|
    |Proprietà<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Ottiene una raccolta di sola lettura degli elementi selezionati in Progettazione modelli.|
    |Proprietà<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Ottiene una raccolta di sola lettura degli elementi selezionati nella finestra attiva.|
    |Proprietà<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Ottiene l'elemento primario della selezione in Progettazione modelli.|
    |Proprietà<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Ottiene l'elemento primario della selezione nella finestra attiva.|

2. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> proprietà della classe fornisce l'accesso all'oggetto che rappresenta la finestra di Progettazione modelli e fornisce accesso aggiuntivo agli <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> elementi selezionati in Progettazione <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> modelli.

3. Inoltre, il codice generato definisce una proprietà della finestra degli strumenti di esplorazione e una proprietà di selezione della finestra di esplorazione nella classe del set di comandi per il linguaggio specifico di dominio.

    - La proprietà della finestra degli strumenti di esplorazione restituisce un'istanza della classe della finestra degli strumenti di esplorazione per il linguaggio specifico di dominio. La classe della finestra degli strumenti di esplorazione deriva dalla <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> classe e rappresenta Esplora modelli per il linguaggio specifico di dominio.

    - La `ExplorerSelection` proprietà restituisce l'elemento selezionato nella finestra esplora modelli per il linguaggio specifico di dominio.

## <a name="determine-which-window-is-active"></a>Determinare quale finestra è attiva

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>L'interfaccia contiene i membri che forniscono l'accesso allo stato di selezione corrente nella shell. È possibile ottenere un oggetto dalla classe del pacchetto o dalla classe del set di comandi per il linguaggio specifico di dominio tramite la proprietà definita <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> nella classe di base di `MonitorSelection` ognuno. La classe del pacchetto deriva dalla classe e la classe del set di comandi <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> deriva dalla <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe .

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Per determinare da un gestore comandi il tipo di finestra attiva

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> proprietà della classe restituisce un oggetto che fornisce <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> l'accesso allo stato di selezione corrente nella shell.

2. La <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> dell'interfaccia ottiene il contenitore di selezione attivo, che può essere diverso dalla finestra attiva.

3. Aggiungere le proprietà seguenti alla classe del set di comandi per il linguaggio specifico di dominio per determinare il tipo di finestra attiva.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Vincolare la selezione

Aggiungendo regole di selezione, è possibile controllare quali elementi vengono selezionati quando l'utente seleziona un elemento nel modello. Ad esempio, per consentire all'utente di considerare un numero di elementi come una singola unità, è possibile usare una regola di selezione.

### <a name="to-create-a-selection-rule"></a>Per creare una regola di selezione

1. Creare un file di codice personalizzato nel progetto DSL

2. Definire una classe di regole di selezione derivata dalla <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> classe .

3. Eseguire <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> l'override del metodo della classe della regola di selezione per applicare i criteri di selezione.

4. Aggiungere una definizione di classe parziale per la classe ClassDiagram al file di codice personalizzato.

     La classe deriva dalla classe ed è definita nel file di `ClassDiagram` <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> codice generato, Diagram.cs, nel progetto DSL.

5. Eseguire <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> l'override della proprietà `ClassDiagram` della classe per restituire la regola di selezione personalizzata.

     L'implementazione predefinita della <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> proprietà ottiene un oggetto regola di selezione che non modifica la selezione.

### <a name="example"></a>Esempio

Il file di codice seguente crea una regola di selezione che espande la selezione in modo da includere tutte le istanze di ogni forma di dominio selezionata inizialmente.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>