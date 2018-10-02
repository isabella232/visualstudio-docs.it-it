---
title: Personalizzazione dei campi testo e immagine | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 125830eed33bd86be983fdc4b48a7c79cf84fa5e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532189"
---
# <a name="customizing-text-and-image-fields"></a>Personalizzazione dei campi testo e immagine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [personalizzazione dei campi testo e immagine](https://docs.microsoft.com/visualstudio/modeling/customizing-text-and-image-fields).  
  
Quando si definisce un elemento decorator di testo in una forma, è rappresentato da un TextField. Per esempi dell'inizializzazione di TextFields e altri ShapeFields, esaminare Dsl\GeneratedCode\Shapes.cs alla soluzione DSL.  
  
 Un TextField non è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un'etichetta. Un'istanza di TextField viene condiviso tra molte forme della stessa classe. L'istanza TextField non archivia il testo dell'etichetta separatamente per ogni istanza: invece di `GetDisplayText(ShapeElement)` assume la forma come parametro di metodo e possibile cercare il testo dipendono dallo stato corrente della forma e il relativo elemento modello.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Come viene determinato l'aspetto di un campo di testo  
 Il `DoPaint()` metodo viene chiamato per consente di visualizzare il campo nella schermata. È ovvero possibile sostituire il valore predefinito `DoPaint(),` oppure è possibile eseguire l'override di alcuni dei metodi chiamati. La seguente versione semplificata dei metodi predefiniti consentono di comprendere come eseguire l'override del comportamento predefinito:  
  
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
  
 Esistono diverse altre coppie di `Get` metodi e `Default` delle proprietà, ad esempio `DefaultMultipleLine/GetMultipleLine()`. È possibile assegnare un valore per la proprietà predefinita per modificare il valore per tutte le istanze del campo della forma. Il valore varia da istanza di una forma a un'altra o dipendenti sullo stato della forma o il relativo elemento modello, eseguire l'override di `Get` (metodo).  
  
## <a name="static-customizations"></a>Personalizzazioni statiche  
 Se si desidera cambiare ogni istanza di questo campo della forma, bisogna innanzitutto sapere se è possibile impostare la proprietà nella definizione DSL. Ad esempio, è possibile impostare la dimensione del carattere e stile di visualizzazione nella finestra Proprietà.  
  
 In caso contrario, quindi eseguire l'override di `InitializeShapeFields` metodo di classe della forma e assegnarle un valore appropriato `Default...` proprietà di campo di testo.  
  
> [!WARNING]
>  Per eseguire l'override `InitializeShapeFields()`, è necessario impostare la **genera una derivata doppia** proprietà della classe di forma a `true` nella definizione DSL.  
  
 In questo esempio, una forma è un campo di testo che verrà usato per i commenti utente. Si vuole usare il tipo di carattere di commento standard. Poiché si tratta di un tipo di carattere standard dal set di stile, è possibile impostare l'id del tipo di carattere predefinito:  
  
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
 Per rendere l'aspetto variano a seconda dello stato di una forma o il relativo elemento modello, derivare una propria sottoclasse di `TextField` ed eseguire l'override di uno o più `Get...` metodi. È anche necessario eseguire l'override di metodo InitializeShapeFields della forma e sostituire l'istanza del campo di testo con un'istanza di una classe personalizzata.  
  
 Nell'esempio seguente fa sì che il tipo di carattere di un campo di testo dipenda lo stato di una proprietà di dominio booleano dell'elemento del modello della forma.  
  
 Per eseguire questo esempio di codice, creare una nuova soluzione DSL usando il modello di linguaggio minimo. Aggiungere una proprietà di dominio booleano `AlternateState` alla classe di dominio ExampleElement. Aggiungere un elemento decorator di icona per la classe ExampleShape e impostare la propria immagine in un file bitmap. Fare clic su **Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.  
  
 Per testare il codice, premere F5 e, nella soluzione di debug, aprire un diagramma di esempio. Dovrebbe essere visualizzato lo stato predefinito dell'icona. Selezionare la forma e nella finestra Proprietà modificare il valore della **AlternateState** proprietà. Il tipo di carattere del nome dell'elemento deve essere modificati.  
  
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
 Nell'esempio precedente viene illustrato come è possibile modificare il campo di testo per qualsiasi tipo di carattere che è disponibile. Tuttavia, un metodo migliore è a modificarlo in un set di stili che è associato con la forma o con l'applicazione. A tale scopo, si esegue l'override <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> o GetTextBrushId().  
  
 In alternativa, provare a modificare il set di stili della forma eseguendo l'override <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Questo ha l'effetto della modifica di tipi di carattere e i pennelli per tutti i campi della forma.  
  
## <a name="customizing-image-fields"></a>Personalizzazione dei campi immagine  
 Quando si definisce un elemento Decorator dell'immagine in una forma e quando si definisce una forma dell'immagine, l'area in cui viene visualizzata la forma è gestito da un ImageField. Per esempi dell'inizializzazione di ImageFields e altri ShapeFields, esaminare Dsl\GeneratedCode\Shapes.cs alla soluzione DSL.  
  
 Un ImageField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un elemento decorator. Un'istanza di ImageField viene condiviso tra molte forme della stessa classe shape. L'istanza di ImageField non archivia un'immagine distinta per ogni forma: invece di `GetDisplayImage(ShapeElement)` assume la forma come parametro di metodo e possibile cercare l'immagine dipendono dallo stato corrente della forma e il relativo elemento modello.  
  
 Se si desidera un comportamento speciale, ad esempio un'immagine di variabili, è possibile creare una classe personalizzata derivata da ImageField.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>Per creare una sottoclasse di ImageField  
  
1.  Impostare il **genera una derivata doppia** proprietà della classe della forma padre nella definizione DSL.  
  
2.  Eseguire l'override di `InitializeShapeFields` metodo della classe della forma.  
  
    -   Creare un nuovo file di codice nel progetto DSL e scrivere una definizione di classe parziale per la classe shape. Sostituire la definizione del metodo non esiste.  
  
3.  Esaminare il codice del `InitializeShapeFields` in DSL\GeneratedCode\Shapes.cs.  
  
     Nel metodo di override, chiamare il metodo di base e quindi creare un'istanza della classe campo immagine. Utilizzare questa opzione per sostituire il campo immagine normale nel `shapeFields` elenco.  
  
## <a name="dynamic-icons"></a>Icone dinamiche  
 In questo esempio fa un'icona Modifica dipenda lo stato dell'elemento del modello della forma.  
  
> [!WARNING]
>  In questo esempio viene illustrato come effettuare un elemento Decorator dell'immagine dinamica. Ma se vuoi solo passare da una o due immagini a seconda dello stato di una variabile del modello, risulta più semplice creare alcuni elementi Decorator di immagine, essi posizionati nella stessa posizione della forma e quindi impostare il filtro di visibilità per dipendono da valori specifici del modello variabile. Per impostare il filtro selezionato, selezionare la mappa della forma nella definizione DSL, aprire la finestra Dettagli DSL e scegliere la scheda elementi Decorator.  
  
 Per eseguire questo esempio di codice, creare una nuova soluzione DSL usando il modello di linguaggio minimo. Aggiungere una proprietà di dominio booleano `AlternateState` alla classe di dominio ExampleElement. Aggiungere un elemento decorator di icona per la classe ExampleShape e impostare la propria immagine in un file bitmap. Fare clic su **Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.  
  
 Per testare il codice, premere F5 e, nella soluzione di debug, aprire un diagramma di esempio. Dovrebbe essere visualizzato lo stato predefinito dell'icona. Selezionare la forma e nella finestra Proprietà modificare il valore della **AlternateState** proprietà. L'icona viene visualizzata ruotata tramite 90 gradi, in tale forma.  
  
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
 [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)   
 [Impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)



