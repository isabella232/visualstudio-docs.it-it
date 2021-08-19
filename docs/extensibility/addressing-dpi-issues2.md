---
title: Risoluzione dei problemi DPI2 | Microsoft Docs
description: Informazioni sui problemi relativi alla programmazione per le schermate ad alta risoluzione, ad esempio la scalabilità verticale del contenuto, i problemi di layout e l'uso delle API di ridimensionamento DPI.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3ca4544b153d5b365d3200a79a519cf6271d29bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133406"
---
# <a name="address-dpi-issues"></a>Risolvere i problemi relativi ai valori DPI
Un numero crescente di dispositivi viene spedto con schermate ad alta risoluzione. Queste schermate hanno in genere più di 200 pixel per pollice (ppi). L'uso di un'applicazione in questi computer richiederà la scalabilità verticale del contenuto per soddisfare le esigenze di visualizzazione del contenuto a una distanza di visualizzazione normale per il dispositivo. A inizio 2014, l'obiettivo principale per gli schermi ad alta densità è quello di dispositivi di elaborazione mobile (tablet, portatili a forma di acino e telefoni).

Windows 8.1 e versioni successive contengono diverse funzionalità che consentono a queste macchine di funzionare con schermi e ambienti in cui la macchina è collegata contemporaneamente a schermi ad alta densità e a densità standard.

- Windows possibile ridimensionare il contenuto nel dispositivo usando l'impostazione "Aumentare o ridimensionare il testo e altri elementi" (disponibile a partire da Windows XP).

- Windows 8.1 e versioni successive ridimensionano automaticamente il contenuto per la maggior parte delle applicazioni in modo che sia coerente quando vengono spostate tra le diverse densità di pixel. Quando lo schermo principale è ad alta densità (ridimensionamento del 200%) e lo schermo secondario è a densità standard (100%), Windows ridimensiona automaticamente il contenuto della finestra dell'applicazione sullo schermo secondario (1 pixel visualizzato ogni 4 pixel sottoposto a rendering dall'applicazione).

- Windows per impostazione predefinita il ridimensionamento destro per la densità in pixel e la distanza di visualizzazione per lo schermo (Windows 7 e versioni successive, configurabile dall'OEM).

- Windows possibile ridimensionare automaticamente il contenuto fino al 250% nei nuovi dispositivi che superano i 280 ppi (a Windows 8.1 S14).

  Windows ha un modo per gestire la scalabilità verticale dell'interfaccia utente per sfruttare i vantaggi di un numero maggiore di pixel. Un'applicazione acconsente esplicitamente a questo sistema dichiarando se stessa "in grado di riconoscere DPI di sistema". Le applicazioni che non ese frecciano a questo livello vengono ridimensionate dal sistema. Ciò può comportare un'esperienza utente "fuzzy" in cui l'intera applicazione è adattata in modo uniforme ai pixel. Esempio:

  ![Problemi DPI - sfocatura](../extensibility/media/dpi-issues-fuzzy.png "Problemi DPI - sfocatura")

  Visual Studio acconsente esplicitamente a essere in grado di riconoscere il ridimensionamento DPI e pertanto non è "virtualizzato".

  Windows (e Visual Studio) sfruttano diverse tecnologie di interfaccia utente, che hanno modi diversi per gestire i fattori di ridimensionamento impostati dal sistema. Esempio:

- WPF misura i controlli in modo indipendente dal dispositivo (unità, non pixel). L'interfaccia utente WPF si ridimensiona automaticamente per il valore DPI corrente.

- Tutte le dimensioni del testo indipendentemente dal framework dell'interfaccia utente sono espresse in punti e pertanto vengono considerate dal sistema come indipendenti da DPI. Il testo in Win32, WinForms e WPF è già ridimensionato correttamente quando viene disegnato sul dispositivo di visualizzazione.

- Le finestre e le finestre win32/WinForms consentono di abilitare il layout che viene ridimensionato con il testo, ad esempio tramite pannelli di layout griglia, di flusso e di tabella. Queste opzioni consentono di evitare posizioni di pixel hard-coded che non vengono ridimensionate quando le dimensioni dei caratteri aumentano.

- Le icone fornite dal sistema o dalle risorse in base alle metriche di sistema (ad esempio, SM_CXICON e SM_CXSMICON) sono già state ridimensionate.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Interfaccia utente basata su Win32 (GDI, GDI+) e WinForms precedente
Anche se WPF supporta già valori DPI elevati, gran parte del codice basato su Win32/GDI non è stata originariamente scritta tenendo presente il riconoscimento DPI. Windows ha fornito API di ridimensionamento DPI. Le correzioni ai problemi di Win32 devono usarle in modo coerente nel prodotto. Visual Studio ha fornito una libreria di classi helper per evitare la duplicazione delle funzionalità e garantire la coerenza nel prodotto.

## <a name="high-resolution-images"></a>Immagini ad alta risoluzione
Questa sezione è destinata principalmente agli sviluppatori che estendono Visual Studio 2013. Per Visual Studio 2015, usare il servizio immagini integrato in Visual Studio. È anche possibile che sia necessario supportare o specificare come destinazione molte versioni di Visual Studio e pertanto l'uso del servizio immagini in 2015 non è un'opzione perché non esiste nelle versioni precedenti. Questa sezione è disponibile anche per l'utente.

## <a name="scaling-up-images-that-are-too-small"></a>Aumento delle dimensioni delle immagini troppo piccole
Le immagini troppo piccole possono essere ridimensionate e sottoposte a rendering in GDI e WPF usando alcuni metodi comuni. Le classi helper DPI gestite sono disponibili per gli integratori di Visual Studio interni ed esterni per risolvere icone di ridimensionamento, bitmap, imagestrip e imagelist. Sono disponibili helper C/C++ nativi basati su Win32 per il ridimensionamento di HICON, HBITMAP, HIMAGELIST e VsUI::GdiplusImage. Il ridimensionamento di una bitmap richiede in genere solo una modifica di una riga dopo aver incluso un riferimento alla libreria helper. Esempio:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Il ridimensionamento di un elenco di immagini dipende dal fatto che l'elenco immagini sia completo in fase di caricamento o aggiunto in fase di esecuzione. Se completato in fase di caricamento, chiamare `LogicalToDeviceUnits()` con imagelist come si farebbe con una bitmap. Quando il codice deve caricare una singola bitmap prima di comporre l'elenco immagini, assicurarsi di ridimensionare le dimensioni dell'immagine dell'elenco immagini:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Nel codice nativo le dimensioni possono essere ridimensionate durante la creazione dell'elenco immagini come indicato di seguito:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Le funzioni nella libreria consentono di specificare l'algoritmo di ridimensionamento. Quando si ridimensionano le immagini da inserire negli elenchi di immagini, assicurarsi di specificare il colore di sfondo usato per la trasparenza oppure usare nearestNeighbor scaling (che causerà distorsioni al 125% e al 150%).

Consultare la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentazione su MSDN.

La tabella seguente mostra esempi di come le immagini devono essere ridimensionate in base ai fattori di scala DPI corrispondenti. Le immagini in arancione indicano la procedura consigliata a Visual Studio 2013 (ridimensionamento DPI da 100%-200)::

![Problemi DPI - ridimensionamento](../extensibility/media/dpi-issues-scaling.png "Problemi DPI - ridimensionamento")

## <a name="layout-issues"></a>Problemi di layout
I problemi di layout comuni possono essere evitati principalmente mantenendo i punti nell'interfaccia utente ridimensionati e relativi l'uno rispetto all'altro anziché usando posizioni assolute (in particolare, in unità pixel). Esempio:

- Le posizioni di layout/testo devono essere modificate per prendere in considerazione le immagini con scalabilità verticale.

- Le colonne nelle griglie devono avere larghezze regolate per il testo ridimensionato.

- Sarà necessario aumentare anche le dimensioni hard-coded o lo spazio tra gli elementi. Le dimensioni basate solo sulle dimensioni del testo sono in genere esatte, perché i tipi di carattere vengono ridimensionati automaticamente.

  Le funzioni helper sono disponibili nella <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe per consentire il ridimensionamento sull'asse X e Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (le funzioni consentono il ridimensionamento sull'asse X/Y)

- int space = DpiHelper.LogicalToDeviceUnitsX (10);

- int height = VsUI::D piHelper::LogicalToDeviceUnitsY(5);

  Sono disponibili overload LogicalToDeviceUnits per consentire il ridimensionamento di oggetti come Rect, Point e Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Uso della libreria/classe DPIHelper per ridimensionare immagini e layout
La Visual Studio helper DPI è disponibile nei moduli nativi e gestiti e può essere usata all'esterno della shell Visual Studio da altre applicazioni.

Per usare la libreria, passare agli esempi di estendibilità [Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) e clonare il High-DPI_Images_Icons esempio.

Nei file di origine includere *VsUIDpiHelper.h* e chiamare le funzioni statiche della `VsUI::DpiHelper` classe :

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Non usare le funzioni helper nelle variabili statiche a livello di modulo o di classe. La libreria usa anche elementi statici per la sincronizzazione dei thread e potrebbero verificarsi problemi di inizializzazione dell'ordine. Convertire le variabili statiche in variabili membro non statiche o eseguire il wrapping in una funzione (in modo che siano costruite al primo accesso).

Per accedere alle funzioni helper DPI dal codice gestito che verrà eseguito all'interno Visual Studio ambiente:

- Il progetto che lo utilizza deve fare riferimento alla versione più recente di Shell MPF. Esempio:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Verificare che il progetto abbia riferimenti **a System.Windows. Forms,** **PresentationCore** e **PresentationUI.**

- Nel codice usare lo spazio **dei nomi Microsoft.VisualStudio.PlatformUI** e chiamare le funzioni statiche della classe DpiHelper. Per i tipi supportati (punti, dimensioni, rettangoli e così via), sono disponibili funzioni di estensione che restituiscono nuovi oggetti ridimensionati. Esempio:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Gestione del fuzziness delle immagini WPF nell'interfaccia utente ingrandibile
In WPF le bitmap vengono ridimensionate automaticamente da WPF per il livello di zoom DPI corrente usando un algoritmo bicubico di alta qualità (impostazione predefinita), che funziona bene per le immagini o gli screenshot di grandi dimensioni, ma non è appropriato per le icone delle voci di menu perché introduce capogiri percepiti.

Consigli:

- Per immagini del logo e banner, è possibile usare la modalità <xref:System.Windows.Media.BitmapScalingMode> di ridimensionamento predefinita.

- Per le voci di menu e le immagini iconografiche, deve essere usato quando non causa altri artefatti di distorsione per eliminare il <xref:System.Windows.Media.BitmapScalingMode> fuzziness (al 200% e al 300%).

- Per i livelli di zoom di grandi dimensioni non multipli del 100% (ad esempio, 250% o 350%), il ridimensionamento delle immagini iconografiche con risultati bicubici comporta un'interfaccia utente fuzzy e senza problemi. Un risultato migliore si ottiene ridimensionando prima di tutto l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o 300%) e il ridimensionamento con bicubico da qui. Per altre informazioni, vedere Caso speciale: pre-scalabilità di immagini WPF per livelli DPI di grandi dimensioni.

  La classe DpiHelper nello spazio dei nomi Microsoft.VisualStudio.PlatformUI fornisce un membro <xref:System.Windows.Media.BitmapScalingMode> che può essere usato per l'associazione. Consente alla shell Visual Studio di controllare in modo uniforme la modalità di ridimensionamento delle bitmap nel prodotto, a seconda del fattore di scala DPI.

  Per usarlo in XAML, aggiungere:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

La Visual Studio shell imposta già questa proprietà nelle finestre e nelle finestre di dialogo di primo livello. L'interfaccia utente basata su WPF in Visual Studio la erediterà già. Se l'impostazione non viene propagata a parti specifiche dell'interfaccia utente, può essere impostata sull'elemento radice dell'interfaccia utente XAML/WPF. Le posizioni in cui si verifica questa situazione includono popup, elementi con elementi padre Win32 e finestre di progettazione che eseguono un processo non eseguito, ad esempio Blend.

Alcune dell'interfaccia utente possono essere ridimensionate indipendentemente dal livello di zoom DPI impostato dal sistema, ad esempio l'editor di testo Visual Studio e le finestre di progettazione basate su WPF (WPF Desktop e Windows Store). In questi casi, DpiHelper.BitmapScalingMode non deve essere usato. Per risolvere questo problema nell'editor, il team IDE ha creato una proprietà personalizzata intitolata RenderOptions.BitmapScalingMode. Impostare il valore della proprietà su HighQuality o NearestNeighbor a seconda del livello di zoom combinato del sistema e dell'interfaccia utente.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso speciale: prescaling di immagini WPF per livelli DPI di grandi dimensioni
Per i livelli di zoom molto grandi che non sono multipli del 100% (ad esempio, 250%, 350% e così via), il ridimensionamento delle immagini iconografiche con bicubic comporta un'interfaccia utente fuzzy e non più disponibile. L'impressione di queste immagini insieme a testo nitido è quasi simile a quella di un'idea ottico. Le immagini sembrano essere più vicine all'occhio e fuori dalla messa a fuoco in relazione al testo. Il risultato del ridimensionamento con queste dimensioni ingrandite può essere migliorato ridimensionando prima l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o 300%) e ridimensionando con bicubico fino al resto (un ulteriore 50%).

Di seguito è riportato un esempio delle differenze nei risultati, in cui la prima immagine viene ridimensionata con l'algoritmo di ridimensionamento doppio migliorato 100% >200% >250% e la seconda solo con bicubico 100% >250%.

![Esempio di scalabilità doppia dei problemi DPI](../extensibility/media/dpi-issues-double-scaling-example.png "Esempio di scalabilità doppia dei problemi DPI")

Per consentire all'interfaccia utente di usare questo doppio ridimensionamento, sarà necessario modificare il markup XAML per la visualizzazione di ogni elemento Image. Gli esempi seguenti illustrano come usare la scalabilità doppia in WPF in Visual Studio usando la libreria DpiHelper e Shell.12/14.

Passaggio 1: Pre-ridimensionare l'immagine al 200%, al 300% e così via usando NearestNeighbor.

Eseguire il ridimensionamento preliminare dell'immagine usando un convertitore applicato a un'associazione o con un'estensione di markup XAML. Esempio:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Se l'immagine deve anche essere con i colori (la maggior parte, se non tutte, dovrebbero), il markup può usare un convertitore diverso che esegue prima il ridimensionamento dell'immagine e quindi il pre-ridimensionamento. Il markup può usare o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> , a seconda dell'output di conversione desiderato.

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

Passaggio 2: Verificare che le dimensioni finali siano corrette per il valore DPI corrente.

Poiché WPF ridimensiona l'interfaccia utente per il valore DPI corrente usando la proprietà BitmapScalingMode impostata su UIElement, un controllo Immagine che usa un'immagine prescalata come origine avrà un aspetto due o tre volte più grande del necessario. Di seguito sono riportati due modi per contrastare questo effetto:

- Se si conosce la dimensione dell'immagine originale al 100%, è possibile specificare le dimensioni esatte del controllo Immagine. Queste dimensioni rifletteranno le dimensioni dell'interfaccia utente prima dell'applicazione del ridimensionamento.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Se le dimensioni dell'immagine originale non sono note, è possibile usare LayoutTransform per ridimensionare l'oggetto Image finale. Esempio:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Abilitazione del supporto HDPI per WebOC
Per impostazione predefinita, i controlli WebOC (ad esempio il controllo WebBrowser in WPF o l'interfaccia IWebBrowser2) non abilitano il rilevamento e il supporto HDPI. Il risultato sarà un controllo incorporato con contenuto di visualizzazione troppo piccolo su uno schermo ad alta risoluzione. Di seguito viene descritto come abilitare il supporto di valori DPI elevati in un'istanza WebOC specifica.

Implementare l'interfaccia IDocHostUIHandler (vedere l'articolo MSDN su [IDocHostUIHandler):](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))

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

Facoltativamente, implementare l'interfaccia ICustomDoc (vedere l'articolo MSDN su [ICustomDoc:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Associare la classe che implementa IDocHostUIHandler al documento di WebOC. Se è stata implementata l'interfaccia ICustomDoc precedente, non appena la proprietà document di WebOC è valida, eseguire il cast a un oggetto ICustomDoc e chiamare il metodo SetUIHandler, passando la classe che implementa IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Se NON è stata implementata l'interfaccia ICustomDoc, non appena la proprietà document di WebOC è valida, sarà necessario eseguire il cast a un oggetto IOleObject e chiamare il metodo , passando la classe che implementa `SetClientSite` IDocHostUIHandler. Impostare il flag DOCHOSTUIFLAG_DPI_AWARE sull'oggetto DOCHOSTUIINFO passato alla `GetHostInfo` chiamata al metodo :

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

Questo dovrebbe essere tutto ciò che serve per ottenere il controllo WebOC per supportare HPDI.

## <a name="tips"></a>Suggerimenti

1. Se la proprietà del documento nel controllo WebOC cambia, potrebbe essere necessario riassociare il documento alla classe IDocHostUIHandler.

2. Se l'opzione precedente non funziona, si è verificato un problema noto con weboc che non ha rilevato la modifica al flag DPI. Il modo più affidabile per risolvere questo problema è attivare o disattivare lo zoom ottico di WebOC, ovvero due chiamate con due valori diversi per la percentuale di zoom. Inoltre, se questa soluzione alternativa è necessaria, potrebbe essere necessario eseguirla a ogni chiamata di navigazione.

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
