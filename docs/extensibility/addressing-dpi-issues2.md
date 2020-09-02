---
title: Addressing DPI Issues2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740098"
---
# <a name="address-dpi-issues"></a>Risolvere i problemi di DPI
Un numero crescente di dispositivi viene distribuito con schermate ad alta risoluzione. Queste schermate hanno in genere più di 200 pixel per pollice (PPI). L'uso di un'applicazione su questi computer richiede il ridimensionamento del contenuto per soddisfare le esigenze di visualizzazione del contenuto a una distanza di visualizzazione normale per il dispositivo. A partire da 2014, la destinazione principale per i display ad alta densità è costituita dai dispositivi di elaborazione mobile (tablet, portatili a copertura mobile e telefoni).

Windows 8.1 e versioni successive contengono diverse funzionalità per consentire a tali computer di lavorare con gli schermi e gli ambienti in cui il computer è collegato a una visualizzazione a densità elevata e a densità standard nello stesso momento.

- Windows consente di ridimensionare il contenuto al dispositivo usando l'impostazione "Crea testo e altri elementi più grandi o più piccoli" (disponibile a partire da Windows XP).

- Windows 8.1 e versioni successive scaleranno automaticamente il contenuto per la maggior parte delle applicazioni in modo che sia coerente quando lo spostamento tra le visualizzazioni di densità di pixel diversi. Quando la visualizzazione primaria è ad alta densità (200% di ridimensionamento) e la visualizzazione secondaria è densità standard (100%), Windows ridimensiona automaticamente il contenuto della finestra dell'applicazione sullo schermo secondario (1 pixel visualizzato per ogni 4 pixel di cui è stato eseguito il rendering dall'applicazione).

- Windows utilizzerà per impostazione predefinita la scalabilità corretta per la densità dei pixel e la distanza di visualizzazione per la visualizzazione (Windows 7 e versioni successive, configurabili dall'OEM).

- Windows può ridimensionare automaticamente il contenuto fino al 250% nei nuovi dispositivi che superano 280 ppi (Windows 8.1 S14).

  Windows è in grado di gestire la scalabilità verticale dell'interfaccia utente per sfruttare i vantaggi dell'aumento dei conteggi dei pixel. Un'applicazione è in grado di optare per questo sistema dichiarando "compatibilità DPI di sistema". Le applicazioni che non eseguono questa operazione vengono ridimensionate dal sistema. Ciò può comportare un'esperienza utente "fuzzy" in cui l'intera applicazione è allungata in modo uniforme in pixel. Ad esempio:

  ![Problemi DPI - sfocatura](../extensibility/media/dpi-issues-fuzzy.png "Problemi DPI - sfocatura")

  Visual Studio opta per la compatibilità con il ridimensionamento DPI e pertanto non è "virtualizzato".

  Windows (e Visual Studio) sfruttano diverse tecnologie dell'interfaccia utente, che hanno diversi modi per gestire i fattori di scalabilità impostati dal sistema. Ad esempio:

- WPF misura i controlli in modo indipendente dal dispositivo (unità, non pixel). L'interfaccia utente di WPF viene scalata automaticamente per il valore DPI corrente.

- Tutte le dimensioni del testo indipendentemente dal framework dell'interfaccia utente sono espresse in punti, quindi vengono trattate dal sistema come indipendenti da DPI. Il testo in Win32, WinForms e WPF è già stato scalato correttamente quando viene disegnato sul dispositivo di visualizzazione.

- Le finestre di dialogo Win32/WinForms e le finestre consentono di abilitare il layout che viene ridimensionato con il testo (ad esempio, tramite i pannelli di layout Grid, Flow e Table). Questi consentono di evitare percorsi di pixel hardcoded che non vengono ridimensionati quando le dimensioni del carattere aumentano.

- Le icone fornite dal sistema o dalle risorse basate sulle metriche di sistema, ad esempio SM_CXICON e SM_CXSMICON, sono già aumentate.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 precedente (GDI, GDI+) e interfaccia utente basata su Windows Form
Sebbene WPF sia già compatibile con DPI, gran parte del codice basato su Win32/GDI non è stata originariamente scritta con la consapevolezza DPI. Windows ha fornito le API di scalabilità DPI. Le correzioni ai problemi Win32 devono essere utilizzate in modo coerente nel prodotto. Visual Studio ha fornito una libreria di classi helper per evitare la duplicazione delle funzionalità e garantire la coerenza tra il prodotto.

## <a name="high-resolution-images"></a>Immagini ad alta risoluzione
Questa sezione è destinata principalmente agli sviluppatori che estendono Visual Studio 2013. Per Visual Studio 2015, usare il servizio immagini incorporato in Visual Studio. È anche possibile che sia necessario supportare/destinare molte versioni di Visual Studio e quindi usare il servizio immagini in 2015 non è un'opzione perché non esiste nelle versioni precedenti. Questa sezione è anche per te.

## <a name="scaling-up-images-that-are-too-small"></a>Ridimensionamento di immagini troppo piccole
Le immagini troppo piccole possono essere ridimensionate e sottoposte a rendering in GDI e WPF usando alcuni metodi comuni. Le classi helper DPI gestite sono disponibili per gli integratori interni ed esterni di Visual Studio per l'indirizzamento delle icone, delle bitmap, della imagestrips e degli altri. Gli Helper C/C + + nativi basati su Win32 sono disponibili per la scalabilità di HICON, HBITMAP, HIMAGELIST e incorporati vsui:: GdiplusImage. Il ridimensionamento di una bitmap richiede in genere solo una modifica a una riga dopo l'inclusione di un riferimento alla libreria helper. Ad esempio:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Il ridimensionamento di un oggetto ImageList varia a seconda che l'oggetto ImageList venga completato in fase di caricamento o venga aggiunto in fase di esecuzione. Se completato in fase di caricamento, chiamare `LogicalToDeviceUnits()` con ImageList come si farebbe con una bitmap. Quando il codice deve caricare una singola bitmap prima di comporre ImageList, assicurarsi di ridimensionare le dimensioni dell'immagine di ImageList:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Nel codice nativo, le dimensioni possono essere ridimensionate quando si crea l'oggetto ImageList come indicato di seguito:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Le funzioni nella libreria consentono di specificare l'algoritmo di ridimensionamento. Quando si ridimensionano le immagini in modo che vengano posizionate in unagels, assicurarsi di specificare il colore di sfondo usato per la trasparenza oppure usare il ridimensionamento NearestNeighbor, che causerà distorsioni al 125% e 150%).

Consultare la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentazione su MSDN.

La tabella seguente illustra alcuni esempi di come le immagini devono essere ridimensionate in corrispondenza dei fattori di scala DPI corrispondenti. Le immagini delineate in arancione denotano la procedura consigliata a partire da Visual Studio 2013 (100%-200% DPI ridimensionamento):

![Problemi DPI - ridimensionamento](../extensibility/media/dpi-issues-scaling.png "Problemi DPI - ridimensionamento")

## <a name="layout-issues"></a>Problemi di layout
I problemi di layout comuni possono essere evitati principalmente mantenendo i punti nell'interfaccia utente ridimensionati e relativi tra loro anziché usando posizioni assolute (in particolare, in unità pixel). Ad esempio:

- Le posizioni di layout/testo devono essere modificate per tenere conto delle immagini con scalabilità verticale.

- Per le colonne nelle griglie è necessario modificare le larghezze per il testo con scalabilità verticale.

- Sarà inoltre necessario aumentare le dimensioni o lo spazio hardcoded tra gli elementi. Le dimensioni basate solo sulle dimensioni del testo sono in genere adeguate, poiché i tipi di carattere vengono ridimensionati automaticamente.

  Le funzioni di supporto sono disponibili nella <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe per consentire il ridimensionamento sull'asse X e Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funzioni che consentono il ridimensionamento sull'asse X/Y)

- spazio int = DpiHelper. LogicalToDeviceUnitsX (10);

- int height = incorporati vsui::D piHelper:: LogicalToDeviceUnitsY (5);

  Sono disponibili overload LogicalToDeviceUnits per consentire il ridimensionamento di oggetti, ad esempio Rect, Point e size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Uso della libreria/classe DPIHelper per scalare immagini e layout
La libreria helper DPI di Visual Studio è disponibile in moduli nativi e gestiti e può essere usata all'esterno della shell di Visual Studio da altre applicazioni.

Per usare la libreria, vedere gli [esempi di estendibilità di Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) e clonare l'esempio High-DPI_Images_Icons.

Nei file di origine includere *VsUIDpiHelper. h* e chiamare le funzioni statiche della `VsUI::DpiHelper` classe:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Non usare le funzioni helper nelle variabili statiche a livello di modulo o di classe. La libreria usa anche gli elementi statici per la sincronizzazione dei thread ed è possibile che si verifichino problemi di inizializzazione degli ordini. Convertire tali elementi statici in variabili membro non statiche o eseguirne il wrapping in una funzione, in modo che vengano costruiti al primo accesso.

Per accedere alle funzioni helper DPI dal codice gestito che viene eseguito all'interno dell'ambiente di Visual Studio:

- Il progetto consumer deve fare riferimento alla versione più recente di Shell MPF. Ad esempio:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Verificare che il progetto includa riferimenti a **System. Windows. Forms**, **PresentationCore**e **presentationui**.

- Nel codice usare lo spazio dei nomi **Microsoft. VisualStudio. PlatformUI** e chiamare le funzioni statiche della classe DpiHelper. Per i tipi supportati (punti, dimensioni, rettangoli e così via), sono disponibili funzioni di estensione che restituiscono nuovi oggetti ridimensionati. Ad esempio:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Gestione delle immagini WPF confusione nell'interfaccia utente Zoomable
In WPF, le bitmap vengono ridimensionate automaticamente da WPF per il livello di zoom DPI corrente usando un algoritmo bicubico di alta qualità (impostazione predefinita), che funziona bene per immagini o screenshot di grandi dimensioni, ma non è appropriato per le icone delle voci di menu perché introduce confusione percepite.

Consigli:

- Per l'immagine del logo e i banner, <xref:System.Windows.Media.BitmapScalingMode> è possibile usare la modalità di ridimensionamento predefinita.

- Per le voci di menu e le immagini di iconografia, è <xref:System.Windows.Media.BitmapScalingMode> necessario usare quando non provoca l'eliminazione di altri elementi di distorsione confusione (al 200% e 300%).

- Per i livelli di zoom di grandi dimensioni non multipli del 100% (ad esempio, 250% o 350%), ridimensionando le immagini iconografiche con risultati bicubici nell'interfaccia utente fuzzy e sbiadita. Per ottenere un risultato migliore, è necessario innanzitutto ridimensionare l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o 300%) e la scalabilità con bicubico da qui. Vedere caso speciale: prescalare le immagini WPF per i livelli DPI di grandi dimensioni per altre informazioni.

  La classe DpiHelper nello spazio dei nomi Microsoft. VisualStudio. PlatformUI fornisce un membro <xref:System.Windows.Media.BitmapScalingMode> che può essere utilizzato per l'associazione. Consente la shell di Visual Studio per controllare la modalità di ridimensionamento delle bitmap nel prodotto in modo uniforme, a seconda del fattore di scala DPI.

  Per usarlo in XAML, aggiungere:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

La shell di Visual Studio già imposta questa proprietà nelle finestre di primo livello e nei dialoghi. L'interfaccia utente basata su WPF in esecuzione in Visual Studio lo erediterà già. Se l'impostazione non viene propagata alle parti specifiche dell'interfaccia utente, può essere impostata sull'elemento radice dell'interfaccia utente XAML/WPF. I punti in cui si verifica questo evento includono i popup, gli elementi con i padri Win32 e le finestre di progettazione che esauriscono il processo, ad esempio Blend.

Alcune interfacce utente possono essere ridimensionate indipendentemente dal livello di zoom DPI impostato dal sistema, ad esempio l'editor di testo di Visual Studio e le finestre di progettazione basate su WPF (desktop WPF e Windows Store). In questi casi, non è consigliabile usare DpiHelper. BitmapScalingMode. Per risolvere questo problema nell'editor, il team IDE ha creato una proprietà personalizzata denominata RenderOptions. BitmapScalingMode. Impostare il valore della proprietà su HighQuality o NearestNeighbor a seconda del livello di zoom combinato del sistema e dell'interfaccia utente.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso speciale: ridimensionare le immagini WPF per i livelli DPI di grandi dimensioni
Per i livelli di zoom molto grandi che non sono multipli del 100% (ad esempio, 250%, 350% e così via), ridimensionare le immagini iconografiche con risultati bicubici nell'interfaccia utente sfocata. L'impressione di queste immagini insieme a testo nitido è quasi come quella di un'illusione ottica. Le immagini sembrano essere più vicine all'occhio e sfocate rispetto al testo. Il risultato di ridimensionamento a questa dimensione ingrandita può essere migliorato scalando prima l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o 300%) e la scalabilità con un valore bicubico al resto (un ulteriore 50%).

Di seguito è riportato un esempio delle differenze nei risultati, in cui la prima immagine viene ridimensionata con l'algoritmo a doppio ridimensionamento migliorato 100%->200%->250% e il secondo solo con il 100%->250%.

![Esempio di scalabilità doppia dei problemi DPI](../extensibility/media/dpi-issues-double-scaling-example.png "Esempio di scalabilità doppia dei problemi DPI")

Per consentire all'interfaccia utente di usare questo doppio ridimensionamento, è necessario modificare il markup XAML per la visualizzazione di ogni elemento immagine. Gli esempi seguenti illustrano come usare la scalabilità doppia in WPF in Visual Studio usando la libreria DpiHelper e la Shell. 12/14.

Passaggio 1: eseguire la scalabilità dell'immagine in base al 200%, 300% e così via usando NearestNeighbor.

Ridimensionare l'immagine utilizzando un convertitore applicato a un'associazione o con un'estensione di markup XAML. Ad esempio:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Se l'immagine deve anche essere con tema (la maggior parte, se non tutte, dovrebbe), il markup può usare un convertitore diverso che prima esegue l'applicazione dell'immagine e quindi esegue il pre-ridimensionamento. Il markup può usare <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> , a seconda dell'output di conversione desiderato.

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

Passaggio 2: verificare che le dimensioni finali siano corrette per il valore DPI corrente.

Poiché WPF ridimensiona l'interfaccia utente per il valore DPI corrente usando la proprietà BitmapScalingMode impostata su UIElement, un controllo immagine che usa un'immagine con scalabilità orizzontale come origine avrà un aspetto due o tre volte superiore rispetto a quello previsto. Di seguito sono riportati alcuni modi per contrastare questo effetto:

- Se si conosce la dimensione dell'immagine originale al 100%, è possibile specificare la dimensione esatta del controllo immagine. Queste dimensioni riflettono le dimensioni dell'interfaccia utente prima che venga applicato il ridimensionamento.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Se le dimensioni dell'immagine originale non sono note, è possibile usare un LayoutTransform per ridurre l'oggetto immagine finale. Ad esempio:

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
Per impostazione predefinita, i controlli WebOC (ad esempio il controllo WebBrowser in WPF o l'interfaccia IWebBrowser2) non abilitano il rilevamento e il supporto di HDPI. Il risultato sarà un controllo incorporato con contenuto di visualizzazione troppo piccolo in una visualizzazione ad alta risoluzione. Di seguito viene descritto come abilitare il supporto di valori DPI alti in un'istanza di WebOC Web specifica.

Implementare l'interfaccia IDocHostUIHandler (vedere l'articolo di MSDN su [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Facoltativamente, implementare l'interfaccia ICustomDoc (vedere l'articolo di MSDN su [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Associare la classe che implementa IDocHostUIHandler al documento di WebOC. Se è stata implementata l'interfaccia ICustomDoc precedente, non appena la proprietà del documento del WebOC è valida, eseguirne il cast a un ICustomDoc e chiamare il metodo SetUIHandler, passando la classe che implementa IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Se non è stata implementata l'interfaccia ICustomDoc, non appena la proprietà del documento del WebOC è valida, sarà necessario eseguirne il cast a un oggetto IOleObject e chiamare il `SetClientSite` metodo, passando la classe che implementa IDocHostUIHandler. Impostare il flag DOCHOSTUIFLAG_DPI_AWARE in DOCHOSTUIINFO passato alla chiamata al `GetHostInfo` Metodo:

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

Questa operazione dovrebbe essere necessaria per ottenere il controllo WebOC per il supporto di HPDI.

## <a name="tips"></a>Suggerimenti

1. Se la proprietà Document sul controllo WebOC viene modificata, potrebbe essere necessario riassociare il documento alla classe IDocHostUIHandler.

2. Se il valore precedente non funziona, si verifica un problema noto con WebOC che non preleva la modifica al flag DPI. Il modo più affidabile per correggere questo problema consiste nell'abilitare/disabilitare lo zoom ottico del WebOC, vale a dire due chiamate con due valori diversi per la percentuale di zoom. Inoltre, se questa soluzione alternativa è obbligatoria, potrebbe essere necessario eseguirla a ogni chiamata di esplorazione.

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
