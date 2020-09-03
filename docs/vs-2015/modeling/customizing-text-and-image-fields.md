---
title: Personalizzazione dei campi testo e immagine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6baaa9ceba8f40aa5ad7888384027131e0ffe94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654979"
---
# <a name="customizing-text-and-image-fields"></a>Personalizzazione dei campi testo e immagine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si definisce un elemento Decorator di testo in una forma, questo viene rappresentato da un TextField. Per esempi di inizializzazione di TextField e altri ShapeField, controllare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.

 Un TextField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un'etichetta. Un'istanza di TextField è condivisa tra molte forme della stessa classe. L'istanza di TextField non archivia il testo dell'etichetta separatamente per ogni istanza: il `GetDisplayText(ShapeElement)` metodo accetta la forma come parametro e può cercare il testo che dipende dallo stato corrente della forma e del relativo elemento del modello.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Determinazione dell'aspetto di un campo di testo
 Il `DoPaint()` metodo viene chiamato per visualizzare il campo sullo schermo. È possibile eseguire l'override dell'impostazione predefinita `DoPaint(),` oppure è possibile eseguire l'override di alcuni dei metodi chiamati. La versione semplificata seguente dei metodi predefiniti può essere utile per comprendere come eseguire l'override del comportamento predefinito:

```
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
// To change the brush for every field, change the shape’s styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application’s styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape’s styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application’s styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }

```

 Sono disponibili diverse altre coppie di `Get` metodi e `Default` proprietà, ad esempio `DefaultMultipleLine/GetMultipleLine()` . È possibile assegnare un valore alla proprietà predefinita per modificare il valore di tutte le istanze del campo della forma. Per fare in modo che il valore sia diverso da un'istanza di forma a un'altra o che dipenda dallo stato della forma o del relativo elemento del modello, eseguire l'override del `Get` metodo.

## <a name="static-customizations"></a>Personalizzazioni statiche
 Se si desidera modificare ogni istanza di questo campo della forma, verificare innanzitutto se è possibile impostare la proprietà nella definizione DSL. È ad esempio possibile impostare la dimensione e lo stile del carattere nel Finestra Proprietà.

 In caso contrario, eseguire l'override del `InitializeShapeFields` metodo della classe Shape e assegnare un valore alla proprietà appropriata `Default...` del campo di testo.

> [!WARNING]
> Per eseguire l'override di `InitializeShapeFields()` , è necessario impostare la proprietà **generata doppia derivata** della classe Shape su `true` nella definizione DSL.

 In questo esempio, una forma include un campo di testo che verrà usato per i commenti degli utenti. Si vuole usare il tipo di carattere standard per i commenti. Poiché si tratta di un tipo di carattere standard del set di stili, è possibile impostare l'ID del tipo di carattere predefinito:

```

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
 Per rendere l'aspetto variabile a seconda dello stato di una forma o del relativo elemento del modello, derivare la propria sottoclasse di `TextField` ed eseguire l'override di uno o più `Get...` metodi. È anche necessario eseguire l'override del Metodo InitializeShapeFields della forma e sostituire l'istanza del TextField con un'istanza della propria classe.

 Nell'esempio seguente il tipo di carattere di un campo di testo dipende dallo stato di una proprietà di dominio booleano dell'elemento del modello della forma.

 Per eseguire questo esempio di codice, creare una nuova soluzione DSL usando il modello di linguaggio minimo. Aggiungere una proprietà di dominio booleano `AlternateState` alla classe di dominio ExampleElement. Aggiungere un elemento Decorator Icon alla classe ExampleShape e impostarne l'immagine su un file bitmap. Fare clic su **trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.

 Per testare il codice, premere F5 e, nella soluzione di debug, aprire un diagramma di esempio. Verrà visualizzato lo stato predefinito dell'icona. Selezionare la forma e nella Finestra Proprietà modificare il valore della proprietà **AlternateState** . Il tipo di carattere del nome dell'elemento deve essere modificato.

```
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
 Nell'esempio precedente viene illustrato come è possibile modificare il campo di testo in qualsiasi tipo di carattere disponibile. Tuttavia, un metodo preferibile consiste nel modificarlo in uno di un set di stili associato alla forma o all'applicazione. A tale scopo, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> o GetTextBrushId ().

 In alternativa, è consigliabile modificare il set di stili della forma eseguendo l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Questo ha l'effetto di modificare i tipi di carattere e i pennelli per tutti i campi della forma.

## <a name="customizing-image-fields"></a>Personalizzazione dei campi immagine
 Quando si definisce un elemento Decorator immagine in una forma e quando si definisce una forma immagine, l'area in cui viene visualizzata la forma viene gestita da un ImageField. Per esempi di inizializzazione di ImageField e altri ShapeField, controllare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.

 ImageField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un elemento Decorator. Un'istanza ImageField viene condivisa tra molte forme della stessa classe Shape. L'istanza ImageField non archivia un'immagine separata per ogni forma: al contrario, il `GetDisplayImage(ShapeElement)` metodo accetta la forma come parametro e può cercare l'immagine a seconda dello stato corrente della forma e del relativo elemento del modello.

 Se si desidera un comportamento speciale, ad esempio un'immagine di variabile, è possibile creare una classe derivata da ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Per creare una sottoclasse di ImageField

1. Impostare la proprietà **generata Double derivata** della classe della forma padre nella definizione DSL.

2. Eseguire l'override del `InitializeShapeFields` metodo della classe Shape.

    - Creare un nuovo file di codice nel progetto DSL e scrivere una definizione di classe parziale per la classe Shape. Eseguire l'override della definizione del metodo.

3. Esaminare il codice di `InitializeShapeFields` in DSL\GeneratedCode\Shapes.cs.

     Nel metodo di override chiamare il metodo di base e quindi creare un'istanza della classe del campo Image personalizzata. Utilizzare questo oggetto per sostituire il campo dell'immagine normale nell' `shapeFields` elenco.

## <a name="dynamic-icons"></a>Icone dinamiche
 Questo esempio rende una modifica dell'icona dipendente dallo stato dell'elemento del modello della forma.

> [!WARNING]
> Questo esempio illustra come creare un elemento Decorator immagine dinamica. Tuttavia, se si desidera passare da una o due immagini a seconda dello stato di una variabile di modello, è più semplice creare diversi elementi Decorator di immagini, individuarli nella stessa posizione sulla forma e quindi impostare il filtro di visibilità in modo che dipenda da valori specifici della variabile del modello. Per impostare questo filtro, selezionare il mapping di forme nella definizione DSL, aprire la finestra Dettagli DSL, quindi fare clic sulla scheda elementi Decorator.

 Per eseguire questo esempio di codice, creare una nuova soluzione DSL usando il modello di linguaggio minimo. Aggiungere una proprietà di dominio booleano `AlternateState` alla classe di dominio ExampleElement. Aggiungere un elemento Decorator Icon alla classe ExampleShape e impostarne l'immagine su un file bitmap. Fare clic su **trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.

 Per testare il codice, premere F5 e, nella soluzione di debug, aprire un diagramma di esempio. Verrà visualizzato lo stato predefinito dell'icona. Selezionare la forma e nella Finestra Proprietà modificare il valore della proprietà **AlternateState** . L'icona deve quindi essere visualizzata ruotata fino a 90 gradi, su tale forma.

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

## <a name="see-also"></a>Vedere anche
 [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md) [impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md) [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md) [scrittura di codice per personalizzare un Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md)
