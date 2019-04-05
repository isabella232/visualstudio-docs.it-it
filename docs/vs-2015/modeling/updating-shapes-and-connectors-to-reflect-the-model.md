---
title: Aggiornamento di forme e connettori per riflettere il modello di | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e5c03fa6a04abd06af9e24b83977d491e9809265
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969716"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aggiornamento di forme e di connettori per riflettere il modello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un linguaggio specifico di dominio in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile rendere l'aspetto di una forma riflettono lo stato del modello sottostante.  
  
 Gli esempi di codice in questo argomento devono essere aggiunto a un `.cs` del file nei `Dsl` progetto. È necessario in ogni file queste istruzioni:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Impostare le proprietà di mappa della forma per controllare la visibilità di un elemento decorator  
 È possibile controllare la visibilità di un elemento decorator senza scrivere codice programma, configurando il mapping tra la forma e la classe di dominio nella definizione DSL. Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Procedura: Controllare la visibilità di un elemento Decorator-reindirizzamento](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)  
  
-   [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)  
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Esporre il colore e lo stile di una forma come proprietà  
 Nella definizione DSL, fare doppio clic la classe di forma, scegliere **Aggiungi esposta**, quindi fare clic su uno degli elementi, ad esempio **colore riempimento**.  
  
 A questo punto, la forma presenta una proprietà di dominio che è possibile impostare nel codice programma o un utente. Per impostarla nel codice del programma di un comando o una regola, ad esempio, è possibile scrivere:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Se si desidera rendere la variabile di proprietà solo nel controllo del programma e non dall'utente, selezionare la nuova proprietà di dominio, ad esempio **colore riempimento** nel diagramma di definizione DSL. Quindi, nella finestra Proprietà impostare **è visualizzabile** a `false` o impostare **sola lettura dell'interfaccia utente viene** per `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definire le regole di modifica per rendere colore, stile o il percorso variano a seconda delle proprietà di elemento di modello  
 È possibile definire regole che aggiornano l'aspetto della forma dipende da altre parti del modello. Ad esempio, è possibile definire una regola di modifica su un elemento del modello che aggiorna il colore della forma dipende dalle proprietà dell'elemento del modello. Per altre informazioni sulle regole di modifica, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Utilizzare le regole solo per aggiornare le proprietà che vengono mantenute in Store, perché le regole non vengono richiamate quando viene eseguito il comando di annullamento. Questo non include alcune funzionalità con interfaccia grafica, ad esempio le dimensioni e la visibilità di una forma. Per aggiornare le funzionalità di una forma, vedere [funzionalità di aggiornamento Non-Store grafica](#OnAssociatedProperty).  
  
 Nell'esempio seguente si presuppone che sia stata esposta `FillColor` come una proprietà di dominio come descritto nella sezione precedente.  
  
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
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Usare OnChildConfigured per inizializzare le proprietà della forma  
 Per impostare le proprietà di una forma quando viene inizialmente creato, l'override `OnChildConfigured()` in una definizione parziale della classe diagramma. Classe del diagramma viene specificata nella definizione DSL, e il codice generato è nella **Dsl\Generated Code\Diagram.cs**. Ad esempio:  
  
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
  
 Questo metodo può essere utilizzato sia per le proprietà di dominio e le funzionalità senza store, ad esempio le dimensioni della forma.  
  
##  <a name="OnAssociatedProperty"></a> Usare AssociateValueWith () per aggiornare altre funzionalità di una forma  
 Per alcune funzionalità di una forma, ad esempio se ha un'ombreggiatura o lo stile della freccia di un connettore, non vi è alcun metodo incorporato di esporre la funzionalità come una proprietà di dominio.  Le modifiche apportate a tali funzionalità non sono sotto il controllo del sistema delle transazioni. Pertanto, non è appropriato per aggiornarli utilizzando le regole, perché le regole non vengono richiamate quando l'utente esegue il comando di annullamento.  
  
 In alternativa, è possibile aggiornare queste funzionalità usando <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. Nell'esempio seguente, lo stile della freccia di un connettore è controllato da un valore della proprietà del dominio nella relazione che consente di visualizzare il connettore:  
  
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
  
 `AssociateValueWith()` deve essere chiamato una volta per ogni proprietà di dominio che si desidera registrare. Dopo che è stato chiamato, tutte le modifiche alla proprietà specificata chiamerà `OnAssociatedPropertyChanged()` in tutte le forme che presentano l'elemento del modello della proprietà.  
  
 Non è necessario chiamare `AssociateValueWith()` per ogni istanza. Anche se InitializeResources è un metodo di istanza, viene richiamato solo una volta per ogni classe della forma.
