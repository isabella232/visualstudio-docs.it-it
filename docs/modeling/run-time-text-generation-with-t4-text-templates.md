---
title: Generazione di testo in fase di esecuzione con modelli di testo T4
description: Informazioni su come generare stringhe di testo nell'applicazione in fase di esecuzione usando Visual Studio di testo di runtime.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0599c7739388b44bcbb0c6413a0ee4213ecd3797
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040086"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generazione di testo in fase di esecuzione con modelli di testo T4

È possibile generare stringhe di testo nell'applicazione in fase di esecuzione usando Visual Studio di testo di runtime. Il computer in cui viene eseguita l'applicazione non deve avere Visual Studio. I modelli di runtime vengono talvolta chiamati "modelli di testo pre-elaborato" perché in fase di compilazione il modello genera codice che viene eseguito in fase di esecuzione.

Ogni modello è una combinazione del testo così come verrà visualizzato nella stringa generata e dei frammenti di codice del programma. I frammenti di programma forniscono valori per le parti variabili della stringa e controllano anche le parti condizionali e ripetute.

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

Si noti che il modello è una pagina HTML in cui le parti delle variabili sono state sostituite con il codice del programma. È possibile iniziare la progettazione di una pagina di questo tipo scrivendo un prototipo statico della pagina HTML. È quindi possibile sostituire la tabella e altre parti variabili con codice programma che genera il contenuto che varia da un'occasione all'altra.

L'uso di un modello nell'applicazione semplifica la visualizzazione della forma finale dell'output rispetto a quanto è possibile in, ad esempio, in una lunga serie di istruzioni di scrittura. Apportare modifiche alla forma dell'output è più semplice e affidabile.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Creazione di un Run-Time di testo in qualsiasi applicazione

### <a name="to-create-a-run-time-text-template"></a>Per creare un modello di testo di run-time

1. Nel Esplora soluzioni scegliere Aggiungi nuovo elemento dal menu di scelta  >  **rapida del progetto.**

2. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Modello di testo **runtime**. (In Visual Basic in **Elementi comuni**  >  **Generale**.)

3. Digitare un nome per il file modello.

    > [!NOTE]
    > Il nome del file modello verrà usato come nome di classe nel codice generato. Pertanto, non deve contenere spazi o punteggiatura.

4. Scegliere **Aggiungi**.

    Viene creato un nuovo file con estensione **tt**. La **proprietà Strumento** personalizzato è impostata su **TextTemplatingFilePreprocessor.** Contiene le righe seguenti:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Conversione di un file esistente in un modello Run-Time dati

Un buon modo per creare un modello è convertire un esempio esistente dell'output. Ad esempio, se l'applicazione genererà file HTML, è possibile iniziare creando un file HTML normale. Assicurarsi che funzioni correttamente e che il relativo aspetto sia corretto. Includerlo quindi nel progetto Visual Studio e convertirlo in un modello.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Per convertire un file di testo esistente in un modello di run-time

1. Includere il file nel progetto Visual Studio progetto. Nel Esplora soluzioni scegliere Aggiungi elemento esistente dal menu di scelta  >  **rapida del progetto.**

2. Impostare la proprietà **Strumenti** personalizzati del file su **TextTemplatingFilePreprocessor**. Nel Esplora soluzioni scegliere Proprietà dal menu di scelta **rapida del** file.

    > [!NOTE]
    > Se la proprietà è già impostata, assicurarsi che sia **TextTemplatingFilePreprocessor** e non **TextTemplatingFileGenerator**. Questo problema può verificarsi se si include un file che ha già l'estensione **.tt**.

3. Modificare l'estensione del nome file **in .tt**. Anche se questo passaggio è facoltativo, consente di evitare di aprire il file in un editor non corretto.

4. Rimuovere eventuali spazi o punteggiatura dalla parte principale del nome file. Ad esempio, "My Web Page.tt" non sarebbe corretto, ma "MyWebPage.tt" è corretto. Il nome file verrà usato come nome di classe nel codice generato.

5. Inserire la riga seguente all'inizio del file. Se si lavora in un progetto Visual Basic, sostituire "C#" con "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Contenuto del modello Run-Time dati

### <a name="template-directive"></a>Direttiva del modello

Mantenere la prima riga del modello così come era al momento della creazione del file:

`<#@ template language="C#" #>`

Il parametro language dipende dal linguaggio del progetto.

### <a name="plain-content"></a>Contenuto normale

Modificare il file **con estensione tt** in modo che contenga il testo che deve essere generato dall'applicazione. Esempio:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Codice programma incorporato

È possibile inserire il codice del programma tra `<#` e `#>` . Esempio:

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

Si noti che le istruzioni vengono inserite tra `<# ... #>` le espressioni e tra `<#= ... #>` . Per altre informazioni, vedere [Scrittura di un modello di testo T4.](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-template"></a>Uso del modello

### <a name="the-code-built-from-the-template"></a>Codice compilato dal modello

Quando si salva il file **con estensione tt,** viene generato un file **cs** o **vb** sussidiaria. Per visualizzare questo file in **Esplora soluzioni**, espandere il nodo del file con estensione **tt.** In un Visual Basic progetto, scegliere mostra tutti i **file** nella barra Esplora soluzioni barra **degli** strumenti.

Si noti che il file sussidiaria contiene una classe parziale che contiene un metodo denominato `TransformText()` . È possibile chiamare questo metodo dall'applicazione.

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

Per inserire la classe generata in uno spazio dei nomi specifico, impostare la **proprietà Spazio** dei nomi dello strumento personalizzato del file modello di testo.

### <a name="debugging-runtime-text-templates"></a>Debug di modelli di testo di runtime

Eseguire il debug e il test dei modelli di testo di runtime nello stesso modo del codice normale.

È possibile impostare un punto di interruzione in un modello di testo. Se si avvia l'applicazione in modalità di debug da Visual Studio, è possibile esaminare il codice e valutare le espressioni di controllo nel modo consueto.

### <a name="passing-parameters-in-the-constructor"></a>Passaggio di parametri nel costruttore

In genere un modello deve importare alcuni dati da altre parti dell'applicazione. Per semplificare questa operazione, il codice compilato dal modello è una classe parziale. È possibile creare un'altra parte della stessa classe in un altro file del progetto. Tale file può includere un costruttore con parametri, proprietà e funzioni accessibili sia dal codice incorporato nel modello che dal resto dell'applicazione.

Ad esempio, è possibile creare un file separato **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

Nel file modello **MyWebPage.tt** scrivere:

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

In Visual Basic il file separato **MyWebPageCode.vb** contiene:

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

Il file modello può contenere:

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

Il modello può essere richiamato passando il parametro nel costruttore :

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Passaggio di dati nelle proprietà del modello

Un modo alternativo per passare dati al modello consiste nell'aggiungere proprietà pubbliche alla classe modello in una definizione di classe parziale. L'applicazione può impostare le proprietà prima di richiamare `TransformText()` .

È anche possibile aggiungere campi alla classe modello in una definizione parziale. In questo modo è possibile passare dati tra esecuzioni successive del modello.

### <a name="use-partial-classes-for-code"></a>Usare classi parziali per il codice

Molti sviluppatori preferiscono evitare di scrivere grandi quantità di codice nei modelli. È invece possibile definire metodi in una classe parziale con lo stesso nome del file modello. Chiamare questi metodi dal modello. In questo modo, il modello mostra più chiaramente l'aspetto della stringa di output di destinazione. Le discussioni sull'aspetto del risultato possono essere separate dalla logica di creazione dei dati visualizzati.

### <a name="assemblies-and-references"></a>Assembly e riferimenti

Se si vuole che il codice del modello faccia riferimento a un assembly .NET  o a un altro **assembly, ad** esempioSystem.Xml.dll, aggiungerlo ai riferimenti del progetto nel modo consueto.

Se si vuole importare uno spazio dei nomi nello stesso modo di un'istruzione , è possibile eseguire questa operazione `using` con la `import` direttiva :

```
<#@ import namespace="System.Xml" #>
```

Queste direttive devono essere inserite all'inizio del file, immediatamente dopo la `<#@template` direttiva .

### <a name="shared-content"></a>Contenuto condiviso

Se si dispone di testo condiviso tra diversi modelli, è possibile posizionarlo in un file separato e includerlo in ogni file in cui dovrebbe essere visualizzato:

```
<#@include file="CommonHeader.txt" #>
```

Il contenuto incluso può contenere qualsiasi combinazione di codice programma e testo normale e può contenere altre direttive include e altre direttive .

La direttiva include può essere usata in qualsiasi punto all'interno del testo di un file modello o di un file incluso.

### <a name="inheritance-between-run-time-text-templates"></a>Ereditarietà tra Run-Time di testo

È possibile condividere il contenuto tra modelli di run-time scrivendo un modello di classe di base, che può essere astratto. Usare il `inherits` parametro della direttiva per fare riferimento a `<@#template#>` un'altra classe modello di runtime.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Modello di ereditarietà: frammenti nei metodi di base

Nel modello usato nell'esempio seguente si notino i punti seguenti:

- La classe di base `SharedFragments` definisce i metodi all'interno dei blocchi di funzionalità della classe `<#+ ... #>` .

- La classe base non contiene testo libero. Al contrario, tutti i blocchi di testo si verificano all'interno dei metodi di funzionalità della classe .

- La classe derivata richiama i metodi definiti in `SharedFragments` .

- L'applicazione chiama `TextTransform()` il metodo della classe derivata, ma non trasforma la classe base `SharedFragments` .

- Sia la classe di base che le classi derivate sono modelli di testo di runtime. ciò significa che la **proprietà Strumento** personalizzato è impostata su **TextTemplatingFilePreprocessor.**

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

In questo approccio alternativo all'uso dell'ereditarietà del modello, la maggior parte del testo è definita nel modello di base. I modelli derivati forniscono frammenti di dati e di testo che rientrano nel contenuto di base.

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

Modelli in fase di progettazione: se si vuole usare un modello per generare codice che diventa parte dell'applicazione, vedere Generazione di codice in fase di progettazione tramite modelli [di testo T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

I modelli di run-time possono essere usati in qualsiasi applicazione in cui i modelli e il relativo contenuto vengono determinati in fase di compilazione. Se tuttavia si vuole scrivere un'estensione Visual Studio che genera testo da modelli che cambiano in fase di esecuzione, vedere Richiamo della trasformazione testo [in un'estensione di Visual Studio.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

## <a name="see-also"></a>Vedi anche

- [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)
- [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)
- [Casella degli strumenti T4](http://olegsych.com/T4Toolbox/)
