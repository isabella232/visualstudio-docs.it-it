---
title: Tipi di carattere e formattazione per Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd2e8a41ef4b9708df079e94bcac8b8c06189116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536110"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Tipi di carattere e formattazione per Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Tipo di carattere ambiente
 Tutti i tipi di carattere in Visual Studio devono essere esposti all'utente per la personalizzazione. Questa operazione viene eseguita principalmente tramite la pagina **tipi di carattere e colori** della finestra di dialogo **strumenti > opzioni** . Le tre categorie principali di impostazioni del tipo di carattere sono:

- **Tipo di carattere ambiente** : il tipo di carattere principale per l'IDE (Integrated Development Environment), usato per tutti gli elementi dell'interfaccia, inclusi i dialoghi, i menu, le finestre degli strumenti e le finestre dei documenti. Per impostazione predefinita, il tipo di carattere dell'ambiente è associato a un tipo di carattere di sistema che viene visualizzato come 9 PT Segoe UI nelle versioni correnti di Windows. L'uso di un tipo di carattere per tutti gli elementi dell'interfaccia consente di garantire un aspetto coerente del tipo di carattere nell'IDE.

- **Editor di testo** : gli elementi che emergono nel codice e altri editor basati su testo possono essere personalizzati nella pagina editor di testo in **strumenti > opzioni**.

- **Raccolte specifiche** : le finestre di progettazione che offrono la personalizzazione degli utenti degli elementi di interfaccia possono esporre i tipi di carattere specifici dell'area di progettazione nella relativa pagina delle impostazioni in **strumenti > opzioni**.

### <a name="editor-font-customization-and-resizing"></a>Personalizzazione e ridimensionamento dei tipi di carattere dell'editor
 Spesso gli utenti possono ingrandire o ingrandire le dimensioni e/o il colore del testo nell'editor in base alle preferenze, indipendentemente dall'interfaccia utente generale. Poiché il tipo di carattere dell'ambiente viene usato su elementi che possono apparire all'interno o come parte di un editor/finestra di progettazione, è importante notare il comportamento previsto quando una di queste classificazioni dei tipi di carattere viene modificata.

 Quando si creano elementi dell'interfaccia utente che vengono visualizzati nell'editor ma che non fanno parte del *contenuto*, è importante usare il tipo di carattere dell'ambiente e non il tipo di carattere del testo in modo che gli elementi vengano ridimensionati in modo prevedibile.

1. Per il testo del codice nell'editor, ridimensionare con l'impostazione del tipo di carattere del testo del codice e rispondere al livello di zoom del testo dell'editor.

2. Tutti gli altri elementi dell'interfaccia devono essere associati all'impostazione del tipo di carattere ambiente e rispondere alle eventuali modifiche globali nell'ambiente. includendo tra l'altro:

    - Testo nei menu di scelta rapida

    - Testo in un'area di visualizzazione dell'editor, ad esempio testo del menu lampadina, riquadro Editor ricerca veloce e riquadro passa a

    - Testo dell'etichetta nelle finestre di dialogo, ad esempio **ricerca nei file** o **refactoring**

### <a name="accessing-the-environment-font"></a>Accesso al tipo di carattere ambiente
 Nel codice nativo o WinForms, è possibile accedere al tipo di carattere dell'ambiente chiamando il metodo `IUIHostLocale::GetDialogFont` dopo avere eseguito una query sull'interfaccia dal `SID_SUIHostLocale` servizio.

 Per Windows Presentation Foundation (WPF), derivare la classe della finestra di dialogo dalla `DialogWindow` classe della shell invece della `Window` classe di WPF.

 In XAML il codice ha un aspetto simile al seguente:

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

 Sostituire `Microsoft.VisualStudio.Shell.11.0` con la versione corrente della DLL di MPF.

 Per visualizzare la finestra di dialogo, chiamare " `ShowModal()` " sulla classe `ShowDialog()` . `ShowModal()` imposta lo stato modale corretto nella shell, assicura che la finestra di dialogo sia centrata nella finestra padre e così via.

 Il codice è indicato di seguito:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` Restituisce un valore bool? (valore booleano nullable) con `DialogResult` , che può essere usato se necessario. Il valore restituito è true se la finestra di dialogo è stata chiusa con **OK**.

 Se è necessario visualizzare un'interfaccia utente di WPF che non è una finestra di dialogo e che è ospitata in modo autonomo `HwndSource` , ad esempio una finestra popup o una finestra figlio WPF di una finestra padre Win32/WinForms, sarà necessario impostare `FontFamily` e `FontSize` sull'elemento radice dell'elemento WPF. La shell imposta le proprietà nella finestra principale, ma non verranno ereditate dopo `HWND` . La shell fornisce le risorse a cui è possibile associare le proprietà, come indicato di seguito:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Guida di riferimento alla formattazione (ridimensionamento/grassetto)
 Alcune finestre di dialogo richiedono un testo particolare in grassetto o una dimensione diversa dal tipo di carattere ambiente. In precedenza, i caratteri più grandi del tipo di carattere dell'ambiente venivano codificati come " `environment font +2` " o simili. L'uso dei frammenti di codice forniti supporterà i monitoraggi con valori DPI alti e assicurerà che il testo visualizzato venga sempre visualizzato con le dimensioni e il peso corretti (ad esempio, Light o Semilight).

> [!NOTE]
> Prima di applicare la formattazione, assicurarsi di seguire le indicazioni disponibili in [stile testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle). * *

 Per ridimensionare il tipo di carattere ambiente, impostare lo stile dell'elemento TextBlock o Label come indicato. Ognuno di questi frammenti di codice, usati in modo appropriato, genererà il tipo di carattere corretto, incluse le variazioni appropriate per le dimensioni e il peso.

 Dove " `vsui` " è un riferimento allo spazio dei nomi `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>tipo di carattere ambiente 375% + chiaro

**Visualizzato come:** 34 PT Segoe UI chiaro

::: moniker range="vs-2017"

**Usare per:** (rare) interfaccia utente personalizzata, come nella pagina iniziale

::: moniker-end

::: moniker range=">=vs-2019"

**USA per:** (rare) interfaccia utente con marchio univoco

::: moniker-end

**Codice procedurale:** Dove `textBlock` è un TextBlock definito in precedenza ed `label` è un'etichetta definita in precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Imposta lo stile dell'elemento TextBlock o Label come illustrato.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>tipo di carattere ambiente 310% + chiaro
 **Visualizzato come:** 28 PT Segoe UI **uso leggero per:** titoli di finestre di firma di grandi dimensioni, intestazione principale nei report

 **Codice procedurale:** Dove `textBlock` è un TextBlock definito in precedenza ed `label` è un'etichetta definita in precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Imposta lo stile dell'elemento TextBlock o Label come illustrato.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>tipo di carattere ambiente 200% + Semilight
 **Viene visualizzato come:** 18 PT Segoe UI **uso di Semilight per:** sottointestazioni, titoli nelle finestre di dialogo piccole e medie

 **Codice procedurale:** Dove `textBlock` è un TextBlock definito in precedenza ed `label` è un'etichetta definita in precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>tipo di carattere ambiente 155%
 **Viene visualizzato come:** 14 PT Segoe UI **usare per:** intestazioni di sezione nell'interfaccia utente dei documenti e nei report

 **Codice procedurale:** Dove `textBlock` è un TextBlock definito in precedenza ed `label` è un'etichetta definita in precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>tipo di carattere ambiente 133%
 **Viene visualizzato come:** 12 PT Segoe UI **usare per:** sottointestazioni più piccole nelle finestre di dialogo della firma e interfaccia utente dei documenti

 **Codice procedurale:** Dove `textBlock` è un TextBlock definito in precedenza ed `label` è un'etichetta definita in precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>tipo di carattere ambiente 122%
 **Viene visualizzato come:** 11 PT Segoe UI **usare per:** intestazioni di sezione nelle finestre di dialogo della firma, nodi principali nella visualizzazione albero, navigazione con tabulazione verticale

 **Codice procedurale:** Dove `textBlock` è un TextBlock definito in precedenza ed `label` è un'etichetta definita in precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto
 **Viene visualizzato come:** grassetto 9 PT Segoe UI **usare per:** etichette e sottointestazioni nelle finestre di dialogo della firma, rapporti e interfaccia utente dei documenti

 **Codice procedurale:** Dove `textBlock` è un TextBlock definito in precedenza ed `label` è un'etichetta definita in precedenza:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Stili localizzabili
 In alcuni casi, i localizzatori dovranno modificare gli stili dei tipi di carattere per impostazioni locali diverse, ad esempio la rimozione del grassetto dal testo per le lingue asiatiche orientali. Per rendere possibile la localizzazione degli stili dei tipi di carattere, è necessario che tali stili siano inclusi nel file. resx. Il modo migliore per eseguire questa operazione e modificare gli stili dei tipi di carattere in progettazione form di Visual Studio consiste nell'impostare in modo esplicito gli stili dei caratteri in fase di progettazione. Sebbene venga creato un oggetto del tipo di carattere completo e potrebbe sembrare che interrompa l'ereditarietà dei tipi di carattere padre, per impostare il tipo di carattere viene utilizzata solo la proprietà FontStyle.

 La soluzione consiste nell'associare l'evento del form della finestra di dialogo `FontChanged` . Nell' `FontChanged` evento, esaminare tutti i controlli e verificare se il tipo di carattere è impostato. Se è impostato, modificarlo in un nuovo tipo di carattere in base al tipo di carattere del form e allo stile del carattere precedente del controllo. Un esempio di questo codice è:

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

 Con questo codice si garantisce che, quando viene aggiornato il tipo di carattere del modulo, anche i tipi di carattere dei controlli vengono aggiornati. Questo metodo deve essere chiamato anche dal costruttore del form, perché la finestra di dialogo potrebbe non riuscire a ottenere un'istanza di `IUIService` e l' `FontChanged` evento non verrà mai attivato. L'hook `FontChanged` consentirà ai dialoghi di prelevare dinamicamente il nuovo tipo di carattere anche se la finestra di dialogo è già aperta.

### <a name="testing-the-environment-font"></a>Test del tipo di carattere ambiente
 Per assicurarsi che l'interfaccia utente usi il tipo di carattere ambiente e rispetti le impostazioni delle dimensioni, aprire **strumenti > opzioni > ambiente > tipi di carattere e colori** e selezionare "tipo di carattere ambiente" nel menu a discesa "Mostra impostazioni per:".

 ![Impostazioni tipi di carattere e colori nella &gt; finestra di dialogo Opzioni strumenti](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Impostazioni tipi di carattere e colori nella &gt; finestra di dialogo Opzioni strumenti

 Impostare il tipo di carattere su un valore molto diverso rispetto a quello predefinito. Per ovviare a quale interfaccia utente non viene aggiornata, scegliere un tipo di carattere con serifs (ad esempio "Times New Roman") e impostare dimensioni molto grandi. Testare quindi l'interfaccia utente per assicurarsi che rispetti l'ambiente. Di seguito è riportato un esempio di utilizzo della finestra di dialogo di licenza:

 ![Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere dell'ambiente](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere dell'ambiente

 In questo caso, "informazioni utente" e "informazioni sul prodotto" non rispettano il tipo di carattere. In alcuni casi potrebbe trattarsi di una scelta di progettazione esplicita, ma può trattarsi di un bug se il tipo di carattere esplicito non è specificato come parte delle specifiche di Redline.

 Per reimpostare il tipo di carattere, fare clic su "Usa impostazioni predefinite" in **strumenti > opzioni > ambiente > tipi di carattere e colori**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Stile testo
 Lo stile del testo si riferisce a dimensioni, peso e maiuscole e minuscole. Per informazioni aggiuntive sull'implementazione, vedere [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Maiuscole/minuscole testo

#### <a name="all-caps"></a>Tutti i limiti
 Non usare tutti i tappi per i titoli o le etichette in Visual Studio.

#### <a name="all-lowercase"></a>Tutto minuscole
 Non usare tutti i caratteri minuscoli per i titoli o le etichette in Visual Studio.

#### <a name="sentence-and-title-case"></a>Maiuscole e minuscole
 Il testo in Visual Studio deve usare maiuscole o minuscole, a seconda della situazione.

|USA titolo case per:|Usa la frase maiuscola per:|
|-------------------------|----------------------------|
|Titoli delle finestre di dialogo|Etichette|
|Caselle di gruppo|Caselle di controllo|
|Voci di menu|Pulsanti di opzione|
|Voci del menu di scelta rapida|Elementi casella di riepilogo|
|Pulsanti|Barre di stato|
|Etichette di tabella||
|Intestazioni di colonna||
|Descrizioni comando||

##### <a name="title-case"></a>Iniziali maiuscole
 Il titolo è uno stile in cui le prime lettere della maggior parte o di tutte le parole all'interno di una frase sono maiuscole. In Visual Studio, case del titolo viene usato per molti elementi, tra cui:

- **Descrizioni comandi.** Esempio: "anteprima elementi selezionati"

- **Intestazioni di colonna.** Esempio: "risposta di sistema"

- **Voci di menu.** Esempio: "Save All"

  Quando si usa il titolo, queste sono le linee guida per i casi in cui è possibile capitalizzare le parole e quando lasciarle minuscole:

|Maiuscolo|Commenti ed esempi|
|---------------|---------------------------|
|Tutti i sostantivi||
|Tutti i verbi|Inclusione di "is" e di altre forme di "to be"|
|Tutti gli avverbi|Inclusi "than" e "When"|
|Tutti gli aggettivi|Inclusi "This" e "This"|
|Tutte le prosostantive|Includendo la "sua" e l'"it", una contrazione del pronome "it" e il verbo "is"|
|Prima e ultima parola, indipendentemente dalle parti del discorso||
|Preposizioni che fanno parte di una frase verbo|"Chiusura di tutte le finestre" o "arresto del sistema"|
|Tutte le lettere di un acronimo|HTML, XML, URL, IDE, RGB|
|Seconda parola in una parola composta se è un sostantivo o un aggettivo appropriato oppure se le parole hanno un peso uguale|Riferimento incrociato, software pre-Microsoft, accesso in lettura/scrittura, Runtime|

|Lettere minuscole|Esempi|
|---------------|--------------|
|Seconda parola in una parola composta se è un'altra parte del discorso o un participio che modifica la prima parola|Procedura, take-off|
|Articoli, a meno che non si tratti della prima parola nel titolo|un, uno, una, il, lo, la, i, gli, le|
|Congiunzioni Coordinate|e, ma, per, né o|
|Preposizioni con parole di quattro o meno lettere al di fuori di una frase verbo|into, su, come per, su, su|
|"A" se usato in una frase infinita|"Come formattare il disco rigido"|

##### <a name="sentence-case"></a>Maiuscole/minuscole
 La frase maiuscola è il metodo standard per la creazione di maiuscole per la scrittura, in cui solo la prima parola della frase è in maiuscolo, insieme ai sostantivi appropriati e al pronome "I". In generale, la frase maiuscola e minuscola è più semplice da leggere per un pubblico di tutto il mondo, soprattutto quando il contenuto verrà tradotto da un computer. Usa la frase maiuscola per:

1. **Messaggi della barra di stato.** Si tratta di semplici e brevi e forniscono solo informazioni sullo stato. Esempio: "caricamento del file di progetto"

2. **Tutti gli altri elementi dell'interfaccia utente**, tra cui etichette, caselle di controllo, pulsanti di opzione e elementi della casella di riepilogo. Esempio: "selezionare tutti gli elementi nell'elenco"

### <a name="text-formatting"></a>Formattazione del testo
 La formattazione del testo predefinita nelle Visual Studio 2013 è controllata dal [tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Questo servizio contribuisce a garantire un aspetto coerente del tipo di carattere nell'IDE (Integrated Development Environment) ed è necessario usarlo per garantire un'esperienza coerente agli utenti.

 Le dimensioni predefinite usate dal servizio del tipo di carattere di Visual Studio provengono da Windows e vengono visualizzate come 9 PT.

 È possibile applicare la formattazione al tipo di carattere ambiente. Questo argomento descrive come e dove usare gli stili. Per informazioni sull'implementazione, fare riferimento al [tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Testo in grassetto
 Il testo in grassetto viene usato sporadicamente in Visual Studio e deve essere riservato per:

- etichette delle domande nelle procedure guidate

- designazione del progetto attivo nel Esplora soluzioni

- valori sottoposti a override nella finestra degli strumenti Proprietà

- alcuni eventi negli elenchi a discesa dell'editor Visual Basic

- contenuto generato dal server nella struttura del documento per le pagine Web

- intestazioni di sezione nella finestra di dialogo complessa o nell'interfaccia utente di progettazione

#### <a name="italics"></a>Corsivo
 Visual Studio non usa il testo in corsivo o in grassetto.

#### <a name="color"></a>Color

- Il blu è riservato per i collegamenti ipertestuali (navigazione e comando) e non deve mai essere usato per l'orientamento.

- Le intestazioni più grandi (tipo di carattere dell'ambiente x 155% o superiore) possono essere colorate per questi scopi:

  - Per fornire un appeal visivo alla firma dell'interfaccia utente di Visual Studio

  - Per richiamare l'attenzione su un'area specifica

  - Per offrire sollievo dal colore del testo dell'ambiente grigio scuro/nero standard

- Il colore nelle intestazioni dovrebbe sfruttare i colori esistenti del marchio di Visual Studio, principalmente il viola principale, #FF68217A.

- Quando si usa il colore nelle intestazioni, è necessario rispettare le [linee guida](/windows/desktop/uxguide/vis-color)per i colori di Windows, inclusi il rapporto di contrasto e altre considerazioni sull'accessibilità.

### <a name="font-size"></a>Dimensioni del carattere
 Progettazione dell'interfaccia utente di Visual Studio offre un aspetto più chiaro con più spazio vuoto. Laddove possibile, le barre Chrome e title sono state ridotte o rimosse. Sebbene la densità delle informazioni sia un requisito in Visual Studio, la tipografia continua a essere importante, con particolare attenzione a una maggiore interlinea di apertura e a una variazione di dimensioni e pesi dei tipi di carattere.

 Le tabelle seguenti includono i dettagli di progettazione e gli esempi visivi per i tipi di carattere visualizzati usati in Visual Studio. Alcune variazioni dei tipi di carattere di visualizzazione hanno sia la dimensione che il peso, ad esempio Semilight o Light, codificati nell'aspetto.

 I frammenti di codice di implementazione per tutti i tipi di carattere di visualizzazione sono disponibili nel [riferimento di formattazione (ridimensionamento/grassetto)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>tipo di carattere ambiente 375% + chiaro

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:** Rari. Unica interfaccia utente personalizzata.<br /><br /> **Fare**<br /><br /> -Usa la frase maiuscola<br />-Usare sempre il peso chiaro<br /><br /> **Non:**<br /><br /> -Usare per l'interfaccia utente diversa dall'interfaccia utente della firma, ad esempio la pagina iniziale<br />-Grassetto, corsivo o corsivo grassetto<br />-Use per il testo del corpo<br />-Usare nelle finestre degli strumenti|**Visualizzato come:** 34 PT Segoe UI chiaro<br /><br /> **Esempio visivo:**<br /><br /> *Attualmente non utilizzato. Può essere usato nella pagina iniziale di Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>tipo di carattere ambiente 310% + chiaro

::: moniker range="vs-2017"

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> -Intestazione più grande nelle finestre di dialogo della firma<br />-Intestazione report principale<br /><br /> **Fare**<br /><br /> -Usa la frase maiuscola<br />-Usare sempre il peso chiaro<br /><br /> **Non:**<br /><br /> -Usare per l'interfaccia utente diversa dall'interfaccia utente della firma, ad esempio la pagina iniziale<br />-Grassetto, corsivo o corsivo grassetto<br />-Use per il testo del corpo<br />-Usare nelle finestre degli strumenti|**Visualizzato come:** 28 PT Segoe UI chiaro<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente 310% &#43; intestazione chiara](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> -Intestazione più grande nelle finestre di dialogo della firma<br />-Intestazione report principale<br /><br /> **Fare**<br /><br /> -Usa la frase maiuscola<br />-Usare sempre il peso chiaro<br /><br /> **Non:**<br /><br /> -Usare per un'interfaccia utente diversa dall'interfaccia utente della firma<br />-Grassetto, corsivo o corsivo grassetto<br />-Use per il testo del corpo<br />-Usare nelle finestre degli strumenti|**Visualizzato come:** 28 PT Segoe UI chiaro<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente 310% &#43; intestazione chiara](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>tipo di carattere ambiente 200% + Semilight

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> -Sottointestazioni<br />-Titoli nelle finestre di dialogo piccole e medie<br /><br /> **Fare**<br /><br /> -Usa la frase maiuscola<br />-Usare sempre Semilight Weight<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o corsivo grassetto<br />-Use per il testo del corpo<br />-Usare nelle finestre degli strumenti|**Viene visualizzato come:** 18 PT Segoe UI Semillight<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>tipo di carattere ambiente 155%

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> -Intestazioni di sezione nell'interfaccia utente di Document well<br />-Report<br /><br /> **Do:** Usa la frase maiuscola<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o corsivo grassetto<br />-Use per il testo del corpo<br />-Usare nei controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Visualizzato come:** 14 PT Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>tipo di carattere ambiente 133%

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> -Sottointestazioni più piccole nelle finestre di dialogo della firma<br />-Sottotitoli più piccoli nell'interfaccia utente di Document well<br /><br /> **Do:** Usa la frase maiuscola<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o corsivo grassetto<br />-Use per il testo del corpo<br />-Usare nei controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Viene visualizzato come:** 12 PT Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>tipo di carattere ambiente 122%

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> -Intestazioni di sezione nelle finestre di dialogo della firma<br />-Nodi principali nella visualizzazione albero<br />-Navigazione con tabulazione verticale<br /><br /> **Do:** Usa la frase maiuscola<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o corsivo grassetto<br />-Use per il testo del corpo<br />-Usare nei controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Visualizzato come:** 11 PT Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:**<br /><br /> -Etichette e sottointestazioni nelle finestre di dialogo della firma<br />-Etichette e sottointestazioni nei report<br />-Etichette e sottointestazioni nell'interfaccia utente di Document well<br /><br /> **Fare**<br /><br /> -Usa la frase maiuscola<br />-USA peso grassetto<br /><br /> **Non:**<br /><br /> -Corsivo o grassetto corsivo<br />-Use per il testo del corpo<br />-Usare nei controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Visualizzato come:** grassetto 9 PT Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente &#43; intestazione grassetto](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Tipo di carattere ambiente

|Utilizzo|Aspetto|
|-|-|
|**Utilizzo:** Tutto il testo<br /><br /> **Do:** Usa la frase maiuscola<br /><br /> **Non:** Corsivo o grassetto corsivo|**Viene visualizzato come:** 9 PT Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Spaziatura interna e spaziatura
 Le intestazioni necessitano di spazio per fornire loro l'accento appropriato. Questo spazio varia a seconda delle dimensioni dei punti e degli altri elementi che si avvicinano all'intestazione, ad esempio una regola orizzontale o una riga di testo nel tipo di carattere dell'ambiente.

- La spaziatura interna ideale per un'intestazione deve essere pari al 90% dello spazio di altezza dei caratteri maiuscoli. Ad esempio, un'intestazione della luce del Segoe UI 28 PT ha un'altezza del CAP di 26 PT e la spaziatura interna deve essere approssimativamente 23 PT o circa 31 pixel.

- Lo spazio minimo intorno a un'intestazione deve essere pari al 50% dell'altezza dei caratteri maiuscoli. È possibile utilizzare meno spazio quando un'intestazione è accompagnata da una regola o da un altro elemento aderente.

- Il testo del tipo di carattere dell'ambiente con grassetto deve seguire la spaziatura e la spaziatura interna.

## <a name="see-also"></a>Vedere anche

- [Tipi di carattere (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Testo dell'interfaccia utente (Windows)](/windows/desktop/uxguide/text-ui)
