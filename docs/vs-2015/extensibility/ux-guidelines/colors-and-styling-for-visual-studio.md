---
title: Colori e stile
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0330ef80fc1127893590ef8d326cb5b8e0cf0160
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291604"
---
# <a name="colors-and-styling-for-visual-studio"></a>Colori e stile per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>Uso del colore in Visual Studio
 In Visual Studio, il colore viene usato principalmente come strumento di comunicazione, non solo come decorazione. Usare il colore minimo e riservarlo per le situazioni in cui si desidera:

- Comunicare il significato o l'affiliazione (ad esempio, modificatori della piattaforma o della lingua)

- Attirare l'attenzione (ad esempio, indicando una modifica dello stato)

- Migliorare la leggibilità e fornire punti di riferimento per l'esplorazione dell'interfaccia utente

- Aumenta la desiderabilità

  Sono disponibili diverse opzioni per l'assegnazione di colori agli elementi dell'interfaccia utente in Visual Studio. In alcuni casi può essere difficile individuare l'opzione che si prevede di usare o come usarla in modo corretto. Questo argomento consente di:

1. Comprendere i diversi servizi e sistemi usati per definire i colori in Visual Studio.

2. Selezionare l'opzione corretta per un determinato elemento.

3. Usare correttamente l'opzione scelta.

   **Importante:** Non codificare mai i colori Hex, RGB o di sistema negli elementi dell'interfaccia utente. L'utilizzo dei servizi consente di ottimizzare la tonalità. Inoltre, senza il servizio, non sarà possibile sfruttare le funzionalità di cambio del tema del [servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metodi per l'assegnazione di colori agli elementi dell'interfaccia di Visual Studio
 Scegliere il metodo più adatto agli elementi dell'interfaccia utente.

|Interfaccia utente|Metodo|Cosa sono?|
|-------------|------------|--------------------|
|Sono presenti finestre di dialogo incorporate o autonome.|**Colori di sistema**|Nomi di sistema che consentono al sistema operativo di definire il colore e l'aspetto degli elementi dell'interfaccia utente, ad esempio per i controlli della finestra di dialogo comuni.|
|Si dispone di un'interfaccia utente personalizzata che si desidera sia coerente con l'ambiente di Visual Studio e che si disponga di elementi dell'interfaccia utente che corrispondono alla categoria e al significato semantico dei token condivisi.|**Colori condivisi comuni**|Nomi di token di colore predefiniti esistenti per elementi dell'interfaccia utente specifici|
|Si dispone di una singola funzionalità o di un gruppo di funzionalità e non è disponibile alcun colore condiviso per gli elementi simili.|**Colori personalizzati**|Nomi di token di colore specifici di un'area che non devono essere condivisi con altre interfacce utente|
|Si desidera consentire all'utente finale di personalizzare l'interfaccia utente o il contenuto, ad esempio per gli editor di testo o per le finestre di progettazione specializzate.|**Personalizzazione dell'utente finale**<br /><br /> **(Strumenti > finestra di dialogo Opzioni)**|Impostazioni definite nella pagina "tipi di carattere e colori" della finestra di dialogo **strumenti > opzioni** o una pagina specializzata specifica di una funzionalità dell'interfaccia utente.|

### <a name="visual-studio-themes"></a>Temi di Visual Studio
 Visual Studio presenta tre diversi temi di colore: chiaro, scuro e blu. Viene inoltre rilevato Contrasto elevato Mode, ovvero un tema di colore a livello di sistema progettato per l'accessibilità.

 Agli utenti viene richiesto di selezionare un tema durante il primo utilizzo di Visual Studio e possono cambiare i temi in un secondo momento passando a **strumenti > opzioni > ambiente > generale** e scegliendo un nuovo tema dal menu a discesa "tema colori".

 Gli utenti possono anche usare il pannello di controllo per cambiare l'intero sistema in uno dei diversi temi Contrasto elevato. Se un utente seleziona un tema Contrasto elevato, il selettore del tema colori di Visual Studio non influisca più sui colori in Visual Studio, anche se le modifiche al tema vengono salvate quando l'utente esce dalla modalità di Contrasto elevato. Per ulteriori informazioni sulla modalità di Contrasto elevato, vedere [scelta di contrasto elevato colori](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Il servizio VSColor
 Visual Studio fornisce un servizio colori ambiente, noto come servizio VSColor, che consente di associare i valori dei colori degli elementi dell'interfaccia utente a una voce denominata che contiene i valori di colore per ogni tema di Visual Studio. In questo modo si garantisce che i colori cambieranno automaticamente per riflettere il tema selezionato dall'utente corrente o la modalità di Contrasto elevato di sistema. L'uso del servizio significa che l'implementazione di tutte le modifiche dei colori correlate al tema viene gestita in un'unica posizione e, se si usano i colori condivisi comuni dal servizio, l'interfaccia utente rifletterà automaticamente i nuovi temi nelle versioni future di Visual Studio.

### <a name="implementation"></a>Implementazione
 Il codice sorgente di Visual Studio include diversi file di definizione del pacchetto contenenti elenchi di nomi di token e i rispettivi valori di colore per ogni tema. Il servizio colori legge i VSColors definiti nei file di definizione del pacchetto. A questi colori viene fatto riferimento nel markup XAML o nel codice, quindi viene caricato tramite il metodo **IVsUIShell5. GetThemedColor** o un mapping DynamicResource.

### <a name="system-colors"></a>Colori di sistema
 Per impostazione predefinita, i controlli comuni fanno riferimento ai colori di sistema. Se si vuole che l'interfaccia utente usi i colori di sistema, ad esempio quando si crea una finestra di dialogo incorporata o autonoma, non è necessario eseguire alcuna operazione.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colori condivisi comuni nel servizio VSColor
 Gli elementi dell'interfaccia devono riflettere l'ambiente generale di Visual Studio. Riutilizzando i colori condivisi comuni appropriati per il componente dell'interfaccia utente che si sta progettando, si garantisce che l'interfaccia sia coerente con altre interfacce di Visual Studio e che i colori vengano aggiornati automaticamente quando vengono aggiunti o aggiornati temi.

 Prima di usare i colori condivisi comuni, verificare di aver compreso come utilizzarli correttamente. Un uso errato dei colori condivisi comuni potrebbe causare un'esperienza incoerente, frustrante o confusa per gli utenti.

### <a name="user-customizable-colors"></a>Colori personalizzabili dall'utente
 Vedere: [esposizione dei colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 In alcuni casi, è possibile consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o un'area di progettazione. I componenti dell'interfaccia utente personalizzabili sono disponibili nella sezione **tipi di carattere e colori** della finestra di dialogo **Strumenti > Opzioni** , in cui gli utenti possono scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi.

 ![Finestra &#62; di dialogo Opzioni strumenti in Visual Studio](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")

 **Strumenti > finestra di dialogo Opzioni**

## <a name="BKMK_TheVSColorService"></a>Il servizio VSColor
 Visual Studio fornisce un servizio colori ambiente, detto anche servizio VSColor o Shell Color. Questo servizio consente di associare i valori dei colori degli elementi dell'interfaccia utente a un set di colori nome-valore contenente i colori per ogni tema. Il servizio VSColor deve essere usato per tutti gli elementi dell'interfaccia utente, in modo che i colori cambiano automaticamente per riflettere il tema selezionato dall'utente corrente e in modo che l'interfaccia utente associata al servizio colori ambiente si integrerà con i nuovi temi nelle versioni future di Visual Studio.

### <a name="how-the-service-works"></a>Funzionamento del servizio
 Il servizio colori ambiente legge VSColors definito nel pkgdef per il componente dell'interfaccia utente. A questi VSColors viene quindi fatto riferimento nel markup o nel codice XAML e vengono caricati tramite **IVsUIShell5. GetThemedColor** o un mapping DynamicResource.

 ![Architettura del servizio colori ambiente](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")

 **Architettura del servizio colori ambiente**

### <a name="accessing-the-service"></a>Accesso al servizio
 Esistono diversi modi per accedere al servizio VSColor, a seconda del tipo di token di colore in uso e del tipo di codice.

#### <a name="predefined-environment-colors"></a>Colori ambiente predefiniti

##### <a name="from-native-code"></a>Da codice nativo
 La shell fornisce un servizio che consente di accedere al COLORREF dei colori. Il servizio/interfaccia è:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 Nel file VSShell80. idl, l'enumerazione **__VSSYSCOLOREX** contiene costanti colore della shell. Per usarlo, passare come valore di indice uno dei valori dell'enumerazione __VSSYSCOLOREX documentati in MSDN o un numero di indice regolare che l'API di sistema di Windows, **GetSysColor**, accetta. Questa operazione ottiene il valore RGB del colore da usare nel secondo parametro.

 Se si archivia una penna o un pennello con un nuovo colore, è necessario AdviseBroadcastMessages (fuori dalla shell di Visual Studio) e restare in ascolto dei messaggi WM_SYSCOLORCHANGE e WM_THEMECHANGED.

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **Nota:** I valori COLORREF restituiti da **GetVSSysColorEx ()** contengono solo i componenti R, G, B di un colore del tema. Se una voce del tema usa la trasparenza, il valore del canale alfa viene ignorato prima della restituzione. Pertanto, se è necessario utilizzare il colore dell'ambiente di interesse in una posizione in cui il canale di trasparenza è importante, è consigliabile utilizzare IVsUIShell5. GetThemedColor anziché IVsUIShell2:: GetVSSysColorEx, come descritto più avanti in questo argomento.

##### <a name="from-managed-code"></a>Da codice gestito
 L'accesso al servizio VSColor tramite codice nativo è piuttosto semplice. Se si utilizza codice gestito, tuttavia, determinare come utilizzare il servizio può risultare complesso. Tenendo presente questo aspetto, ecco un C# frammento di codice che illustra questo processo:

```
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

 Se si lavora in Visual Basic, usare:

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Dall'interfaccia utente di WPF
 È possibile eseguire l'associazione ai colori di Visual Studio tramite i valori esportati nell'oggetto ResourceDictionary dell'applicazione. Di seguito è riportato un esempio dell'uso delle risorse dalla tabella dei colori, nonché dell'associazione ai dati del tipo di carattere dell'ambiente in XAML.

```
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Classi e metodi helper per codice gestito
 Per il codice gestito, la libreria del Framework di pacchetto gestito della shell (Microsoft. VisualStudio. Shell. 12.0. dll) contiene un paio di classi helper che facilitano l'uso dei colori con tema.

 I metodi helper della classe **Microsoft. VisualStudio. Shell. VsColors** in MPF includono **GetThemedGDIColor ()** e **GetThemedWPFColor ()** . Questi metodi helper restituiscono il valore di colore di una voce del tema come System. Drawing. Color o System. Windows. Media. color, da usare nell'interfaccia utente di WinForms o WPF.

```
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

```

 La classe può essere usata anche per ottenere gli identificatori VSCOLOR per una chiave di risorsa di colore WPF specificata o viceversa.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 I metodi della classe **VsColors** eseguono una query sul servizio VSColor per restituire il valore del colore ogni volta che vengono richiamati. Per ottenere un valore di colore come **System. Drawing. Color**, un'alternativa con prestazioni migliori consiste nel usare invece i metodi della classe **Microsoft. VisualStudio. PlatformUI. VSThemeColor** , che memorizza nella cache i valori di colore ottenuti dal servizio VSColor. La classe sottoscrive internamente gli eventi di trasmissione dei messaggi della shell ed Elimina il valore memorizzato nella cache quando si verifica un evento di modifica del tema. Inoltre, la classe fornisce un oggetto. Evento semplice da usare per sottoscrivere le modifiche del tema. Utilizzare l'evento **ThemeChanged** per aggiungere un nuovo gestore e utilizzare il metodo **GetThemedColor ()** per ottenere i valori di colore per **ThemeResourceKeys** di interesse. Un codice di esempio potrebbe essere simile al seguente:

```
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="BKMK_ChoosingHighContrastColors"></a>Scelta di colori Contrasto elevato

### <a name="overview"></a>Panoramica
 Windows utilizza diversi temi a livello di sistema a contrasto elevato che aumentano il contrasto dei colori di testo, sfondi e immagini, rendendo gli elementi più distinti sullo schermo. Per motivi di accessibilità, è importante che gli elementi dell'interfaccia di Visual Studio rispondano correttamente quando gli utenti passano a un tema Contrasto elevato.

 Per Contrasto elevato temi è possibile usare solo alcuni colori di sistema. Quando si scelgono i nomi dei colori del sistema, tenere presenti i suggerimenti seguenti:

1. **Scegliere i colori di sistema che hanno lo stesso significato semantico** dell'elemento che si sta colorando. Ad esempio, se si sceglie un colore a contrasto elevato per il testo all'interno di una finestra, usare WindowText e non ControlText.

2. **Scegliere tra coppie di primo piano/sfondo** oppure non si è certi che la scelta dei colori funzionerà in tutti i temi contrasto elevato.

3. **Determinare quali parti dell'interfaccia utente sono le più importanti e assicurarsi che le aree di contenuto si trovino.** Si perderanno molto dettaglio che le sottili differenze nella tonalità dei colori verrebbero normalmente distinti, quindi l'uso di colori con bordi forti è comune per definire le aree di contenuto, perché non sono disponibili varianti di colore per aree di contenuto diverse.

### <a name="system-color-set"></a>Set di colori di sistema
 La tabella nel [Blog del team WPF: riferimento a SystemColors](https://devblogs.microsoft.com/wpf/systemcolors-reference/) indica il set completo di nomi dei colori di sistema e le tonalità corrispondenti visualizzate in ogni tema.

 Quando si applica questo set limitato di colori all'interfaccia utente, si *prevede che si perderanno dettagli sottili che erano presenti nei temi "normali"* . Di seguito è riportato un esempio di interfaccia utente con colori grigio sottili che vengono usati per distinguere le aree all'interno di una finestra degli strumenti. Una volta abbinato alla stessa finestra visualizzata in modalità Contrasto elevato, è possibile osservare che tutti gli sfondi sono della stessa tonalità e che i bordi di tali aree sono indicati solo da un bordo:

 ![Finestra Proprietà](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303-a_PropertiesWindow")

 **Esempio del modo in cui i dettagli vengono persi quando si Contrasto elevato**

#### <a name="choosing-text-colors-in-an-editor"></a>Scelta di colori di testo in un editor
 Il testo colorato viene utilizzato in un editor o in un'area di progettazione per indicare un significato, ad esempio per facilitare l'identificazione di gruppi di elementi simili. In un tema Contrasto elevato, tuttavia, non si ha la possibilità di distinguere tra più di tre colori di testo. WindowText, GrayText e HotTrackText sono gli unici colori disponibili sulle superfici WindowBackground. Poiché non è possibile utilizzare più di tre colori, scegliere con attenzione le differenze più importanti che si desidera visualizzare in modalità Contrasto elevato.

 Tonalità per ogni nome di token consentito in una superficie dell'editor, così come appaiono in ogni tema Contrasto elevato:

 ![Confronto tra Editor Contrasto elevato](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303-b_HCEditorComparison")

 **Confronto tra Editor Contrasto elevato**

 Esempi della superficie dell'editor nel tema blu:

 ![Editor con tema blu](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303-c_EditorBlue")

 **Editor con tema blu**

 ![Editor nel tema Contrasto elevato](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303-d_EditorHC1")

 **Editor in Contrasto elevato tema #1**

### <a name="usage-patterns"></a>Modelli di utilizzo
 Molti elementi dell'interfaccia utente comuni hanno già colori a contrasto elevato definiti. È possibile fare riferimento a questi modelli di utilizzo quando si scelgono i nomi dei colori di sistema personalizzati, in modo che gli elementi dell'interfaccia utente siano coerenti con componenti simili.

|Colore di sistema|Utilizzo|
|------------------|-----------|
|ActiveCaption|-Icone dell'IDE attivo e del pulsante della finestra con rafting al passaggio del mouse e premere<br />-Sfondo della barra del titolo per l'IDE e le finestre con rafting<br />-Sfondo della barra di stato predefinita|
|ActiveCaptionText|-IDE attivo e finestre con rafting per il primo piano della barra del titolo (testo e glifi)<br />-Sfondo e bordo dei pulsanti della finestra attiva al passaggio del mouse e premere|
|Control|-Casella combinata, elenco a discesa e controllo di ricerca predefinito e disabilitato sfondo, incluso il pulsante a discesa<br />-Sfondo del pulsante di destinazione di ancoraggio<br />-Sfondo della barra comandi<br />-Sfondo della finestra degli strumenti|
|ControlDark|-Sfondo IDE<br />-Separatori dei menu e della barra dei comandi<br />-Bordo barra del comando<br />-Ombreggiature dei menu<br />-Scheda della finestra degli strumenti predefinita e bordo e separatore del passaggio del mouse<br />-Sfondo del pulsante di overflow del documento<br />-Bordo del glifo di destinazione dell'ancoraggio|
|ControlDarkDark|-Non attivo, finestra scheda documento selezionata|
|ControlLight|-Nascondi automaticamente bordo scheda<br />-Casella combinata e bordo dell'elenco a discesa<br />-Ancoraggio dello sfondo e del bordo della destinazione|
|ControlLightLight|-Bordo provvisorio selezionato, con stato attivo|
|ControlText|-Casella combinata e glifo elenco a discesa<br />-Testo della scheda deselezionato della finestra degli strumenti|
|GrayText|-Casella combinata ed elenco a discesa: bordo disabilitato, glifo a discesa, testo e testo della voce di menu<br />-Testo del menu disabilitato<br />-Testo intestazione ' opzioni di ricerca ' del controllo di ricerca<br />-Separatore della sezione di controllo Search|
|Evidenziazione|-Tutti i bordi, il passaggio del mouse e gli sfondi e i bordi, eccetto il bordo del pulsante a discesa della casella combinata e del pulsante di overflow<br />-Sfondi elementi selezionati|
|HighlightText|-Tutti i primi passi del passaggio del mouse e quelli premuti (testo e glifi)<br />Finestra degli strumenti con stato attivo e primo piano del controllo finestra scheda documento<br />Bordo della barra del titolo della finestra degli strumenti con stato attivo<br />-Primo piano selezionato per la scheda provvisoria<br />-Bordo del pulsante di overflow del documento al passaggio del mouse e premere<br />-Bordo icona selezionato|
|HotTrack|-Sfondo del cursore della barra di scorrimento e bordo sulla pressione<br />-Glifo della freccia della barra di scorrimento alla pressione|
|InactiveCaption|-Icone IDE inattive e pulsanti finestra con rafting al passaggio del mouse<br />-Sfondo della barra del titolo per l'IDE e le finestre con rafting<br />-Sfondo del controllo di ricerca disabilitato|
|InactiveCaptionText|-Primo piano della barra del titolo di Windows e dell'IDE inattivo (testo e glifi)<br />-Pulsanti finestra inattivi-sfondo e bordo al passaggio del mouse<br />-Sfondo e bordo del pulsante della finestra degli strumenti con stato non attivo<br />-Primo piano del controllo di ricerca disabilitato|
|Menu|-Sfondo del menu a discesa<br />-Sfondo segno di spunta selezionato e disabilitato|
|MenuText|-Bordo del menu a discesa<br />-Segno di spunta<br />-Icone dei menu<br />-Testo menu a discesa<br />-Bordo icona selezionato|
|Barra di scorrimento|-Barra di scorrimento e sfondo della freccia della barra di scorrimento, tutti gli Stati|
|Finestra|-Sfondo scheda Nascondi automaticamente<br />-Sfondo della barra dei menu e dello scaffale dei comandi<br />-Sfondo della scheda della finestra del documento con stato non attivo o non selezionato e bordo del documento per le schede aperte e provvisorie<br />-Sfondo della barra del titolo della finestra degli strumenti con stato non attivo<br />-Sfondo scheda della finestra degli strumenti, sia selezionati che deselezionati|
|WindowFrame|-Bordo IDE|
|WindowText|-Nascondi automaticamente tabulazione in primo piano<br />-Primo piano della scheda della finestra degli strumenti selezionata<br />-Scheda della finestra del documento con stato non attivo e in primo piano della scheda provvisoria o non selezionata<br />-Visualizzazione albero-primo piano predefinito e passaggio del mouse su glifo non selezionato<br />-Bordo scheda selezionato della finestra degli strumenti<br />-Sfondo del cursore della barra di scorrimento, bordo e glifo|

## <a name="BKMK_ExposingColorsForEndUsers"></a>Esposizione dei colori per gli utenti finali

### <a name="overview"></a>Panoramica
 In alcuni casi è necessario consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o un'area di progettazione. Il modo più comune per eseguire questa operazione consiste nell'utilizzare la finestra di dialogo **strumenti > opzioni** . A meno che non si disponga di un'interfaccia utente altamente specializzata che richiede controlli speciali, il modo più semplice per presentare la personalizzazione è tramite la pagina **tipi di carattere e colori** all'interno della sezione **ambiente** della finestra di dialogo. Per ogni elemento esposto per la personalizzazione, l'utente può scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Creazione di un pacchetto VSPackage per i colori personalizzabili
 Un pacchetto VSPackage può controllare i tipi di carattere e i colori tramite le categorie personalizzate e gli elementi visualizzati nella pagina delle proprietà tipi di carattere e colori. Quando si usa questo meccanismo, i pacchetti VSPackage devono implementare l'interfaccia [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) e le interfacce associate.

 In linea di principio, questo meccanismo può essere usato per modificare tutti gli elementi visualizzati esistenti e le categorie che li contengono. Tuttavia, non deve essere usato per modificare la categoria dell'editor di testo o i relativi elementi visualizzati. Per altre informazioni sulla categoria Editor di testo, vedere [Cenni preliminari su tipi di carattere e colori](https://msdn.microsoft.com/library/bb165065.aspx).

 Per implementare categorie personalizzate o elementi visualizzati, un pacchetto VSPackage deve:

- **Creare o identificare le categorie nel registro di sistema.** L'implementazione dell'IDE della pagina delle proprietà **tipi di carattere e colori** usa queste informazioni per eseguire una query corretta per il servizio che supporta una determinata categoria.

- **Creare o identificare i gruppi nel registro di sistema (facoltativo).** Potrebbe essere utile definire un gruppo, che rappresenta l'Unione di due o più categorie. Se viene definito un gruppo, l'IDE unisce automaticamente le sottocategorie e distribuisce gli elementi visualizzati all'interno del gruppo.

- **Implementare il supporto dell'IDE.**

- **Gestire le modifiche ai tipi di carattere e ai colori.**

#### <a name="to-create-or-identify-categories"></a>Per creare o identificare categorie
 Costruire un tipo speciale di voce del registro di sistema Category in [Hklm\software\microsoft. \Visual Studio\\< Visual Studio Version\>\FontAndColors\\< Category\>]. \<Category > è il nome non localizzato della categoria.

 Popolare il registro di sistema con due valori:

|Name|Type|Data|Descrizione|
|----------|----------|----------|-----------------|
|Categoria|REG_SZ|GUID|GUID creato per identificare la categoria|
|Pacchetto|REG_SZ|GUID|GUID del servizio VSPackage che supporta la categoria|

 Il servizio specificato nel registro di sistema deve fornire un'implementazione di [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) per la categoria corrispondente.

#### <a name="to-create-or-identify-groups"></a>Per creare o identificare i gruppi
 Costruire un tipo speciale di voce del registro di sistema Category in [Hklm\software\microsoft. \Visual Studio\\< Visual Studio Version\>\FontAndColors\\< Group\>]. \<Group > è il nome non localizzato del gruppo.

 Popolare il registro di sistema con due valori:

|Name|Type|Data|Descrizione|
|----------|----------|----------|-----------------|
|Categoria|REG_SZ|GUID|GUID creato per identificare la categoria|
|Pacchetto|REG_SZ|GUID|GUID del servizio VSPackage che supporta la categoria|

 Il servizio specificato nel registro di sistema deve fornire un'implementazione di **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** per il gruppo corrispondente.

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>Per implementare il supporto dell'IDE
 Implementare [GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), che restituisce un'interfaccia [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) o un'interfaccia **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** all'IDE per ogni categoria o GUID di gruppo fornito.

 Per ogni categoria supportata, un pacchetto VSPackage implementa un'istanza separata dell'interfaccia [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) .

 I metodi implementati tramite [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) devono fornire l'IDE con:

- Elenchi di elementi visualizzati nella categoria

- Nomi localizzabili per gli elementi visualizzati

- Visualizza le informazioni per ogni membro della categoria

  **Nota:** Ogni categoria deve contenere almeno un elemento visualizzato.

  L'IDE utilizza l'interfaccia **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** per definire un'Unione di diverse categorie.

  La relativa implementazione fornisce l'IDE con:

- Elenco delle categorie che costituiscono un determinato gruppo

- Accesso alle istanze di [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) che supportano ogni categoria all'interno del gruppo

- Nomi dei gruppi localizzabili

#### <a name="updating-the-ide"></a>Aggiornamento dell'IDE
 L'IDE memorizza nella cache le informazioni sulle impostazioni del tipo di carattere e del colore. Quindi, dopo la modifica della configurazione del tipo di carattere e del colore dell'IDE, verificare che la cache sia aggiornata è una procedura consigliata.

 L'aggiornamento della cache viene eseguito tramite l'interfaccia [IvsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) e può essere eseguito a livello globale o solo in elementi selezionati.

### <a name="handling-font-and-color-changes"></a>Gestione delle modifiche dei colori e dei tipi di carattere
 Per supportare correttamente la colorazione del testo visualizzato da un pacchetto VSPackage, il servizio di colorazione che supporta il pacchetto VSPackage deve rispondere alle modifiche avviate dall'utente apportate tramite la pagina delle proprietà tipi di carattere e colori.

 A tale scopo, un pacchetto VSPackage deve:

- **gestire gli eventi generati dall'IDE** implementando l'interfaccia [IVsFontAndColorEvents](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) . L'IDE chiama il metodo appropriato che segue le modifiche dell'utente della pagina tipi di carattere e colori. Ad esempio, chiama il metodo [OnFontChanged](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) se è selezionato un nuovo tipo di carattere.

  **OPPURE**

- eseguire **il polling dell'IDE per le modifiche**. Questa operazione può essere eseguita tramite l'interfaccia [errore IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) implementata dal sistema. Sebbene principalmente per il supporto della persistenza, il metodo [GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) può ottenere informazioni relative al tipo di carattere e al colore per gli elementi visualizzati. Per ulteriori informazioni sulle impostazioni relative a tipi di carattere e colori, vedere l'articolo di MSDN [accesso alle impostazioni dei tipi di carattere e colori archiviati](https://msdn.microsoft.com/library/bb166382.aspx).

  **Nota:** Per assicurarsi che i risultati del polling siano corretti, utilizzare l'interfaccia [IVsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) per determinare se sono necessari uno scaricamento e un aggiornamento della cache prima di chiamare i metodi di recupero dell'interfaccia [errore IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) .

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrazione della categoria di tipi di carattere e colori personalizzati senza implementare interfacce
 Nell'esempio di codice seguente viene illustrato come registrare la categoria di tipi di carattere e colori personalizzati senza implementare interfacce:

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **NOTA:**

- "NameID" = ID risorsa del nome della categoria localizzata nel pacchetto

- "ToolWindowPackage" = GUID pacchetto

- "Category" = "{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" è solo un esempio e il valore effettivo può essere un nuovo GUID fornito dall'implementatore.

### <a name="set-the-font-and-color-property-category-guid"></a>Impostazione del GUID della categoria di tipi di carattere e colori
 Nell'esempio di codice seguente viene illustrata l'impostazione di GUID di categoria.

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
