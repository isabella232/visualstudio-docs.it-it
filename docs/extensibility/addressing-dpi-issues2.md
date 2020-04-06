---
title: Risoluzione dei problemi relativi ai valori DPI2 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740098"
---
# <a name="address-dpi-issues"></a>Risolvere i problemi relativi ai valori DPI
Un numero crescente di dispositivi viene spedito con schermi "ad alta risoluzione". Questi schermi hanno in genere più di 200 pixel per pollice (ppi). L'utilizzo di un'applicazione su questi computer richiederà la scalabilità verticale del contenuto per soddisfare le esigenze di visualizzazione del contenuto a una distanza di visualizzazione normale per il dispositivo. A partire dal 2014, l'obiettivo principale per i display ad alta densità sono i dispositivi di elaborazione mobile (tablet, computer portatili a conchiglia e telefoni).

Windows 8.1 e versioni successive contiene diverse funzionalità per consentire a questi computer di funzionare con schermi e ambienti in cui la macchina è collegata contemporaneamente a schermi ad alta densità e a densità standard.

- Windows può consentire di ridimensionare il contenuto nel dispositivo utilizzando l'impostazione "Ingrandisci o meno il testo e altri elementi" (disponibile a partire da Windows XP).

- Windows 8.1 e versioni successive scaleranno automaticamente il contenuto per la maggior parte delle applicazioni in modo che sia coerente quando viene spostato tra le visualizzazioni di densità di pixel diverse. Quando lo schermo principale è ad alta densità (ridimensionamento del 200%) e lo schermo secondario è la densità standard (100%), Windows ridimensiona automaticamente il contenuto della finestra dell'applicazione verso il basso sullo schermo secondario (1 pixel visualizzato per ogni 4 pixel sottoposti a rendering dall'applicazione).

- Per impostazione predefinita, Windows verrà impostato sul ridimensionamento corretto per la densità di pixel e la distanza di visualizzazione per la visualizzazione (Windows 7 e versioni successive, configurabili dall'OEM).

- Windows può scalare automaticamente il contenuto fino al 250% sui nuovi dispositivi che superano i 280 ppi (a partire da Windows 8.1 S14).

  Windows ha un modo per gestire la scalabilità verticale dell'interfaccia utente per sfruttare i vantaggi di un numero maggiore di pixel. Un'applicazione acconsente esplicitamente a questo sistema dichiarandosi "consapevole dei dPI di sistema". Le applicazioni che non eseguono questa operazione vengono aumentate dal sistema. Ciò può comportare un'esperienza utente "fuzzy" in cui l'intera applicazione è uniformemente pixel-allungato. Ad esempio:

  ![Problemi DPI - sfocatura](../extensibility/media/dpi-issues-fuzzy.png "Problemi DPI - sfocatura")

  Visual Studio acconsente esplicitamente a essere in grado di riconoscere il ridimensionamento DPI e pertanto non è "virtualizzato".

  Windows (e Visual Studio) sfruttano diverse tecnologie dell'interfaccia utente, che hanno modi diversi di gestire i fattori di scala impostati dal sistema. Ad esempio:

- WPFWPF misura i controlli in modo indipendente dal dispositivo (unità, non pixel). L'interfaccia utente WPF viene ridimensionata automaticamente per il valore DPI corrente.

- Tutte le dimensioni del testo indipendentemente dal framework dell'interfaccia utente sono espresse in punti e pertanto vengono considerate dal sistema come indipendenti dai valori DPI. Testo in Win32, WinForms e WPF già scalare correttamente quando viene disegnato sul dispositivo di visualizzazione.

- Le finestre di dialogo e le finestre Win32/WinForms dispongono di mezzi per abilitare il layout che viene ridimensionato con il testo (ad esempio, tramite i pannelli griglia, flusso e layout tabella). Ciò consente di evitare posizioni dei pixel hardcoded che non vengono ridimensionate quando le dimensioni dei caratteri vengono aumentate.

- Le icone fornite dal sistema o le risorse in base alle metriche di sistema (ad esempio, SM_CXICON e SM_CXSMICON) sono già aumentate.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Interfaccia utente precedente di Win32 (GDI, GDI) e basata su WinForms
Mentre WPFWPF è già ad alto contenuto di DPI, gran parte del codice basato su Win32/GDI non è stato originariamente scritto con riconoscimento DPI in mente. Windows ha fornito API di ridimensionamento DPI. Correzioni ai problemi Win32 devono utilizzare questi in modo coerente in tutto il prodotto. Visual Studio ha fornito una libreria di classi helper per evitare la duplicazione delle funzionalità e garantire la coerenza tra il prodotto.

## <a name="high-resolution-images"></a>Immagini ad alta risoluzione
Questa sezione è destinata principalmente agli sviluppatori che estendono Visual Studio 2013.This section is primarily for developers extending Visual Studio 2013. Per Visual Studio 2015, usare il servizio immagini incorporato in Visual Studio.For Visual Studio 2015, use image service which is built into Visual Studio. È inoltre possibile che sia necessario supportare/indirizzare molte versioni di Visual Studio e pertanto l'utilizzo del servizio immagini in 2015 non è un'opzione poiché non esiste nelle versioni precedenti. Questa sezione è anche per voi.

## <a name="scaling-up-images-that-are-too-small"></a>Ridimensionamento di immagini troppo piccole
Le immagini troppo piccole possono essere ridimensionate e sottoposte a rendering in GDI e WPF usando alcuni metodi comuni. Le classi helper DPI gestite sono disponibili per gli integratori interni ed esterni di Visual Studio per indirizzare le icone di ridimensionamento, le bitmap, le immagini e gli elenchi di immagini. Gli helper nativi C/C/C basati su Win32 sono disponibili per il ridimensionamento di HICON, HBITMAP, HIMAGELIST e VsUI::GdiplusImage. Il ridimensionamento di una bitmap richiede in genere solo una modifica di una riga dopo l'inclusione di un riferimento alla libreria helper. Ad esempio:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Il ridimensionamento di un elenco immagini dipende dal fatto che l'elenco immagini sia completo in fase di caricamento o venga aggiunto in fase di esecuzione. Se il completamento `LogicalToDeviceUnits()` al momento del caricamento, chiamare con l'elenco immagini come si farebbe con una bitmap. Quando il codice deve caricare una singola bitmap prima di comporre l'elenco immagini, assicurarsi di ridimensionare le dimensioni dell'immagine dell'elenco immagini:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Nel codice nativo, le dimensioni possono essere ridimensionate durante la creazione dell'elenco immagini come segue:In native code, the dimensions can be scaled when creating the imagelist as follows:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Le funzioni nella libreria consentono di specificare l'algoritmo di ridimensionamento. Quando ridimensionate le immagini da inserire negli elenchi immagini, assicuratevi di specificare il colore di sfondo utilizzato per la trasparenza o usate il ridimensionamento NearestNeighbor (che causerà distorsioni al 125% e al 150%).

Consultare <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> la documentazione su MSDN.

Nella tabella seguente vengono illustrati esempi di come le immagini devono essere ridimensionate in base ai fattori di scala DPI corrispondenti. Le immagini delineate in arancione denotano la nostra procedura consigliata a partire da Visual Studio 2013 (ridimensionamento DPI 100%-200%):

![Problemi DPI - ridimensionamento](../extensibility/media/dpi-issues-scaling.png "Problemi DPI - ridimensionamento")

## <a name="layout-issues"></a>Problemi di layout
Problemi di layout comuni possono essere evitati principalmente mantenendo i punti nell'interfaccia utente ridimensionati e relativi tra loro anziché utilizzando posizioni assolute (in particolare, in unità pixel). Ad esempio:

- Le posizioni di layout/testo devono essere regolate per tenere conto delle immagini in scala.

- Le colonne nelle griglie devono avere larghezze regolate per il testo in scala.

- Anche le dimensioni hardcoded o lo spazio tra gli elementi dovranno essere ridimensionati. Le dimensioni basate solo sulle dimensioni del testo sono in genere ideali, perché i font vengono automaticamente scalati.

  Le funzioni di <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> supporto sono disponibili nella classe per consentire il ridimensionamento sugli assi X e Y:Helper functions are available in the class to allow scaling on the X and Y axis:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (le funzioni consentono il ridimensionamento sull'asse X/Y)

- spazio int : DpiHelper.LogicalToDeviceUnitsX (10);

- altezza int : VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Sono presenti overload LogicalToDeviceUnits per consentire il ridimensionamento di oggetti quali Rect, Point e Size.There are LogicalToDeviceUnits overloads to allow scaling objects such as Rect, Point, and Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Utilizzo della libreria/classe DPIHelper per ridimensionare immagini e layout
La libreria helper DPI di Visual Studio è disponibile nei form nativi e gestiti e può essere utilizzata all'esterno della shell di Visual Studio da altre applicazioni.

Per usare la libreria, passare agli esempi di [estendibilità](https://github.com/Microsoft/VSSDK-Extensibility-Samples) di Visual Studio VSSDK e clonare l'esempio High-DPI_Images_Icons.

Nei file di origine, includere VsUIDpiHelper.h `VsUI::DpiHelper` e chiamare le funzioni statiche della classe:In source files, include *VsUIDpiHelper.h* and call the static functions of class:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Non usare le funzioni di supporto nelle variabili statiche a livello di modulo o di classe. La libreria utilizza anche statici per la sincronizzazione dei thread e si potrebbero incorrere in problemi di inizializzazione dell'ordine. Convertire tali elementi statici in variabili membro non statiche o eseguirne il wrapping in una funzione (in modo che vengano costruite al primo accesso).

Per accedere alle funzioni helper DPI dal codice gestito che verrà eseguito all'interno dell'ambiente di Visual Studio:To access the DPI helper functions from managed code that will run inside the Visual Studio environment:

- Il progetto consumer deve fare riferimento alla versione più recente di Shell MPF. Ad esempio:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Assicurarsi che il progetto condisponga riferimenti a **System.Windows.Forms**, **PresentationCore**e **PresentationUI**.

- Nel codice usare lo spazio dei nomi Microsoft.VisualStudio.PlatformUI e chiamare le funzioni statiche della classe DpiHelper.In code, use the **Microsoft.VisualStudio.PlatformUI** namespace and call static functions of DpiHelper class. Per i tipi supportati (punti, dimensioni, rettangoli e così via), vengono fornite funzioni di estensione che restituiscono nuovi oggetti in scala. Ad esempio:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Gestione del confusione dell'immagine WPF nell'interfaccia utente ingrandibile
In WPFWPF, le bitmap vengono ridimensionate automaticamente da WPFWPF per il livello di zoom DPI corrente usando un algoritmo bicubico di alta qualità (impostazione predefinita), che funziona bene per immagini o schermate di grandi dimensioni, ma non è appropriato per le icone delle voci di menu perché introduce la confusione percepita.

Consigli:

- Per la grafica dell'immagine <xref:System.Windows.Media.BitmapScalingMode> del logo e dei banner, è possibile utilizzare la modalità di ridimensionamento predefinita.

- Per le voci di menu <xref:System.Windows.Media.BitmapScalingMode> e le immagini iconografiche, il deve essere utilizzato quando non causa altri artefatti di distorsione per eliminare la confusione (al 200% e al 300%).

- Per livelli di zoom di grandi dimensioni non multipli del 100% (ad esempio, 250% o 350%), il ridimensionamento delle immagini iconografiche con risultati bicubici in un'interfaccia utente sfocata e sbiadita. Un risultato migliore si ottiene prima scalando l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o 300%) e scalare con bicubica da lì. Per altre informazioni, vedere Caso speciale: pre-scalabilità di immagini WPF per livelli DPI di grandi dimensioni.

  La classe DpiHelper nello spazio dei nomi Microsoft.VisualStudio.PlatformUI fornisce un membro <xref:System.Windows.Media.BitmapScalingMode> che può essere utilizzato per l'associazione. Consentirà alla shell di Visual Studio di controllare la modalità di ridimensionamento bitmap nel prodotto in modo uniforme, a seconda del fattore di scala DPI.

  Per usarlo in XAML, aggiungi:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

La shell di Visual Studio imposta già questa proprietà nelle finestre e nelle finestre di dialogo di primo livello. L'interfaccia utente basata su WPF in esecuzione in Visual Studio la erediterà già. Se l'impostazione non viene propagata alle parti specifiche dell'interfaccia utente, può essere impostata sull'elemento radice dell'interfaccia utente XAML/WPF. I luoghi in cui ciò accade includono i popup, gli elementi con elementi con elementi padre Win32 e le finestre di progettazione che esauriscono il processo, ad esempio Blend.

Alcune interfaccia utente possono essere ridimensionate indipendentemente dal livello di zoom DPI impostato dal sistema, ad esempio l'editor di testo di Visual Studio e le finestre di progettazione basate su WPF (WPF Desktop e Windows Store). In questi casi, DpiHelper.BitmapScalingMode non deve essere utilizzato. Per risolvere questo problema nell'editor, il team IDE ha creato una proprietà personalizzata denominata RenderOptions.BitmapScalingMode.To fix this issue in the editor, the IDE team created a custom property titled RenderOptions.BitmapScalingMode. Impostare il valore della proprietà su HighQuality o NearestNeighbor a seconda del livello di zoom combinato del sistema e dell'interfaccia utente.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso speciale: prescalabilità delle immagini WPF per livelli DPI di grandi dimensioni
Per livelli di zoom molto grandi che non sono multipli del 100% (ad esempio, 250%, 350% e così via), il ridimensionamento delle immagini iconografiche con risultati bicubici in un'interfaccia utente sfocata e sbiadita. L'impressione di queste immagini accanto a testo nitido è quasi simile a quella di un'illusione ottica. Le immagini sembrano essere più vicine all'occhio e sfocate rispetto al testo. Il risultato del ridimensionamento con queste dimensioni ingrandite può essere migliorato innanzitutto ridimensionando l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o 300%) e scalando con bicubica al resto (un ulteriore 50%).

Di seguito è riportato un esempio delle differenze nei risultati, in cui la prima immagine viene ridimensionata con l'algoritmo a doppio ridimensionamento migliorato 100%->200%->250% e la seconda solo con bicubica 100%->250%.

![Esempio di ridimensionamento doppio dei problemi DPI](../extensibility/media/dpi-issues-double-scaling-example.png "Esempio di ridimensionamento doppio dei problemi DPI")

Per consentire all'interfaccia utente di usare questo doppio ridimensionamento, sarà necessario modificare il markup XAML per la visualizzazione di ogni elemento Image.In order to enable UI to use this double-scaling, XAML markup for displaying each Image element will need to be modified. The following examples demonstrate how to use double-scaling in WPF in Visual Studio using the DpiHelper library and Shell.12/14.

Passaggio 1: Eseguire il preridimensionamento dell'immagine al 200%, 300% e così via utilizzando NearestNeighbor.

Ridimensiona l'immagine usando un convertitore applicato a un'associazione o con un'estensione di markup XAML. Ad esempio:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Se anche l'immagine deve essere a tema (la maggior parte, se non tutti, dovrebbe), il markup può utilizzare un convertitore diverso che prima fa il tema dell'immagine e quindi pre-ridimensionamento. Il markup può <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>utilizzare o , a seconda dell'output di conversione desiderato.

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

Passo 2: Assicurarsi che la dimensione finale sia corretta per il valore DPI corrente.

Poiché WPFWPF scalerà l'interfaccia utente per il valore DPI corrente usando la proprietà BitmapScalingMode impostata su UIElement, un controllo Image che usa un'immagine prescalata in quanto l'origine avrà un aspetto due o tre volte più grande di quanto dovrebbe. Di seguito sono riportati alcuni modi per contrastare questo effetto:

- Se si conosce la dimensione dell'immagine originale al 100%, è possibile specificare le dimensioni esatte del controllo Immagine. Queste dimensioni rifletteranno le dimensioni dell'interfaccia utente prima dell'applicazione del ridimensionamento.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Se le dimensioni dell'immagine originale non sono note, è possibile utilizzare un LayoutTransform per ridurre l'oggetto Image finale. Ad esempio:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Abilitazione del supporto HDPI per il WebOC
Per impostazione predefinita, i controlli WebOC (ad esempio il controllo WebBrowser in WPFWPF o l'interfaccia IWebBrowser2) non abilitano il rilevamento e il supporto HDPI. Il risultato sarà un controllo incorporato con contenuto di visualizzazione troppo piccolo su uno schermo ad alta risoluzione. Di seguito viene descritto come abilitare il supporto DPI elevato in una specifica istanza WebOC Web.

Implementare l'interfaccia IDocHostUIHandler (vedere l'articolo MSDN su [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

Facoltativamente, implementare l'interfaccia ICustomDoc (vedere l'articolo MSDN su [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Associare la classe che implementa IDocHostUIHandler al documento del WebOC. Se è stata implementata l'interfaccia ICustomDoc precedente, non appena la proprietà del documento del WebOC è valida, eseguire il cast a un ICustomDoc e chiamare il metodo SetUIHandler, passando la classe che implementa IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Se NON è stata implementata l'interfaccia ICustomDoc, non appena la proprietà del documento del WebOC è valida, `SetClientSite` sarà necessario eseguire il cast a un oggetto IOleObject e chiamare il metodo, passando la classe che implementa IDocHostUIHandler. Impostare il flag di DOCHOSTUIFLAG_DPI_AWARE sul `GetHostInfo` DOCHOSTUIINFO passato alla chiamata al metodo:

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

Questo dovrebbe essere tutto ciò di cui hai bisogno per ottenere il tuo controllo WebOC per supportare HPDI.

## <a name="tips"></a>Suggerimenti

1. Se la proprietà del documento nel controllo WebOC viene modificata, potrebbe essere necessario riassociare il documento alla classe IDocHostUIHandler.

2. Se quanto sopra non funziona, c'è un problema noto con il WebOC non captare la modifica al flag DPI. Il modo più affidabile per risolvere questo problema consiste nell'alternare lo zoom ottico del WebOC, ovvero due chiamate con due valori diversi per la percentuale di zoom. Inoltre, se questa soluzione è necessaria, potrebbe essere necessario eseguirla a ogni chiamata di navigazione.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
