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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302413"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Tipi di carattere e formattazione per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>Il tipo di carattere dell'ambiente
 Tutti i tipi di carattere all'interno di Visual Studio devono essere esposti all'utente per la personalizzazione. Questa operazione viene eseguita principalmente tramite la pagina **Tipi di carattere e colori** nella finestra di dialogo Strumenti > **Opzioni.** Le tre categorie principali di impostazioni dei caratteri sono:

- **Tipo di carattere** dell'ambiente: il tipo di carattere principale per l'IDE (ambiente di sviluppo integrato), utilizzato per tutti gli elementi dell'interfaccia, incluse le finestre di dialogo, i menu, le finestre degli strumenti e le finestre di documento. Per impostazione predefinita, il tipo di carattere dell'ambiente è collegato a un tipo di carattere di sistema che viene visualizzato come 9 pt Segoe UI nelle versioni correnti di Windows. L'utilizzo di un tipo di carattere per tutti gli elementi dell'interfaccia consente di garantire un aspetto coerente del tipo di carattere in tutto l'IDE.

- Editor di **testo:** gli elementi che escano nel codice e in altri editor basati su testo possono essere personalizzati nella pagina Editor di testo in **Strumenti > Opzioni**.

- **Raccolte specifiche:** le finestre di progettazione che offrono la personalizzazione dell'interfaccia dell'utente possono esporre tipi di carattere specifici per l'area di progettazione nella propria pagina delle impostazioni in **Strumenti > Opzioni**.

### <a name="editor-font-customization-and-resizing"></a>Personalizzazione e ridimensionamento dei caratteri dell'editor
 Gli utenti spesso ingrandiscono o ingrandiscono le dimensioni e/o il colore del testo nell'editor in base alle loro preferenze, indipendentemente dall'interfaccia utente generale. Poiché il tipo di carattere dell'ambiente viene utilizzato negli elementi che potrebbero essere visualizzati all'interno o come parte di un editor/designer, è importante notare il comportamento previsto quando viene modificata una di queste classificazioni dei tipi di carattere.

 Quando si creano elementi dell'interfaccia utente che vengono visualizzati nell'editor ma non fanno parte del *contenuto*, è importante utilizzare il tipo di carattere dell'ambiente e non il tipo di carattere del testo in modo che gli elementi vengano ridimensionati in modo prevedibile.

1. Per il testo di codice nell'editor, ridimensionate con l'impostazione del carattere del testo del codice e rispondete al livello di zoom del testo dell'editor.

2. Tutti gli altri elementi dell'interfaccia devono essere legati all'impostazione del tipo di carattere dell'ambiente e rispondere a eventuali modifiche globali nell'ambiente. Ciò include (ma non è limitato a):

    - Testo nei menu di scelta rapida

    - Testo in un'area di controllo dell'editor, ad esempio il testo del menu lampadina, il riquadro dell'editor di ricerca rapida e passare al riquadro

    - Etichettare il testo nelle finestre di dialogo, ad esempio Trova nei file o Effettua refactoring

### <a name="accessing-the-environment-font"></a>Accesso al tipo di carattere dell'ambiente
 Nel codice nativo o WinForms, è possibile accedere al tipo di carattere dell'ambiente chiamando il metodo **IUIHostLocale::GetDialogFont** dopo l'esecuzione di query sull'interfaccia dal servizio SID_SUIHostLocale.

 Per Windows Presentation Foundation (WPF), derivare la classe della finestra di dialogo dalla classe **DialogWindow** della shell anziché dalla classe **Window** di WPF.

 In XAML, il codice è simile al seguente:In XAML, the code looks like this:

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

 Per visualizzare la finestra di dialogo, chiamare "**ShowModal()**" sulla classe tramite **ShowDialog()**. **ShowModal()** imposta lo stato modale corretto nella shell, assicura che la finestra di dialogo sia centrata nella finestra padre e così via.

 Il codice è indicato di seguito:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** restituisce un valore bool? (booleano nullable) con **DialogResult**, che può essere utilizzato se necessario. Il valore restituito è true se la finestra di dialogo è stata chiusa con **OK**.

 Se è necessario visualizzare un'interfaccia utente WPF che non è una finestra di dialogo ed è ospitata nel proprio **HwndSource**, ad esempio una finestra popup o una finestra figlio WPF di una finestra padre Win32/WinForms, è necessario impostare **il FontFamily** e **FontSize** sull'elemento radice dell'elemento WPF. (La shell imposta le proprietà nella finestra principale, ma non verranno ereditate oltre un HWND). La shell fornisce le risorse a cui le proprietà possono essere associate, in questo modo:The shell provides resources to which the properties can be bound, like this:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Riferimento alla formattazione (ridimensionamento/ridimensionamento)
 Alcune finestre di dialogo richiedono che un testo specifico sia in grassetto o una dimensione diversa dal tipo di carattere dell'ambiente. In precedenza, i tipi di carattere più grandi del tipo di carattere dell'ambiente erano codificati come "font dell'ambiente n. 2" o simili. L'utilizzo dei frammenti di codice forniti supporterà i monitor DPI ad alta risoluzione e garantirà che il testo visualizzato venga sempre visualizzato con le dimensioni e il peso corretti (ad esempio Light o Semilight).

> **Nota: prima di applicare la formattazione, assicurarsi di seguire le indicazioni disponibili in [Stile testo.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)**

 Per ridimensionare il tipo di carattere dell'ambiente, impostate lo stile di TextBlock o Label come indicato. Ognuno di questi frammenti di codice, utilizzato correttamente, genererà il tipo di carattere corretto, incluse le dimensioni appropriate e le variazioni di peso.

 Dove "vsui" è un riferimento allo spazio dei nomi Microsoft.VisualStudio.Shell:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>375% Tipo di carattere ambiente - Luce
 **Appare come:** 34 pt Segoe UI Light

 **Usa per:** (rara) un'interfaccia utente di marca unica, ad esempio nella pagina iniziale

 **Codice procedurale:** Dove "textBlock" è un TextBlock definito in precedenza e "label" è un Label definito in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>310% Tipo di carattere dell'ambiente - Luce
 **Appare come:** 28 pt Segoe UI Light

 **Usa per:** titoli di finestra di dialogo con firma grande, intestazione principale nei report

 **Codice procedurale:** Dove "textBlock" è un TextBlock definito in precedenza e "label" è un Label definito in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>Carattere ambiente 200% - Semiluce
 **Appare come:** 18 pt Segoe UI Semilight

 **Usa per:** sottotitoli, titoli in finestre di dialogo di piccole e medie dimensioni

 **Codice procedurale:** Dove "textBlock" è un TextBlock definito in precedenza e "label" è un Label definito in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>155% Tipo di carattere ambiente
 **Appare come:** 14 pt Segoe UI

 **Usa per:** intestazioni di sezione nell'interfaccia utente o nei report del riquadro dei documenti

 **Codice procedurale:** Dove "textBlock" è un TextBlock definito in precedenza e "label" è un Label definito in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>133% Tipo di carattere ambiente
 **Appare come:** 12 pt Segoe UI

 **Usa per:** sottotitoli più piccoli nelle finestre di dialogo della firma e nell'interfaccia utente del documento

 **Codice procedurale:** Dove "textBlock" è un TextBlock definito in precedenza e "label" è un Label definito in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>122% Tipo di carattere ambiente
 **Appare come:** 11 pt Segoe UI

 **Usa per:** intestazioni di sezione nelle finestre di dialogo delle firme, nodi superiori nella visualizzazione albero, navigazione verticale nelle schede

 **Codice procedurale:** Dove "textBlock" è un TextBlock definito in precedenza e "label" è un Label definito in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Tipo di carattere dell'ambiente - grassetto
 **Appare come:** in grassetto 9 pt Segoe UI

 **Usa per:** etichette e sottotitoli nelle finestre di dialogo della firma, nei report e nell'interfaccia utente dei documenti

 **Codice procedurale:** Dove "textBlock" è un TextBlock definito in precedenza e "label" è un Label definito in precedenza.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** Impostare lo stile di TextBlock o Label come illustrato.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Stili localizzabili
 In alcuni casi, i localizzatori dovranno modificare gli stili dei caratteri per impostazioni locali diverse, ad esempio rimuovendo il grassetto dal testo per le lingue dell'Asia orientale. Per rendere possibile la localizzazione degli stili di carattere, tali stili devono trovarsi all'interno del file RESX. Il modo migliore per eseguire questa operazione e modificare comunque gli stili dei tipi di carattere nella finestra di progettazione del modulo di Visual Studio consiste nell'impostare in modo esplicito gli stili dei tipi di carattere in fase di progettazione. Anche se questo crea un oggetto font completo e potrebbe sembrare interrompere l'ereditarietà dei font padre, solo il FontStyle proprietà viene utilizzata per impostare il tipo di carattere.

 La soluzione consiste nell'associare il form della finestra di dialogo **FontChanged** evento. Nell'evento **FontChanged,** esaminare tutti i controlli e verificare se il tipo di carattere è impostato. Se è impostato, modificarlo in un nuovo tipo di carattere basato sul tipo di carattere del form e sullo stile di carattere precedente del controllo. Un esempio di questo nel codice è:An example of this in code is:

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

 L'utilizzo di questo codice garantisce che quando il tipo di carattere del form viene aggiornato, verranno aggiornati anche i tipi di carattere dei controlli. Questo metodo deve essere chiamato anche dal costruttore del form, perché la finestra di dialogo potrebbe non riuscire a ottenere un'istanza di **IUIService** e l'evento **FontChanged** non verrà mai generato. Hooking **FontChanged** consentirà alle finestre di dialogo di selezionare dinamicamente il nuovo tipo di carattere anche se la finestra di dialogo è già aperta.

### <a name="testing-the-environment-font"></a>Test del tipo di carattere dell'ambiente
 Per assicurarti che l'interfaccia utente utilizzi il tipo di carattere dell'ambiente e rispetti le impostazioni delle dimensioni, apri **Opzioni > > Ambiente > tipi di** carattere e colori e seleziona "Carattere ambiente" nel menu a discesa "Mostra impostazioni per:".

 ![Pagina Tipi di carattere e colori nella finestra di dialogo Opzioni &#62; strumenti](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-a_OptionsFonts")

 **Impostazioni Tipi di carattere e colori nella finestra di dialogo Opzioni > Strumenti**

 Impostare il tipo di carattere su un nome molto diverso da quello predefinito. Per rendere evidente quale interfaccia utente non viene aggiornata, scegliere un tipo di carattere con serif (ad esempio "Times New Roman") e impostare una dimensione molto grande. Quindi testare l'interfaccia utente per assicurarsi che rispetti l'ambiente. Di seguito è riportato un esempio di utilizzo della finestra di dialogo della licenza:Here is an example using the license dialog:

 ![Esempio di finestra di dialogo che non usa il tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-b_WrongFontDialog")

 **Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere dell'ambiente**

 In questo caso, "Informazioni utente" e "Informazioni sul prodotto" non rispettano il tipo di carattere. In alcuni casi potrebbe trattarsi di una scelta di progettazione esplicita, ma può essere un bug se il tipo di carattere esplicito non è specificato come parte delle specifiche redline.

 Per reimpostare il tipo di carattere, fare clic su "Usa impostazioni predefinite" in **Strumenti > Opzioni > Ambiente > colori**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Stile testo
 Lo stile del testo si riferisce alla dimensione, allo spessore e all'uso di maiuscole e minuscole del carattere. Per istruzioni sull'implementazione, vedere Tipo di [carattere dell'ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Maiuscole/minuscole del testo

#### <a name="all-caps"></a>Tutti i tappi
 Non usare tutte maiuscole per titoli o etichette in Visual Studio.

#### <a name="all-lowercase"></a>Tutte minuscole
 Non usare tutti i caratteri minuscoli per titoli o etichette in Visual Studio.

#### <a name="sentence-and-title-case"></a>Frase e maiuscole/minuscole
 Il testo in Visual Studio deve usare la combinazione di maiuscole e minuscole o una combinazione di maiuscole e minuscole, a seconda della situazione.

|Usa custodia titolo per:|Usa la distinzione tra maiuscole e minuscole per:|
|-------------------------|----------------------------|
|Titoli delle finestre di dialogo|Etichette|
|Caselle di gruppo|Caselle di controllo|
|Voci di menu|Pulsanti di opzione|
|Voci del menu di scelta rapida|Elementi della casella di riepilogo|
|Pulsanti|Barre di stato|
|Etichette tabella||
|Intestazioni di colonna||
|Tooltips||

##### <a name="title-case"></a>Iniziali maiuscole
 La custodia del titolo è uno stile in cui le prime lettere della maggior parte o di tutte le parole all'interno di una frase sono in maiuscolo. In Visual Studio, il caso del titolo viene usato per molti elementi, tra cui:In Visual Studio, title case is used for many items, including:

- **Le descrizioni comandi.** Esempio: "Anteprima elementi selezionati"

- **Intestazioni di colonna.** Esempio: "Risposta del sistema"

- **Voci di menu.** Esempio: "Salva tutto"

  Quando si utilizza la combinazione di maiuscole/minuscole, queste sono le linee guida per le lettere maiuscole e quando lasciarle minuscole:

|Maiuscolo|Commenti ed esempi|
|---------------|---------------------------|
|Tutti i sostantivi||
|Tutti i verbi|Tra cui "Is" e altre forme di "essere"|
|Tutti gli avverbi|Inclusi "Than" e "Quando"|
|Tutti gli aggettivi|Compresi "This" e "That"|
|Tutti i pronomi|Compreso il "Its" possessivo e "It's", una contrazione del pronome "it" e il verbo "è"|
|Prima e ultima parola, indipendentemente da parti del discorso||
|Preposizioni che fanno parte di una frase verbale|"Chiusura di tutte le finestre" o "Arresto del sistema"|
|Tutte le lettere di un acronimo|HTML, XML, URL, IDE, RGB|
|La seconda parola in una parola composta se è un sostantivo o un aggettivo adeguato, o se le parole hanno lo stesso peso|Cross-Reference, Software pre-Microsoft, Accesso in lettura/scrittura, Runtime|

|Lettere minuscole|Esempi|
|---------------|--------------|
|La seconda parola in una parola composta se è un'altra parte del discorso o un participio che modifica la prima parola|Come fare, decollare|
|Articoli, a meno che non sia la prima parola nel titolo|un, uno, una, il, lo, la, i, gli, le|
|Coordinare le congiunzioni|e, ma, per, né, né|
|Preposizioni con parole di quattro o meno lettere al di fuori di una frase verbale|in, su, come per, fuori, in cima|
|"A" quando viene utilizzato in una frase infinita|"Come formattare il disco rigido"|

##### <a name="sentence-case"></a>Caso di frase
 Il caso della frase è il metodo di capitalizzazione standard per la scrittura in cui solo la prima parola della frase è maiuscola, insieme a eventuali nomi propri e al pronome "I". In generale, il caso della frase è più facile da leggere per un pubblico mondiale, soprattutto quando il contenuto sarà tradotto da una macchina. Usa la distinzione tra maiuscole e minuscole per:

1. **Messaggi della barra di stato.** Questi sono semplici, brevi e forniscono solo informazioni sullo stato. Esempio: "Caricamento del file di progetto"

2. **Tutti gli altri elementi dell'interfaccia utente,** incluse etichette, caselle di controllo, pulsanti di opzione ed elementi della casella di riepilogo. Esempio: "Seleziona tutti gli elementi nell'elenco"

### <a name="text-formatting"></a>Formattazione del testo
 La formattazione predefinita del testo in Visual Studio 2013 è controllata da un tipo di [carattere di ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Questo servizio consente di garantire un aspetto coerente del carattere in tutto l'IDE (ambiente di sviluppo integrato) ed è necessario utilizzarlo per garantire un'esperienza coerente per gli utenti.

 La dimensione predefinita utilizzata dal servizio tipi di carattere di Visual Studio proviene da Windows e viene visualizzata come 9 pt.

 È possibile applicare la formattazione al tipo di carattere dell'ambiente. In questo argomento viene illustrato come e dove utilizzare gli stili. Per informazioni sull'implementazione, fare riferimento a Tipo di [carattere dell'ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Grassetto
 Il testo in grassetto viene usato con parsimonia in Visual Studio e deve essere riservato per:Bold text is used sparingly in Visual Studio and should be reserved for:

- etichette di domande nelle procedure guidate

- designazione del progetto attivo in Esplora soluzioni

- valori sottoposti a override nella finestra degli strumenti Proprietà

- alcuni eventi negli elenchi a discesa dell'editor di Visual Basic

- contenuto generato dal server nella struttura del documento per le pagine Web

- intestazioni di sezione nell'interfaccia utente complessa della finestra di dialogo o della finestra di progettazione

#### <a name="italics"></a>corsivo
 Visual Studio non utilizza testo in corsivo o in grassetto.

#### <a name="color"></a>Colore

- Il blu è riservato ai collegamenti ipertestuali (navigazione e comandi) e non deve mai essere utilizzato per l'orientamento.

- Le intestazioni più grandi (carattere ambiente x 155% o superiore) possono essere colorate per questi scopi:

  - To provide visual appeal to signature Visual Studio UI

  - Per richiamare l'attenzione su un'area specifica

  - Per offrire sollievo dal colore standard del testo dell'ambiente grigio scuro/nero

- Il colore nelle intestazioni deve sfruttare i colori del marchio Visual Studio esistenti, principalmente il viola principale, #FF68217A.

- Quando si utilizza il colore nelle intestazioni, è necessario rispettare le linee guida per i colori di [Windows,](https://msdn.microsoft.com/library/dn742482.aspx)inclusi il rapporto di contrasto e altre considerazioni sull'accessibilità.

### <a name="font-size"></a>Dimensioni carattere
 La progettazione dell'interfaccia utente di Visual Studio presenta un aspetto più chiaro con più spazi vuoti. Se possibile, le barre cromate e del titolo sono state ridotte o rimosse. Mentre la densità delle informazioni è un requisito in Visual Studio, la tipografia continua ad essere importante, con un'enfasi sull'interlinea più aperta e una variazione delle dimensioni e degli spessori dei caratteri.

 The tables below includes design details and visual examples for the display fonts used in Visual Studio. Alcune varianti dei font di visualizzazione hanno sia la dimensione che lo spessore, come Semiluce o Luce, codificati nel loro aspetto.

 I frammenti di codice di implementazione per tutti i tipi di carattere di visualizzazione sono disponibili in [Formattazione (ridimensionamento/grassetto) di riferimento](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>375% Tipo di carattere ambiente - Luce

|||
|-|-|
|**Utilizzo:** Raro. Solo interfaccia utente con marchio univoco.<br /><br /> **fare:**<br /><br /> - Usa caso frase<br />- Utilizzare sempre Peso leggero<br /><br /> **Non:**<br /><br /> - Utilizzare per l'interfaccia utente diversa dall'interfaccia utente della firma, ad esempio pagina iniziale-Use for UI other than signature UI such as Start Page<br />- Grassetto, corsivo o grassetto corsivo<br />- Utilizzare per il corpo del testo<br />- Utilizzare nelle finestre degli strumenti|**Appare come:** 34 pt Segoe UI Light<br /><br /> **Esempio visivo:**<br /><br /> *Attualmente non utilizzato. Può essere utilizzato nella pagina iniziale.*|

#### <a name="310-environment-font--light"></a>310% Tipo di carattere dell'ambiente - Luce

|||
|-|-|
|**Utilizzo:**<br /><br /> - Intestazione più grande nelle finestre di dialogo della firma<br />- Intestazione del rapporto principale<br /><br /> **fare:**<br /><br /> - Usa caso frase<br />- Utilizzare sempre Peso leggero<br /><br /> **Non:**<br /><br /> - Utilizzare per l'interfaccia utente diversa dall'interfaccia utente della firma, ad esempio pagina iniziale-Use for UI other than signature UI such as Start Page<br />- Grassetto, corsivo o grassetto corsivo<br />- Utilizzare per il corpo del testo<br />- Utilizzare nelle finestre degli strumenti|**Appare come:** 28 pt Segoe UI Light<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di carattere 310% Ambiente &#43; Intestazione luce](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|

#### <a name="200-environment-font--semilight"></a>Carattere ambiente 200% - Semiluce

|||
|-|-|
|**Utilizzo:**<br /><br /> - Sottotitoli<br />- Titoli in finestre di dialogo piccole e medie<br /><br /> **fare:**<br /><br /> - Usa caso frase<br />- Utilizzare sempre il peso Semilight<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o grassetto corsivo<br />- Utilizzare per il corpo del testo<br />- Utilizzare nelle finestre degli strumenti|**Appare come:** 18 pt Segoe UI Semillight<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di carattere 200% Environment &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% Tipo di carattere ambiente

|||
|-|-|
|**Utilizzo:**<br /><br /> - Intestazioni di sezione nell'interfaccia utente del documento<br />- Rapporti<br /><br /> **Procedere come:** Usa maiuscole/minuscole frasi<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o grassetto corsivo<br />- Utilizzare per il corpo del testo<br />- Utilizzare nei controlli standard di Visual Studio- Use in standard Visual Studio controls<br />- Utilizzare nelle finestre degli strumenti|**Appare come:** 14 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 155%](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% Tipo di carattere ambiente

|||
|-|-|
|**Utilizzo:**<br /><br /> - Sottovoci più piccoli nelle finestre di dialogo della firma<br />- Sottotitoli più piccoli nell'interfaccia utente del documento<br /><br /> **Procedere come:** Usa maiuscole/minuscole frasi<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o grassetto corsivo<br />- Utilizzare per il corpo del testo<br />- Utilizzare nei controlli standard di Visual Studio- Use in standard Visual Studio controls<br />- Utilizzare nelle finestre degli strumenti|**Appare come:** 12 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 133%](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% Tipo di carattere ambiente

|||
|-|-|
|**Utilizzo:**<br /><br /> - Intestazioni di sezione nelle finestre di dialogo della firma<br />- Nodi principali nella vista ad albero<br />- Navigazione scheda verticale<br /><br /> **Procedere come:** Usa maiuscole/minuscole frasi<br /><br /> **Non:**<br /><br /> - Grassetto, corsivo o grassetto corsivo<br />- Utilizzare per il corpo del testo<br />- Utilizzare nei controlli standard di Visual Studio- Use in standard Visual Studio controls<br />- Utilizzare nelle finestre degli strumenti|**Appare come:** 11 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 122%](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Tipo di carattere dell'ambiente - grassetto

|||
|-|-|
|**Utilizzo:**<br /><br /> - Etichette e sottotitoli nelle finestre di dialogo delle firme<br />- Etichette e sottotitoli nei rapporti<br />- Etichette e sottotitoli nell'interfaccia utente del documento<br /><br /> **fare:**<br /><br /> - Usa caso frase<br />- Utilizzare il peso grassetto<br /><br /> **Non:**<br /><br /> - Corsivo o grassetto corsivo<br />- Utilizzare per il corpo del testo<br />- Utilizzare nei controlli standard di Visual Studio- Use in standard Visual Studio controls<br />- Utilizzare nelle finestre degli strumenti|**Appare come:** in grassetto 9 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di carattere Ambiente &#43; intestazione in grassetto](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Tipo di carattere dell'ambiente

|||
|-|-|
|**Utilizzo:** Tutto il testo<br /><br /> **Procedere come:** Usa maiuscole/minuscole frasi<br /><br /> **Non:** Corsivo o grassetto corsivo|**Appare come:** 9 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Esempio di tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Spaziatura e spaziatura
 Le intestazioni richiedono spazio intorno a loro per dare loro l'enfasi appropriata. Questo spazio varia a seconda delle dimensioni in punti e di ciò che si trova vicino all'intestazione, ad esempio una regola orizzontale o una riga di testo nel tipo di carattere dell'ambiente.

- L'imbottitura ideale per un titolo da solo dovrebbe essere il 90% dello spazio di altezza del carattere maiuscolo. Ad esempio, un'intestazione Segoe UI Light di 28 pt ha un'altezza del tappo di 26 pt e la spaziatura interna deve essere di circa 23 pt o circa 31 pixel.

- Lo spazio minimo intorno a un titolo deve essere pari al 50% dell'altezza del carattere maiuscolo. Meno spazio può essere utilizzato quando un titolo è accompagnato da una regola o da un altro elemento aderente.

- Il testo del carattere dell'ambiente in grassetto deve seguire l'interlinea e la spaziatura interna predefiniti dell'altezza della riga.

## <a name="see-also"></a>Vedere anche
 [MSDN: Tipi di carattere (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: Testo dell'interfaccia utente (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
