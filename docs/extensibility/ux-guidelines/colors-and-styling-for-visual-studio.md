---
title: I colori e stili per Visual Studio | Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ba49e1ab3e25e3f22a9ca8642673aa0a62869f6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114769"
---
# <a name="colors-and-styling-for-visual-studio"></a>I colori e stili per Visual Studio

## <a name="use-color-in-visual-studio"></a>Usare il colore in Visual Studio

In Visual Studio, colore viene usato principalmente come strumento di comunicazione, non solo come effetto. Usare il colore minimo e si riserva per le situazioni in cui si desidera:

- Comunicare significato o un'affiliazione (ad esempio, i modificatori di piattaforma o linguaggio)

- Attirare l'attenzione (ad esempio, che indica una modifica dello stato)

- Migliorare la leggibilità e forniscono punti di riferimento per l'esplorazione dell'interfaccia utente

- Effettiva necessità di aumento

Sono disponibili diverse opzioni per l'assegnazione di colori per gli elementi dell'interfaccia utente in Visual Studio. In alcuni casi, può essere difficile figura out quale opzione opportuno per utilizzare, o su come usarla in modo corretto. In questo argomento consentono di:

- Comprendere i diversi servizi e sistemi usati per definire i colori in Visual Studio.

- Selezionare l'opzione corretta per l'elemento specificato.

- Usare correttamente l'opzione scelto.

> [!NOTE]
> Mai impostare come hardcoded esadecimale, RGB o colori di sistema a elementi dell'interfaccia utente. Utilizzo dei servizi offre una flessibilità nell'ottimizzazione hue. Inoltre, senza il servizio, non sarà in grado di sfruttare le funzionalità del cambio di tema [VSColor service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metodi per l'assegnazione di colori per gli elementi dell'interfaccia di Visual Studio

Scegliere il metodo più adatto a elementi dell'interfaccia utente.

| L'interfaccia utente | Metodo | Cosa sono? |
| --- | --- | --- |
| Non è stato incorporato o finestre di dialogo autonomo. | **Colori di sistema** | Nomi di sistema che consentono al sistema operativo definire il colore e l'aspetto degli elementi dell'interfaccia utente, come i controlli di finestra di dialogo comuni. |
| Si dispone di interfaccia utente personalizzata che si desidera essere coerente con l'ambiente generale di Visual Studio e si dispongono di elementi dell'interfaccia utente che corrispondono alla categoria e il significato semantico dei token condiviso. | **Colori condivisi comuni** | I nomi di token di colore predefiniti per specifici elementi dell'interfaccia utente esistente |
| Si dispone di una singola funzionalità o un gruppo di funzionalità e non vi è alcun colore condiviso per gli elementi simili. | **Colori personalizzati** | Nomi di token di colore specifici da un'area e non devono essere condiviso con altri dell'interfaccia utente |
| Si vuole consentire all'utente finale di personalizzare l'interfaccia utente o il contenuto (ad esempio, per gli editor di testo o finestre di progettazione specializzate). | **Personalizzazione degli utenti finali**<br /><br />**(Strumenti &gt; finestra di dialogo Opzioni)** | Le impostazioni definite nella pagina di "Tipi di carattere e colori" il **degli strumenti &gt; opzioni** finestra di dialogo o una pagina specializzata specifica di una funzionalità dell'interfaccia utente. |

### <a name="visual-studio-themes"></a>Temi di Visual Studio

Visual Studio offre tre temi di colore diverso: chiaro, scuro e blu. Rileva anche modalità a contrasto elevato, ovvero una combinazione di colori a livello di sistema progettata per l'accessibilità.

Gli utenti viene richiesto di selezionare un tema durante l'uso prima di Visual Studio e sono in grado di cambiare tema in un secondo momento, passare a **Tools &gt; opzioni &gt; ambiente &gt; generale** e scegliendo un nuovo tema dal il menu di scelta rapida "tema colori".

Gli utenti possono anche usare il pannello di controllo per passare i propri sistemi interi in uno dei diversi temi a contrasto elevato. Se un utente seleziona un tema a contrasto elevato, quindi il selettore di tema colori di Visual Studio non è più interessa i colori in Visual Studio, anche se le modifiche di tema vengono salvate per quando l'utente esce dalla modalità a contrasto elevato. Per altre informazioni sulla modalità a contrasto elevato, vedere [colori a contrasto elevato scelta](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>VSColor service

Visual Studio offre un servizio colori ambiente, noto come VSColor service, che consente di associare i valori di colore degli elementi dell'interfaccia utente per una voce denominata contenente i valori di colore per ogni tema di Visual Studio. Ciò garantisce che i colori cambierà automaticamente per riflettere la corrente selezionate dall'utente del sistema o del tema modalità contrasto elevato. Uso del servizio significa che l'implementazione di tutte le modifiche correlate alla tema colori viene gestito in un'unica posizione, e se si Usa colori condivisi comuni del servizio, l'interfaccia utente verrà applicata automaticamente nuovi temi nelle versioni future di Visual Studio.

### <a name="implementation"></a>Implementazione

Il codice sorgente di Visual Studio include diversi file di definizione pacchetto che contengono elenchi di nomi di token e i valori del rispettivo colore per ogni tema. Il servizio di colore legge il VSColors definito in questi file di definizione del pacchetto. Tali colori vengono usato come riferimento nel markup XAML o nel codice e successivamente caricati tramite il `IVsUIShell5.GetThemedColor` metodo o un mapping DynamicResource.

### <a name="system-colors"></a>Colori di sistema

Controlli comuni di fare riferimento a colori di sistema per impostazione predefinita. Se si desidera che l'interfaccia utente di utilizzare i colori di sistema, ad esempio quando si crea una finestra di dialogo incorporata o autonomo, non devi eseguire alcuna operazione.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colori condivisi comuni in VSColor service

Gli elementi di interfaccia devono riflettere l'ambiente di Visual Studio complessiva. Riutilizza i colori condivisi comuni che sono appropriati per il componente dell'interfaccia utente che si sta progettando, garantisce che l'interfaccia sia coerenza con altre interfacce di Visual Studio e che i colori verranno aggiornati automaticamente quando vengono aggiunti o aggiornati temi.

Prima di usare colori condivisi comuni, assicurarsi di comprendere come usarli in modo corretto. Uso non corretto di colori condivisi comuni potrebbe comportare un'esperienza coerente, frustrante o poco chiara per gli utenti.

### <a name="user-customizable-colors"></a>Colori personalizzabili dall'utente

Vedere: [Esposizione di colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

In alcuni casi, è opportuno consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o l'area di progettazione. Personalizzabili componenti dell'interfaccia utente sono disponibili nel **i tipi di carattere e colori** sezione del **Tools &gt; opzioni** finestra di dialogo in cui gli utenti possono scegliere di modificare il colore primo piano, il colore di sfondo o entrambi.

![Tools &gt; Options dialog](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Strumenti &gt; finestra di dialogo Opzioni

## <a name="BKMK_TheVSColorService"></a> VSColor Service

Visual Studio offre un servizio colori ambiente, denominato anche VSColor service o il servizio di colore della shell. Questo servizio consente di associare i valori di colore degli elementi dell'interfaccia utente per un set contenente i colori per ogni tema colori di nome-valore. VSColor service deve essere usato per tutti gli elementi dell'interfaccia utente, in modo da colori automaticamente cambiano per riflettere il tema selezionato dall'utente corrente, in modo che l'interfaccia utente associato al servizio colori ambiente si integreranno con nuovi temi nelle future versioni di Visual Studio.

### <a name="how-the-service-works"></a>Come funziona il servizio

Il servizio colori ambiente legge che vscolors definito nel pkgdef per il componente dell'interfaccia utente. Questi VSColors viene quindi fatto riferimento nel codice o markup XAML e vengono caricati tramite il `IVsUIShell5.GetThemedColor` o un `DynamicResource` mapping.

![Architettura del servizio colori ambiente](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Architettura del servizio colori ambiente

### <a name="accessing-the-service"></a>L'accesso al servizio

Esistono diversi modi per accesso VSColor service, a seconda della tipologia di colori dei token si usano e inviare commenti di codice.

#### <a name="predefined-environment-colors"></a>Colori dell'ambiente predefinito

##### <a name="from-native-code"></a>Dal codice nativo

La shell fornisce un servizio che fornisce l'accesso per il `COLORREF` dei colori. L'interfaccia del servizio/è:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

Nel file VSShell80.idl, l'enumerazione `__VSSYSCOLOREX` ha costanti dei colori della shell. Per usarlo, passare come il valore di indice uno dei valori di `enum __VSSYSCOLOREX` documentata in MSDN o un indice regolare numerica che il sistema di Windows API, `GetSysColor`, accetta. Questa operazione consente di ottenere il valore RGB di colore da utilizzare nel secondo parametro.

Se archiviano una penna o il pennello con un nuovo colore, è necessario `AdviseBroadcastMessages` (all'esterno di Visual Studio shell) e attendere `WM_SYSCOLORCHANGE` e `WM_THEMECHANGED` messaggi.

Per accedere al servizio di colore nel codice nativo, è possibile effettuare una chiamata simile alla seguente:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Il `COLORREF` valori restituiti da `GetVSSysColorEx()` contengono solo R, G, componenti B di un colore del tema. Se una voce di tema usa la trasparenza, il valore di canale alfa viene eliminato prima della restituzione. Pertanto, se il colore di ambiente di interesse deve essere utilizzata in una posizione in cui il canale di trasparenza è importante, è necessario utilizzare `IVsUIShell5.GetThemedColor` invece di `IVsUIShell2::GetVSSysColorEx`, come descritto più avanti in questo argomento.

##### <a name="from-managed-code"></a>Dal codice gestito

L'accesso al servizio VSColor attraverso il codice nativo è piuttosto semplice. Se si lavora con codice gestito, tuttavia, che determina come usare il servizio può essere difficile. Con tali presupposti, ecco un frammento di codice c# che illustra questo processo:

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

È possibile associare ai colori di Visual Studio tramite valori esportati all'applicazione `ResourceDictionary`. Di seguito è riportato un esempio di utilizzo delle risorse dalla tabella di colore, così come l'associazione ai dati di tipo di carattere ambiente XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Classi helper e metodi per il codice gestito

Per codice gestito, libreria di Framework di pacchetto gestito della shell (`Microsoft.VisualStudio.Shell.12.0.dll`) contiene una coppia di classi di helper agevolare l'uso di temi colori.

I metodi di supporto nel `Microsoft.VisualStudio.Shell.VsColors` includere classe MPF `GetThemedGDIColor()` e `GetThemedWPFColor()`. Tali metodi helper restituisce il valore del colore di una voce di tema come `System.Drawing.Color` o `System.Windows.Media.Color`, da usare in Windows Form o WPF UI.

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

La classe è anche utilizzabile per ottenere gli identificatori VSCOLOR per una chiave di risorsa di colore WPF specificata, o viceversa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

I metodi di `VsColors` classe query VSColor service per restituire il valore del colore ogni volta che vengono richiamati. Per ottenere un valore di colore come `System.Drawing.Color`, alternativa con prestazioni migliori, è possibile usare invece i metodi del `Microsoft.VisualStudio.PlatformUI.VSThemeColor` (classe), che memorizza nella cache i valori di colore ottenuti dal servizio VSColor. La classe internamente sottoscrive gli eventi dei messaggi trasmessi shell e ignora il valore memorizzato nella cache quando si verifica un evento di modifica del tema. Inoltre, la classe fornisce una. NET-friendly evento da sottoscrivere modifiche al tema. Usare la `ThemeChanged` eventi per aggiungere un nuovo gestore e usare il `GetThemedColor()` metodo per ottenere colore i valori per il `ThemeResourceKeys` di interesse. Un codice di esempio può avere un aspetto simile al seguente:

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

## <a name="BKMK_ChoosingHighContrastColors"></a> Scelta di colori a contrasto elevato

### <a name="overview"></a>Panoramica

Windows Usa diversi temi a livello di sistema a contrasto elevato che aumentare il contrasto dei colori di testo, sfondi e immagini, rendendo gli elementi vengono visualizzati più distinta sullo schermo. Per motivi di accessibilità, è importante che gli elementi dell'interfaccia di Visual Studio rispondano correttamente quando gli utenti passano a un tema a contrasto elevato.

Solo un numero limitato di colori di sistema può essere utilizzato per temi a contrasto elevato. Quando si sceglie il sistema di nomi di colore, ricordare i suggerimenti seguenti:

- **Scegliere i colori di sistema che hanno lo stesso significato semantico** come elemento che è colorazione. Ad esempio, se si sceglie un colore a contrasto elevato per il testo all'interno di una finestra, usare WindowText e non ControlText.

- **Scegliere coppie di primo piano/sfondo** insieme, altrimenti non sarà la certezza che la scelta colori funziona in tutti i temi a contrasto elevato.

- **Determinare quali parti dell'interfaccia utente sono quelle più importanti e assicurarsi che le aree del contenuto verranno distinguiti.** Si perderà una grande quantità di dettaglio che normalmente verrebbero distinguono esservi differenze minime nei tonalità di colore, in modo che l'uso di colori del bordo sicuro è comune per definire le aree del contenuto, poiché non vi sono alcun varianti di colore per le diverse aree del contenuto.

### <a name="system-color-set"></a>Set di colori di sistema

La tabella in [Blog del Team WPF: Riferimento SystemColors](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) indica il set completo di nomi di colori di sistema e le corrispondenti tonalità visualizzate in ogni tema.

Quando si applica questo set di colori per l'interfaccia utente, limitato *è previsto che perderai dettagli che erano presenti nei temi "normali"*. Ecco un esempio dell'interfaccia utente con colori grigi meno evidenti che vengono usati per distinguere le aree all'interno di una finestra degli strumenti. Quando viene utilizzata con la stessa finestra visualizzata in modalità a contrasto elevato, si noterà che tutti gli sfondi siano la stessa tonalità e i bordi di tali aree sono indicati dal bordo autonomo:

![Esempio del modo in cui dettagli vengono perse in contrasto elevato](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Esempio del modo in cui dettagli vengono perse in contrasto elevato

#### <a name="choosing-text-colors-in-an-editor"></a>Scelta di colori del testo in un editor

Testo colorato viene utilizzato in un editor o in un'area di progettazione per indicare un significato, ad esempio consentire per facilitare l'identificazione dei gruppi di elementi simili. Un tema a contrasto elevato, tuttavia, non è la possibilità di distinguere tra più di tre colori del testo. WindowText, GrayText e HotTrackText sono i colori soli disponibili nelle aree WindowBackground. Poiché non è possibile utilizzare più di tre colori, scegliere con attenzione le differenze più importanti che si desidera visualizzare in modalità a contrasto elevato.

Sfumature diverse per ognuno dei nomi di token è consentiti in una superficie dell'editor, così come appaiono in ogni tema a contrasto elevato:

![Confronto di editor a contrasto elevato](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Confronto di editor a contrasto elevato

Esempi dell'area dell'editor del tema blu:

![Editor con tema blu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Editor con tema blu

![Editor con tema a contrasto elevato n. 1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Editor con tema a contrasto elevato n. 1

### <a name="usage-patterns"></a>Modelli di utilizzo

Molti elementi dell'interfaccia utente comuni già definiti colori a contrasto elevato. È possibile fare riferimento a questi modelli di utilizzo quando si sceglie il proprio sistema di nomi di colore, in modo che gli elementi dell'interfaccia utente siano coerenti con i componenti simili.

| Colore di sistema | Utilizzo |
| --- | --- |
| ActiveCaption | -IDE active e finestra rafted pulsante glifi su hover e premere<br />-Sfondo della barra del titolo per IDE e rafted windows<br />-Sfondo della barra di stato default |
| ActiveCaptionText | -IDE active e rafted finestre di primo piano sulla barra del titolo (testo e icone)<br />-In background e il bordo di pulsanti della finestra attiva al passaggio del mouse e premere |
| Control | -Pole se seznamem, elenco a discesa elenco e ricerca di controllare l'impostazione predefinita e in background, tra cui pulsante a discesa disabilitato<br />-Dello sfondo di pulsante di ancoraggio destinazione<br />: Sfondo della barra di comando<br />-Sfondo casella degli strumenti |
| ControlDark | -In background IDE<br />-Menu e comandi il separatore barra<br />: Bordo barra dei comandi<br />-Shadows menu<br />-Strumento bordo predefinito e al passaggio del mouse della scheda della finestra e il separatore<br />-Documentare anche in background di pulsante di overflow<br />-Bordo del glifo di destinazione di ancoraggio |
| ControlDarkDark |-Finestra scheda documento con stato non attivo e selezionato |
| ControlLight |-Bordo scheda Nascondi automaticamente<br />: Bordo casella combinata finestra e l'elenco a discesa elenco<br />-Ancorare bordo e sfondo di destinazione |
| ControlLightLight | -Bordo provisional selezionata, con lo stato attivo |
| ControlText | -Glifo combinata finestra e l'elenco a discesa elenco<br />-Testo scheda della finestra deselezionato strumento |
| GrayText |-Pole se seznamem e l'elenco di riepilogo a discesa disabilitato bordo, elenco a discesa glifo, testo e testo delle voci di menu<br />-Testo del menu disabilitato<br />-Testo dell'intestazione 'opzioni di ricerca' controllo ricerca<br />-Separatore di sezione controllo ricerca |
| Evidenziazione | -Tutti i al passaggio del mouse e premuto di sfondo e i bordi, ad eccezione di combinata pulsante a discesa in background e dei documenti overflow ben pulsante bordo della casella<br />-Sfondi elemento selezionato |
| HighlightText | -Tutti al passaggio del mouse e premuti primi piani (testo e icone)<br />-Mirato tool window e document scheda finestra controllo in primo piano<br />-Bordo barra del titolo della finestra strumento con lo stato attivo<br />-In primo piano con lo stato attivo, selezionato scheda provvisoria<br />-Documentare anche bordo del pulsante di overflow al passaggio del mouse e premere<br />-Bordo dell'icona selezionata|
| HotTrack | -Scorrimento della barra sfondo del cursore e bordo al clic del mouse<br />-Barra di scorrimento glifo freccia al clic del mouse |
| InactiveCaption | -IDE inattivo e finestra rafted glifi pulsante al passaggio del mouse<br />-Sfondo della barra del titolo per IDE e rafted windows<br />-Dello sfondo del controllo ricerca disabilitato |
| InactiveCaptionText | -IDE inattivi e in primo piano sulla barra del titolo windows rafted (testo e icone)<br />-Finestra inattiva pulsanti sfondo e bordo al passaggio del mouse<br />-Bordo e sfondo pulsante della finestra degli strumenti con stato non attivo<br />-Primo piano di controllo di ricerca disabilitato |
| Menu | Elenco a discesa dello sfondo del menu<br />-Segno di spunta selezionata e disabilitata in background |
| MenuText | -Bordo del menu elenco a discesa<br />-Segno di spunta<br />-Glifi menu<br />-Testo del menu elenco a discesa<br />-Bordo dell'icona selezionata |
| Barra di scorrimento | -Scorrere verso il barra e scorrimento dello sfondo freccia, tutti gli stati della barra |
| Finestra | Nascondi automaticamente dello sfondo della scheda<br />-Menu barra e dello sfondo dello scaffale dei comandi<br />-Sfondo della scheda della finestra documento selezionato o con stato non attivo e il bordo di documento, per schede provvisorie sia aperte<br />-Sfondo della barra del titolo di finestra strumento con stato non attivo<br />-Sfondo casella degli strumenti della scheda, sia selezionato e deselezionato |
| WindowFrame | -Bordo IDE |
| WindowText | -In primo piano della scheda Nascondi automaticamente<br />-In primo piano della scheda finestra strumento selezionato<br />-Scheda della finestra documento con stato non attivo e in primo piano deselezionato o con stato non attivo della scheda provvisoria<br />-Ad albero in primo piano predefinito di visualizzazione e al passaggio del mouse sul glifo non selezionato<br />-Bordo selezionato scheda della finestra strumento<br />-Barra di scorrimento del glifo, del bordo e sfondo del cursore |

## <a name="BKMK_ExposingColorsForEndUsers"></a> Esposizione di colori per gli utenti finali

### <a name="overview"></a>Panoramica

In alcuni casi è opportuno consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o l'area di progettazione. Il modo più comune per eseguire questa operazione consiste nell'usare la **degli strumenti &gt; opzioni** finestra di dialogo. A meno che non si dispone di altamente specializzati dell'interfaccia utente che richiede controlli speciali, il modo più semplice per presentare la personalizzazione è tramite il **tipi di carattere e colori** pagina all'interno di **ambiente** sezione della finestra di dialogo. Per ogni elemento che espone per la personalizzazione, l'utente può scegliere di modificare il colore primo piano, il colore di sfondo o entrambi.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Creazione di un pacchetto VSPackage per i colori personalizzabili

Un pacchetto VSPackage può controllare i tipi di carattere e colori tramite le categorie personalizzate e visualizzare gli elementi nella pagina delle proprietà di tipi di carattere e colori. Quando si usa questo meccanismo, i pacchetti VSPackage devono implementare il [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) interfaccia e le interfacce associate.

In teoria, questo meccanismo è utilizzabile per modificare tutti gli elementi di visualizzazione esistente e le categorie che li contengono. Tuttavia non usare per modificare la categoria dell'Editor di testo o i relativi elementi visualizzati. Per altre informazioni sulla categoria di Editor di testo, vedere [tipo di carattere e colore Panoramica](../font-and-color-overview.md).

Per implementare le categorie personalizzate o visualizzare gli elementi, un pacchetto VSPackage deve:

- **Creare o identificare le categorie nel Registro di sistema.** Implementazione dell'IDE del **Fonts and Colors** pagina delle proprietà Usa queste informazioni per eseguire correttamente le query per il servizio che supporta una determinata categoria.

- **Creare o identificare i gruppi nel Registro di sistema (facoltativo).** Potrebbe essere utile definire un gruppo, che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE automaticamente unisce le sottocategorie e distribuisce elementi visualizzati all'interno del gruppo.

- **Implementazione del supporto IDE.**

- **Gestire le modifiche di carattere e colori.**

#### <a name="to-create-or-identify-categories"></a>Per creare o identificare le categorie

Costruire un tipo speciale di voce del Registro di sistema categoria sotto `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` in cui `<Category>` è il nome non localizzato della categoria.

Popolare il Registro di sistema con due valori:

| Nome | Tipo | Dati | Descrizione |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Creato da un GUID per identificare la categoria |
| Pacchetto | REG_SZ | GUID | Il GUID del servizio di VSPackage che supporta la categoria |

 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) per la categoria corrispondente.

#### <a name="to-create-or-identify-groups"></a>Per creare o identificare i gruppi

Costruire un tipo speciale di voce del Registro di sistema categoria sotto `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` in cui `<group>` è il nome non localizzato del gruppo.

Popolare il Registro di sistema con due valori:

| Nome | Tipo | Dati | Descrizione |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Creato da un GUID per identificare la categoria |
| Pacchetto | REG_SZ | GUID | Il GUID del servizio di VSPackage che supporta la categoria |

Il servizio specificato nel Registro di sistema deve fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> per il gruppo corrispondente.

![Implementazione dell'interfaccia IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />Implementazione di `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Per implementare il supporto dell'IDE

Implementare [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), che restituisce un' [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaccia o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaccia all'IDE per ogni categoria o il gruppo GUID fornito.

Per tutte le categorie supporta, un pacchetto VSPackage implementa un'istanza separata del [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaccia.

I metodi implementati tramite [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) deve fornire l'IDE con:

- Elenchi di elementi visualizzati nella categoria

- Nomi localizzabili per elementi visualizzati

- Visualizza le informazioni per ogni membro della categoria

> [!NOTE]
> Tutte le categorie devono contenere almeno un elemento di visualizzazione.

L'IDE Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaccia per definire un'unione delle categorie diverse.

L'implementazione fornisce l'IDE con:

- Un elenco di categorie che costituiscono un gruppo specifico

- Accedere alle istanze del [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) ogni categoria all'interno del gruppo di supporto

- Nomi dei gruppi localizzabili

#### <a name="updating-the-ide"></a>L'aggiornamento dell'IDE

L'IDE memorizza nella cache le informazioni sulle impostazioni del tipo di carattere e colore. Pertanto, dopo l'eventuale modifica della configurazione del tipo di carattere dell'IDE e il colore, assicurando che la cache è aggiornata è una procedura consigliata.

Aggiornamento della cache viene eseguita tramite il [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaccia e può essere eseguiti elementi a livello globale o solo sulla selezionati.

### <a name="handling-font-and-color-changes"></a>Gestione delle modifiche di carattere e colori

Per supportare correttamente la colorazione del testo che consente di visualizzare un pacchetto VSPackage, il servizio di colorazione che supporta il pacchetto VSPackage deve rispondere alle modifiche apportate tramite la pagina delle proprietà di tipi di carattere e colori avviata dall'utente.

A tale scopo, un pacchetto VSPackage deve:

- **gestire gli eventi generati dal IDE** implementando il [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) interfaccia. L'IDE chiama il metodo appropriato dopo le modifiche apportate dall'utente della pagina tipi di carattere e colori. Ad esempio, chiama il [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) metodo se si seleziona un nuovo tipo di carattere.

  **OPPURE**

- **eseguire il polling per le modifiche IDE**. Questa operazione può essere eseguita tramite il sistema implementata [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfaccia. Anche se principalmente per il supporto di persistenza, il [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) metodo possibile ottenere informazioni di carattere e colori per gli elementi di visualizzazione. Per altre informazioni sulle impostazioni di carattere e colori, vedere l'articolo MSDN [l'accesso a tipi di carattere archiviate e le impostazioni dei colori](../accessing-stored-font-and-color-settings.md).

> [!NOTE]
> Per assicurarsi che il polling risultati siano corretti, usare il [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaccia per determinare se una cache flush e aggiornamento sono necessari prima di chiamare i metodi di recupero del [IVsFontAndColorStorage ](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfaccia.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>La registrazione di categoria di colore e tipo di carattere personalizzato senza implementare interfacce

Esempio di codice seguente viene illustrato come registrare il tipo di carattere personalizzato e categoria di colore senza implementare interfacce:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Per questo esempio di codice:

- `"NameID"` : ID risorsa del nome della categoria localizzata nel pacchetto
- `"ToolWindowPackage"` = GUID del pacchetto
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` è solo un esempio e il valore effettivo può essere un nuovo GUID forniti dall'implementatore.

### <a name="set-the-font-and-color-property-category-guid"></a>Impostare il tipo di carattere e colore proprietà GUID di categoria

Esempio di codice seguente viene illustrata l'impostazione di GUID di categoria.

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
