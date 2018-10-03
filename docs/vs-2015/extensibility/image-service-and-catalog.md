---
title: Immagine di servizio e catalogo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3079bada9b8d3e9a0b2644e4aaa3d9e3ee3bebe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526339"
---
# <a name="image-service-and-catalog"></a>Catalogo e servizio immagini
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [servizio immagini e il catalogo](https://docs.microsoft.com/visualstudio/extensibility/image-service-and-catalog).  
  
Questa Guida di riferimento dettagliata contiene indicazioni e procedure consigliate per adottare il catalogo di immagini introdotto in Visual Studio 2015 e Visual Studio Image Service.  
  
 Il servizio immagini introdotto in Visual Studio 2015 consente agli sviluppatori di ottenere le immagini ottimali per il dispositivo e il tema scelto dell'utente per visualizzare l'immagine, inclusi corretto dei temi per il contesto in cui sono visualizzate. Adozione del servizio immagini consentirà di eliminare i punti deboli principali correlati alla manutenzione di asset, il ridimensionamento HDPI e temi.  
  
|||  
|-|-|  
|**Problemi di oggi**|**Soluzioni**|  
|La sfumatura di colore di sfondo|Fusione alfa predefiniti|  
|Immagini dei temi (alcuni)|Metadati di tema|  
|Modalità a contrasto elevato|Risorse alternative a contrasto elevato|  
|Più risorse necessarie per una modalità a altra DPI|Risorse selezionabile con fallback basato su vettore|  
|Immagini duplicate|Un identificatore per il concetto di immagine|  
  
 Perché adottare il servizio immagini?  
  
-   Ottenere sempre l'immagine "di impaginazione" più recente da Visual Studio  
  
-   È possibile inviare e Usa le tue immagini  
  
-   Non è necessario per testare le immagini out quando Windows aggiunge il ridimensionamento DPI del nuovo  
  
-   Vecchi ostacoli architetturale nelle implementazioni di indirizzi  
  
 Visual Studio shell barra degli strumenti prima e dopo aver usato il servizio immagini:  
  
 ![Servizio immagini prima e dopo aver](../extensibility/media/image-service-before-and-after.png "servizio immagini prima e dopo")  
  
## <a name="how-it-works"></a>Come funziona  
 Il servizio immagini può fornire un'immagine bitmap adatta per qualsiasi framework dell'interfaccia utente supportate:  
  
-   WPF: BitmapSource  
  
-   Windows Form: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 Diagramma di flusso del servizio immagini  
  
 ![Diagramma di flusso del servizio di immagine](../extensibility/media/image-service-flow-diagram.png "immagine di diagramma di flusso del servizio")  
  
 **Moniker di immagine**  
  
 Un moniker di immagine (o moniker breve) è una coppia GUID/ID che identifica in modo univoco un asset di immagine o un asset di elenco immagini della raccolta.  
  
 **Moniker noti**  
  
 Il set di moniker immagine contenuta nel catalogo di immagine di Visual Studio e pubblicamente che può essere utilizzato da qualsiasi componente di Visual Studio o estensione.  
  
 **File manifesto di immagini**  
  
 I file di immagine manifesto (.imagemanifest) sono file XML che definiscono un set di asset di immagini, i moniker che rappresentano tali asset e l'immagine reale o le immagini per rappresentare ogni asset. Manifesti dell'immagine può definire le immagini autonome o elenchi di immagini per il supporto legacy dell'interfaccia utente. Inoltre, esistono attributi che è possano impostare l'asset o le singole immagini protetti da ogni asset modificare quando e come vengono visualizzati tali asset.  
  
 **Schema del manifesto dell'immagine**  
  
 Un manifesto del completamento dell'immagine è simile alla seguente:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Import, Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **Simboli**  
  
 Come favorire una leggibilità e la manutenzione, il manifesto di immagini è possibile usare i simboli per i valori di attributo. I simboli sono definiti come segue:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**Sottoelemento**|**Definizione**|  
|Import|Importa i simboli del file manifesto specificato per l'uso nel manifesto corrente|  
|GUID|Il simbolo rappresenta un GUID e deve corrispondere la formattazione di GUID|  
|Id|Il simbolo rappresenta un ID e deve essere un numero intero non negativo|  
|Stringa|Il simbolo rappresenta un valore di stringa arbitrario|  
  
 I simboli sono tra maiuscole e minuscole e usando la sintassi $(symbol-name) riferimento:  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Alcuni simboli sono predefiniti per tutti i manifesti. Possono essere usati nell'attributo dell'Uri di \<Source > o \<importazione > elemento ai percorsi di riferimento sul computer locale.  
  
|||  
|-|-|  
|**Simbolo**|**Descrizione**|  
|CommonProgramFiles|Il valore della variabile di ambiente % CommonProgramFiles %|  
|LocalAppData|Il valore della variabile di ambiente % LocalAppData %|  
|ManifestFolder|La cartella contenente il file manifesto|  
|MyDocuments|Il percorso completo della cartella documenti dell'utente corrente|  
|ProgramFiles|Il valore della variabile di ambiente % ProgramFiles %|  
|System|Nella cartella Windows\System32|  
|WinDir|Il valore della variabile di ambiente % WinDir %|  
  
 **Immagine**  
  
 Il \<immagine > elemento definisce un'immagine che è possibile farvi riferimento da un moniker. Il GUID e ID nel loro insieme costituiscono il moniker di immagine. Moniker per l'immagine deve essere univoco tra la libreria di immagini intero. Se più di un'immagine è un moniker specificato, il primo ha rilevato durante la compilazione della libreria è quello che viene mantenuto.  
  
 Deve contenere almeno un'origine. Indipendente dalla dimensione origini fornirà i migliori risultati attraverso un'ampia gamma di dimensioni, ma non sono necessarie. Se il servizio è richiesto per un'immagine di dimensioni non è definita nel \<immagine > elemento ed è presente alcuna origine indipendente dalla dimensione, il servizio scegliere la migliore fonte di dimensioni specifiche e passare al piano la dimensione richiesta.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|GUID|[Obbligatorio] La parte GUID del moniker immagine|  
|Id|[Obbligatorio] La parte ID del moniker immagine|  
|AllowColorInversion|[Facoltativo, valore predefinito true] Indica se l'immagine può avere i colori invertiti a livello di codice quando viene utilizzata su uno sfondo scuro.|  
  
 **Origine**  
  
 Il \<origine > elemento definisce una risorsa di origine immagine singola (XAML e PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|URI|[Obbligatorio] URI che definisce dove è possibile caricare l'immagine da. Può essere uno dei seguenti:<br /><br /> -A [URI di tipo Pack](http://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) utilizzando l'applicazione: / / / autorità<br />-Riferimento a una risorsa un componente assoluto<br />-Un percorso di un file contenente una risorsa nativa|  
|Sfondo|[Facoltativo] Indica l'operazione nel tipo di origine dovrà essere utilizzato in background.<br /><br /> Può essere uno dei seguenti:<br /><br /> *Illuminazione:* l'origine può essere usata su uno sfondo chiaro.<br /><br /> *Scuro:* l'origine può essere usata su uno sfondo scuro.<br /><br /> *Contrasto elevato:* l'origine può essere usata su qualsiasi dello sfondo nella modalità a contrasto elevato.<br /><br /> *HighContrastLight:* l'origine può essere usata su uno sfondo chiaro in modalità a contrasto elevato.<br /><br /> *HighContrastDark:* l'origine può essere usata su uno sfondo scuro in modalità a contrasto elevato.<br /><br /> Se si omette l'attributo in Background, l'origine sono utilizzabili in qualsiasi dello sfondo.<br /><br /> Se è in Background *Light*, *scuro*, *HighContrastLight*, oppure *HighContrastDark*, i colori dell'origine non vengono mai invertiti. Se viene omesso o impostato su sfondo *contrasto elevato*, l'inversione di colori dell'origine viene controllata nell'immagine **AllowColorInversion** attributo.|  
|||  
  
 Oggetto \<origine > elemento può includere esattamente uno dei sottoelementi facoltativi seguenti:  
  
||||  
|-|-|-|  
|**Elemento**|**Attributi (tutti necessari)**|**Definizione**|  
|\<Dimensioni >|Valore|L'origine verrà utilizzata per le immagini della dimensione specificata (in unità di dispositivo). L'immagine sarà quadrato.|  
|\<SizeRange >|MinSize, MaxSize|L'origine verrà utilizzata per le immagini da MinSize alle dimensioni massime (in unità di dispositivo), inclusi. L'immagine sarà quadrato.|  
|\<Dimensioni >|Larghezza, altezza|L'origine verrà utilizzata per le immagini della larghezza specificata e dell'altezza (espressa in unità di dispositivo).|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|L'origine verrà utilizzata per le immagini dalla larghezza/altezza minima per la larghezza/altezza massima (in unità di dispositivo), inclusi.|  
  
 Oggetto \<Source > elemento può anche avere facoltativo \<NativeResource > sottoelemento, che definisce un \<origine > che viene caricato da un assembly nativo piuttosto che da un assembly gestito.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Tipo|[Obbligatorio] Il tipo di risorsa nativa, XAML o PNG|  
|Id|[Obbligatorio] Il quoziente di ID di risorsa nativa|  
  
 **ImageList**  
  
 Il \<ImageList > elemento definisce una raccolta di immagini che possono essere restituiti in un singolo elenco. L'elenco viene compilato su richiesta, in base alle esigenze.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|GUID|[Obbligatorio] La parte GUID del moniker immagine|  
|Id|[Obbligatorio] La parte ID del moniker immagine|  
|Altre informazioni|[Impostazione predefinita è false, facoltativo] Indica se il moniker di immagine fa riferimento a un'immagine nel manifesto corrente.|  
  
 Moniker per l'immagine contenuta non è necessario fare riferimento a un'immagine definita nel manifesto corrente. Se l'immagine del contenuto non viene trovato nella raccolta immagini, un'immagine segnaposto vuoto verrà utilizzata al suo posto.  
  
## <a name="using-the-image-service"></a>Usando il servizio immagini  
  
### <a name="first-steps-managed"></a>Primi passaggi (gestiti)  
 Per usare il servizio immagini, è necessario aggiungere riferimenti ad alcuni o tutti gli assembly seguenti al progetto:  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   Obbligatorio se si usa il catalogo di immagine incorporata KnownMonikers  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   Obbligatorio se si usa **CrispImage** e **ImageThemingUtilities** nella UI di WPF  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   Obbligatorio se si usa la **ImageMoniker** e **ImageAttributes** tipi  
  
    -   **EmbedInteropTypes** deve essere impostato su true  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   Obbligatorio se si usa la **IVsImageService2** tipo  
  
    -   **EmbedInteropTypes** deve essere impostato su true  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   Obbligatorio se si usa la **BrushToColorConverter** per il ImageThemingUtilities. **ImageBackgroundColor** nell'interfaccia utente di WPF  
  
-   **Microsoft.VisualStudio.Shell. \<VSVersion >,0**  
  
    -   Obbligatorio se si usa la **IVsUIObject** tipo  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   Necessario se si usano gli helper dell'interfaccia utente basate su Windows Form  
  
    -   **EmbedInteropTypes** deve essere impostato su true  
  
### <a name="first-steps-native"></a>Primi passaggi (nativo)  
 Per usare il servizio immagini, è necessario includere alcune o tutte le intestazioni seguenti al progetto:  
  
-   **KnownImageIds.h**  
  
    -   Obbligatorio se si usa il catalogo di immagine incorporata **KnownMonikers**, ma non è possibile utilizzare il **ImageMoniker** tipo, ad esempio quando la restituzione di valori da **IVsHierarchy GetGuidProperty**oppure **GetProperty** chiamate.  
  
-   **KnownMonikers.h**  
  
    -   Obbligatorio se si usa il catalogo di immagine incorporata **KnownMonikers**.  
  
-   **ImageParameters140.h**  
  
    -   Obbligatorio se si usa la **ImageMoniker** e **ImageAttributes** tipi.  
  
-   **VSShell140.h**  
  
    -   Obbligatorio se si usa la **IVsImageService2** tipo.  
  
-   **ImageThemingUtilities.h**  
  
    -   Obbligatorio per i non è possibile che il servizio immagini gestisca i temi per l'utente.  
  
    -   Non utilizzare questa intestazione se il servizio immagini può gestire i temi di immagine.  
  
-   **VSUIDPIHelper.h**  
  
    -   Necessario se si usano gli helper DPI per ottenere il valore DPI corrente.  
  
## <a name="how-do-i-write-new-wpf-ui"></a>Come si scrivono nuove WPF UI?  
  
1.  Avvio tramite l'aggiunta di riferimenti ad assembly richiesti nell'esempio precedente sezione passaggi prima di tutto al progetto. Non è necessario aggiungere tutti gli elementi, quindi, aggiungere semplicemente i riferimenti che è necessario. (Nota: se si usa o si ha accesso al **colori** invece di **pennelli**, quindi è possibile ignorare il riferimento al **utilità**, dal momento che non è necessario utilizzare il convertitore.)  
  
2.  Selezionare l'immagine desiderata e ottenere il moniker. Usare un **KnownMoniker**, oppure usare il proprio se si dispone di propri immagini personalizzate e il moniker.  
  
3.  Aggiungere **CrispImages** a di XAML. (Vedere l'esempio seguente.)  
  
4.  Impostare il **ImageThemingUtilities.ImageBackgroundColor** proprietà della gerarchia dell'interfaccia utente. (Deve essere impostata in corrispondenza della posizione in cui il colore di sfondo è noto, non necessariamente per la **CrispImage**.) (Vedere l'esempio seguente.)  
  
```xaml  
<Window  
  x:Class="WpfApplication.MainWindow"  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"  
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">  
  <Window.Resources>  
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>  
  </Window.Resources>  
  <StackPanel Background="White" VerticalAlignment="Center"   
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">  
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />  
  </StackPanel>  
</Window>  
```  
  
 **Come si aggiorna UI WPF esistenti?**  
  
 L'aggiornamento di UI WPF esistente è un processo relativamente semplice costituito da tre passaggi di base:  
  
1.  Sostituisci tutto \<immagine > elementi nell'interfaccia utente di con \<CrispImage > elementi  
  
2.  Modificare tutti gli attributi di origine per gli attributi di Moniker  
  
    -   Se l'immagine non cambia mai e si usa **KnownMonikers**, quindi associare in modo statico tale proprietà per il **KnownMoniker**. (Vedere l'esempio precedente).  
  
    -   Se l'immagine non cambia mai e si usa un'immagine personalizzata, quindi in modo statico associato al proprio moniker.  
  
    -   Se l'immagine può modificare, associare l'attributo Moniker da una proprietà del codice che invia una notifica sulle modifiche di proprietà.  
  
3.  In una posizione nella gerarchia dell'interfaccia utente, impostare **ImageThemingUtilities.ImageBackgroundColor** per rendere l'inversione di colore che funzioni correttamente.  
  
    -   Ciò potrebbe richiedere l'uso del **BrushToColorConverter** classe. (Vedere l'esempio precedente).  
  
## <a name="how-do-i-update-win32-ui"></a>Come si aggiorna dell'interfaccia utente di Win32?  
 Aggiungere quanto segue al codice ogni volta che è appropriato per sostituire il caricamento di immagini non elaborato. Passare i valori per restituire gli HBITMAP e gli oggetti HICON rispetto a HIMAGELIST in base alle esigenze.  
  
 **Ottenere il servizio immagini**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **La richiesta dell'immagine**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>Come si aggiorna WinForms UI?  
 Aggiungere quanto segue al codice ogni volta che è appropriato per sostituire il caricamento di immagini non elaborato. Passare i valori per la restituzione di bitmap e icone in base alle esigenze.  
  
 **Utile istruzione using**  
  
```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **Ottenere il servizio immagini**  
  
```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **Richiedono l'immagine**  
  
```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Utilizzo di moniker di immagine in una nuova finestra degli strumenti  
 Il modello di progetto di pacchetto VSIX è stato aggiornato per Visual Studio 2015. Per creare una nuova finestra degli strumenti, fare clic sul progetto VSIX e selezionare "Aggiungi nuovo elemento..." (Ctrl + Maiusc + A). Sotto il nodo di estendibilità per il linguaggio del progetto, selezionare "Finestra degli strumenti personalizzata", assegnare un nome di finestra degli strumenti e fare clic sul pulsante "Aggiungi".  
  
 Questi sono i punti chiave da usare i moniker in una finestra degli strumenti. Seguire le istruzioni per ognuno:  
  
1.  La scheda casella degli strumenti quando le schede di piccole dimensioni sufficienti (anche usato nel cambio modalità per la finestra Ctrl + Tab).  
  
     Aggiungere questa riga al costruttore della classe che deriva dal **ToolWindowPane** tipo:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  Il comando per aprire la finestra degli strumenti.  
  
     Nel file vsct per il pacchetto, pulsante di comando della finestra degli strumenti di modifica:  
  
    ```xml  
    <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <!-- Replace this KnownMoniker with your desired ImageMoniker -->  
      <Icon guid="ImageCatalogGuid" id="Blank" />  
      <!-- Add this -->  
      <CommandFlag>IconIsMoniker</CommandFlag>  
      <Strings>  
        <ButtonText>MyToolWindow</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
 **Come usare i moniker di immagine in una finestra degli strumenti esistenti?**  
  
 L'aggiornamento di una finestra degli strumenti esistenti per usare i moniker immagine è simile alle procedure per la creazione di una nuova finestra degli strumenti.  
  
 Questi sono i punti chiave da usare i moniker in una finestra degli strumenti. Seguire le istruzioni per ognuno:  
  
1.  La scheda casella degli strumenti quando le schede di piccole dimensioni sufficienti (anche usato nel cambio modalità per la finestra Ctrl + Tab).  
  
    1.  Rimuovere le righe seguenti (se presenti) nel costruttore della classe che deriva dal **ToolWindowPane** tipo:  
  
        ```csharp  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  Vedere il passaggio #1 di "Ricerca per categorie usare immagine moniker in una nuova finestra degli strumenti?" sezione precedente.  
  
2.  Il comando per aprire la finestra degli strumenti.  
  
    -   Vedere il passaggio #2 di "Ricerca per categorie usare immagine moniker in una nuova finestra degli strumenti?" sezione precedente.  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Utilizzo di moniker di immagine in un file con estensione vsct  
 Aggiornare il file con estensione vsct, come indicato dalle righe commentate riportato di seguito:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
             Change the id attribute to be the ID of the desired image moniker. -->  
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <CommandFlag>DefaultInvisible</CommandFlag>  
        <CommandFlag>DefaultDisabled</CommandFlag>  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>IconAndText</CommandFlag>  
        <!-- Add the IconIsMoniker CommandFlag -->  
        <CommandFlag>IconIsMoniker</CommandFlag>  
        <Strings>  
          <ButtonText>Quick Fixes...</ButtonText>  
          <CommandName>Show Quick Fixes</CommandName>  
          <CanonicalName>ShowQuickFixes</CanonicalName>  
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>  
        </Strings>  
      </Button>  
    </Buttons>  
  </Commands>  
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->  
  <Symbols>  
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />  
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">  
      <IDSymbol name="cmdidMyCommand" value="0x9437" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```  
  
 **Cosa accade se il file con estensione vsct dovrà anche essere letti dalle versioni precedenti di Visual Studio?**  
  
 Le versioni precedenti di Visual Studio non è possibile riconoscere il **IconIsMoniker** flag di comando. È possibile usare le immagini dal servizio di immagine su versioni di Visual Studio che lo supportano, ma continuano a usare le immagini di vecchio stile nelle versioni precedenti di Visual Studio. A tale scopo, si potrebbe lasciare il file con estensione vsct invariato (e pertanto compatibile con le versioni precedenti di Visual Studio) e creare un file CSV (valori delimitati da virgole) che esegue il mapping dalle coppie GUID/ID definite in un file con estensione vsct \<bitmap > elemento immagine coppie / ID GUID del moniker.  
  
 Il formato del file CSV di mapping è:  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 Il file CSV viene distribuito con il pacchetto e il percorso specificato dal **IconMappingFilename** proprietà delle **ProvideMenuResource** attributo del pacchetto:  
  
```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 Il **IconMappingFilename** è un percorso relativo rooted in modo implicito in $ $PackageFolder (come nell'esempio precedente) o un percorso assoluto con radice in modo esplicito in una directory definita dalla variabile di ambiente, ad esempio @"%UserProfile%\ dir1\dir2\MyMappingFile.csv".  
  
## <a name="how-do-i-port-a-project-system"></a>Come si trasferisce un sistema di progetto?  
 **Come fornire ImageMonikers per un progetto**  
  
1.  Implementare **VSHPROPID_SupportsIconMonikers** del progetto **IVsHierarchy**e restituisce true.  
  
2.  Implementano **VSHPROPID_IconMonikerImageList** (se il progetto originale utilizzato **VSHPROPID_IconImgList**) o **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (se il progetto originale usato  **VSHPROPID_IconHandle** e **VSHPROPID_OpenFolderIconHandle**).  
  
3.  Modificare l'implementazione del VSHPROPIDs originali per le icone per creare versioni "legacy" delle icone se li hanno richiesti punti di estensione. **IVsImageService2** fornisce la funzionalità necessaria per ottenere tali icone  
  
 **Requisiti aggiuntivi per VB / caratteristiche progetti c#**  
  
 Implementare solo **VSHPROPID_SupportsIconMonikers** se si rileva che il progetto sia la **flavor più esterno**. In caso contrario, la versione più esterna effettiva potrebbe non supportare i moniker di immagine in realtà, e la versione di base potrebbe essere effettivamente "nascondere" immagini personalizzate.  
  
 **Utilizzo di moniker di immagine in CPS**  
  
 L'impostazione delle immagini personalizzate in CPS (Common Project System) può essere eseguita manualmente o tramite un modello di elemento che viene fornito con il SDK di estendibilità del sistema di progetto.  
  
 **Usando l'estensibilità di sistema di progetto SDK**  
  
 Seguire le istruzioni in [fornire le icone personalizzate per il tipo del tipo di progetto/elemento](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) per personalizzare le immagini di CPS. Altre informazioni sull'istruzione CPS sono reperibile in [documentazione sull'estendibilità di Visual Studio Project System](https://github.com/Microsoft/VSProjectSystem)  
  
 **Usare manualmente ImageMonikers**  
  
1.  Implementare ed esportare le **IProjectTreeModifier** interfaccia nel sistema di progetto.  
  
2.  Determinare quale **KnownMoniker** o moniker di immagine personalizzata da usare.  
  
3.  Nel **ApplyModifications** (metodo), eseguire le operazioni seguenti in una posizione nel metodo prima di restituire il nuovo albero, simile all'esempio seguente:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  Se si sta creando un nuovo albero, è possibile impostare le immagini personalizzate, passando i moniker desiderati nel metodo NewTree, simile all'esempio seguente:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
    ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  
  
    return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                 /*filePath*/<value>,  
                                                 /*browseObjectProperties*/<value>,  
                                                 icon,  
                                                 expandedIcon);  
    ```  
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Come convertire da un elenco di immagini reale per un elenco di immagini basate su moniker?  
 **Deve supportare HIMAGELISTs**  
  
 Se è presente un elenco di immagini già esistente per il codice che si desidera aggiornare per usare il servizio immagini, ma sono limitati dalle API che richiedono il passaggio intorno a elenchi di immagini, è ancora possibile ottenere i vantaggi del servizio di immagine. Per creare un elenco di immagini basate su moniker, seguire questa procedura per creare un manifesto da moniker esistente.  
  
1.  Eseguire la **ManifestFromResources** strumento, passandolo nella sequenza di immagini. Verrà generato un manifesto per la striscia.  
  
    -   Consigliato: specificare un nome non predefinito per il manifesto in base alle proprie sul relativo utilizzo.  
  
2.  Se si utilizza solo **KnownMonikers**, quindi eseguire le operazioni seguenti:  
  
    -   Sostituire il \<immagini > sezione del manifesto con \<immagini / >.  
  
    -   Rimuovere tutti l'icona della regione ID (qualsiasi valore con \<nome imagestrip > _ # #).  
  
    -   Consigliato: rinominare il simbolo AssetsGuid e il simbolo striscia di immagine in base alle proprie sul relativo utilizzo.  
  
    -   Sostituire ogni **ContainedImage**del GUID con $(ImageCatalogGuid), sostituire ogni **ContainedImage**dell'ID con $(\<moniker >) e aggiungere l'attributo "true" = esterno a ogni **ContainedImage**  
  
        -   \<moniker > deve essere sostituito con il **KnownMoniker** corrispondente dell'immagine, ma con la "KnownMonikers". rimosso dal nome.  
  
    -   Aggiungere < Import Manifest="$(ManifestFolder)\\< relativo installare dir verso\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\> all'inizio del \<simboli > sezione.  
  
        -   Il percorso relativo è dipende dalla località di distribuzione definito durante la configurazione di creazione per il manifesto.  
  
3.  Eseguire la **ManifestToCode** strumento per generare wrapper in modo che il codice esistente dispone di un moniker può usare per eseguire query sul servizio di immagine per l'elenco immagini.  
  
    -   Consigliato: fornire nomi diversi da quelli predefiniti per il wrapper e spazi dei nomi in base alle loro utilizzo.  
  
4.  Tutte le operazioni di aggiunge, il programma di installazione di creazione o la distribuzione e altre modifiche al codice per usare il servizio immagini e i nuovi file.  
  
 Manifesto di esempio incluse le immagini di interne ed esterne per vedere cosa sarà simile:  
  
```xml  
<?xml version="1.0"?>  
<ImageManifest  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  
  <Symbols>  
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest  
         where $(ManifestFolder) is the deployed location of this manifest. -->  
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />  
  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />  
    <ID Name="MyImage_0" Value="100" />  
    <ID Name="MyImage_1" Value="101" />  
    <ID Name="InternalList" Value="1001" />  
    <ID Name="ExternalList" Value="1002" />  
  </Symbols>  
  
  <Images>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">  
      <Source Uri="$(Resources)/MyImage_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">  
      <Source Uri="$(Resources)/MyImage_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  
  <ImageLists>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />  
    </ImageList>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />  
    </ImageList>  
  </ImageLists>  
  
</ImageManifest>  
```  
  
 **Non è necessario supportare HIMAGELISTs**  
  
1.  Determinare l'insieme degli **KnownMonikers** che corrispondono le immagini nell'elenco di immagini o creare i proprio i moniker per le immagini nell'elenco di immagini.  
  
2.  Aggiorna qualsiasi mapping usato per ottenere l'immagine in corrispondenza dell'indice nell'elenco di immagini da usare in alternativa i moniker obbligatorio.  
  
3.  Aggiornare il codice per usare il servizio immagini per richiedere i moniker tramite il mapping aggiornato. (Ciò potrebbe significare aggiornare a **CrispImages** per codice gestito, o richiedere gli HBITMAP o gli oggetti HICON al servizio di immagine e passarli intorno a per il codice nativo.)  
  
## <a name="testing-your-images"></a>Le immagini di test  
 È possibile utilizzare lo strumento Visualizzatore di libreria di immagini per testare i manifesti di immagine per assicurarsi che tutto ciò che è stato creato correttamente. È possibile trovare lo strumento nel [Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx). Documentazione relativa a questo e altri strumenti sono reperibili [qui](http://aka.ms/VSImageThemeTools).  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
  
### <a name="samples"></a>Esempi  
 Molti degli esempi di Visual Studio su GitHub sono stati aggiornati per mostrare come usare il servizio immagini come parte di vari punti di estendibilità di Visual Studio.  
  
 Controllare [ http://github.com/Microsoft/VSSDK-Extensibility-Samples ](http://github.com/Microsoft/VSSDK-Extensibility-Samples) per gli esempi più recenti.  
  
### <a name="tooling"></a>Strumenti  
 Per facilitare la creazione o l'aggiornamento dell'interfaccia utente che interagisce con il servizio immagini è stato creato un set di strumenti di supporto per il servizio immagini. Per altre informazioni su ogni strumento, vedere la documentazione fornita con gli strumenti. Gli strumenti sono inclusi come parte di [Visual Studio 2015 SDK.](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 Il manifesto dallo strumento di risorse accetta un elenco di risorse di immagini (PNG o XAML) e genera un file manifesto di immagini per l'uso delle immagini con il servizio immagini.  
  
 **ManifestToCode**  
  
 Il manifesto per lo strumento di Code accetta un file manifesto dell'immagine e genera un file wrapper per i valori del manifesto nel codice (C++, c# o Visual Basic) o file con estensione vsct di riferimento.  
  
 **ImageLibraryViewer**  
  
 Lo strumento Visualizzatore della libreria di immagini in grado di caricare i manifesti di immagine e consente all'utente di modificarli in modo identico a Visual Studio per assicurarsi che il manifesto è stato creato correttamente. L'utente potrà modificare in background, dimensioni, impostazione DPI, contrasto elevato e altre impostazioni. Inoltre vengono visualizzate le informazioni di caricamento per individuare errori nei manifesti e visualizza le informazioni di origine per ogni immagine nel manifesto.  
  
## <a name="faq"></a>Domande frequenti  
  
-   Sono presenti dipendenze che è necessario includere quando si caricano \<Include="Microsoft.VisualStudio.* di riferimento. Interop.14.0.DesignTime"/ >?  
  
    -   Impostare EmbedInteropTypes = "true" in tutte le DLL di interoperabilità.  
  
-   Come si distribuisce un manifesto di immagini con l'estensione?  
  
    -   Aggiungere il file .imagemanifest al progetto.  
  
    -   Impostare "Includi in VSIX" su True.  
  
-   Si aggiorna il sistema di progetto CPS. Cosa è successo al **ImageName** e **StockIconService**?  
  
    -   o che queste sono state rimosse quando l'istruzione CPS è stato aggiornato per usare i moniker. Non è più necessario chiamare il **StockIconService**, è sufficiente passare il valore desiderato **KnownMoniker** al metodo o proprietà utilizzando il **ToProjectSystemType()** metodo di estensione in le utilità di CPS. È possibile trovare un mapping dagli **ImageName** al **KnownMonikers** sotto:  
  
        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  
  
    -   Si aggiorna il provider di elenco di completamento. Che cosa **KnownMonikers** corrispondono ai precedenti **StandardGlyphGroup** e **StandardGlyph** valori?  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
        |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
        |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
        |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
        |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
        |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
        |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
        |GlyphGroupType|GlyphItemPublic|TypePublic|  
        |GlyphGroupType|GlyphItemInternal|TypeInternal|  
        |GlyphGroupType|GlyphItemFriend|TypeInternal|  
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||ClassFile|  
        |GlyphAssembly||Riferimenti|  
        |GlyphLibrary||Libreria|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||Finestra di dialogo|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||GoToNext|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||Frammento di codice|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||Ricorsione|  
        |GlyphXmlItem||Tag|  
        |GlyphJSharpProject||DocumentCollection|  
        |GlyphJSharpDocument||Document|  
        |GlyphForwardType||GoToNext|  
        |GlyphCallersGraph||Callto://|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||Callto://|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||XmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|

