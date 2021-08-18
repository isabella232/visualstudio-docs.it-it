---
title: Aggiornamento di forme e di connettori per riflettere il modello
description: Si apprenderà che in un linguaggio specifico di dominio in Visual Studio è possibile fare in modo che l'aspetto di una forma rifletta lo stato del modello sottostante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0f667821a9940603f887850a9b26fc1d8ca2f073
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085325"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Aggiornare forme e connettori per riflettere il modello

In un linguaggio specifico di dominio in Visual Studio, è possibile fare in modo che l'aspetto di una forma rifletta lo stato del modello sottostante.

Gli esempi di codice in questo argomento devono essere aggiunti a `.cs` un file nel `Dsl` progetto. In ogni file sono necessarie le direttive seguenti:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Impostare le proprietà di forme mappa per controllare la visibilità di un elemento Decorator

È possibile controllare la visibilità di un elemento Decorator senza scrivere codice programma, configurando il mapping tra la forma e la classe di dominio nella definizione DSL. Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Esporre il colore e lo stile di una forma come proprietà

Nella definizione DSL fare clic con il pulsante destro del mouse sulla classe shape, scegliere **Aggiungi** esposto e quindi fare clic su uno degli elementi, ad esempio **Colore riempimento.**

La forma ha ora una proprietà di dominio che è possibile impostare nel codice programma o come utente. Ad esempio, per impostarlo nel codice programma di un comando o di una regola, è possibile scrivere:

`shape.FillColor = System.Drawing.Color.Red;`

Se si vuole rendere la variabile di proprietà solo sotto il controllo del programma e non dall'utente, selezionare la nuova proprietà di dominio, ad esempio **Colore** riempimento nel diagramma di definizione DSL. Nella finestra di Finestra Proprietà impostare **Is Browsable** su `false` o Impostare Is UI **Readonly** su `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definire le regole di modifica per fare in modo che colore, stile o posizione dipersi dalle proprietà degli elementi del modello
 È possibile definire regole che aggiornano l'aspetto della forma in base ad altre parti del modello. Ad esempio, è possibile definire una regola di modifica su un elemento del modello che aggiorna il colore della forma in base alle proprietà dell'elemento del modello. Per altre informazioni sulle regole di modifica, vedere [Regole di propagazione delle modifiche all'interno del modello.](../modeling/rules-propagate-changes-within-the-model.md)

 È consigliabile usare le regole solo per aggiornare le proprietà mantenute all'interno dell'archivio, perché le regole non vengono richiamate quando viene eseguito il comando Annulla. Non sono incluse alcune funzionalità grafiche, ad esempio le dimensioni e la visibilità di una forma. Per aggiornare queste funzionalità di una forma, vedere [Aggiornamento di funzionalità grafiche non di archivio.](#OnAssociatedProperty)

 Nell'esempio seguente si presuppone che sia stata `FillColor` esposta come proprietà di dominio, come descritto nella sezione precedente.

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

Per impostare le proprietà di una forma quando viene creata per la prima volta, eseguire l'override `OnChildConfigured()` in una definizione parziale della classe diagramma. La classe diagramma viene specificata nella definizione DSL e il codice generato si trova in **Dsl\Generated Code\Diagram.cs.** Esempio:

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

Questo metodo può essere usato sia per le proprietà di dominio che per le funzionalità non di archiviazione, ad esempio le dimensioni della forma.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Usare AssociateValueWith() per aggiornare altre funzionalità di una forma

Per alcune funzionalità di una forma, ad esempio se ha un'ombreggiatura o lo stile freccia di un connettore, non esiste un metodo predefinito per esporre la funzionalità come proprietà di dominio.  Le modifiche apportate a tali funzionalità non sono sotto il controllo del sistema di transazioni. Pertanto, non è appropriato aggiornarle usando regole, perché le regole non vengono richiamate quando l'utente esegue il comando Annulla.

È invece possibile aggiornare tali funzionalità usando <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . Nell'esempio seguente lo stile della freccia di un connettore è controllato da un valore di una proprietà di dominio nella relazione visualizzata dal connettore:

```csharp
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
        { // Update the shape's built-in Decorator feature:
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

`AssociateValueWith()` deve essere chiamato una volta per ogni proprietà di dominio che si vuole registrare. Dopo la chiamata, qualsiasi modifica alla proprietà specificata chiamerà in tutte le forme che `OnAssociatedPropertyChanged()` presentano l'elemento del modello della proprietà.

Non è necessario chiamare per `AssociateValueWith()` ogni istanza. Sebbene InitializeResources sia un metodo di istanza, viene richiamato una sola volta per ogni classe shape.
