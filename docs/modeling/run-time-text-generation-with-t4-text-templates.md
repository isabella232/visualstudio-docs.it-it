---
title: Generazione di testo in fase di esecuzione con modelli di testo T4
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1ee422ec549ced0995db22258edf9ef21540804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660303"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generazione di testo in fase di esecuzione con modelli di testo T4

È possibile generare stringhe di testo nell'applicazione in fase di esecuzione usando i modelli di testo di runtime di Visual Studio. Il computer in cui viene eseguita l'applicazione non deve avere Visual Studio. I modelli di runtime sono talvolta denominati "modelli di testo pre-elaborati" perché in fase di compilazione il modello genera il codice che viene eseguito in fase di esecuzione.

Ogni modello è una combinazione del testo che verrà visualizzato nella stringa generata e frammenti del codice programma. I frammenti di programma forniscono valori per le parti variabili della stringa e controllano anche le parti condizionali e ripetute.

Ad esempio, il modello seguente può essere usato in un'applicazione che crea un report HTML.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Si noti che il modello è una pagina HTML in cui le parti variabili sono state sostituite con codice programma. È possibile iniziare la progettazione di tale pagina scrivendo un prototipo statico della pagina HTML. È quindi possibile sostituire la tabella e altre parti variabili con il codice programma che genera il contenuto che varia da un'occasione all'altra.

L'uso di un modello nell'applicazione rende più semplice la visualizzazione del formato finale dell'output, ad esempio una serie di istruzioni Write lunghe. Apportare modifiche al modulo dell'output è più semplice e più affidabile.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Creazione di un modello di testo in fase di esecuzione in qualsiasi applicazione

### <a name="to-create-a-run-time-text-template"></a>Per creare un modello di testo in fase di esecuzione

1. In Esplora soluzioni scegliere **aggiungi**  > **nuovo elemento**dal menu di scelta rapida del progetto.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **modello di testo runtime**. In Visual Basic esaminare **gli elementi comuni**  > **generale**).

3. Digitare un nome per il file modello.

    > [!NOTE]
    > Il nome del file modello verrà utilizzato come nome di classe nel codice generato. Pertanto, non deve contenere spazi o segni di punteggiatura.

4. Scegliere **Aggiungi**.

    Viene creato un nuovo file con estensione **TT**. La proprietà **strumento personalizzato** è impostata su **TextTemplatingFilePreprocessor**. Contiene le righe seguenti:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Conversione di un file esistente in un modello in fase di esecuzione

Un modo efficace per creare un modello consiste nel convertire un esempio esistente di output. Se, ad esempio, l'applicazione genera file HTML, è possibile iniziare creando un file HTML normale. Verificare che funzioni correttamente e che l'aspetto sia corretto. Quindi includerlo nel progetto di Visual Studio e convertirlo in un modello.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Per convertire un file di testo esistente in un modello in fase di esecuzione

1. Includere il file nel progetto di Visual Studio. In Esplora soluzioni scegliere **aggiungi**  > **elemento esistente**dal menu di scelta rapida del progetto.

2. Impostare la proprietà **strumenti personalizzati** del file su **TextTemplatingFilePreprocessor**. In Esplora soluzioni scegliere **Proprietà**dal menu di scelta rapida del file.

    > [!NOTE]
    > Se la proprietà è già impostata, verificare che sia **TextTemplatingFilePreprocessor** e non **TextTemplatingFileGenerator**. Questo problema può verificarsi se si include un file che ha già l'estensione **TT**.

3. Modificare l'estensione del nome file in **. TT**. Sebbene questo passaggio sia facoltativo, consente di evitare l'apertura del file in un editor errato.

4. Rimuovere spazi o punteggiatura dalla parte principale del nome file. "My Web Page.tt", ad esempio, non è corretto, ma "MyWebPage.tt" è corretto. Il nome del file verrà utilizzato come nome di classe nel codice generato.

5. Inserire la riga seguente all'inizio del file. Se si utilizza un progetto di Visual Basic, sostituire "C#" con "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Contenuto del modello in fase di esecuzione

### <a name="template-directive"></a>Template (direttiva)

Conserva la prima riga del modello così com'era quando è stato creato il file:

`<#@ template language="C#" #>`

Il parametro Language dipenderà dalla lingua del progetto.

### <a name="plain-content"></a>Contenuto normale

Modificare il file con **estensione TT** in modo che contenga il testo che si desidera venga generato dall'applicazione. Esempio:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Codice programma incorporato

È possibile inserire il codice programma tra `<#` e `#>`. Esempio:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Si noti che le istruzioni vengono inserite tra `<# ... #>` e le espressioni vengono inserite tra `<#= ... #>`. Per altre informazioni, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Uso del modello

### <a name="the-code-built-from-the-template"></a>Codice compilato dal modello

Quando si salva il file con **estensione TT** , viene generato un file sussidiario con estensione **CS** o **VB** . Per visualizzare questo file in **Esplora soluzioni**, espandere il nodo del file con **estensione TT** . In un progetto Visual Basic scegliere **Mostra tutti i file** nella barra degli strumenti **Esplora soluzioni** .

Si noti che il file sussidiario contiene una classe parziale che contiene un metodo denominato `TransformText()`. È possibile chiamare questo metodo dall'applicazione.

### <a name="generating-text-at-run-time"></a>Generazione di testo in fase di esecuzione

Nel codice dell'applicazione è possibile generare il contenuto del modello usando una chiamata simile alla seguente:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Per inserire la classe generata in un determinato spazio dei nomi, impostare la proprietà **spazio dei nomi dello strumento personalizzato** del file del modello di testo.

### <a name="debugging-runtime-text-templates"></a>Debug di modelli di testo di runtime

Eseguire il debug e testare i modelli di testo in fase di esecuzione in modo analogo al codice ordinario.

È possibile impostare un punto di interruzione in un modello di testo. Se l'applicazione viene avviata in modalità di debug da Visual Studio, è possibile eseguire il codice un'istruzione alla volta e valutare le espressioni Watch nel modo consueto.

### <a name="passing-parameters-in-the-constructor"></a>Passaggio di parametri nel costruttore

In genere, un modello deve importare alcuni dati da altre parti dell'applicazione. Per semplificare questa operazione, il codice creato dal modello è una classe parziale. È possibile creare un'altra parte della stessa classe in un altro file del progetto. Tale file può includere un costruttore con parametri, proprietà e funzioni a cui è possibile accedere sia dal codice incorporato nel modello che dal resto dell'applicazione.

Ad esempio, è possibile creare un file separato **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

Nel file di modello **mywebpage.TT**, è possibile scrivere:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Per usare questo modello nell'applicazione:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Parametri del costruttore in Visual Basic

In Visual Basic, il file separato **MyWebPageCode. vb** contiene:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Il file modello potrebbe contenere:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Il modello può essere richiamato passando il parametro nel costruttore:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Passaggio di dati nelle proprietà del modello

Un metodo alternativo per passare dati al modello consiste nell'aggiungere proprietà pubbliche alla classe modello in una definizione di classe parziale. L'applicazione può impostare le proprietà prima di richiamare `TransformText()`.

È anche possibile aggiungere campi alla classe modello in una definizione parziale. In questo modo è possibile passare i dati tra le esecuzioni successive del modello.

### <a name="use-partial-classes-for-code"></a>Usare classi parziali per il codice

Molti sviluppatori preferiscono evitare di scrivere corpi di codice di grandi dimensioni nei modelli. È invece possibile definire metodi in una classe parziale con lo stesso nome del file modello. Chiamare tali metodi dal modello. In questo modo, il modello Mostra più chiaramente come sarà la stringa di output di destinazione. Le discussioni sull'aspetto del risultato possono essere separate dalla logica di creazione dei dati visualizzati.

### <a name="assemblies-and-references"></a>Assembly e riferimenti

Se si vuole che il codice del modello faccia riferimento a .NET o ad altri assembly, ad esempio **System. XML. dll**, aggiungerlo ai **riferimenti** del progetto nel modo consueto.

Se si desidera importare uno spazio dei nomi allo stesso modo di un'istruzione `using`, è possibile eseguire questa operazione con la direttiva `import`:

```
<#@ import namespace="System.Xml" #>
```

Queste direttive devono essere inserite all'inizio del file immediatamente dopo la direttiva `<#@template`.

### <a name="shared-content"></a>Contenuto condiviso

Se si dispone di testo condiviso tra più modelli, è possibile inserirlo in un file separato e includerlo in ogni file in cui deve essere visualizzato:

```
<#@include file="CommonHeader.txt" #>
```

Il contenuto incluso può contenere qualsiasi combinazione di codice programma e testo normale e può contenere altre direttive di inclusione e altre direttive.

La direttiva include può essere utilizzata in qualsiasi punto all'interno del testo di un file modello o di un file incluso.

### <a name="inheritance-between-run-time-text-templates"></a>Ereditarietà tra modelli di testo in fase di esecuzione

È possibile condividere contenuto tra modelli di runtime scrivendo un modello di classe base, che può essere astratto. Usare il parametro `inherits` della direttiva `<@#template#>` per fare riferimento a un'altra classe modello di Runtime.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Modello di ereditarietà: frammenti nei metodi di base

Nel modello usato nell'esempio seguente si notino i punti seguenti:

- La classe di base `SharedFragments` definisce i metodi all'interno dei blocchi di funzionalità della classe `<#+ ... #>`.

- La classe base non contiene testo libero. Al contrario, tutti i relativi blocchi di testo si verificano all'interno dei metodi della funzionalità della classe.

- La classe derivata richiama i metodi definiti in `SharedFragments`.

- L'applicazione chiama il metodo `TextTransform()` della classe derivata, ma non trasforma la classe di base `SharedFragments`.

- Entrambe le classi base e derivate sono modelli di testo di runtime; ovvero la proprietà **strumento personalizzato** è impostata su **TextTemplatingFilePreprocessor**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Output risultante:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Modello di ereditarietà: testo nel corpo di base

In questo approccio alternativo all'utilizzo dell'ereditarietà dei modelli, la maggior parte del testo viene definita nel modello di base. I modelli derivati forniscono frammenti di dati e di testo che rientrano nel contenuto di base.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Codice dell'applicazione:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Output risultante:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Argomenti correlati

Modelli della fase di progettazione: se si vuole usare un modello per generare codice che diventa parte dell'applicazione, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

I modelli in fase di esecuzione possono essere utilizzati in qualsiasi applicazione in cui i modelli e il relativo contenuto vengono determinati in fase di compilazione. Tuttavia, se si vuole scrivere un'estensione di Visual Studio che genera testo da modelli che cambiano in fase di esecuzione, vedere [richiamo della trasformazione del testo in un'estensione vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Vedere anche

- [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)
- [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)
- [Casella degli strumenti T4](http://olegsych.com/T4Toolbox/)
