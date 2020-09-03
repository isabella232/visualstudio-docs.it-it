---
title: Aggiornamento di forme e connettori per riflettere il modello | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c31d54a87ff305504496eac6ae02900334c0966a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659452"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aggiornamento di forme e di connettori per riflettere il modello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un linguaggio specifico di dominio in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , è possibile fare in modo che l'aspetto di una forma rispecchi lo stato del modello sottostante.

 Gli esempi di codice in questo argomento devono essere aggiunti a un `.cs` file nel `Dsl` progetto. Queste istruzioni sono necessarie in ogni file:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Impostare le proprietà della mappa di forme per controllare la visibilità di un elemento Decorator
 È possibile controllare la visibilità di un elemento Decorator senza scrivere codice programma, configurando il mapping tra la forma e la classe di dominio nella definizione DSL. Per altre informazioni, vedere gli argomenti seguenti:

- [Procedura: controllare la visibilità di un elemento Decorator (reindirizzamento)](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Esporre il colore e lo stile di una forma come proprietà
 Nella definizione DSL, fare clic con il pulsante destro del mouse sulla classe Shape, scegliere **Aggiungi esposto**, quindi fare clic su uno degli elementi, ad esempio **colore riempimento**.

 La forma dispone ora di una proprietà di dominio che è possibile impostare nel codice programma o come utente. Ad esempio, per impostarlo nel codice programma di un comando o di una regola, è possibile scrivere:

 `shape.FillColor = System.Drawing.Color.Red;`

 Se si desidera rendere la variabile della proprietà solo sotto il controllo del programma e non dall'utente, selezionare la nuova proprietà del dominio, ad esempio **colore riempimento** nel diagramma di definizione DSL. Quindi, nel Finestra Proprietà, il set **è esplorabile** `false` o impostato **è UI ReadOnly** su `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definire le regole di modifica per impostare il colore, lo stile o la posizione dipendono dalle proprietà degli elementi del modello
 È possibile definire regole che aggiornano l'aspetto della forma dipendente da altre parti del modello. Ad esempio, è possibile definire una regola di modifica su un elemento del modello che aggiorna il colore della relativa forma dipendente dalle proprietà dell'elemento del modello. Per ulteriori informazioni sulle regole di modifica, vedere la pagina relativa [alla propagazione delle modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

 È consigliabile utilizzare le regole solo per aggiornare le proprietà gestite nell'archivio, perché le regole non vengono richiamate quando viene eseguito il comando Annulla. Non sono incluse alcune funzionalità grafiche, ad esempio le dimensioni e la visibilità di una forma. Per aggiornare le funzionalità di una forma, vedere [aggiornamento delle funzionalità grafiche non di archivio](#OnAssociatedProperty).

 Nell'esempio seguente si presuppone che sia stata esposta `FillColor` come proprietà di dominio, come descritto nella sezione precedente.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }

```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Usare OnChildConfigured per inizializzare le proprietà di una forma
 Per impostare le proprietà di una forma quando viene creata per la prima volta, l'override `OnChildConfigured()` in una definizione parziale della classe del diagramma. La classe Diagram è specificata nella definizione DSL e il codice generato è in **Dsl\Generated Code\Diagram.cs**. Ad esempio:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}

```

 Questo metodo può essere utilizzato sia per le proprietà del dominio che per le funzionalità non di archivio, ad esempio la dimensione della forma.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Utilizzare AssociateValueWith () per aggiornare altre funzionalità di una forma
 Per alcune funzionalità di una forma, ad esempio se presenta un'ombreggiatura o lo stile della freccia di un connettore, non esiste alcun metodo incorporato per esporre la funzionalità come proprietà di dominio.  Le modifiche apportate a tali funzionalità non sono sotto il controllo del sistema di transazione. Non è pertanto appropriato aggiornarle utilizzando le regole, perché le regole non vengono richiamate quando l'utente esegue il comando Annulla.

 In alternativa, è possibile aggiornare tali funzionalità usando <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . Nell'esempio seguente lo stile della freccia di un connettore è controllato da un valore di una proprietà di dominio nella relazione visualizzata dal connettore:

```
public partial class ArrowConnector // My connector class.
{
   /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape’s built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }
    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}

```

 `AssociateValueWith()` deve essere chiamato una volta per ogni proprietà del dominio che si desidera registrare. Una volta chiamato, qualsiasi modifica apportata alla proprietà specificata chiamerà `OnAssociatedPropertyChanged()` in qualsiasi forma che presenta l'elemento del modello della proprietà.

 Non è necessario chiamare `AssociateValueWith()` per ogni istanza. Sebbene InitializeResources sia un metodo di istanza, viene richiamato solo una volta per ogni classe Shape.
