---
title: Personalizzazione dei campi testo e immagine
description: Informazioni sulla personalizzazione dei file di testo e immagine. Si apprenderà anche che quando si definisce un elemento Decorator di testo in una forma, è rappresentato da un oggetto TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8f56c67a16b59b17de5a4bd95ad9a074203b097224844f541adc8b658d60edea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386056"
---
# <a name="customizing-text-and-image-fields"></a>Personalizzazione dei campi testo e immagine
Quando si definisce un elemento Decorator di testo in una forma, viene rappresentato da un oggetto TextField. Per esempi di inizializzazione di TextFields e di altri ShapeField, esaminare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.

 TextField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un'etichetta. Un'istanza TextField è condivisa tra molte forme della stessa classe. L'istanza TextField non archivia separatamente il testo dell'etichetta per ogni istanza: il metodo accetta invece la forma come parametro e può cercare il testo dipendente dallo stato corrente della forma e dal relativo elemento del `GetDisplayText(ShapeElement)` modello.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Come viene determinato l'aspetto di un campo di testo
 Il `DoPaint()` metodo viene chiamato per visualizzare il campo sullo schermo. È possibile eseguire l'override del valore predefinito oppure `DoPaint(),` è possibile eseguire l'override di alcuni dei metodi che chiama. La versione semplificata seguente dei metodi predefiniti consente di comprendere come eseguire l'override del comportamento predefinito:

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Esistono diverse altre coppie di `Get` metodi e `Default` proprietà, ad esempio `DefaultMultipleLine/GetMultipleLine()` . È possibile assegnare un valore alla proprietà Default per modificare il valore per tutte le istanze del campo della forma. Per fare in modo che il valore vari da un'istanza di forma a un'altra o dipendente dallo stato della forma o dal relativo elemento del modello, eseguire l'override del `Get` metodo .

## <a name="static-customizations"></a>Personalizzazioni statiche
 Se si vuole modificare ogni istanza di questo campo della forma, verificare innanzitutto se è possibile impostare la proprietà nella definizione DSL. Ad esempio, è possibile impostare le dimensioni e lo stile del carattere nel Finestra Proprietà.

 In caso contrario, eseguire l'override del metodo della classe shape e assegnare un valore alla `InitializeShapeFields` proprietà appropriata del campo di `Default...` testo.

> [!WARNING]
> Per eseguire l'override di , è necessario impostare la proprietà Generates Double Derived della `InitializeShapeFields()` classe shape su nella definizione  `true` DSL.

 In questo esempio una forma ha un campo di testo che verrà usato per i commenti dell'utente. Si vuole usare il tipo di carattere di commento standard. Poiché si tratta di un tipo di carattere standard del set di stili, è possibile impostare l'ID carattere predefinito:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Personalizzazioni dinamiche
 Per fare in modo che l'aspetto vari a seconda dello stato di una forma o del relativo elemento del modello, derivare la propria sottoclasse di ed eseguire `TextField` l'override di uno o più `Get...` metodi. È anche necessario eseguire l'override del metodo InitializeShapeFields della forma e sostituire l'istanza di TextField con un'istanza della propria classe.

 Nell'esempio seguente il tipo di carattere di un campo di testo dipende dallo stato di una proprietà di dominio booleana dell'elemento del modello della forma.

 Per eseguire questo codice di esempio, creare una nuova soluzione DSL usando il modello Linguaggio minimo. Aggiungere una proprietà di dominio `AlternateState` booleana alla classe di dominio ExampleElement. Aggiungere un elemento Decorator icona alla classe ExampleShape e impostarne l'immagine su un file bitmap. Fare **clic su Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.

 Per testare il codice, premere F5 e nella soluzione di debug aprire un diagramma di esempio. Verrà visualizzato lo stato predefinito dell'icona. Selezionare la forma e nel Finestra Proprietà modificare il valore della **proprietà AlternateState.** Il tipo di carattere del nome dell'elemento deve cambiare.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Set di stili
 Nell'esempio precedente viene illustrato come modificare il campo di testo con qualsiasi tipo di carattere disponibile. Tuttavia, un metodo preferibile è modificarlo in uno dei set di stili associati alla forma o all'applicazione. A tale scopo, eseguire l'override <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> di o GetTextBrushId().

 In alternativa, provare a modificare il set di stili della forma eseguendo l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Ciò ha l'effetto di modificare i tipi di carattere e i pennelli per tutti i campi forma.

## <a name="customizing-image-fields"></a>Personalizzazione dei campi immagine
 Quando si definisce un elemento Decorator di immagine in una forma e quando si definisce una forma immagine, l'area in cui viene visualizzata la forma viene gestita da un oggetto ImageField. Per esempi di inizializzazione di ImageFields e di altri ShapeField, esaminare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.

 ImageField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un elemento Decorator. Un'istanza di ImageField è condivisa tra molte forme della stessa classe shape. L'istanza ImageField non archivia un'immagine separata per ogni forma: il metodo assume invece la forma come parametro e può cercare l'immagine dipendente dallo stato corrente della forma e dal relativo elemento `GetDisplayImage(ShapeElement)` del modello.

 Se si desidera un comportamento speciale, ad esempio un'immagine variabile, è possibile creare una classe personalizzata derivata da ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Per creare una sottoclasse di ImageField

1. Impostare la **proprietà Generates Double Derived** della classe shape padre nella definizione DSL.

2. Eseguire `InitializeShapeFields` l'override del metodo della classe shape.

    - Creare un nuovo file di codice nel progetto DSL e scrivere una definizione di classe parziale per la classe shape. Eseguire l'override della definizione del metodo.

3. Esaminare il codice di `InitializeShapeFields` in DSL\GeneratedCode\Shapes.cs.

     Nel metodo di override chiamare il metodo di base e quindi creare un'istanza della classe del campo immagine. Usare questa opzione per sostituire il campo immagine normale `shapeFields` nell'elenco.

## <a name="dynamic-icons"></a>Icone dinamiche
 Questo esempio rende una modifica dell'icona dipendente dallo stato dell'elemento del modello della forma.

> [!WARNING]
> Questo esempio illustra come creare un elemento Decorator dinamico dell'immagine. Tuttavia, se si vuole passare solo da una o due immagini a seconda dello stato di una variabile di modello, è più semplice creare diversi elementi Decorator di immagine, individuarli nella stessa posizione della forma e quindi impostare il filtro Visibilità in modo che dipersi da valori specifici della variabile del modello. Per impostare questo filtro, selezionare la mappa delle forme nella definizione DSL, aprire la finestra Dettagli DSL e fare clic sulla scheda Decorator.

 Per eseguire questo codice di esempio, creare una nuova soluzione DSL usando il modello Linguaggio minimo. Aggiungere una proprietà di dominio `AlternateState` booleana alla classe di dominio ExampleElement. Aggiungere un elemento Decorator icona alla classe ExampleShape e impostarne l'immagine su un file bitmap. Fare **clic su Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.

 Per testare il codice, premere F5 e nella soluzione di debug aprire un diagramma di esempio. Verrà visualizzato lo stato predefinito dell'icona. Selezionare la forma e nel Finestra Proprietà modificare il valore della **proprietà AlternateState.** L'icona dovrebbe quindi apparire ruotata di 90 gradi su tale forma.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>Vedi anche

- [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)
- [Impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md)
- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)