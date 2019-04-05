---
title: Indirizzamento Problemi2 DPI | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c5ae2abeea1e1e6b5a2fe360ff8515e5096341
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955334"
---
# <a name="addressing-dpi-issues"></a>Risoluzione dei problemi relativi a DPI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un numero crescente di dispositivi è distribuiti con "schermi". Queste schermate hanno in genere più di 200 pixel per pollice (PPID). Per lavorare con un'applicazione in tali computer sarà necessario il contenuto per la scalabilità verticale per soddisfare le esigenze di visualizzazione del contenuto a una distanza di visualizzazione normale per il dispositivo. A partire dal 2014, la destinazione principale per schermi ad alta densità è mobile computing dispositivi (Tablet, computer portatili conchiglia e telefoni).  
  
 Windows 8.1 e versioni successive sono disponibili molte funzionalità per abilitare questi computer lavorare con gli ambienti in cui la macchina è collegata a entrambi ad alta densità e densità standard consente di visualizzare contemporaneamente e consente di visualizzare.  
  
- Windows può consentire di ridimensiona il contenuto nel dispositivo usando il "rendere il testo e altri elementi superiori o inferiori" impostazione (disponibile a partire da Windows XP).  
  
- Windows 8.1 e versioni successive verranno automaticamente scalati in contenuto per la maggior parte delle applicazioni sia coerente quando spostato tra schermi di diverse densità di pixel. Quando la visualizzazione principale è ad alta densità (200% scalabilità) e la visualizzazione secondaria è densità standard (100%), Windows ridimensionerà automaticamente il contenuto della finestra dell'applicazione verso il basso nella visualizzazione secondaria (1 pixel visualizzati per ogni 4 pixel eseguito il rendering tramite il applicazione).  
  
- Windows predefinita sarà il diritto di ridimensionamento per la densità di pixel e la visualizzazione di distanza per la visualizzazione (Windows 7 e versioni successive, configurabile dall'OEM).  
  
- Windows può ridimensionare automaticamente il contenuto di 250% su nuovi dispositivi che superano 280 ppi (a partire da Windows 8.1 S14).  
  
  Windows dispone di una soluzione per gestire la scalabilità verticale dell'interfaccia utente per sfruttare i vantaggi del numero di pixel maggiore di. Un'applicazione consente di partecipare a questo sistema dichiarando stesso "DPI del sistema." Le applicazioni che non eseguire questa operazione vengono aumentate dal sistema. Ciò può comportare un'esperienza utente "fuzzy" in cui l'intera applicazione è in modo uniforme pixel in modalità estesa. Ad esempio:  
  
  ![Valore DPI emette Fuzzy](../extensibility/media/dpi-issues-fuzzy.png "DPI emette Fuzzy")  
  
  Visual Studio consente di partecipare alla scalabilità compatibile con DPI e pertanto non è "virtualizzato."  
  
  Windows (e Visual Studio) sfruttare diverse tecnologie dell'interfaccia utente, che sono diversi modi di affrontare fattori impostati dal sistema di scalabilità. Ad esempio:  
  
- WPF misura i controlli in modo indipendente dalla periferica (unità, non pixel). WPF UI offre scalabilità automatica per il valore DPI corrente.  
  
- Tutte le dimensioni di testo indipendentemente dal framework dell'interfaccia utente sono espresse in punti e pertanto vengono considerate dal sistema come indipendente da DPI. Testo in WPF, WinForms e Win32 già aumentare le prestazioni in modo corretto quando viene disegnata sulla periferica di visualizzazione.  
  
- Finestre e finestre di dialogo Win32/WinForms dispongono di mezzi per l'abilitazione di layout che viene ridimensionato con testo, ad esempio, tramite griglia, flow e pannelli di layout di tabella. Che permettono di evitare i percorsi hardcoded pixel che non vengono scalati quando vengono aumentate le dimensioni dei caratteri.  
  
- Icone fornite dal sistema o risorse in base alle metriche di sistema (ad esempio, SM_CXICON e SM_CXSMICON) sono già ridimensionate.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 meno recenti (GDI, GDI+) e l'interfaccia utente basata su Windows Form  
 Mentre WPF è ancora compatibile con elevata DPI, gran parte del codice basata su Win32/GDI non è stato scritto originariamente con compatibilità con DPI in considerazione. Windows ha fornito le API con ridimensionamento DPI. Le correzioni ai problemi di Win32 devono essere considerati in modo uniforme per il prodotto. Visual Studio ha fornito un supporto di libreria di classi per evitare la duplicazione di funzionalità e la garanzia di coerenza interno del prodotto.  
  
## <a name="high-resolution-images"></a>Immagini ad alta risoluzione  
 In questa sezione viene utilizzato principalmente per gli sviluppatori di estendere Visual Studio 2013. Per Visual Studio 2015, usare il servizio immagini integrato in Visual Studio. È inoltre possibile trovare che è necessario il supporto e la destinazione molte versioni di Visual Studio e quindi usando il servizio di immagine nel 2015 non è disponibile poiché non esiste nelle versioni precedenti. In questa sezione è inoltre quindi.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Scalabilità verticale di immagini che sono troppo piccole  
 Le immagini che sono troppo piccole possono essere "aumentate" e il rendering su GDI e WPF usando alcuni metodi comuni. Classi helper DPI gestite sono disponibili per gli integratori di Visual Studio interni ed esterni all'indirizzo ridimensionamento delle icone, bitmap, imagestrips e imagelists. Basata su Win32 nativo C / C++ helper sono disponibili per la scalabilità HICON, HBITMAP, HIMAGELIST e VsUI::GdiplusImage. Ridimensionamento di una bitmap in genere richiede solo una modifica di una riga dopo l'inserimento di un riferimento alla libreria helper. Ad esempio:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Ridimensionamento di un oggetto imagelist varia a seconda se è stato completato in fase di caricamento, il componente imagelist o viene aggiunto in fase di esecuzione. Se in fase di caricamento è completo, chiamare LogicalToDeviceUnits() con imagelist come si farebbe con un'immagine bitmap. Quando il codice deve caricare una bitmap singoli prima di scrivere imagelist, assicurarsi di aumentare le dimensioni dell'immagine di imagelist:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 In codice nativo, le dimensioni possono essere ridimensionate quando si crea l'oggetto imagelist come indicato di seguito:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funzioni della libreria consentono l'utilizzo dell'algoritmo di ridimensionamento. Quando ridimensionamento immagini da inserire nella imagelists, assicurarsi di specificare il colore di sfondo usato per la trasparenza o usare la scalabilità NearestNeighbor (che determina le distorsioni al 125% e % 150).  
  
 Consultare il <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentazione su MSDN.  
  
 Nella tabella seguente vengono illustrati esempi di modalità di ridimensionamento immagini DPI corrispondente fattori di scala. Le immagini in verde indicano la procedura consigliata a partire da Visual Studio 2013 (ridimensionamento DPI del 100%, 200%):  
  
 ![Problemi DPI-ridimensionamento](../extensibility/media/dpi-issues-scaling.png "problemi DPI-ridimensionamento")  
  
## <a name="layout-issues"></a>Problemi di layout  
 È possibile evitare problemi di layout comuni principalmente, mantenendo i punti nell'interfaccia utente di scalabilità e una rispetto a altra, anziché usare posizioni assolute (in particolare, in unità di pixel). Ad esempio:  
  
- Le posizioni di layout di testo/necessario modificare account per le immagini con scalabilità verticale.  
  
- Le colonne nelle griglie necessario hanno larghezze regolate per il testo con scalabilità verticale.  
  
- Nonché aumentare le dimensioni impostate come hardcoded o uno spazio tra gli elementi. Dimensioni basate solo sulle dimensioni di testo sono in genere tutto bene, perché i tipi di carattere vengono aumentate automaticamente.  
  
  Sono disponibili in funzioni di supporto di <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe per consentire la scalabilità sull'asse X e Y:  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funzioni di consentono la scalabilità in X o asse Y)  
  
- int space = DpiHelper.LogicalToDeviceUnitsX (10);  
  
- int altezza = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
  Esistono overload LogicalToDeviceUnits per consentire il ridimensionamento di oggetti, ad esempio Rect, Point e Size.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Usando la libreria/classe DPIHelper per ridimensionare le immagini e layout  
 La libreria helper DPI di Visual Studio è disponibile nei moduli nativi e gestiti e può essere usata all'esterno di Visual Studio shell da altre applicazioni.  
  
 Per usare la libreria, vedere la [esempi di estendibilità di Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) e clonare l'esempio di elevata DPI_Images_Icons  
  
 Nel file di origine, includere VsUIDpiHelper.h e chiamare le funzioni statiche della classe VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Non usare le funzioni di supporto in variabili statiche a livello di modulo o a livello di classe. La libreria Usa inoltre gli elementi statici per la sincronizzazione dei thread ed è possibile incontrare problemi di ordine-inizializzazione. Convertire tali elementi statici per le variabili di membro non statiche oppure wrap in una funzione (in modo da ottenere costruite al primo accesso).  
  
 Per accedere le funzioni di supporto di valori DPI dal codice gestito che verrà eseguito all'interno dell'ambiente di Visual Studio:  
  
-   Il progetto utilizzato deve fare riferimento alla versione più recente di MPF di Shell. Ad esempio:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Verificare che il progetto contiene riferimenti a **Forms**, **PresentationCore**, e **PresentationUI**.  
  
-   Nel codice, usare il **Microsoft.VisualStudio.PlatformUI** dello spazio dei nomi e chiamare funzioni statiche della classe DpiHelper. Per i tipi supportati (punti, dimensioni, rettangoli e così via), sono disponibili fornite funzioni di estensione che restituiscono nuovi oggetti di scalabilità. Ad esempio:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Gestione di tolleranza di immagini WPF nell'interfaccia utente Ingrandibile  
 In WPF, le bitmap vengono ridimensionate automaticamente da WPF per il livello di zoom DPI corrente mediante un algoritmo bicubica di elevata qualità (impostazione predefinita), che funziona bene per schermate di grandi dimensioni o immagini, ma non è appropriata per le icone di voce di menu perché introduce confusa percepito .  
  
 Indicazioni:  
  
- Per il logo banner e immagine grafica, il valore predefinito <xref:System.Windows.Media.BitmapScalingMode> può essere usato la modalità di ridimensionamento.  
  
- Per le voci di menu e le immagini visualizzato, il <xref:System.Windows.Media.BitmapScalingMode> deve essere usato quando non causa altri elementi di una distorsione a eliminare confusa (nel server % 200 e 300%).  
  
- • Per zoom grandi livelli non multipli di 100% (ad esempio, 250% o % 350), ridimensionamento delle immagini visualizzato con risultati bicubica nell'interfaccia utente fuzzy, sbiadito consentendo di riprodurre. Un risultato migliore ottenuto aumentando prima l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o % 300) e scalabilità con Bicubica da tale posizione. Vedere caso speciale: prescaling immagini WPF per DPI elevato dei livelli per altre informazioni.  
  
  La classe DpiHelper nello spazio dei nomi Microsoft.VisualStudio.PlatformUI fornisce un membro <xref:System.Windows.Media.BitmapScalingMode> che può essere utilizzato per l'associazione. Consentirà la shell di Visual Studio controllare la modalità ridimensionamento delle bitmap interno del prodotto in modo uniforme, in base al fattore di scala DPI.  
  
  Per usarlo in XAML, aggiungere:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 La shell di Visual Studio imposta questa proprietà su finestre di dialogo e finestre di primo livello. Interfaccia utente basato su WPF in esecuzione in Visual Studio già erediterà la proprietà. Se l'impostazione non si propaga le porzioni specifico dell'interfaccia utente, è possibile impostare per l'elemento radice dell'interfaccia utente XAML/WPF. Posizioni in cui ciò accade includono popup, per gli elementi con gli elementi padre Win32, e finestre di progettazione che eseguono di processo, ad esempio Blend.  
  
 Parte dell'interfaccia utente può ridimensionare indipendentemente dal livello di zoom DPI di sistema-set, ad esempio l'editor di testo di Visual Studio e finestre di progettazione basate su WPF (Desktop WPF e Windows Store). In questi casi, DpiHelper.BitmapScalingMode non deve essere utilizzato. Per risolvere il problema nell'editor, il team IDE creato una proprietà personalizzata denominata RenderOptions.BitmapScalingMode. Impostare il valore della proprietà da riprodurre o NearestNeighbor a seconda del livello di zoom combinato del sistema e l'interfaccia utente.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso speciale: prescaling immagini WPF per i livelli di DPI elevati  
 Per i livelli di zoom di dimensioni molto grandi che non sono multipli di 100% (ad esempio, 250%, % 350 e così via), ridimensionamento delle immagini visualizzato con risultati bicubica nell'interfaccia utente fuzzy, sbiadito consentendo di riprodurre. L'impressione di queste immagini insieme a testo nitido è quasi simile a quella di un'illusione ottica. Le immagini sembrano essere più da vicino l'occhio del lettore e in uscita da stato attivo in relazione al testo. Il risultato della scalabilità in queste dimensioni ingrandita può essere migliorato ridimensionando prima l'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, 200% o % 300) e scalabilità con Bicubica al resto (un ulteriore % 50).  
  
 Il seguente è un esempio delle differenze nei risultati, in cui viene ridimensionata la prima immagine con l'algoritmo di ridimensionamento doppia migliorato -> 100%, 200% -> 250% e il secondo avviene con Bicubica 100% -> 250%.  
  
 ![DPI problemi di esempio di ridimensionamento doppia](../extensibility/media/dpi-issues-double-scaling-example.png "DPI emette Double esempio scala")  
  
 Per abilitare l'interfaccia utente per usare questa scalabilità doppia, markup XAML per la visualizzazione di ogni elemento di immagine devono essere modificate. Gli esempi seguenti illustrano come usare la scalabilità double in WPF in Visual Studio usando la libreria di DpiHelper e Shell.12/14.  
  
 Passaggio 1: Prescale l'immagine da % 200, 300% e così via usando NearestNeighbor.  
  
 Prescale l'immagine utilizzando un convertitore di applicare un'associazione, o con un'estensione di markup XAML. Ad esempio:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Se l'immagine deve inoltre essere con temi (la maggior parte, se non tutti, devono), il markup è possibile usare un convertitore di tipi diversi che prima esegue dei temi dell'immagine e quindi pre-ridimensionamento. Può usare il markup <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, a seconda l'output di conversione desiderato.  
  
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
  
 Passaggio 2: Verificare che la dimensione finale sia corretta per il valore DPI corrente.  
  
 Poiché WPF del ridimensionamento dell'interfaccia utente per il valore DPI corrente utilizzando la proprietà BitmapScalingMode nastavit UIElement, un controllo immagine usando un'immagine prescaled perché la relativa origine avrà un aspetto due o tre volte più grandi rispetto al necessario. Di seguito sono un paio di modi per contrastare questo effetto:  
  
-   Se si conosce la dimensione dell'immagine originale al 100%, è possibile specificare la dimensione esatta del controllo immagine. Queste dimensioni riporterà che le dimensioni dell'interfaccia utente prima del ridimensionamento sono applicata.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Se le dimensioni dell'immagine originale non sono noto, una proprietà LayoutTransform è utilizzabile per la scalabilità verso il basso l'oggetto immagine finale. Ad esempio:  
  
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
 Per impostazione predefinita, i controlli WebOC (ad esempio, il controllo WebBrowser in WPF, o l'interfaccia IWebBrowser2) non abilitare il supporto e il rilevamento di HDPI. Il risultato sarà un controllo incorporato con il contenuto visualizzato è troppo piccolo su un display ad alta risoluzione. Di seguito viene descritto come abilitare il supporto di valori DPI alti in un'istanza di WebOC web specifico.  
  
 Implementare l'interfaccia IDocHostUIHandler (vedere l'articolo MSDN sul [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interface):  
  
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
  
 Facoltativamente, implementare l'interfaccia ICustomDoc (vedere l'articolo MSDN sul [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interface):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Associare la classe che implementa IDocHostUIHandler con documento del WebOC. Se è stato implementato l'interfaccia ICustomDoc sopra, come proprietà del documento del WebOC è valida, eseguirne il cast a un ICustomDoc e chiamare il metodo SetUIHandler, passando la classe che implementa IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Se non si ha implementato l'interfaccia ICustomDoc, quindi, non appena la proprietà del documento del WebOC è valida, è necessario eseguirne il cast a un oggetto in IOleObject e chiamare il metodo SetClientSite, passando la classe che implementa IDocHostUIHandler. Impostare il flag DOCHOSTUIFLAG_DPI_AWARE il DOCHOSTUIINFO passato alla chiamata al metodo GetHostInfo:  
  
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
  
 Deve trattarsi di tutto ciò che è necessario ottenere il controllo WebOC per supportare HPDI.  
  
## <a name="tips"></a>Suggerimenti  
  
1.  Se la proprietà di documento nel controllo WebOC cambia, si potrebbe essere necessario riassociare il documento con la classe IDocHostUIHandler.  
  
2.  Se il codice precedente non funziona, è presente un problema noto con WebOC non preleva la modifica al flag DPI. Il modo più affidabile di risoluzione di questo errore è per attivare o disattivare lo zoom ottico del WebOC due chiamate al significato con due valori diversi per la percentuale di zoom. Inoltre, se questa soluzione è necessaria, potrebbe essere necessario per eseguirle in ogni chiamata navigate.  
  
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
