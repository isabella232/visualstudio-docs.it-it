---
title: Tipi di carattere e formattazione
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ede8844b34473e1c900bd6af040cac99ceee1514
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824059"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Tipi di carattere e formattazione per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_TheEnvironmentFont"></a> Il tipo di carattere ambiente
 Tutti i tipi di carattere all'interno di Visual Studio deve essere esposto all'utente per la personalizzazione. Ciò avviene principalmente attraverso il **i tipi di carattere e colori** pagina il **strumenti > Opzioni** finestra di dialogo. Le tre categorie principali di impostazioni del tipo di carattere sono:

- **Tipo di carattere ambiente** , ovvero il tipo di carattere primario dell'IDE (integrated development environment), usato per tutti gli elementi di interfaccia, tra cui le finestre di dialogo, menu, finestre degli strumenti e finestre di documento. Per impostazione predefinita, il tipo di carattere ambiente è associato a un tipo di carattere di sistema che viene visualizzato come 9 pt Segoe interfaccia utente nelle versioni correnti di Windows. Uso di un tipo di carattere per tutti gli elementi dell'interfaccia aiuta a garantire un aspetto coerente del tipo di carattere nell'IDE.

- **Editor di testo** , ovvero gli elementi che superficie nel codice e altri editor basati su testo può essere personalizzato nell'Editor di testo nella pagina **strumenti > Opzioni**.

- **Raccolte specifiche** , ovvero le finestre di progettazione che offrono personalizzazione dell'utente dei rispettivi elementi di interfaccia può esporre i tipi di carattere specifici alla progettazione della superficie di attacco nella propria pagina delle impostazioni in **strumenti > Opzioni**.

### <a name="editor-font-customization-and-resizing"></a>Personalizzazione dell'editor del tipo di carattere e il ridimensionamento
 Gli utenti spesso saranno ingrandire o ingrandire le dimensioni e/o il colore del testo nell'editor in base alle loro preferenze, indipendenti dell'interfaccia utente generale. Poiché il tipo di carattere ambiente viene usato per gli elementi che possono essere visualizzate all'interno o come parte di un editor o la finestra di progettazione, è importante notare il comportamento previsto quando viene modificata una delle classificazioni seguenti del tipo di carattere.

 Durante la creazione non fa parte di elementi dell'interfaccia utente che vengono visualizzati nell'editor, ma sono le *contenuto*, è importante usare il tipo di carattere ambiente e non il tipo di carattere di testo in modo che gli elementi di ridimensionare in modo prevedibile.

1. Per il testo di codice nell'editor, ridimensionare con l'impostazione del tipo di carattere del testo codice e rispondere a livello di zoom del testo dell'editor.

2. Tutti gli altri elementi dell'interfaccia devono essere associati all'impostazione del tipo di carattere ambiente e riflettere le modifiche nell'ambiente globale. Ciò include (ma non limitata a):

    - Testo nel menu di scelta rapida

    - Testo in un'area di controllo dell'editor, ad esempio testo del menu lampadina, veloce trovare riquadro dell'editor e passare al riquadro

    - Testo dell'etichetta nelle finestre di dialogo, ad esempio Cerca nei file e il refactoring

### <a name="accessing-the-environment-font"></a>L'accesso al tipo di carattere ambiente
 Nel codice nativo o Windows Form, il tipo di carattere ambiente sono accessibili tramite il metodo **IUIHostLocale::GetDialogFont** dopo l'esecuzione di query l'interfaccia dal servizio SID_SUIHostLocale.

 Per Windows Presentation Foundation (WPF), derivare la classe di finestra di dialogo della shell **DialogWindow** classe invece di WPF **finestra** classe.

 In XAML, il codice di aspetto simile al seguente:

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 (Sostituire `Microsoft.VisualStudio.Shell.11.0` con la versione corrente della dll MPF.)

 Per visualizzare la finestra di dialogo, chiamare "**ShowModal ()** " nella classe failover **OpenFileDialog**. **ShowModal ()** imposta lo stato modale corretto nella shell, assicura la finestra di dialogo viene centrata nella finestra padre e così via.

 Il codice è indicato di seguito:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** restituisce un valore booleano? (valore booleano che ammette valori null) con i **DialogResult**, che può essere utilizzato se necessario. Il valore restituito è true se la finestra di dialogo è stata chiusa con **OK**.

 Se è necessario visualizzare alcuni UI WPF che non è una finestra di dialogo e ospitato in un proprio **HwndSource**, ad esempio una finestra popup o una finestra figlio WPF di una finestra di finestra padre Win32/Windows Form, è necessario impostare il **FontFamily**e **FontSize** nell'elemento radice dell'elemento WPF. (La shell imposta le proprietà nella finestra principale, ma non essere ereditate oltre un HWND). La shell fornisce risorse a cui possono essere associate le proprietà e simile al seguente:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="BKMK_Formatting"></a> Formattazione di riferimento (ridimensionamento/mettere in grassetto)
 Alcune finestre di dialogo richiedono particolare testo in grassetto o una dimensione diversa da quella di tipo di carattere ambiente. I tipi di carattere maggiori di carattere ambiente sono state in precedenza, codificato come "tipo di carattere ambiente + 2" o simili. Usando i frammenti di codice fornito supporterà i monitor ad alta risoluzione e assicurarsi che il testo di visualizzazione viene sempre visualizzata nel server di dimensioni corrette e peso (ad esempio chiaro o Semilight).

> **Nota: Prima di applicare la formattazione, verificare che si seguono le istruzioni disponibili nella [stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Per ridimensionare il tipo di carattere ambiente, impostare lo stile del controllo TextBlock o etichetta come indicato. Ognuno di questi frammenti di codice, se usati correttamente, verrà generato il tipo di carattere corretto, incluse le varianti appropriate per le dimensioni e peso.

 Dove "VsUI non è stato" è un riferimento allo spazio dei nomi Microsoft.VisualStudio.Shell:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>Tipo di carattere ambiente 375% + Light
 **Viene visualizzata come:** pt 34 Segoe UI Light

 **Utilizzo per:** (raro) univoco personalizzato dell'interfaccia utente, ad esempio la pagina iniziale

 **Codice procedurale:** Dove "textBlock" è un elemento TextBlock e "label" definito in precedenza è un'etichetta definita in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile del controllo TextBlock o etichetta come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>Tipo di carattere ambiente 310% + Light
 **Viene visualizzata come:** 28 pt Segoe UI Light

 **Utilizzo per:** titoli di finestra di dialogo firma di grandi dimensioni, nel report principali

 **Codice procedurale:** Dove "textBlock" è un elemento TextBlock e "label" definito in precedenza è un'etichetta definita in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile del controllo TextBlock o etichetta come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>Tipo di carattere ambiente 200% + Semilight
 **Viene visualizzata come:** 18 pt Segoe UI Semilight

 **Utilizzo per:** sottotitoli, titoli nelle finestre di dialogo di piccole e medie dimensioni

 **Codice procedurale:** Dove "textBlock" è un elemento TextBlock e "label" definito in precedenza è un'etichetta definita in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile del controllo TextBlock o etichetta come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>Tipo di carattere ambiente 155%
 **Viene visualizzata come:** 14 pt Segoe UI

 **Utilizzo per:** intestazioni di sezione nel documento e dell'interfaccia utente o i report

 **Codice procedurale:** Dove "textBlock" è un elemento TextBlock e "label" definito in precedenza è un'etichetta definita in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile del controllo TextBlock o etichetta come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>Tipo di carattere ambiente 133%
 **Viene visualizzata come:** 12 pt Segoe UI

 **Utilizzo per:** più piccole sezioni in finestre di dialogo firma e documenti e dell'interfaccia utente

 **Codice procedurale:** Dove "textBlock" è un elemento TextBlock e "label" definito in precedenza è un'etichetta definita in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile del controllo TextBlock o etichetta come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>Tipo di carattere ambiente 122%
 **Viene visualizzata come:** 11 pt Segoe UI

 **Utilizzo per:** sezione intestazioni nelle finestre di dialogo firma, dall'alto nodi nella visualizzazione ad albero, navigazione tramite tabulazione verticale

 **Codice procedurale:** Dove "textBlock" è un elemento TextBlock e "label" definito in precedenza è un'etichetta definita in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile del controllo TextBlock o etichetta come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto
 **Viene visualizzato come:** in grassetto pt 9 Segoe interfaccia utente

 **Utilizzo per:** etichette e sottotitoli nel documento, report e le finestre di dialogo firma anche l'interfaccia utente

 **Codice procedurale:** Dove "textBlock" è un elemento TextBlock e "label" definito in precedenza è un'etichetta definita in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** Impostare lo stile del controllo TextBlock o etichetta come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Stili localizzabili
 In alcuni casi, i localizzatori saranno necessario modificare gli stili dei caratteri per impostazioni locali diverse, ad esempio la rimozione di mettere in grassetto dal testo per lingue dell'Asia orientale. Per rendere possibile la localizzazione degli stili di carattere, tali stili devono essere all'interno del file con estensione resx. Il modo migliore per eseguire questa operazione e comunque modificare gli stili dei caratteri in Progettazione Windows form Visual Studio consiste nell'impostare in modo esplicito gli stili di carattere in fase di progettazione. Anche se si crea un oggetto completo del tipo di carattere e potrebbe sembrare per interrompere l'ereditarietà dei tipi di carattere padre, solo la proprietà FontStyle consente di impostare il tipo di carattere.

 La soluzione consiste nell'associare il form di finestra di dialogo **FontChanged** evento. Nel **FontChanged** evento, esaminare tutti i controlli e controllare se il carattere è impostato. Se è impostata, modificarlo in un nuovo tipo di carattere basata carattere del modulo e lo stile del controllo precedente. È un esempio di questo nel codice:

```
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

 Tramite questo codice garantisce che, quando tipo di carattere del form viene aggiornato, verrà aggiornato anche i tipi di carattere dei controlli. Questo metodo deve anche essere chiamato dal costruttore del form, perché la finestra di dialogo potrebbe non riuscire a ottenere un'istanza di **implementa IUIService** e il **FontChanged** evento non verrà mai attivato. Eseguire l'hook **FontChanged** consentirà le finestre di dialogo prelevare dinamicamente il nuovo tipo di carattere, anche se la finestra di dialogo è già aperto.

### <a name="testing-the-environment-font"></a>Il tipo di carattere ambiente di test
 Per assicurarsi che l'interfaccia utente utilizza il tipo di carattere ambiente e rispetta le impostazioni della dimensione, aprire **strumenti > Opzioni > ambiente > tipi di carattere e colori** e selezionare "Tipo di carattere ambiente" nel "Mostra impostazioni per:" menu a discesa.

 ![Pagina tipi di carattere e colori in strumenti di &#62; finestra di dialogo Opzioni](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201 a_OptionsFonts")

 **Le impostazioni di tipi di carattere e colori in Strumenti > finestra di dialogo Opzioni**

 Impostare il tipo di carattere a un elemento molto diverso da quello predefinito. Per rendere più ovvio che non vengono aggiornate dell'interfaccia utente, scegliere un tipo di carattere con grazie (ad esempio "Times New Roman") e impostare le dimensioni molto grandi. Testare quindi l'interfaccia utente per garantire che rispetta l'ambiente. Di seguito è riportato un esempio con la finestra di dialogo licenza:

 ![Esempio di finestra di dialogo non utilizzando il tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201 b_WrongFontDialog")

 **Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere ambiente**

 In questo caso, "Informazioni utente" e "Informazioni sul prodotto" sono non rispettano il tipo di carattere. In alcuni casi potrebbe trattarsi di una scelta di progettare in modo esplicito, ma può trattarsi di un bug, se il tipo di carattere esplicito non viene specificato come parte delle specifiche con linea rossa.

 Per reimpostare il tipo di carattere, fare clic su "Usa impostazioni predefinite" in **strumenti > Opzioni > ambiente > tipi di carattere e colori**.

## <a name="BKMK_TextStyle"></a> Stile del testo
 Stile del testo fa riferimento a maiuscole e minuscole, peso e dimensioni del carattere. Per informazioni aggiuntive sull'implementazione, vedere [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Testo maiuscolo

#### <a name="all-caps"></a>Tutte maiuscole
 Non utilizzare tutte maiuscole per i titoli o le etichette in Visual Studio.

#### <a name="all-lowercase"></a>Tutto minuscole
 Non usare solo lettere minuscole per i titoli o le etichette in Visual Studio.

#### <a name="sentence-and-title-case"></a>Case di frase e titolo
 Testo in Visual Studio debba usare tutte iniziali maiuscole o maiuscola, a seconda della situazione.

|Usare tutte iniziali maiuscole per:|Usare maiuscola per:|
|-------------------------|----------------------------|
|Titoli di finestra di dialogo|Etichette|
|Caselle di gruppo|Caselle di controllo|
|Voci di menu|Pulsanti di opzione|
|Voci del menu di scelta rapida|Elementi casella di riepilogo|
|Pulsanti|Barre di stato|
|In una tabella pivot||
|Intestazioni di colonna||
|Tooltips||

##### <a name="title-case"></a>Iniziali maiuscole
 Iniziali maiuscole sono uno stile in cui sono in maiuscolo le prime lettere della maggior parte o tutte le parole all'interno di una frase. In Visual Studio, tutte iniziali maiuscole viene usata per molti elementi, tra cui:

- **Descrizioni comandi.** Esempio: "Anteprima elementi selezionati"

- **Intestazioni di colonna.** Esempio: "Risposta di sistema"

- **Voci di menu.** Esempio: "Salva tutto"

  Quando si usano tutte iniziali maiuscole, queste sono le linee guida per i casi da convertire in maiuscolo parole o lasciare le lettere minuscole:

|Maiuscole|I commenti e gli esempi|
|---------------|---------------------------|
|Tutti i sostantivi||
|Tutti i verbi|Tra cui "Is" e altre forme di "per essere"|
|Avverbi tutti|Che includono "Di" e ""|
|Tutti gli aggettivi|Tra cui "This" e "Cui"|
|Tutti i pronomi|Tra cui l'impropri "Relativo" anche essendo"," una contrazione del Pronome "it" e il verbo "is"|
|Parole e il cognome, indipendentemente dalle parti del discorso||
|Preposizioni che fanno parte di una frase verbale|"La chiusura di tutti i Windows" o "In corso l'arresto del sistema"|
|Tutte le lettere di un acronimo|HTML, XML, URL, IDE, RGB|
|La seconda parola in una parola composta se si tratta di un sostantivo o aggettivo appropriato o se le parole hanno lo stesso peso|Riferimento incrociato, prodotti Software pre-Microsoft, accesso di lettura/scrittura, in fase di esecuzione|

|Minuscole|Esempi|
|---------------|--------------|
|La seconda parola in una parola composta se si tratta di un'altra parte del discorso o un participio modifica la prima parola|Procedure, come derivazione|
|Articoli, a meno che uno è la prima parola nel titolo|un oggetto, un oggetto, il|
|Congiunzioni coordinate|e, ma, per, e non, o|
|Preposizioni con parole di un massimo di quattro lettere di fuori di una frase verbale|in, in, come per rifiutarla, nella parte superiore del|
|"A" quando utilizzato in una frase infinita che|"Come formattare il disco rigido"|

##### <a name="sentence-case"></a>Maiuscola
 Maiuscola è il metodo di utilizzo delle maiuscole standard per la scrittura in cui ha iniziale maiuscola solo la prima parola della frase, insieme a eventuali nomi propri e il Pronome "I". In generale, maiuscola è più semplice per un gruppo di destinatari in tutto il mondo per la lettura, in particolare quando il contenuto verrà convertito da un computer. Usare maiuscola per:

1. **Messaggi della barra di stato.** Queste sono semplici, short e fornire solo informazioni sullo stato. Esempio: "Caricamento dei file di progetto"

2. **Tutti gli altri elementi dell'interfaccia utente**, tra cui le etichette, caselle di controllo, pulsanti di opzione ed elencare elementi casella. Esempio: "Seleziona tutti gli elementi nell'elenco"

### <a name="text-formatting"></a>Formattazione del testo
 Testo predefinito di formattazione in Visual Studio 2013 è controllato da un [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Questo servizio aiuta a garantire un aspetto coerente del tipo di carattere dell'IDE (integrated development environment) ed è necessario usarlo per garantire un'esperienza coerente per gli utenti.

 La dimensione predefinita utilizzata dal servizio del tipo di carattere di Visual Studio provenienza da Windows e viene visualizzato come 9 pt.

 È possibile applicare la formattazione per il tipo di carattere ambiente. Questo argomento illustra come e dove usare stili. Per informazioni sull'implementazione, vedere [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Testo in grassetto
 Testo in grassetto viene usato con cautela in Visual Studio e deve essere riservato anche per:

- etichette di domanda nelle procedure guidate

- che designa il progetto attivo in Esplora soluzioni

- valori sottoposti a override nella finestra degli strumenti proprietà

- alcuni eventi negli elenchi a discesa editor di Visual Basic

- generati dal server di contenuti nella struttura documento per le pagine web

- intestazioni delle sezioni nella finestra di dialogo complessa o finestra di progettazione dell'interfaccia utente

#### <a name="italics"></a>Corsivo
 Visual Studio non usa corsivo o visualizzato in grassetto il testo in corsivo.

#### <a name="color"></a>Colore

- Blu è riservato per i collegamenti ipertestuali (spostamento e l'esecuzione di comandi) e non deve mai essere usata per l'orientamento.

- Le intestazioni di dimensioni maggiori (tipo di carattere ambiente 155% o superiore) possono essere colorate per questi scopi:

  - Per fornire l'impatto visivo alla firma dell'interfaccia utente di Visual Studio

  - Per attirare l'attenzione su un'area specifica

  - Per offrire una maggiore efficacia dal colore del testo standard ambiente/nero grigio scuro

- Colore nelle intestazioni deve sfruttare Visual Studio esistente marchio colori, principalmente il principale viola, & FF68217A.

- Quando si Usa colore nelle intestazioni, è necessario rispettare le [Windows colorare le linee guida](https://msdn.microsoft.com/library/dn742482.aspx), tra cui contrasto e altre considerazioni sull'accessibilità.

### <a name="font-size"></a>Dimensione carattere
 Progettazione di Visual Studio dell'interfaccia utente presenta un aspetto più leggero con più spazi. Dove possibile, le barre del titolo e chrome sono state ridotte o rimosse. Densità di informazioni è un requisito in Visual Studio, tipografia continua a essere importanti, grazie a un'enfasi sulla interlinea più aperta e una variante dei pesi e le dimensioni dei caratteri.

 Nella tabella seguente sono inclusi i dettagli di progettazione ed esempi visivi per i tipi di carattere visualizzazione usate in Visual Studio. Alcune varianti del tipo di carattere visualizzazione abbiano sia le dimensioni e peso, ad esempio Semilight o Light, codificato nel proprio aspetto.

 Frammenti di codice di implementazione per tutti i tipi di carattere visualizzazione sono reperibile nel [formattazione di riferimento (ridimensionamento/mettere in grassetto)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>Tipo di carattere ambiente 375% + Light

|||
|-|-|
|**Utilizzo:** Rari. Univoco personalizzato solo interfaccia utente.<br /><br /> **Eseguire:**<br /><br /> -Usare maiuscola<br />: Viene sempre utilizzato leggero<br /><br /> **Non:**<br /><br /> -Usare per l'interfaccia utente diversa da firma dell'interfaccia utente, ad esempio pagina iniziale<br />-Grassetto, corsivo o grassetto corsivo<br />-Usare per il corpo del testo<br />-Usare nelle finestre degli strumenti|**Viene visualizzata come:** pt 34 Segoe UI Light<br /><br /> **Esempio visivo:**<br /><br /> *Attualmente non usato. Possono essere utilizzati nella pagina iniziale.*|

#### <a name="310-environment-font--light"></a>Tipo di carattere ambiente 310% + Light

|||
|-|-|
|**Utilizzo:**<br /><br /> -Intestazione maggiori nelle finestre di dialogo firma<br />-Intestazione di report principale<br /><br /> **Eseguire:**<br /><br /> -Usare maiuscola<br />: Viene sempre utilizzato leggero<br /><br /> **Non:**<br /><br /> -Usare per l'interfaccia utente diversa da firma dell'interfaccia utente, ad esempio pagina iniziale<br />-Grassetto, corsivo o grassetto corsivo<br />-Usare per il corpo del testo<br />-Usare nelle finestre degli strumenti|**Viene visualizzata come:** 28 pt Segoe UI Light<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente 310% &#43; intestazione Light](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202 a_EF310")|

#### <a name="200-environment-font--semilight"></a>Tipo di carattere ambiente 200% + Semilight

|||
|-|-|
|**Utilizzo:**<br /><br /> -Sottotitoli<br />-Titoli nelle finestre di dialogo di piccole e medie dimensioni<br /><br /> **Eseguire:**<br /><br /> -Usare maiuscola<br />-Sempre usare il peso Semilight<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto corsivo<br />-Usare per il corpo del testo<br />-Usare nelle finestre degli strumenti|**Viene visualizzata come:** 18 pt Segoe UI Semillight<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202 b_EF200")|

#### <a name="155-environment-font"></a>Tipo di carattere ambiente 155%

|||
|-|-|
|**Utilizzo:**<br /><br /> -Intestazioni di sezione nel documento e dell'interfaccia utente<br />-Report<br /><br /> **Eseguire:** Caso d'uso di frase<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto corsivo<br />-Usare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Viene visualizzata come:** 14 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione del tipo di carattere ambiente 155%](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202 c_EF155")|

#### <a name="133-environment-font"></a>Tipo di carattere ambiente 133%

|||
|-|-|
|**Utilizzo:**<br /><br /> -Più piccole sezioni in finestre di dialogo firma<br />-Sottotitoli inferiori nel documento e dell'interfaccia utente<br /><br /> **Eseguire:** Caso d'uso di frase<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto corsivo<br />-Usare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Viene visualizzata come:** 12 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione del tipo di carattere ambiente 133%](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202 d_EF133")|

#### <a name="122-environment-font"></a>Tipo di carattere ambiente 122%

|||
|-|-|
|**Utilizzo:**<br /><br /> -Intestazioni di sezione nelle finestre di dialogo firma<br />-Primi nodi nella visualizzazione ad albero<br />-Navigazione tramite tabulazione verticale<br /><br /> **Eseguire:** Caso d'uso di frase<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto corsivo<br />-Usare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Viene visualizzata come:** 11 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione del tipo di carattere ambiente 122%](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202 e_EF122")|

#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto

|||
|-|-|
|**Utilizzo:**<br /><br /> -Le etichette e i sottotitoli nelle finestre di dialogo firma<br />-Le etichette e i sottotitoli nei report<br />-Le etichette, nonché di sottotitoli nel documento dell'interfaccia utente<br /><br /> **Eseguire:**<br /><br /> -Usare maiuscola<br />-Usare il peso in grassetto<br /><br /> **Non:**<br /><br /> -Corsivo o grassetto corsivo<br />-Usare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Usare nelle finestre degli strumenti|**Viene visualizzato come:** in grassetto pt 9 Segoe interfaccia utente<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente &#43; intestazione grassetto](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202 f_EFB")|

#### <a name="environment-font"></a>Tipo di carattere ambiente

|||
|-|-|
|**Utilizzo:** Qualsiasi altro testo<br /><br /> **Eseguire:** Caso d'uso di frase<br /><br /> **Non:** Corsivo in grassetto o corsivo|**Viene visualizzata come:** 9 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202 g_EF")|

### <a name="padding-and-spacing"></a>Spaziatura interna e la spaziatura
 Intestazioni richiedono spazio attorno a esse per concedere loro l'enfasi appropriato. Questo spazio varia a seconda delle dimensioni del punto e cos'altro è in prossimità di intestazione, ad esempio una regola orizzontale o di una riga di testo nel tipo di carattere ambiente.

- La spaziatura interna ideale per un'intestazione di per sé deve essere 90% dello spazio di altezza di carattere capitale. Ad esempio, un'intestazione di Segoe UI Light pt 28 ha un'altezza di limite di 26 pt e la spaziatura interna deve essere circa 23 pt, o circa 31 pixel.

- Lo spazio intorno a un'intestazione minimo pari al 50% dell'altezza del carattere capitale. Meno spazio può essere utilizzata quando un'intestazione è accompagnata da una regola o un altro elemento di una stretta adattamento.

- Testo del carattere di ambiente in grassetto deve seguire la spaziatura interna e spaziatura altezza riga predefinita.

## <a name="see-also"></a>Vedere anche
 [MSDN: I tipi di carattere (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: Testo dell'interfaccia utente (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
