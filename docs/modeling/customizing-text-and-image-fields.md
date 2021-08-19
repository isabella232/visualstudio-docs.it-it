---
title: Personalizzazione dei campi testo e immagine
description: Informazioni sulla personalizzazione di file di testo e di immagine. Si apprenderà anche che quando si definisce un elemento Decorator di testo in una forma, questo è rappresentato da un oggetto TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 13cde2406402f6afc2d61deca4e6e95e838e5dff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085637"
---
# <a name="customizing-text-and-image-fields"></a>Personalizzazione dei campi testo e immagine
Quando si definisce un elemento Decorator di testo in una forma, questo viene rappresentato da un oggetto TextField. Per esempi di inizializzazione di TextFields e di altri oggetti ShapeField, esaminare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.

 TextField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un'etichetta. Un'istanza TextField è condivisa tra molte forme della stessa classe. L'istanza TextField non archivia separatamente il testo dell'etichetta per ogni istanza: il metodo accetta la forma come parametro e può cercare il testo dipendente dallo stato corrente della forma e dal relativo elemento del `GetDisplayText(ShapeElement)` modello.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Come viene determinato l'aspetto di un campo di testo
 Il `DoPaint()` metodo viene chiamato per visualizzare il campo sullo schermo. È possibile eseguire l'override `DoPaint(),` del valore predefinito oppure eseguire l'override di alcuni dei metodi che chiama. La versione semplificata seguente dei metodi predefiniti consente di comprendere come eseguire l'override del comportamento predefinito:

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

 Esistono diverse altre coppie di `Get` metodi e `Default` proprietà, ad esempio `DefaultMultipleLine/GetMultipleLine()` . È possibile assegnare un valore alla proprietà Default per modificare il valore per tutte le istanze del campo della forma. Per fare in modo che il valore vari da un'istanza della forma a un'altra o che dipende dallo stato della forma o dal relativo elemento del modello, eseguire l'override del `Get` metodo .

## <a name="static-customizations"></a>Personalizzazioni statiche
 Se si vuole modificare ogni istanza di questo campo della forma, verificare prima di tutto se è possibile impostare la proprietà nella definizione DSL. Ad esempio, è possibile impostare le dimensioni e lo stile del carattere nel Finestra Proprietà.

 In caso contrario, eseguire l'override del metodo della classe shape e assegnare un valore `InitializeShapeFields` alla proprietà appropriata del campo di `Default...` testo.

> [!WARNING]
> Per eseguire l'override di , è necessario impostare la proprietà `InitializeShapeFields()` **Generates Double Derived** della classe shape su nella `true` definizione DSL.

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

 Per eseguire questo codice di esempio, creare una nuova soluzione DSL usando il modello Linguaggio minimo. Aggiungere una proprietà di dominio `AlternateState` booleana alla classe di dominio ExampleElement. Aggiungere un elemento Decorator dell'icona alla classe ExampleShape e impostarne l'immagine su un file bitmap. Fare clic **su Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.

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
 Nell'esempio precedente viene illustrato come modificare il campo di testo in qualsiasi tipo di carattere disponibile. Tuttavia, un metodo preferibile è modificarlo in uno di un set di stili associato alla forma o all'applicazione. A tale scopo, eseguire l'override <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> di o GetTextBrushId().

 In alternativa, provare a modificare il set di stili della forma eseguendo l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Ciò ha l'effetto di modificare i tipi di carattere e i pennelli per tutti i campi della forma.

## <a name="customizing-image-fields"></a>Personalizzazione dei campi immagine
 Quando si definisce un elemento Decorator dell'immagine in una forma e quando si definisce una forma immagine, l'area in cui viene visualizzata la forma viene gestita da un imageField. Per esempi di inizializzazione di ImageFields e di altri oggetti ShapeField, esaminare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.

 ImageField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un elemento Decorator. Un'istanza di ImageField è condivisa tra molte forme della stessa classe shape. L'istanza ImageField non archivia un'immagine separata per ogni forma: il metodo assume invece la forma come parametro e può cercare l'immagine in base allo stato corrente della forma e al relativo elemento del `GetDisplayImage(ShapeElement)` modello.

 Se si vuole un comportamento speciale, ad esempio un'immagine di variabile, è possibile creare una classe personalizzata derivata da ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Per creare una sottoclasse di ImageField

1. Impostare la **proprietà Generates Double Derived** della classe shape padre nella definizione DSL.

2. Eseguire `InitializeShapeFields` l'override del metodo della classe shape.

    - Creare un nuovo file di codice nel progetto DSL e scrivere una definizione di classe parziale per la classe shape. Eseguire l'override della definizione del metodo.

3. Esaminare il codice di `InitializeShapeFields` in DSL\GeneratedCode\Shapes.cs.

     Nel metodo di override chiamare il metodo di base e quindi creare un'istanza della classe del campo immagine. Usare questa opzione per sostituire il campo immagine normale `shapeFields` nell'elenco.

## <a name="dynamic-icons"></a>Icone dinamiche
 Questo esempio rende una modifica dell'icona dipendente dallo stato dell'elemento del modello della forma.

> [!WARNING]
> In questo esempio viene illustrato come creare un elemento Decorator dinamico dell'immagine. Tuttavia, se si vuole passare solo da una o due immagini a seconda dello stato di una variabile del modello, è più semplice creare più elementi Decorator immagine, individuarli nella stessa posizione nella forma e quindi impostare il filtro Visibilità in modo che dipersi da valori specifici della variabile del modello. Per impostare questo filtro, selezionare la mappa delle forme nella definizione DSL, aprire la finestra Dettagli DSL e fare clic sulla scheda Decorator.

 Per eseguire questo codice di esempio, creare una nuova soluzione DSL usando il modello Linguaggio minimo. Aggiungere una proprietà di dominio `AlternateState` booleana alla classe di dominio ExampleElement. Aggiungere un elemento Decorator dell'icona alla classe ExampleShape e impostarne l'immagine su un file bitmap. Fare clic **su Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.

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