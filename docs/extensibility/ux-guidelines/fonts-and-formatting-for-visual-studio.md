---
title: Tipi di carattere e formattazione per Visual Studio | Microsoft Docs
description: Informazioni sui tipi di carattere e sulla formattazione per le nuove funzionalità Visual Studio, incluso come usare il tipo di carattere dell'ambiente.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 98c1b58fe3d06e9ea9c9e85679b13a0cfdb50ce2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102103"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Tipi di carattere e formattazione per Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Tipo di carattere dell'ambiente
 Tutti i tipi di carattere Visual Studio devono essere esposti all'utente per la personalizzazione. Questa operazione viene eseguita principalmente tramite la **pagina Tipi di** carattere e colori nella finestra di dialogo > **opzioni.** Le tre categorie principali di impostazioni dei tipi di carattere sono:

- **Tipo di carattere** ambiente: tipo di carattere principale per l'IDE (ambiente di sviluppo integrato), usato per tutti gli elementi dell'interfaccia, tra cui finestre di dialogo, menu, finestre degli strumenti e finestre dei documenti. Per impostazione predefinita, il tipo di carattere dell'ambiente è associato a un tipo di carattere di sistema visualizzato come 9 pt Segoe UI nelle versioni correnti di Windows. L'uso di un solo tipo di carattere per tutti gli elementi dell'interfaccia consente di garantire un aspetto coerente del tipo di carattere in tutto l'IDE.

- **Editor di** testo: gli elementi presenti nel codice e in altri editor basati su testo possono essere personalizzati nella pagina Editor di testo in Strumenti **> Opzioni**.

- **Raccolte specifiche:** le finestre di progettazione che offrono all'utente la **personalizzazione** degli elementi dell'interfaccia possono esporre tipi di carattere specifici dell'area di progettazione nella propria pagina delle impostazioni in Strumenti > opzioni .

### <a name="editor-font-customization-and-resizing"></a>Personalizzazione e ridimensionamento dei tipi di carattere dell'editor
 Spesso gli utenti ingrandisce o ingrandisce le dimensioni e/o il colore del testo nell'editor in base alle proprie preferenze, indipendentemente dall'interfaccia utente generale. Poiché il tipo di carattere dell'ambiente viene usato in elementi che potrebbero essere presenti all'interno o come parte di un editor/finestra di progettazione, è importante notare il comportamento previsto quando viene modificata una di queste classificazioni dei tipi di carattere.

 Quando si creano elementi dell'interfaccia utente visualizzati nell'editor ma non fanno parte del contenuto *,* è importante usare il tipo di carattere ambiente e non il tipo di carattere del testo in modo che gli elementi vengano ridimensionati in modo prevedibile.

1. Per il testo del codice nell'editor, ridimensionarlo con l'impostazione del tipo di carattere del testo del codice e rispondere al livello di zoom del testo dell'editor.

2. Tutti gli altri elementi dell'interfaccia devono essere associati all'impostazione del tipo di carattere dell'ambiente e rispondere a eventuali modifiche globali nell'ambiente. includendo tra l'altro:

    - Testo nei menu di scelta rapida

    - Testo in un'area di controllo dell'editor, ad esempio il testo del menu lampadina, il riquadro dell'editor di ricerca rapida e passare al riquadro

    - Etichettare il testo nelle finestre di dialogo, **ad esempio Trova nei file** o **Refactoring**

### <a name="accessing-the-environment-font"></a>Accesso al tipo di carattere dell'ambiente
 Nel codice nativo o WinForms è possibile accedere al tipo di carattere dell'ambiente chiamando il metodo dopo l'esecuzione di `IUIHostLocale::GetDialogFont` query sull'interfaccia dal `SID_SUIHostLocale` servizio.

 Ad Windows Presentation Foundation (WPF), derivare la classe della finestra di dialogo dalla classe della shell anziché dalla `DialogWindow` classe di `Window` WPF.

 In XAML il codice è simile al seguente:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Code-behind:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 Sostituire `Microsoft.VisualStudio.Shell.11.0` con la versione corrente della dll MPF.

 Per visualizzare la finestra di dialogo, `ShowModal()` chiamare " " nella classe su `ShowDialog()` . `ShowModal()` imposta lo stato modale corretto nella shell, assicura che il dialogo sia centrato nella finestra padre e così via.

 Il codice è indicato di seguito:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` restituisce un valore bool? (valore booleano nullable) con `DialogResult` , che può essere usato se necessario. Il valore restituito è true se il dialogo è stato chiuso con **OK.**

 Se devi visualizzare un'interfaccia utente WPF che non è una finestra di dialogo ed è ospitata in una finestra popup o in una finestra figlio WPF di una finestra padre `HwndSource` Win32/WinForms, dovrai impostare e sull'elemento radice dell'elemento `FontFamily` `FontSize` WPF. La shell imposta le proprietà nella finestra principale, ma non verranno ereditate oltre un `HWND` . La shell fornisce risorse a cui possono essere associate le proprietà, come nell'esempio seguente:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Informazioni di riferimento sulla formattazione (ridimensionamento/grassetto)
 Alcune finestre di dialogo richiedono che il testo specifico sia in grassetto o di dimensioni diverse dal tipo di carattere dell'ambiente. In precedenza, i tipi di carattere più grandi del tipo di carattere dell'ambiente venivano codificati come " `environment font +2` " o simili. L'uso dei frammenti di codice forniti supporterà monitor con valori DPI elevati e garantisce che il testo visualizzato venga sempre visualizzato con le dimensioni e lo spessore corretti,ad esempio Chiaro o Semilight.

> [!NOTE]
> Prima di applicare la formattazione, assicurarsi di seguire le indicazioni disponibili in [Stile testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Per ridimensionare il tipo di carattere dell'ambiente, imposta lo stile di TextBlock o Label come indicato. Ognuno di questi frammenti di codice, usati correttamente, genererà il tipo di carattere corretto, incluse le dimensioni e le variazioni di spessore appropriate.

 Dove " `vsui` " è un riferimento allo spazio dei nomi `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% Carattere ambiente + Chiaro

**Viene visualizzato come:** 34 pt Segoe UI Chiaro

::: moniker range="vs-2017"

**Usare per:** (raro) interfaccia utente personalizzata univoca, ad esempio nella pagina iniziale

::: moniker-end

::: moniker range=">=vs-2019"

**Usare per:** (raro) interfaccia utente personalizzata univoca

::: moniker-end

**Codice procedurale:** Dove `textBlock` è un oggetto TextBlock definito in precedenza ed è un elemento Label definito in `label` precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Imposta lo stile di TextBlock o Label come illustrato.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% Carattere ambiente + Chiaro
 **Viene visualizzato come:** 28 pt Segoe UI Light **Use for:** large signature dialog titles, main heading in reports

 **Codice procedurale:** Dove `textBlock` è un oggetto TextBlock definito in precedenza ed è un elemento Label definito in `label` precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Imposta lo stile di TextBlock o Label come illustrato.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% Carattere ambiente + Semilight
 **Viene visualizzato come:** 18 pt Segoe UI Semilight **Use for:** subheadings, titles in small and medium dialogs

 **Codice procedurale:** Dove `textBlock` è un oggetto TextBlock definito in precedenza ed è un elemento Label definito in `label` precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Imposta lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>Tipo di carattere 155% ambiente
 **Viene visualizzato come:** 14 pt Segoe UI **usare per: intestazioni** di sezione nell'interfaccia utente o nei report dell'well document

 **Codice procedurale:** Dove `textBlock` è un oggetto TextBlock definito in precedenza ed è un elemento Label definito in `label` precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Imposta lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>Tipo di carattere Ambiente 133%
 **Viene visualizzato come:** 12 pt Segoe UI **Usare per:** sottotitoli secondari più piccoli nelle finestre di dialogo della firma e nell'interfaccia utente dell'area documenti

 **Codice procedurale:** Dove `textBlock` è un oggetto TextBlock definito in precedenza ed è un elemento Label definito in `label` precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Imposta lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>Tipo di carattere 122% Ambiente
 **Viene visualizzato come:** 11 pt Segoe UI usare **per: intestazioni** di sezione nelle finestre di dialogo della firma, nodi principali nella visualizzazione albero, navigazione verticale tra schede

 **Codice procedurale:** Dove `textBlock` è un oggetto TextBlock definito in precedenza ed è un elemento Label definito in `label` precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Imposta lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto
 **Viene visualizzato come:** grassetto 9 pt Segoe UI usare **per:** etichette e sottotitoli in finestre di dialogo di firma, report e interfaccia utente dell'well document

 **Codice procedurale:** Dove `textBlock` è un oggetto TextBlock definito in precedenza ed è un elemento Label definito in `label` precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Imposta lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Stili localizzabili
 In alcuni casi, i localizzatori dovranno modificare gli stili dei caratteri per impostazioni locali diverse, ad esempio rimuovendo il grassetto dal testo per le lingue dell'Asia orientale. Per rendere possibile la localizzazione degli stili dei caratteri, tali stili devono essere all'interno del file con estensione resx. Il modo migliore per eseguire questa operazione e modificare comunque gli stili dei caratteri nella finestra di progettazione Visual Studio form è impostare in modo esplicito gli stili dei caratteri in fase di progettazione. Anche se in questo modo viene creato un oggetto tipo di carattere completo e potrebbe sembrare che interrompa l'ereditarietà dei tipi di carattere padre, per impostare il tipo di carattere viene usata solo la proprietà FontStyle.

 La soluzione consiste nell'associare l'evento del form del `FontChanged` dialogo. `FontChanged`Nell'evento , eseguire la procedura per tutti i controlli e verificare se il tipo di carattere è impostato. Se è impostato, modificarlo in un nuovo tipo di carattere in base al tipo di carattere del form e allo stile del carattere precedente del controllo. Di seguito è riportato un esempio nel codice:

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 L'uso di questo codice garantisce che, quando il tipo di carattere del form viene aggiornato, verranno aggiornati anche i tipi di carattere dei controlli. Questo metodo deve essere chiamato anche dal costruttore del form, perché il dialogo potrebbe non riuscire a ottenere un'istanza di e l'evento `IUIService` `FontChanged` non verrà mai generato. L'hook consentirà alle finestre di dialogo di selezionare dinamicamente il nuovo tipo di `FontChanged` carattere anche se la finestra di dialogo è già aperta.

### <a name="testing-the-environment-font"></a>Test del tipo di carattere dell'ambiente
 Per assicurarsi che l'interfaccia utente utilizzi il tipo di carattere dell'ambiente e rispetti le impostazioni delle dimensioni, aprire Strumenti **> Opzioni >** Ambiente > Tipi di carattere e colori e selezionare "Tipo di carattere ambiente" nel menu a discesa "Mostra impostazioni per".

 ![Impostazioni Tipi di carattere e colori nella finestra di &gt; dialogo Opzioni strumenti](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Impostazioni Tipi di carattere e colori nella finestra di &gt; dialogo Opzioni strumenti

 Impostare il tipo di carattere su un valore molto diverso da quello predefinito. Per rendere evidente quale interfaccia utente non viene aggiornato, scegliere un tipo di carattere con serifs (ad esempio "Times New Roman") e impostare dimensioni molto grandi. Testare quindi l'interfaccia utente per assicurarsi che rispetti l'ambiente. Di seguito è riportato un esempio di uso della finestra di dialogo di licenza:

 ![Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere dell'ambiente](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere dell'ambiente

 In questo caso, "User Information" e "Product Information" non rispettano il tipo di carattere. In alcuni casi può trattarsi di una scelta di progettazione esplicita, ma può trattarsi di un bug se il tipo di carattere esplicito non viene specificato come parte delle specifiche redline.

 Per reimpostare il tipo di carattere, fare clic su "Usa impostazioni predefinite" in Strumenti > opzioni > ambiente > **tipi di carattere e colori**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Stile del testo
 Lo stile del testo si riferisce alle dimensioni del carattere, allo spessore e all'applicazione di maiuscole e minuscole. Per indicazioni sull'implementazione, vedere [Il tipo di carattere dell'ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Distinzione tra maiuscole e minuscole per il testo

#### <a name="all-caps"></a>Tutti i limiti
 Non usare tutte le maiuscole per i titoli o le etichette Visual Studio.

#### <a name="all-lowercase"></a>Tutte minuscole
 Non usare tutte le lettere minuscole per i titoli o le etichette Visual Studio.

#### <a name="sentence-and-title-case"></a>Maiuscole/minuscole per frasi e titoli
 Il testo in Visual Studio deve usare la distinzione tra maiuscole e minuscole o la frase, a seconda della situazione.

|Usare la distinzione tra maiuscole e minuscole per:|Usare la distinzione tra maiuscole e minuscole per:|
|-------------------------|----------------------------|
|Titoli delle finestre di dialogo|Etichette|
|Caselle di gruppo|Caselle di controllo|
|Voci di menu|Pulsanti di opzione|
|Voci del menu di scelta rapida|Elementi della casella di riepilogo|
|Pulsanti|Barre di stato|
|Etichette di tabella||
|Intestazioni di colonna||
|Descrizioni comando||

##### <a name="title-case"></a>Iniziali maiuscole
 La combinazione di maiuscole/minuscole è uno stile in cui le prime lettere della maggior parte o di tutte le parole all'interno di una frase vengono scritte in maiuscolo. In Visual Studio, la distinzione tra maiuscole e minuscole viene usata per molti elementi, tra cui:

- **Le descrizioni comandi.** Esempio: "Anteprima elementi selezionati"

- **Intestazioni di colonna.** Esempio: "Risposta di sistema"

- **Voci di menu.** Esempio: "Salva tutto"

  Quando si usa la combinazione di maiuscole e minuscole, queste sono le linee guida per l'uso di maiuscole e minuscole:

|Maiuscole|Commenti ed esempi|
|---------------|---------------------------|
|Tutti i sostantivi||
|Tutti i verbi|Inclusione di "Is" e di altre forme di "essere"|
|Tutti gli avverbi|Inclusione di "Than" e "When"|
|Tutti gli aggettivi|Inclusione di "This" e "That"|
|Tutti i pronomi|Includendo il possessivo "Its" e "It's", una contrazione del pronome "it" e del verbo "is"|
|Prima e ultima parola, indipendentemente dalle parti del parlato||
|Preposizioni che fanno parte di una frase verbo|"Closing Out All Windows" o "Shutting Down the System"|
|Tutte le lettere di un acronimo|HTML, XML, URL, IDE, RGB|
|Seconda parola in una parola composta se è un sostantivo o un aggettivo appropriato o se le parole hanno lo stesso peso|Riferimenti incrociati, software pre-Microsoft, accesso in lettura/scrittura, Run-Time|

|Minuscole|Esempio|
|---------------|--------------|
|Seconda parola in una parola composta se è un'altra parte del parlato o un participio che modifica la prima parola|Procedura, take-off|
|Articoli, a meno che non sia la prima parola nel titolo|un, uno, una, il, lo, la, i, gli, le|
|Coordinare le congiunzioni|e , ma, per, né o|
|Preposizioni con parole di quattro o meno lettere all'esterno di una frase verbo|into, on, as for, out of, on top of|
|"To" se usato in una frase infinitiva|"Come formattare il disco rigido"|

##### <a name="sentence-case"></a>Maiuscole/minuscole delle frasi
 La distinzione tra maiuscole e minuscole è il metodo di lettere maiuscole standard per la scrittura in cui solo la prima parola della frase è in maiuscolo, insieme ai sostantivi e al pronome "I" appropriato. In generale, la distinzione tra maiuscole e minuscole è più semplice per un pubblico di tutto il mondo, soprattutto quando il contenuto verrà tradotto da un computer. Usare la distinzione tra maiuscole e minuscole per:

1. **Messaggi della barra di stato.** Si tratta di semplici, brevi e forniscono solo informazioni sullo stato. Esempio: "Caricamento del file di progetto"

2. **Tutti gli altri elementi dell'interfaccia** utente, incluse etichette, caselle di controllo, pulsanti di opzione ed elementi della casella di riepilogo. Esempio: "Selezionare tutti gli elementi nell'elenco"

### <a name="text-formatting"></a>Formattazione del testo
 La formattazione predefinita del testo Visual Studio 2013 è controllata dal [tipo di carattere dell'ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Questo servizio consente di garantire un aspetto del carattere coerente in tutto l'IDE (ambiente di sviluppo integrato) ed è necessario usarlo per garantire un'esperienza coerente per gli utenti.

 Le dimensioni predefinite usate dal servizio Visual Studio tipo di carattere derivano Windows e vengono visualizzate come 9 pt.

 È possibile applicare la formattazione al tipo di carattere dell'ambiente. Questo argomento illustra come e dove usare gli stili. Per informazioni sull'implementazione, vedere [Il tipo di carattere dell'ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Grassetto
 Il testo in grassetto viene usato con parsimon Visual Studio e deve essere riservato per:

- Etichette delle domande nelle procedure guidate

- designazione del progetto attivo in Esplora soluzioni

- Valori sottoposti a override nella finestra degli strumenti Proprietà

- determinati eventi negli elenchi Visual Basic a discesa dell'editor

- contenuto generato dal server nella struttura del documento per le pagine Web

- intestazioni di sezione nella finestra di dialogo complessa o nell'interfaccia utente della finestra di progettazione

#### <a name="italics"></a>Corsivo
 Visual Studio non usa il testo in corsivo o in grassetto.

#### <a name="color"></a>Color

- Il blu è riservato ai collegamenti ipertestuali (navigazione e comandi) e non deve mai essere usato per l'orientamento.

- Le intestazioni più grandi (tipo di carattere ambiente x 155% o superiore) possono essere colorate per questi scopi:

  - Per offrire un impatto visivo sulla firma Visual Studio'interfaccia utente

  - Per richiamare l'attenzione su un'area specifica

  - Per offrire rilievo dal colore standard del testo dell'ambiente grigio/nero scuro

- Il colore nelle intestazioni deve sfruttare Visual Studio colori del marchio, principalmente il viola principale, #FF68217A.

- Quando si usa il colore nelle intestazioni, è necessario rispettare le linee [guida](/windows/desktop/uxguide/vis-color)Windows colore, tra cui il rapporto di contrasto e altre considerazioni sull'accessibilità.

### <a name="font-size"></a>Dimensioni del carattere
 Visual Studio La progettazione dell'interfaccia utente ha un aspetto più leggero con più spazi vuoti. Dove possibile, le barre del titolo e del chrome sono state ridotte o rimosse. Anche se la densità delle informazioni è un requisito in Visual Studio, la tipografia continua a essere importante, con particolare attenzione all'interlinea più aperta e a una variazione delle dimensioni e dei pesi dei caratteri.

 Le tabelle seguenti includono dettagli di progettazione ed esempi visivi per i tipi di carattere di visualizzazione usati in Visual Studio. Alcune varianti del carattere di visualizzazione hanno sia le dimensioni che lo spessore, ad esempio Semilight o Light, codificate nell'aspetto.

 I frammenti di codice di implementazione per tutti i tipi di carattere visualizzati sono disponibili in Informazioni di riferimento sulla formattazione [(ridimensionamento/grassetto).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>375% Carattere ambiente + Chiaro

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:** Raro. Solo interfaccia utente personalizzata univoca.<br /><br /> **fare:**<br /><br /> - Usa maiuscole/minuscole per le frasi<br />- Usare sempre Il peso leggero<br /><br /> **Non:**<br /><br /> - Usare per l'interfaccia utente diversa dall'interfaccia utente della firma, ad esempio la pagina iniziale<br />- Grassetto, corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** 34 pt Segoe UI Chiaro<br /><br /> **Esempio di oggetto visivo:**<br /><br /> *Attualmente non usato. Può essere usato nella pagina Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>310% Carattere ambiente + Chiaro

::: moniker range="vs-2017"

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> - Intestazione più grande nelle finestre di dialogo della firma<br />- Intestazione del report principale<br /><br /> **fare:**<br /><br /> - Usa maiuscole/minuscole per le frasi<br />- Usare sempre Il peso leggero<br /><br /> **Non:**<br /><br /> - Usare per l'interfaccia utente diversa dall'interfaccia utente della firma, ad esempio la pagina iniziale<br />- Grassetto, corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** 28 pt Segoe UI Chiaro<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di tipo di carattere Environment 310% &#43;'intestazione Light](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> - Intestazione più grande nelle finestre di dialogo della firma<br />- Intestazione del report principale<br /><br /> **fare:**<br /><br /> - Usa maiuscole/minuscole per le frasi<br />- Usare sempre Il peso leggero<br /><br /> **Non:**<br /><br /> - Da usare per l'interfaccia utente diversa dall'interfaccia utente della firma<br />- Grassetto, corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** 28 pt Segoe UI Chiaro<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di tipo di carattere Environment 310% &#43;'intestazione Light](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% Carattere ambiente + Semilight

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> - Sottotitoli<br />- Titoli in finestre di dialogo piccole e medie<br /><br /> **fare:**<br /><br /> - Usa maiuscole/minuscole per le frasi<br />- Usa sempre semilight weight<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** 18 pt Segoe UI Semillight<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di tipo di carattere Environment 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>Tipo di carattere 155% ambiente

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> - Intestazioni di sezione nell'interfaccia utente dell'well document<br />- Report<br /><br /> **Cosa fare:** Usa maiuscole/minuscole per le frasi<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nei controlli Visual Studio standard<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** 14 pt Segoe UI<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>Tipo di carattere Ambiente 133%

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> - Sottotitoli più piccoli nelle finestre di dialogo della firma<br />- Sottotitoli più piccoli nell'interfaccia utente dell'area documenti<br /><br /> **Cosa fare:** Usa maiuscole/minuscole per le frasi<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nei controlli Visual Studio standard<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** 12 pt Segoe UI<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>Tipo di carattere 122% Ambiente

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> - Intestazioni di sezione nelle finestre di dialogo della firma<br />- Nodi principali nella visualizzazione albero<br />- Spostamento verticale tra schede<br /><br /> **Cosa fare:** Usa maiuscole/minuscole per le frasi<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nei controlli Visual Studio standard<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** 11 pt Segoe UI<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> - Etichette e sottotitoli nelle finestre di dialogo della firma<br />- Etichette e sottotitoli nei report<br />- Etichette e sottotitoli nell'interfaccia utente dell'well document<br /><br /> **fare:**<br /><br /> - Usa maiuscole/minuscole per le frasi<br />- Usa spessore grassetto<br /><br /> **Non:**<br /><br /> - Corsivo o corsivo grassetto<br />- Usare per il testo del corpo<br />- Da usare nei controlli Visual Studio standard<br />- Da usare nelle finestre degli strumenti|**Viene visualizzato come:** grassetto 9 pt Segoe UI<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di tipo di carattere Ambiente &#43;'intestazione Grassetto](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Tipo di carattere ambiente

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:** Tutto il testo<br /><br /> **Cosa fare:** Usa maiuscole/minuscole per le frasi<br /><br /> **Non:** Corsivo o corsivo grassetto|**Viene visualizzato come:** 9 pt Segoe UI<br /><br /> **Esempio di oggetto visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Spaziatura interna e spaziatura
 Le intestazioni richiedono uno spazio intorno a esse per dare loro l'enfasi appropriata. Questo spazio varia a seconda delle dimensioni del punto e degli altri elementi vicini all'intestazione, ad esempio una regola orizzontale o una riga di testo nel tipo di carattere dell'ambiente.

- La spaziatura interna ideale per un'intestazione deve essere il 90% dello spazio di altezza dei caratteri maiuscoli. Ad esempio, un titolo 28 pt Segoe UI Light ha un'altezza limite di 26 pt e la spaziatura interna deve essere di circa 23 pt o circa 31 pixel.

- Lo spazio minimo intorno a un'intestazione deve essere il 50% dell'altezza del carattere maiuscolo. È possibile usare meno spazio quando un'intestazione è accompagnata da una regola o da un altro elemento aderente.

- Il testo del tipo di carattere dell'ambiente in grassetto deve seguire la spaziatura e la spaziatura interna predefinite per l'altezza della riga.

## <a name="see-also"></a>Vedi anche

- [Tipi di carattere (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Interfaccia utente testo (Windows)](/windows/desktop/uxguide/text-ui)
