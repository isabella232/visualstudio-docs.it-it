---
title: Colori e applicazione di stili per Visual Studio . Documenti Microsoft
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c7d8a02de9331f268cd06ad35e19faab6494fe0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699858"
---
# <a name="colors-and-styling-for-visual-studio"></a>Colori e stili per Visual Studio

## <a name="use-color-in-visual-studio"></a>Usare il colore in Visual StudioUse color in Visual Studio

In Visual Studio il colore viene usato principalmente come strumento di comunicazione, non solo come decorazione. Utilizzare il colore in modo minimo e riservarlo per le situazioni in cui si desidera:

- Comunicare significato o affiliazione (ad esempio, modificatori di piattaforma o di linguaggio)

- Attirare l'attenzione (ad esempio, indicando una modifica dello stato)

- Migliorare la leggibilità e fornire punti di riferimento per la navigazione nell'interfaccia utente

- Aumentare l'auspicabilità

Esistono diverse opzioni per l'assegnazione di colori agli elementi dell'interfaccia utente in Visual Studio.Several options exist for assigning colors to UI elements in Visual Studio. A volte può essere difficile capire quale opzione si suppone di utilizzare, o come usarlo correttamente. Questo argomento consente di:This topic will help you:

- Comprendere i diversi servizi e sistemi utilizzati per definire i colori in Visual Studio.Understand the different services and systems used to define colors in Visual Studio.

- Selezionare l'opzione corretta per un determinato elemento.

- Utilizzare correttamente l'opzione scelta.

> [!NOTE]
> Non codificare mai i colori esadecimali, RGB o di sistema per gli elementi dell'interfaccia utente. L'utilizzo dei servizi consente flessibilità nella messa a punto della tonalità. Inoltre, senza il servizio, non sarà possibile sfruttare le funzionalità di commutazione di tema [del servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metodi per l'assegnazione di colore agli elementi dell'interfaccia di Visual StudioMethods for assigning color to Visual Studio interface elements

Scegli il metodo più adatto agli elementi dell'interfaccia utente.

| L'interfaccia utente | Metodo | Cosa sono? |
| --- | --- | --- |
| Si dispone di finestre di dialogo incorporate o autonome. | **Colori di sistema** | Nomi di sistema che consentono al sistema operativo di definire il colore e l'aspetto degli elementi dell'interfaccia utente, ad esempio i controlli comuni delle finestre di dialogo. |
| Si dispone di un'interfaccia utente personalizzata che si desidera essere coerente con l'ambiente VS generale e si dispone di elementi dell'interfaccia utente che corrispondono al significato semantico e di categoria dei token condivisi. | **Colori condivisi comuni** | Nomi di token di colore predefiniti esistenti per elementi specifici dell'interfaccia utente |
| Si dispone di una singola feature o di un gruppo di feature e non esiste un colore condiviso per elementi simili. | **Colori personalizzati** | Nomi di token di colore specifici di un'area e che non devono essere condivisi con altre interfaccia utente |
| Si desidera consentire all'utente finale di personalizzare l'interfaccia utente o il contenuto (ad esempio, per gli editor di testo o le finestre di progettazione specializzate). | **Personalizzazione dell'utente finale**<br /><br />**(finestra &gt; di dialogo Opzioni degli strumenti)** | Impostazioni definite nella pagina "Tipi di carattere e colori" della finestra di dialogo **Opzioni degli strumenti &gt; ** o in una pagina specializzata specifica di una funzionalità dell'interfaccia utente. |

### <a name="visual-studio-themes"></a>Temi di Visual Studio

Visual Studio offre tre diversi temi di colore: chiaro, scuro e blu. Rileva anche la modalità Contrasto elevato, che è un tema di colore a livello di sistema progettato per l'accessibilità.

Gli utenti sono richiesto di selezionare un tema durante il primo utilizzo di Visual Studio e sono in grado di passare temi in un secondo momento andando a **Strumenti &gt; Opzioni &gt; Ambiente &gt; generale** e scegliendo un nuovo tema dal menu a discesa "tema di colore".

Gli utenti possono anche utilizzare il Pannello di controllo per passare l'intero sistema in uno dei diversi temi a contrasto elevato. Se un utente seleziona un tema a contrasto elevato, il selettore del tema di Visual Studio non influisce più sui colori in Visual Studio, anche se tutte le modifiche del tema vengono salvate quando l'utente esce dalla modalità Contrasto elevato. Per ulteriori informazioni sulla modalità Contrasto elevato, consultate [Scelta dei colori a contrasto elevato.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)

### <a name="the-vscolor-service"></a>Il servizio VSColorThe VSColor service

Visual Studio fornisce un servizio colore di ambiente, noto come il servizio VSColor, che consente di associare i valori di colore degli elementi dell'interfaccia utente a una voce denominata contenente i valori di colore per ogni tema di Visual Studio. In questo modo i colori cambiano automaticamente per riflettere il tema o la modalità Contrasto elevato del sistema selezionato dall'utente corrente. L'uso del servizio significa che l'implementazione di tutte le modifiche di colore relative al tema viene gestita in un'unica posizione e se si usano colori condivisi comuni dal servizio, l'interfaccia utente rifletterà automaticamente i nuovi temi nelle versioni future di Visual Studio.

### <a name="implementation"></a>Implementazione

Il codice sorgente di Visual Studio include diversi file di definizione del pacchetto che contengono elenchi di nomi di token e i rispettivi valori di colore per ogni tema. Il servizio colore legge i VSColors definiti in questi file di definizione del pacchetto. A questi colori viene fatto riferimento nel markup XAML `IVsUIShell5.GetThemedColor` o nel codice e quindi caricati tramite il metodo o un mapping DynamicResource.These colors are referenced in XAML markup or in code and then loaded through the method or a DynamicResource mapping.

### <a name="system-colors"></a>Colori di sistema

I controlli comuni fanno riferimento ai colori di sistema per impostazione predefinita. Se si desidera che l'interfaccia utente utilizzi i colori di sistema, ad esempio quando si crea una finestra di dialogo incorporata o autonoma, non è necessario eseguire alcuna operazione.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colori condivisi comuni nel servizio VSColorCommon shared colors in the VSColor service

Gli elementi dell'interfaccia devono riflettere l'ambiente di Visual Studio complessivo. Riutilizzando i colori condivisi comuni appropriati per il componente dell'interfaccia utente che si sta progettando, si garantisce che l'interfaccia sia coerente con altre interfacce di Visual Studio e che i colori vengano aggiornati automaticamente quando i temi vengono aggiunti o aggiornati.

Prima di utilizzare i colori condivisi comuni, assicurarsi di aver compreso come utilizzarli correttamente. Un uso non corretto dei colori condivisi comuni potrebbe causare un'esperienza incoerente, frustrante o confusa per gli utenti.

### <a name="user-customizable-colors"></a>Colori personalizzabili dall'utente

Vedere: [Esposizione dei colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

In alcuni momenti, è consigliabile consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o un'area di progettazione. I componenti dell'interfaccia utente personalizzabili si trovano nella sezione **Tipi di carattere e colori** della finestra di dialogo Opzioni **degli &gt; ** strumenti, in cui gli utenti possono scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi.

![Finestra &gt; di dialogo Opzioni degli strumenti](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Finestra &gt; di dialogo Opzioni degli strumenti

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>Il servizio VSColorThe VSColor Service

Visual Studio fornisce un servizio colore di ambiente, denominato anche il servizio VSColor o il servizio colore della shell. Questo servizio consente di associare i valori di colore degli elementi dell'interfaccia utente a un set di colori nome-valore contenente colori per ogni tema. Il servizio VSColor deve essere usato per tutti gli elementi dell'interfaccia utente, in modo che i colori cambino automaticamente per riflettere il tema selezionato dall'utente corrente e in modo che l'interfaccia utente associata al servizio colori dell'ambiente si integri con i nuovi temi nelle versioni future di Visual Studio.

### <a name="how-the-service-works"></a>Funzionamento del servizio

Il servizio colore dell'ambiente legge VSColors definiti nel file con estensione pkgdef per il componente dell'interfaccia utente. A questi VSColors viene quindi fatto riferimento nel markup `IVsUIShell5.GetThemedColor` XAML `DynamicResource` o nel codice e vengono caricati tramite il o un mapping.

![Architettura del servizio colori ambiente](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architettura del servizio colori ambiente

### <a name="accessing-the-service"></a>Accesso al servizio

Esistono diversi modi per accedere al servizio VSColor, a seconda del tipo di token di colore in uso e del tipo di codice in uso.

#### <a name="predefined-environment-colors"></a>Colori predefiniti per l'ambiente

##### <a name="from-native-code"></a>Dal codice nativo

La shell fornisce un servizio `COLORREF` che dà accesso ai colori. Il servizio/interfaccia è:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

Nel file VSShell80.idl, `__VSSYSCOLOREX` l'enumerazione dispone di costanti di colore della shell. Per utilizzarlo, passare come valore di indice uno `enum __VSSYSCOLOREX` dei valori del documentato in MSDN `GetSysColor`o un numero di indice regolare accettato dall'API di sistema di Windows, . In questo modo viene rieseguito il valore RGB del colore da utilizzare nel secondo parametro.

Se si archivia una penna o `AdviseBroadcastMessages` un pennello con un nuovo `WM_SYSCOLORCHANGE` colore, è necessario (fuori dalla shell di Visual Studio) e ascoltare e `WM_THEMECHANGED` messaggi.

Per accedere al servizio colore nel codice nativo, verrà eseguito una chiamata simile alla seguente:To access the color service in native code, you'll make a call that resembles this:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> I `COLORREF` valori restituiti da `GetVSSysColorEx()` contengono solo componenti R,G,B di un colore del tema. Se una voce del tema utilizza la trasparenza, il valore del canale alfa viene eliminato prima della restituzione. Pertanto, se il colore di ambiente di interesse deve essere utilizzato `IVsUIShell5.GetThemedColor` in `IVsUIShell2::GetVSSysColorEx`una posizione in cui il canale di trasparenza è importante, è necessario utilizzare anziché , come descritto più avanti in questo argomento.

##### <a name="from-managed-code"></a>Da codice gestito

L'accesso al servizio VSColor tramite codice nativo è piuttosto semplice. Se si utilizza codice gestito, tuttavia, determinare come utilizzare il servizio può essere difficile. Con questo in mente, ecco un frammento di codice C .

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

Se si utilizza Visual Basic, utilizzare:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Dall'interfaccia utente di WPF

È possibile eseguire l'associazione ai colori `ResourceDictionary`di Visual Studio tramite valori esportati nel file . Di seguito è riportato un esempio di utilizzo delle risorse dalla tabella dei colori e dell'associazione ai dati del tipo di carattere dell'ambiente in XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Classi helper e metodi per il codice gestitoHelper classes and methods for managed code

Per il codice gestito, la libreria`Microsoft.VisualStudio.Shell.12.0.dll`Managed Package Framework ( ) della shell contiene un paio di classi helper che facilitano l'utilizzo di colori a tema.

I metodi di `Microsoft.VisualStudio.Shell.VsColors` supporto nella `GetThemedGDIColor()` classe `GetThemedWPFColor()`in MPF includono e . Tali metodi di supporto restituiscono il `System.Drawing.Color` valore `System.Windows.Media.Color`del colore di una voce del tema come o , da utilizzare nell'interfaccia utente di WinForms o WPF.

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

La classe può essere utilizzata anche per ottenere gli identificatori VSCOLOR per una determinata chiave di risorsa colore WPFWPF o viceversa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

I metodi `VsColors` della classe eseguono una query sul servizio VSColor per restituire il valore del colore ogni volta che vengono richiamati. Per ottenere un `System.Drawing.Color`valore di colore come , un'alternativa `Microsoft.VisualStudio.PlatformUI.VSThemeColor` con prestazioni migliori consiste nell'utilizzare invece i metodi della classe , che memorizza nella cache i valori di colore ottenuti dal servizio VSColor. La classe sottoscrive internamente gli eventi di messaggi di trasmissione della shell ed elimina il valore memorizzato nella cache quando si verifica un evento di modifica del tema. Inoltre, la classe fornisce un oggetto . Evento NET-friendly per sottoscrivere le modifiche del tema. Utilizzare `ThemeChanged` l'evento per aggiungere un `GetThemedColor()` nuovo gestore e `ThemeResourceKeys` utilizzare il metodo per ottenere i valori di colore per l'oggetto di interesse. Un codice di esempio potrebbe essere simile al seguente:A sample code could look like this:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Scelta dei colori a contrasto elevato

### <a name="overview"></a>Panoramica

Windows usa diversi temi a livello di sistema a contrasto elevato che aumentano il contrasto dei colori di testo, sfondi e immagini, rendendo gli elementi più distinti sullo schermo. Per motivi di accessibilità, è importante che gli elementi dell'interfaccia di Visual Studio rispondano correttamente quando gli utenti passano a un tema a contrasto elevato.

Solo una manciata di colori di sistema può essere utilizzato per i temi a contrasto elevato. Quando si scelgono i nomi dei colori di sistema, tenere presente i seguenti suggerimenti:

- Scegliere i colori di **sistema che hanno lo stesso significato semantico** dell'elemento da colorare. Ad esempio, se si sceglie un colore a contrasto elevato per il testo all'interno di una finestra, utilizzare WindowText e non ControlText.

- **Scegli coppie di primo piano/sfondo** insieme o non sarai sicuro che la tua scelta di colore funzionerà in tutti i temi ad alta contrasto.

- **Determina quali parti dell'interfaccia utente sono le più importanti e assicurati che le aree di contenuto si distinguono.** Si perderanno molti dettagli che sottili differenze di colore normalmente distinguerebbe, in modo che l'uso di colori forti bordo è comune per definire le aree di contenuto, perché non ci sono varianti di colore per diverse aree di contenuto.

### <a name="system-color-set"></a>Set di colori di sistema

La tabella in [Blog del team WPF: Riferimento SystemColors](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) indica il set completo di nomi di colori di sistema e le tonalità corrispondenti visualizzate in ogni tema.

Quando si applica questo set limitato di colori all'interfaccia utente, *si prevede di perdere dettagli sottili che erano presenti nei temi "normali".* Ecco un esempio di interfaccia utente con colori grigi sottili utilizzati per distinguere le aree all'interno di una finestra degli strumenti. Se abbinato alla stessa finestra visualizzata in modalità Contrasto elevato, è possibile vedere che tutti gli sfondi sono della stessa tonalità e i bordi di tali aree sono indicati solo dal bordo:

![Esempio di come i dettagli sottili vengono persi in Contrasto elevato](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Esempio di come i dettagli sottili vengono persi in Contrasto elevato

#### <a name="choosing-text-colors-in-an-editor"></a>Scelta dei colori del testo in un editor

Il testo in colori viene utilizzato in un editor o in un'area di progettazione per indicare il significato, ad esempio consentendo una facile identificazione di gruppi di elementi simili. In un tema Contrasto elevato, tuttavia, non è possibile distinguere tra più di tre colori del testo. WindowText, GrayText e HotTrackText sono gli unici colori disponibili sulle superfici WindowBackground. Poiché non è possibile utilizzare più di tre colori, scegliere con attenzione le differenze più importanti che si desidera visualizzare in modalità Contrasto elevato.

Tonalità per ognuno dei nomi di token consentiti in una superficie dell'editor, così come appaiono in ogni tema A contrasto elevato:

![Confronto di editor a contrasto elevato](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Confronto di editor a contrasto elevato

Esempi della superficie dell'editor nel tema Blu:

![Editor con tema blu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor con tema blu

![Tema Editor in contrasto elevato #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Tema Editor in contrasto elevato #1

### <a name="usage-patterns"></a>Modelli di utilizzo

Molti elementi comuni dell'interfaccia utente hanno già colori a contrasto elevato definiti. Puoi fare riferimento a questi pattern di utilizzo quando scegli nomi di colori di sistema personalizzati, in modo che gli elementi dell'interfaccia utente siano coerenti con componenti simili.

| Colore di sistema | Uso |
| --- | --- |
| ActiveCaption | - Glifi dei pulsanti dell'IDE attivo e della finestra in rafted al passaggio del mouse e alla pressione<br />- Sfondo barra del titolo per IDE e finestre in rafed<br />- Sfondo predefinito della barra di stato |
| ActiveCaptionText | - IDE attivo e finestre in rafted per la barra del titolo in primo piano (testo e glifi)<br />- Sfondo e bordo dei pulsanti della finestra attiva al passaggio del mouse e premere |
| Controllo | - Casella combinata, elenco a discesa e controllo di ricerca predefinito e sfondo disabilitato, incluso il pulsante a discesa<br />- Sfondo del pulsante Destinazione Dock<br />- Sfondo della barra dei comandi<br />- Sfondo della finestra degli strumenti |
| ControlDark | - Sfondo IDE<br />- Separatori di menu e barre dei comandi<br />- Bordo della barra dei comandi<br />- Ombre del menu<br />- Impostazione predefinita scheda della finestra degli strumenti e bordo al passaggio del mouse e separatore<br />- Sfondo del pulsante di overflow del pozzo del documento<br />- Bordo del glifo di destinazione del Dock |
| ControlDarkDark |- Finestra della scheda documento selezionata non focalizzata |
| ControlLight |- Nascondi automaticamente il bordo della scheda<br />- Casella combinata e bordo dell'elenco a discesa<br />- Sfondo e bordo di destinazione Dock |
| ControlLightLight | - Confine provvisorio selezionato e mirato |
| ControlText (Testocontrollo) | - Glifo casella combinata ed elenco a discesa<br />- Testo della scheda finestra degli strumenti non selezionato |
| Testo Grigio |- Riquadro combinato ed elenco a discesa delimitato bordo, glifo a discesa, testo e testo della voce di menu<br />- Testo del menu disabilitato<br />- Testo dell'intestazione 'opzioni di ricerca' del controllo di ricerca<br />- Separatore sezione controllo di ricerca |
| Evidenziazione | - Tutti gli sfondi al passaggio del mouse e premuti e bordi, ad eccezione dello sfondo del pulsante a discesa della casella combinata e del bordo del pulsante di overflow del riquadro del documento<br />- Sfondi degli elementi selezionati |
| EvidenziareTesto | - Tutti i primi piani al passaggio del mouse e premuti (testo e glifi)<br />- In primo piano, il controllo della finestra degli strumenti e della scheda documento con lo stato attivo<br />- Bordo della barra del titolo della finestra degli strumenti con lo stato attivo<br />- Focused, selezionato scheda provvisoria primo piano<br />- Bordo del pulsante di overflow del pozzo del documento al passaggio del mouse e premere<br />- Bordo dell'icona selezionato|
| HotTrack (Traccia di hot tracking) | - Sfondo pollice barra di scorrimento e bordo sulla stampa<br />- Glifo freccia barra di scorrimento alla pressione |
| Intestazione inattiva | - Glifi dei pulsanti dell'IDE e della finestra in attivi al passaggio del mouse<br />- Sfondo barra del titolo per IDE e finestre in rafed<br />- Sfondo del controllo di ricerca disabilitato |
| InattivoCaptionText | - IDE inattivo e finestre in catena barra del titolo in primo piano (testo e glifi)<br />- Sfondo dei pulsanti della finestra inattiva e bordo al passaggio del mouse<br />- Sfondo e bordo del pulsante della finestra degli strumenti non focalizzato<br />- Controllo di ricerca disabilitato in primo piano |
| Menu | - Sfondo del menu a discesa<br />- Sfondo dei segni di spunta selezionati e disattivati |
| MenuTesto | - Bordo del menu a discesa<br />- Segni di spunta<br />- Glifi di menu<br />- Testo del menu a discesa<br />- Bordo dell'icona selezionato |
| Barra di scorrimento | - Barra di scorrimento e barra di scorrimento sfondo freccia, tutti gli stati |
| Finestra | - Nascondi automaticamente lo sfondo della scheda<br />- Barra dei menu e comando scaffale sfondo<br />- Sfondo della scheda della finestra del documento non focalizzato o non selezionato e bordo del documento, sia per le schede aperte che provvisorie<br />- Sfondo della barra del titolo della finestra degli strumenti non focalizzata<br />- Sfondo della scheda della finestra degli strumenti, sia selezionato che non selezionato |
| FinestraFrame | - Bordo IDE |
| Testofinestra | - Nascondi automaticamente la scheda in primo piano<br />- Scheda della finestra degli strumenti selezionata in primo piano<br />- Scheda della finestra del documento non focalizzata e tabulazione provvisoria non messa a fuoco o non selezionata in primo piano<br />- In primo piano predefinito nella vista ad albero e al passaggio del mouse sul glifo non selezionato<br />- Bordo scheda selezionata della finestra degli strumenti<br />- Sfondo pollice barra di scorrimento, bordo e glifo |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Esposizione di colori per gli utenti finali

### <a name="overview"></a>Panoramica

A volte è consigliabile consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o un'area di progettazione. Il modo più comune per eseguire questa operazione consiste nell'utilizzare la finestra di dialogo **Opzioni degli strumenti. &gt; ** A meno che non si disponga di un'interfaccia utente altamente specializzata che richiede controlli speciali, il modo più semplice per presentare la personalizzazione è tramite il **tipi di carattere e colori** pagina all'interno della sezione **Ambiente** della finestra di dialogo. Per ogni elemento esposto per la personalizzazione, l'utente può scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Creazione di un pacchetto VSPackage per i colori personalizzabiliBuilding a VSPackage for your customizable colors

Un vsPackage può controllare i tipi di carattere e colori tramite categorie personalizzate ed elementi di visualizzazione nella pagina delle proprietà tipi di carattere e colori. Quando si utilizza questo meccanismo, VSPackage devono implementare il [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) interfaccia e le interfacce associate.

In linea di principio, questo meccanismo può essere utilizzato per modificare tutti gli elementi di visualizzazione esistenti e le categorie che li contengono. Tuttavia, non deve essere utilizzato per modificare la categoria Editor di testo o i relativi elementi di visualizzazione. Per ulteriori informazioni sulla categoria Editor di testo, consultate [Cenni preliminari su tipi di carattere e colori.](/visualstudio/extensibility/font-and-color-overview?view=vs-2015)

Per implementare categorie personalizzate o visualizzare elementi, un VSPackage deve:To implement custom categories or display Items, a VSPackage must:

- **Creare o identificare categorie nel Registro di sistema.** L'implementazione dell'IDE della pagina delle proprietà Tipi di **carattere e colori** utilizza queste informazioni per eseguire correttamente una query per il servizio che supporta una determinata categoria.

- **Creare o identificare gruppi nel Registro di sistema (facoltativo).** Potrebbe essere utile definire un gruppo, che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE unisce automaticamente le sottocategorie e distribuisce gli elementi visualizzati all'interno del gruppo.

- **Implementare il supporto IDE.**

- **Gestire le modifiche di carattere e colore.**

#### <a name="to-create-or-identify-categories"></a>Per creare o identificare categorie

Costruire un tipo speciale di `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` `<Category>` voce del Registro di sistema di categoria in cui è il nome non localizzato della categoria.

Popolare il Registro di sistema con due valori:

| Nome | Type | Data | Descrizione |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID creato per identificare la categoria |
| Pacchetto | REG_SZ | GUID | GUID del servizio VSPackage che supporta la categoria |

 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) per la categoria corrispondente.

#### <a name="to-create-or-identify-groups"></a>Per creare o identificare gruppi

Costruire un tipo speciale di `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` `<group>` voce del Registro di sistema di categoria in cui è il nome non localizzato del gruppo.

Popolare il Registro di sistema con due valori:

| Nome | Type | Data | Descrizione |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID creato per identificare la categoria |
| Pacchetto | REG_SZ | GUID | GUID del servizio VSPackage che supporta la categoria |

Il servizio specificato nel Registro <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> di sistema deve fornire un'implementazione di per il gruppo corrispondente.

![Implementazione di IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementazione di `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Per implementare il supporto IDE

Implementare [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), che restituisce un [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaccia o un'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> all'IDE per ogni categoria o gruppo GUID fornito.

Per ogni categoria che supporta, un VSPackage implementa un'istanza separata del [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaccia.

I metodi implementati tramite [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) devono fornire l'IDE con:

- Elenchi di elementi visualizzati nella categoria

- Nomi localizzabili per gli elementi visualizzati

- Visualizzare le informazioni per ogni membro della categoria

> [!NOTE]
> Ogni categoria deve contenere almeno un elemento di visualizzazione.

L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> utilizza l'interfaccia per definire un'unione di diverse categorie.

La sua implementazione fornisce l'IDE con:

- Un elenco delle categorie che costituiscono un determinato gruppo

- Accesso alle istanze di [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) che supportano ogni categoria all'interno del gruppo

- Nomi dei gruppi localizzabili

#### <a name="updating-the-ide"></a>Aggiornamento dell'IDE

L'IDE memorizza nella cache le informazioni sulle impostazioni di tipo di carattere e colore. Pertanto, dopo qualsiasi modifica della configurazione di tipo di carattere e colore IDE, assicurarsi che la cache è aggiornata è una procedura consigliata.

L'aggiornamento della cache viene eseguito tramite il [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaccia e può essere eseguita a livello globale o solo sugli elementi selezionati.

### <a name="handling-font-and-color-changes"></a>Gestione delle modifiche ai caratteri e ai colori

Per supportare correttamente la colorazione del testo che viene visualizzato un VSPackage, il servizio di colorazione che supporta il pacchetto VSPackage deve rispondere alle modifiche avviate dall'utente apportate tramite il tipi di carattere e colori pagina delle proprietà.

A tale scopo, un pacchetto VSPackage deve:To do this, a VSPackage must:

- **gestire gli eventi generati dall'IDE** implementando il [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) interfaccia. L'IDE chiama il metodo appropriato in seguito alle modifiche dell'utente del tipi di carattere e colori pagina. Ad esempio, chiama il [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) metodo se è selezionato un nuovo tipo di carattere.

  **OR**

- **eseguire il polling dell'IDE per le modifiche**. Questa operazione può essere eseguita tramite il sistema implementato [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfaccia. Anche se principalmente per il supporto della persistenza, il [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) metodo può ottenere informazioni sul tipo di carattere e colore per gli elementi di visualizzazione. Per ulteriori informazioni sulle impostazioni dei tipi di carattere e dei colori, vedere l'articolo MSDN [Accessing Stored Font and Color Settings](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Per assicurarsi che i risultati del polling siano corretti, utilizzare il [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaccia per determinare se uno svuotamento della cache e aggiornamento sono necessari prima di chiamare i metodi di recupero del [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfaccia.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrazione di tipo di carattere personalizzato e colore Categoria senza implementare le interfacce

Esempio di codice seguente viene illustrato come registrare il tipo di carattere personalizzato e colore Category senza implementare le interfacce:The following code example demonstrates how to register the custom font and color Category without implementing interfaces:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Per questo esempio di codice:For this code example:

- `"NameID"`: l'ID risorsa del nome della categoria localizzata nel pacchetto
- `"ToolWindowPackage"`GUID pacchetto
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`è solo un esempio e il valore effettivo può essere un nuovo GUID fornito dall'implementatore.

### <a name="set-the-font-and-color-property-category-guid"></a>Impostare il GUID della categoria di proprietà Carattere e colore

Nell'esempio di codice riportato di seguito viene illustrata l'impostazione di GUID di categoria.

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
