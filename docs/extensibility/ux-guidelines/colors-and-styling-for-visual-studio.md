---
title: Colori e stile per Visual Studio | Microsoft Docs
description: Informazioni su Visual Studio'esperienza utente usa il colore come strumento di comunicazione, anziché per motivi puramente estetici.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 307a4013c06258524c60619c6eff40e4d64740b6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904487"
---
# <a name="colors-and-styling-for-visual-studio"></a>Colori e stili per Visual Studio

## <a name="use-color-in-visual-studio"></a>Usare il colore in Visual Studio

In Visual Studio, il colore viene usato principalmente come strumento di comunicazione, non solo come decorazione. Usare il colore in modo minimo e riservarlo per le situazioni in cui si vuole:

- Comunicare il significato o l'affiliazione (ad esempio, modificatori di piattaforma o di linguaggio)

- Attirare l'attenzione (ad esempio, indicando una modifica dello stato)

- Migliorare la leggibilità e fornire punti di riferimento per l'esplorazione dell'interfaccia utente

- Aumentare la desiderabilità

Esistono diverse opzioni per l'assegnazione di colori agli elementi dell'interfaccia utente in Visual Studio. A volte può essere difficile capire quale opzione si dovrebbe usare o come usarla correttamente. Questo argomento consente di:

- Comprendere i diversi servizi e sistemi usati per definire i colori in Visual Studio.

- Selezionare l'opzione corretta per un determinato elemento.

- Usare correttamente l'opzione scelta.

> [!NOTE]
> Non impostare mai come hardcoded i colori esadecimali, RGB o di sistema per gli elementi dell'interfaccia utente. L'uso dei servizi consente la flessibilità nell'ottimizzazione della tonalità. Inoltre, senza il servizio , non sarà possibile sfruttare le funzionalità di cambio di tema [del servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metodi per assegnare il colore agli elementi Visual Studio interfaccia

Scegliere il metodo più adatto agli elementi dell'interfaccia utente.

| Interfaccia utente | Metodo | Quali sono? |
| --- | --- | --- |
| Sono state incorporate o autonome finestre di dialogo. | **Colori di sistema** | Nomi di sistema che consentono al sistema operativo di definire il colore e l'aspetto degli elementi dell'interfaccia utente, ad esempio i controlli di dialogo comuni. |
| Si dispone di un'interfaccia utente personalizzata che si vuole essere coerente con l'ambiente visuale generale e si dispone di elementi dell'interfaccia utente che corrispondono alla categoria e significato semantico dei token condivisi. | **Colori condivisi comuni** | Nomi di token di colore predefiniti esistenti per elementi specifici dell'interfaccia utente |
| Si dispone di una singola funzionalità o gruppo di funzionalità e non esiste alcun colore condiviso per elementi simili. | **Colori personalizzati** | Nomi di token di colore specifici di un'area e che non devono essere condivisi con un'altra interfaccia utente |
| Si vuole consentire all'utente finale di personalizzare l'interfaccia utente o il contenuto, ad esempio per editor di testo o finestre di progettazione specializzate. | **Personalizzazione dell'utente finale**<br /><br />**(Strumenti &gt; Finestra di dialogo Opzioni)** | Impostazioni definite nella pagina "Tipi di carattere e colori" della **finestra &gt;** di dialogo Opzioni degli strumenti o una pagina specializzata specifica di una funzionalità dell'interfaccia utente. |

### <a name="visual-studio-themes"></a>Visual Studio temi

Visual Studio tre diversi temi di colore: chiaro, scuro e blu. Rileva anche la modalità Contrasto elevato, ovvero un tema a colori a livello di sistema progettato per l'accessibilità.

Agli utenti viene chiesto di selezionare un tema durante il primo utilizzo di Visual Studio e possono cambiare tema in un secondo momento passando a Strumenti Opzioni Ambiente Generale e scegliendo un nuovo tema dal menu a discesa "Tema a colori". **&gt; &gt; &gt;**

Gli utenti possono anche usare Pannello di controllo per passare gli interi sistemi in uno dei diversi Contrasto elevato temi. Se un utente seleziona un tema Contrasto elevato, il selettore del tema colori Visual Studio non influisce più sui colori in Visual Studio, anche se le modifiche al tema vengono salvate quando l'utente esce Contrasto elevato modalità. Per altre informazioni sulla modalità Contrasto elevato, vedere [Scelta Contrasto elevato colori .](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)

### <a name="the-vscolor-service"></a>Servizio VSColor

Visual Studio fornisce un servizio colori dell'ambiente, noto come servizio VSColor, che consente di associare i valori dei colori degli elementi dell'interfaccia utente a una voce denominata contenente valori di colore per ogni tema Visual Studio tema. In questo modo si garantisce che i colori cambino automaticamente per riflettere il tema selezionato dall'utente corrente o la modalità Contrasto elevato sistema. L'uso del servizio significa che l'implementazione di tutte le modifiche di colore correlate al tema viene gestita in un'unica posizione e se si usano colori condivisi comuni dal servizio, l'interfaccia utente rifletterà automaticamente i nuovi temi nelle versioni future di Visual Studio.

### <a name="implementation"></a>Implementazione

Il Visual Studio codice sorgente include diversi file di definizione del pacchetto che contengono elenchi di nomi di token e i rispettivi valori di colore per ogni tema. Il servizio colori legge gli elementi VSColor definiti in questi file di definizione del pacchetto. A questi colori viene fatto riferimento nel markup XAML o nel codice e quindi caricati tramite il `IVsUIShell5.GetThemedColor` metodo o un mapping DynamicResource.

### <a name="system-colors"></a>Colori di sistema

I controlli comuni fanno riferimento ai colori di sistema per impostazione predefinita. Se si vuole che l'interfaccia utente usi i colori di sistema, ad esempio quando si crea una finestra di dialogo incorporata o autonoma, non è necessario eseguire alcun'operazione.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colori condivisi comuni nel servizio VSColor

Gli elementi dell'interfaccia devono riflettere l'ambiente Visual Studio generale. Riutilizzando i colori condivisi comuni appropriati per il componente dell'interfaccia utente che si sta progettando, si garantisce che l'interfaccia sia coerente con altre interfacce Visual Studio e che i colori verranno aggiornati automaticamente quando i temi vengono aggiunti o aggiornati.

Prima di usare i colori condivisi comuni, assicurarsi di comprendere come usarli correttamente. L'uso non corretto di colori condivisi comuni può comportare un'esperienza incoerente, frustrante o confusa per gli utenti.

### <a name="user-customizable-colors"></a>Colori personalizzabili dall'utente

Vedere: [Esposizione di colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

In alcuni casi, è necessario consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o un'area di progettazione. I componenti personalizzabili  dell'interfaccia utente sono disponibili nella sezione Tipi di carattere e colori della finestra di dialogo Opzioni degli strumenti, in cui gli utenti possono scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi. **&gt;**

![Finestra di &gt; dialogo Opzioni degli strumenti](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Finestra di &gt; dialogo Opzioni degli strumenti

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> Servizio VSColor

Visual Studio un servizio colori dell'ambiente, denominato anche servizio VSColor o servizio colori della shell. Questo servizio consente di associare i valori dei colori degli elementi dell'interfaccia utente a un set di colori nome-valore contenente i colori per ogni tema. Il servizio VSColor deve essere usato per tutti gli elementi dell'interfaccia utente, in modo che i colori cambino automaticamente in base al tema selezionato dall'utente corrente e in modo che l'interfaccia utente associata al servizio colori dell'ambiente si integri con i nuovi temi nelle versioni future di Visual Studio.

### <a name="how-the-service-works"></a>Funzionamento del servizio

Il servizio colori dell'ambiente legge VSColors definiti in .pkgdef per il componente dell'interfaccia utente. A questi oggetti VSColor viene quindi fatto riferimento nel markup o nel codice XAML e vengono caricati tramite `IVsUIShell5.GetThemedColor` o un `DynamicResource` mapping.

![Architettura del servizio colori ambiente](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architettura del servizio colori ambiente

### <a name="accessing-the-service"></a>Accesso al servizio

Esistono diversi modi per accedere al servizio VSColor, a seconda del tipo di token di colore in uso e del tipo di codice.

#### <a name="predefined-environment-colors"></a>Colori dell'ambiente predefiniti

##### <a name="from-native-code"></a>Da codice nativo

La shell fornisce un servizio che consente l'accesso `COLORREF` all'oggetto dei colori. Il servizio/interfaccia è:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

Nel file VSShell80.idl l'enumerazione `__VSSYSCOLOREX` include costanti di colore della shell. Per usarlo, passare come valore di indice uno dei valori di documentati in MSDN o un numero di indice normale accettato dall'API di sistema `enum __VSSYSCOLOREX` di Windows, `GetSysColor` , . In questo modo viene restituito il valore RGB del colore che deve essere usato nel secondo parametro.

Se si archivia una penna o un pennello con un nuovo colore, è necessario (al di fuori della shell Visual Studio) e restare in ascolto `AdviseBroadcastMessages` dei `WM_SYSCOLORCHANGE` messaggi e `WM_THEMECHANGED` .

Per accedere al servizio colori nel codice nativo, si effettua una chiamata simile alla seguente:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> I `COLORREF` valori restituiti da `GetVSSysColorEx()` contengono solo componenti R,G,B di un colore del tema. Se una voce del tema usa la trasparenza, il valore del canale alfa viene eliminato prima della restituzione. Pertanto, se il colore dell'ambiente di interesse deve essere usato in una posizione in cui il canale di trasparenza è importante, è consigliabile usare invece di , come descritto più `IVsUIShell5.GetThemedColor` `IVsUIShell2::GetVSSysColorEx` avanti in questo argomento.

##### <a name="from-managed-code"></a>Da codice gestito

L'accesso al servizio VSColor tramite codice nativo è piuttosto semplice. Se si usa codice gestito, tuttavia, determinare come usare il servizio può essere difficile. A tale scopo, ecco un frammento di codice C# che illustra questo processo:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Se si lavora in Visual Basic, usare:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Dall'interfaccia utente WPF

È possibile eseguire l'associazione Visual Studio colori tramite i valori esportati nell'oggetto `ResourceDictionary` dell'applicazione. Di seguito è riportato un esempio di uso delle risorse della tabella dei colori e dell'associazione ai dati del tipo di carattere dell'ambiente in XAML.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Classi e metodi helper per il codice gestito

Per il codice gestito, la libreria Managed Package Framework della shell ( ) contiene un paio di classi helper che facilitano l'uso `Microsoft.VisualStudio.Shell.12.0.dll` di colori a tema.

I metodi helper nella `Microsoft.VisualStudio.Shell.VsColors` classe in MPF includono `GetThemedGDIColor()` e `GetThemedWPFColor()` . Questi metodi helper restituiscono il valore del colore di una voce del tema come `System.Drawing.Color` o , da usare in Windows Form o nell'interfaccia utente `System.Windows.Media.Color` WPF.

```csharp
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

La classe può essere usata anche per ottenere identificatori VSCOLOR per una determinata chiave di risorsa colore WPF o viceversa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

I metodi della classe e consentono di eseguire una query sul `VsColors` servizio VSColor per restituire il valore del colore ogni volta che vengono richiamati. Per ottenere un valore di colore come , un'alternativa con prestazioni migliori consiste nell'usare invece i metodi della classe , che memorizza nella cache i valori dei colori ottenuti dal `System.Drawing.Color` `Microsoft.VisualStudio.PlatformUI.VSThemeColor` servizio VSColor. La classe sottoscrive internamente gli eventi dei messaggi trasmessi dalla shell ed elimina il valore memorizzato nella cache quando si verifica un evento di modifica del tema. Inoltre, la classe fornisce un oggetto . Evento descrittivo per NET per sottoscrivere le modifiche del tema. Usare `ThemeChanged` l'evento per aggiungere un nuovo gestore e usare il metodo per `GetThemedColor()` ottenere i valori di colore per `ThemeResourceKeys` l'oggetto di interesse. Un codice di esempio potrebbe essere simile al seguente:

```csharp
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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Scelta Contrasto elevato colori

### <a name="overview"></a>Panoramica

Windows usa diversi temi a contrasto elevato a livello di sistema che aumentano il contrasto dei colori di testo, sfondi e immagini, rendendo gli elementi più distinti sullo schermo. Per motivi di accessibilità, è importante che gli Visual Studio dell'interfaccia rispondano correttamente quando gli utenti passano a un Contrasto elevato tema.

Solo pochi colori di sistema possono essere usati per Contrasto elevato temi. Quando si scelgono i nomi dei colori di sistema, tenere presente i suggerimenti seguenti:

- **Scegliere i colori di sistema con lo stesso significato semantico** dell'elemento da colorare. Ad esempio, se si sceglie un colore a contrasto elevato per il testo all'interno di una finestra, usare WindowText e non ControlText.

- **Scegliere insieme coppie di** primo piano/sfondo oppure non si è certi che la scelta del colore funzionerà in tutti i Contrasto elevato colori.

- **Determinare quali parti dell'interfaccia utente sono le più importanti e assicurarsi che le aree di contenuto si distingueranno.** Si perderanno molti dettagli che le piccole differenze nella tonalità di colore normalmente distinguerebbero, quindi l'uso di colori del bordo forti è comune per definire le aree di contenuto, perché non esistono varianti di colore per aree di contenuto diverse.

### <a name="system-color-set"></a>Set di colori di sistema

La tabella nel [blog del team WPF: SystemColors Reference (Blog](/archive/blogs/wpf/systemcolors-reference) del team WPF: Riferimento a SystemColors) indica il set completo di nomi di colori di sistema e le sfumature corrispondenti visualizzate in ogni tema.

Quando si applica questo set limitato di colori all'interfaccia utente, è previsto che si perdano i dettagli che erano presenti nei *temi "normali".* Di seguito è riportato un esempio di interfaccia utente con colori grigi tenui usati per distinguere le aree all'interno di una finestra degli strumenti. Se abbinati alla stessa finestra visualizzata in modalità Contrasto elevato, è possibile vedere che tutti gli sfondi hanno la stessa tonalità e i bordi di tali aree sono indicati solo dal bordo:

![Esempio di come si perdono i dettagli in Contrasto elevato](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Esempio di come si perdono i dettagli in Contrasto elevato

#### <a name="choosing-text-colors-in-an-editor"></a>Scelta dei colori del testo in un editor

Il testo colorato viene usato in un editor o in un'area di progettazione per indicare il significato, ad esempio per consentire una facile identificazione di gruppi di elementi simili. In un Contrasto elevato, tuttavia, non è possibile distinguere tra più di tre colori del testo. WindowText, GrayText e HotTrackText sono gli unici colori disponibili nelle superfici WindowBackground. Poiché non è possibile usare più di tre colori, scegliere con attenzione le differenze più importanti da visualizzare in modalità Contrasto elevato predefinita.

Sfumature per ognuno dei nomi di token consentiti in una superficie dell'editor, come vengono visualizzati in ogni Contrasto elevato tema:

![Confronto di editor a contrasto elevato](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Confronto di editor a contrasto elevato

Esempi dell'area dell'editor nel tema Blu:

![Editor con tema blu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor con tema blu

![Editor nel tema Contrasto elevato #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor nel tema Contrasto elevato #1

### <a name="usage-patterns"></a>Modelli di utilizzo

Molti elementi comuni dell'interfaccia utente Contrasto elevato colori definiti. È possibile fare riferimento a questi modelli di utilizzo quando si scelgono i nomi dei colori di sistema, in modo che gli elementi dell'interfaccia utente siano coerenti con componenti simili.

| Colore di sistema | Utilizzo |
| --- | --- |
| ActiveCaption | - IDE attivo e glifi dei pulsanti della finestra in gruppo al passaggio del mouse e premere<br />- Sfondo della barra del titolo per IDE e finestre con gruppo<br />- Sfondo predefinito della barra di stato |
| ActiveCaptionText | - IDE attivo e finestre a scorrimento per la barra del titolo in primo piano (testo e glifi)<br />- Sfondo e bordo dei pulsanti della finestra attiva al passaggio del mouse e premere |
| Control | - Casella combinata, elenco a discesa e sfondo predefinito e disabilitato del controllo di ricerca, incluso il pulsante a discesa<br />- Ancora lo sfondo del pulsante di destinazione<br />- Sfondo della barra dei comandi<br />- Sfondo della finestra degli strumenti |
| ControlDark | - Sfondo DELL'IDE<br />- Separatori di menu e barre dei comandi<br />- Bordo della barra dei comandi<br />- Ombreggiature dei menu<br />- Impostazione predefinita della scheda della finestra degli strumenti e bordo e separatore al passaggio del mouse<br />- Sfondo del pulsante di overflow dell'area documenti<br />- Ancora il bordo del glifo di destinazione |
| ControlDarkDark |- Finestra della scheda del documento selezionata con stato non attivo |
| ControlLight |- Nascondi automaticamente il bordo della scheda<br />- Bordo della casella combinata e dell'elenco a discesa<br />- Ancorare lo sfondo e il bordo di destinazione |
| ControlLightLight | - Bordo provvisorio con stato attivo selezionato |
| ControlText | - Glifo casella combinata e elenco a discesa<br />- Testo della scheda non selezionato nella finestra degli strumenti |
| GrayText |- Bordo disabilitato della casella combinata e dell'elenco a discesa, glifo a discesa, testo e testo della voce di menu<br />- Testo del menu disabilitato<br />- Testo dell'intestazione 'opzioni di ricerca' del controllo di ricerca<br />- Separatore di sezione del controllo di ricerca |
| Evidenziazione | - Tutti gli sfondi e i bordi premuti al passaggio del mouse, ad eccezione dello sfondo del pulsante a discesa della casella combinata e del bordo del pulsante di overflow dell'area del documento<br />- Sfondi degli elementi selezionati |
| HighlightText | - Tutti i primi piani al passaggio del mouse e premuti (testo e glifi)<br />- Finestra degli strumenti con stato attivo e controllo della finestra della scheda del documento in primo piano<br />- Bordo della barra del titolo della finestra degli strumenti con stato attivo<br />- Primo piano della scheda provvisoria selezionata con stato attivo<br />- Bordo del pulsante di overflow dell'area del documento al passaggio del mouse e premere<br />- Bordo dell'icona selezionata|
| HotTrack | - Sfondo e bordo del cursore della barra di scorrimento alla pressione<br />- Glifo della freccia della barra di scorrimento alla pressione |
| InactiveCaption | - IDE inattivo e glifi dei pulsanti delle finestre con gruppo al passaggio del mouse<br />- Sfondo della barra del titolo per IDE e finestre con gruppo<br />- Sfondo del controllo di ricerca disabilitato |
| InactiveCaptionText | - IDE inattivo e barra del titolo delle finestre in primo piano (testo e glifi)<br />- Sfondo e bordo dei pulsanti della finestra inattivi al passaggio del mouse<br />- Sfondo e bordo del pulsante della finestra degli strumenti senza stato attiva<br />- Controllo di ricerca disabilitato in primo piano |
| Menu | - Sfondo del menu a discesa<br />- Sfondo con segno di spunta selezionato e disabilitato |
| MenuText | - Bordo del menu a discesa<br />- Segni di spunta<br />- Glifi di menu<br />- Testo del menu a discesa<br />- Bordo dell'icona selezionata |
| Barra di scorrimento | - Sfondo della barra di scorrimento e della freccia della barra di scorrimento, tutti gli stati |
| Finestra | - Nascondi automaticamente lo sfondo della scheda<br />- Barra dei menu e sfondo dello scaffale dei comandi<br />- Sfondo della scheda della finestra del documento non attivo o non selezionato e bordo del documento, sia per le schede aperte che per le schede provvisorie<br />- Sfondo della barra del titolo della finestra degli strumenti non attiva<br />- Sfondo della scheda della finestra degli strumenti, sia selezionato che deselezionato |
| WindowFrame | - Bordo IDE |
| WindowText | - Nascondi automaticamente la scheda in primo piano<br />- Scheda della finestra degli strumenti selezionata in primo piano<br />- Scheda della finestra del documento non attiva e scheda provvisoria non attiva o non selezionata in primo piano<br />- Primo piano predefinito della visualizzazione albero e passaggio del mouse sul glifo non selezionato<br />- Bordo della scheda selezionata della finestra degli strumenti<br />- Sfondo, bordo e glifo della barra di scorrimento |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Esposizione di colori per gli utenti finali

### <a name="overview"></a>Panoramica

In alcuni casi è necessario consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o un'area di progettazione. Il modo più comune per eseguire questa operazione è usare la finestra **di dialogo &gt; Opzioni** degli strumenti. A meno che non si abbia un'interfaccia utente altamente specializzata che richiede controlli  speciali, il modo più semplice per presentare la personalizzazione è tramite la pagina Tipi di carattere e **colori** nella sezione Ambiente della finestra di dialogo. Per ogni elemento esposto per la personalizzazione, l'utente può scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Compilazione di un VSPackage per i colori personalizzabili

Un VSPackage può controllare i tipi di carattere e i colori tramite categorie personalizzate e visualizzare gli elementi nella pagina delle proprietà Tipi di carattere e colori. Quando si usa questo meccanismo, i pacchetti VSPackage devono implementare [l'interfaccia IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) e le interfacce associate.

In linea di principio, questo meccanismo può essere usato per modificare tutti gli elementi di visualizzazione esistenti e le categorie che li contengono. Tuttavia, non deve essere usato per modificare la categoria Editor di testo o i relativi elementi di visualizzazione. Per altre informazioni sulla categoria Editor di testo, vedere Panoramica dei tipi [di carattere e dei colori](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015).

Per implementare categorie personalizzate o visualizzare elementi, un VSPackage deve:

- **Creare o identificare categorie nel Registro di sistema.** L'implementazione dell'IDE della pagina delle proprietà **Tipi** di carattere e colori usa queste informazioni per eseguire correttamente una query per il servizio che supporta una determinata categoria.

- **Creare o identificare gruppi nel Registro di sistema (facoltativo).** Può essere utile definire un gruppo, che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE unisce automaticamente le sottocategorie e distribuisce gli elementi visualizzati all'interno del gruppo.

- **Implementare il supporto IDE.**

- **Gestire le modifiche al tipo di carattere e al colore.**

#### <a name="to-create-or-identify-categories"></a>Per creare o identificare categorie

Costruire un tipo speciale di voce del Registro di sistema di categoria `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` in dove è il nome non `<Category>` localizzato della categoria.

Popolare il Registro di sistema con due valori:

| Nome | Tipo | Dati | Descrizione |
| --- | --- | --- | --- |
| Categoria | REG_SZ | GUID | GUID creato per identificare la categoria |
| Pacchetto | REG_SZ | GUID | GUID del servizio VSPackage che supporta la categoria |

 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) per la categoria corrispondente.

#### <a name="to-create-or-identify-groups"></a>Per creare o identificare gruppi

Costruire un tipo speciale di voce del Registro di sistema di categoria `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` in dove è il nome non `<group>` localizzato del gruppo.

Popolare il Registro di sistema con due valori:

| Nome | Tipo | Dati | Descrizione |
|--- | --- | --- | --- |
| Categoria | REG_SZ | GUID | GUID creato per identificare la categoria |
| Pacchetto | REG_SZ | GUID | GUID del servizio VSPackage che supporta la categoria |

Il servizio specificato nel Registro di sistema deve fornire un'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> di per il gruppo corrispondente.

![Implementazione di IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementazione di `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Per implementare il supporto IDE

Implementare [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), che restituisce [un'interfaccia IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) o un'interfaccia all'IDE per ogni GUID di categoria o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> gruppo fornito.

Per ogni categoria che supporta, un VSPackage implementa un'istanza separata [dell'interfaccia IVsFontAndColorDefaults.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

I metodi implementati tramite [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) devono fornire all'IDE:

- Elenchi di elementi visualizzati nella categoria

- Nomi localizzabili per gli elementi visualizzati

- Visualizzare le informazioni per ogni membro della categoria

> [!NOTE]
> Ogni categoria deve contenere almeno un elemento visualizzato.

L'IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> l'interfaccia per definire un'unione di diverse categorie.

L'implementazione fornisce all'IDE:

- Elenco delle categorie che costituiscono un determinato gruppo

- Accesso alle istanze di [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) che supportano ogni categoria all'interno del gruppo

- Nomi di gruppi localizzabili

#### <a name="updating-the-ide"></a>Aggiornamento dell'IDE

L'IDE memorizza nella cache le informazioni sulle impostazioni relative a tipo di carattere e colore. Pertanto, dopo qualsiasi modifica della configurazione del tipo di carattere e del colore IDE, assicurarsi che la cache sia aggiornata è una procedura consigliata.

L'aggiornamento della cache viene eseguito tramite [l'interfaccia IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) e può essere eseguito a livello globale o solo su elementi selezionati.

### <a name="handling-font-and-color-changes"></a>Gestione delle modifiche al tipo di carattere e al colore

Per supportare correttamente la colorazione del testo visualizzata da un VSPackage, il servizio di colorazione che supporta il pacchetto VSPackage deve rispondere alle modifiche avviate dall'utente apportate tramite la pagina delle proprietà Tipi di carattere e colori.

A tale scopo, un VSPackage deve:

- **gestire gli eventi generati dall'IDE** implementando [l'interfaccia IVsFontAndColorEvents.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) L'IDE chiama il metodo appropriato in seguito alle modifiche apportate dall'utente alla pagina Tipi di carattere e colori. Ad esempio, chiama il [metodo OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) se è selezionato un nuovo tipo di carattere.

  **OR**

- **Eseguire il polling dell'IDE per le modifiche**. Questa operazione può essere eseguita tramite [l'interfaccia IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) implementata dal sistema. Anche se principalmente per il supporto della persistenza, il [metodo GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) può ottenere informazioni sul tipo di carattere e sul colore per gli elementi visualizzati. Per altre informazioni sulle impostazioni dei tipi di carattere e dei colori, vedere l'articolo MSDN [Accessing Stored Font and Color Settings](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015).

> [!NOTE]
> Per assicurarsi che i risultati del polling siano corretti, usare [l'interfaccia IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) per determinare se sono necessari uno scaricamento e un aggiornamento della cache prima di chiamare i metodi di recupero dell'interfaccia [IVsFontAndColorStorage.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrazione di tipi di carattere e colori personalizzati categoria senza implementare interfacce

L'esempio di codice seguente illustra come registrare il tipo di carattere e la categoria di colori personalizzati senza implementare interfacce:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Per questo esempio di codice:

- `"NameID"` = l'ID risorsa del nome della categoria localizzata nel pacchetto
- `"ToolWindowPackage"` = GUID del pacchetto
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` è solo un esempio e il valore effettivo può essere un nuovo GUID fornito dall'implementatore.

### <a name="set-the-font-and-color-property-category-guid"></a>Impostare il GUID della categoria di proprietà Font e Color

L'esempio di codice seguente illustra l'impostazione dei GUID di categoria.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
