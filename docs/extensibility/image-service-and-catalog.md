---
title: Servizio immagini e catalogo Documenti Microsoft
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710381"
---
# <a name="image-service-and-catalog"></a>Catalogo e servizio immagini
Questo libro di cucina contiene indicazioni e procedure consigliate per l'adozione del servizio immagine di Visual Studio e del catalogo immagini introdotto in Visual Studio 2015.

 Il servizio immagini introdotto in Visual Studio 2015 consente agli sviluppatori di ottenere le immagini migliori per il dispositivo e il tema scelto dall'utente per visualizzare l'immagine, inclusa la correzione dei temi per il contesto in cui vengono visualizzate. L'adozione del servizio immagini contribuirà a eliminare i principali punti di dolore relativi alla manutenzione degli asset, al ridimensionamento HDPI e al tema.

|||
|-|-|
|**Problemi di oggi**|**Soluzioni**|
|Fusione del colore di sfondo|Fusione alfa integrata|
|Tema (alcune) immagini|Metadati del tema|
|Modalità Contrasto elevato|Risorse alternate ad alto contrastoAlternate High Contrast resources|
|Necessità di più risorse per diverse modalità DPI|Risorse selezionabili con fallback basato su vettori|
|Duplicare le immagini|Un identificatore per concetto di immagine|

 Perché adottare il servizio immagini?

- Ottieni sempre l'immagine "pixel-perfect" più recente da Visual Studio

- È possibile inviare e utilizzare le proprie immagini

- Non c'è bisogno di testare le immagini quando Windows aggiunge il nuovo ridimensionamento DPI

- Affrontare i vecchi ostacoli architettonici nelle implementazioni

  La barra degli strumenti della shell di Visual Studio prima e dopo l'uso del servizio immagini:The Visual Studio shell toolbar before and after using the image service:

  ![Servizio immagini prima e dopo](../extensibility/media/image-service-before-and-after.png "Servizio immagini prima e dopo")

## <a name="how-it-works"></a>Funzionamento
 Il servizio immagini può fornire un'immagine bitmap adatta a qualsiasi framework dell'interfaccia utente supportato:The image service can supply a bitmapped image suitable for any supported UI framework:

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Diagramma di flusso del servizio immagini

  ![Diagramma di flusso del servizio immagini](../extensibility/media/image-service-flow-diagram.png "Diagramma di flusso del servizio immagini")

  **Monici immagine**

  Un moniker di immagini (o moniker in breve) è una coppia GUID/ID che identifica in modo univoco una risorsa immagine o un asset di immagini nella raccolta immagini.

  **Monici noti**

  Set di moniker di immagini contenuto nel Catalogo immagini di Visual Studio e utilizzabile pubblicamente da qualsiasi componente o estensione di Visual Studio.

  **File manifesto immagine**

  I file manifesto*dell'immagine ( .imagemanifest*) sono file XML che definiscono un set di risorse immagine, i moniker che rappresentano tali risorse e l'immagine o le immagini reali che rappresentano ogni risorsa. I manifesti immagine possono definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Inoltre, ci sono attributi che possono essere impostati sulla risorsa o sulle singole immagini dietro ogni risorsa per modificare quando e come tali risorse vengono visualizzate.

  **Schema del manifesto dell'immagine**

  Un manifesto completo dell'immagine è simile al seguente:A complete image manifest looks like this:

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

 **Symbols**

 Come aiuto per la leggibilità e la manutenzione, il manifesto dell'immagine può usare simboli per i valori degli attributi. I simboli sono definiti in questo modo:

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
|Importa|Importa i simboli del file manifesto specificato per l'utilizzo nel manifesto corrente|
|Guid|Il simbolo rappresenta un GUID e deve corrispondere alla formattazione GUID|
|ID|Il simbolo rappresenta un ID e deve essere un numero intero non negativo|
|string|Il simbolo rappresenta un valore stringa arbitrario|

 Per i simboli viene fatta distinzione tra maiuscole e minuscole e viene fatto riferimento utilizzando la sintassi di (nome-simbolo):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Alcuni simboli sono predefiniti per tutti i manifesti. Questi possono essere utilizzati nell'attributo Uri dell'elemento \<> di origine o \<import> per fare riferimento ai percorsi nel computer locale.

|||
|-|-|
|**Simbolo**|**Descrizione**|
|CommonProgramFiles|Il valore della variabile di ambiente %CommonProgramFiles%|
|Localappdata|Il valore della variabile di ambiente %LocalAppData%|
|ManifestFolder (cartella manifesta)|La cartella contenente il file manifesto|
|Mydocuments|Il percorso completo della cartella Documenti dell'utente corrente|
|ProgramFiles|Il valore della variabile di ambiente %ProgramFiles%|
|System|La cartella *Windows-System32*|
|Windir|Il valore della variabile di ambiente %WinDir%|

 **Immagine**

 L'elemento \<> Image definisce un'immagine a cui fa riferimento un moniker. Il GUID e l'ID presi insieme formano il moniker dell'immagine. Il moniker per l'immagine deve essere univoco nell'intera libreria di immagini. Se più di un'immagine ha un dato moniker, la prima rilevata durante la creazione della libreria è quella che viene mantenuta.

 Deve contenere almeno una fonte. Le sorgenti neutre di dimensione daranno i migliori risultati in un'ampia gamma di dimensioni, ma non sono necessarie. Se al servizio viene richiesta un'immagine di \<una dimensione non definita nell'elemento Image> e non esiste un'origine neutra per le dimensioni, il servizio sceglierà la fonte specifica per le dimensioni migliori e la scalerà in base alle dimensioni richieste.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Guid|[Obbligatorio] Parte GUID del moniker dell'immagine|
|ID|[Obbligatorio] La parte ID del moniker dell'immagine|
|AllowColorInversion|[Facoltativo, predefinito true] Indica se i colori dell'immagine possono essere invertiti a livello di codice quando vengono utilizzati su uno sfondo scuro.|

 **origine**

 L'elemento \<> di origine definisce un singolo asset di origine dell'immagine (XAML e PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Uri|[Obbligatorio] URI che definisce la posizione da cui è il caricamento dell'immagine. I possibili valori sono i seguenti:<br /><br /> - Un [URI di tipo Pack](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) che utilizza l'autorità application:///<br />- Un riferimento di risorsa componente assoluto- An absolute component resource reference<br />- Un percorso a un file contenente una risorsa nativa- A path to a file containing a native resource|
|Background|[Facoltativo] Indica il tipo di sfondo in cui deve essere utilizzata l'origine.<br /><br /> I possibili valori sono i seguenti:<br /><br /> *Luce:* La sorgente può essere utilizzata su uno sfondo chiaro.<br /><br /> *Scuro:* La sorgente può essere utilizzata su uno sfondo scuro.<br /><br /> *HighContrasto:* L'origine può essere utilizzata su qualsiasi sfondo in modalità Contrasto elevato.<br /><br /> *HighContrastLight:* La sorgente può essere utilizzata su uno sfondo chiaro in modalità Contrasto elevato.<br /><br /> *HighContrastDark:* La sorgente può essere utilizzata su uno sfondo scuro in modalità Contrasto elevato.<br /><br /> Se l'attributo Background viene omesso, l'origine può essere utilizzata in qualsiasi sfondo.<br /><br /> Se Sfondo è *Chiaro*, *Scuro*, *HighContrastLight*o *HighContrastDark*, i colori della sorgente non vengono mai invertiti. Se Sfondo viene omesso o impostato su *HighContrast*, l'inversione dei colori dell'origine è controllata dall'attributo **AllowColorInversion** dell'immagine.|

Un \<elemento Source> può avere esattamente uno dei seguenti sottoelementi facoltativi:

||||
|-|-|-|
|**Elemento**|**Attributi (tutti obbligatori)**|**Definizione**|
|\<> di dimensioni|valore|La sorgente verrà utilizzata per le immagini delle dimensioni specificate (in unità di dispositivo). L'immagine sarà quadrata.|
|\<> SizeRange|MinSize, MaxSize|L'origine verrà utilizzata per le immagini da MinSize a MaxSize (in unità di dispositivo) inclusiva. L'immagine sarà quadrata.|
|\<Dimensioni>|Larghezza, altezza|La sorgente verrà utilizzata per le immagini della larghezza e dell'altezza specificate (in unità di dispositivo).|
|\<> Di DimensionRange|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|L'origine verrà utilizzata per le immagini dalla larghezza/altezza minima alla larghezza/altezza massima (in unità di dispositivo) inclusiva.|

 Un \<elemento Source> può \<anche avere un sottoelemento \<facoltativo NativeResource>, che definisce un oggetto Source> caricato da un assembly nativo anziché da un assembly gestito.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Type|[Obbligatorio] Il tipo della risorsa nativa, XAML o PNG|
|ID|[Obbligatorio] Parte dell'ID intero della risorsa nativa|

 **Imagelist**

 Il \<ImageList> elemento definisce una raccolta di immagini che possono essere restituite in una singola striscia. La striscia è costruita su richiesta, se necessario.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Guid|[Obbligatorio] Parte GUID del moniker dell'immagine|
|ID|[Obbligatorio] La parte ID del moniker dell'immagine|
|Esterno|[Facoltativo, predefinito false] Indica se il moniker dell'immagine fa riferimento a un'immagine nel manifesto corrente.|

 Il moniker per l'immagine contenuta non deve fare riferimento a un'immagine definita nel manifesto corrente. Se non è possibile trovare l'immagine contenuta nella libreria di immagini, al suo posto verrà utilizzata un'immagine segnaposto vuota.

## <a name="using-the-image-service"></a>Utilizzo del servizio immagini

### <a name="first-steps-managed"></a>Primi passi (gestiti)
 Per utilizzare il servizio immagini, è necessario aggiungere riferimenti ad alcuni o a tutti gli assembly seguenti al progetto:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Obbligatorio se si utilizza il catalogo immagini incorporato **KnownMonikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Obbligatorio se si usa **CrispImage** e **ImageThemingUtilities** nell'interfaccia utente WPF.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Obbligatorio se si utilizzano i tipi **ImageMoniker** e **ImageAttributes.**

  - **EmbedInteropTypes** deve essere impostato su true.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Obbligatorio se si utilizza il **tipo IVsImageService2.**

  - **EmbedInteropTypes** deve essere impostato su true.

- *Microsoft.VisualStudio.Utilities.dll*

  - Obbligatorio se si utilizza il **BrushToColorConverter** per il **ImageThemingUtilities.ImageBackgroundColor** nell'interfaccia utente WPF.

- *Microsoft.visualstudio.shell. \<VSVersion>.0*

  - Obbligatorio se si utilizza il **iVsUIObject tipo.**

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Obbligatorio se si utilizzano gli helper dell'interfaccia utente correlati a WinForms.

  - **EmbedInteropTypes** deve essere impostato su true

### <a name="first-steps-native"></a>Primi passi (nativi)
 Per usare il servizio immagini, è necessario includere alcune o tutte le intestazioni seguenti nel progetto:

- **KnownImageIds.h**

  - Obbligatorio se si utilizza il catalogo immagini incorporato **KnownMonikers**, ma non è possibile utilizzare il tipo **ImageMoniker** , ad esempio quando si restituiscono valori da **IVsHierarchy GetGuidProperty** o **GetProperty** chiamate.

- **KnownMonikers.h**

  - Obbligatorio se si utilizza il catalogo immagini incorporato **KnownMonikers**.

- **ImageParameters140.h**

  - Obbligatorio se si utilizzano i tipi **ImageMoniker** e **ImageAttributes.**

- **VSShell140.h**

  - Obbligatorio se si utilizza il **tipo IVsImageService2.**

- **ImageThemingUtilities.h**

  - Obbligatorio se non si è in grado di lasciare che il servizio immagini gestisca i temi per l'utente.

  - Non usare questa intestazione se il servizio immagini è in grado di gestire i temati.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Obbligatorio se si utilizzano gli helper DPI per ottenere il valore DPI corrente.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Obbligatorio se si utilizzano gli helper di riconoscimento DPI per ottenere il valore DPI corrente.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Come si scrive la nuova interfaccia utente WPF?

1. Iniziare aggiungendo al progetto i riferimenti all'assembly necessari nella sezione dei primi passaggi precedenti. Non è necessario aggiungerli tutti, quindi aggiungi solo i riferimenti di cui hai bisogno. (Nota: se si utilizza o si ha accesso a **Colori** anziché a **Pennelli**, è possibile ignorare il riferimento alle **utilità**, poiché non sarà necessario il convertitore.)

2. Selezionare l'immagine desiderata e ottenere il relativo moniker. Utilizzare un **KnownMoniker**o utilizzare il proprio se si dispone di immagini personalizzate e moniker.

3. Aggiungi **CrispImages** al tuo codice XAML. (Vedere l'esempio seguente.)

4. Impostare la proprietà **ImageThemingUtilities.ImageBackgroundColor** nella gerarchia dell'interfaccia utente. (Questo deve essere impostato nella posizione in cui il colore di sfondo è noto, non necessariamente sul **CrispImage**.) (Vedere l'esempio seguente.)

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

 **Come si aggiorna l'interfaccia utente WPF esistente?**

 L'aggiornamento dell'interfaccia utente WPF esistente è un processo relativamente semplice costituito da tre passaggi di base:Updating existing WPF UI is a relatively simple process that consists of three basic steps:

1. Sostituisci \<tutti gli elementi \<Image> nell'interfaccia utente con CrispImage> elementi.

2. Modificare tutti gli attributi Source in Attributi di Moniker.

    - Se l'immagine non cambia mai e si utilizza **KnownMonikers**, associare in modo statico tale proprietà a **KnownMoniker**. (Vedere l'esempio precedente.)

    - Se l'immagine non cambia mai e si utilizza la propria immagine personalizzata, quindi associare staticamente al proprio moniker.

    - Se l'immagine può essere modificata, associare l'attributo Moniker a una proprietà di codice che notifica le modifiche alle proprietà.

3. In un punto qualsiasi della gerarchia dell'interfaccia utente, impostare **ImageThemingUtilities.ImageBackgroundColor** per assicurarsi che l'inversione del colore funzioni correttamente.

    - Ciò potrebbe richiedere l'utilizzo della **brushToColorConverter** classe. (Vedere l'esempio precedente.)

## <a name="how-do-i-update-win32-ui"></a>Come si aggiorna l'interfaccia utente Win32?
 Aggiungere quanto segue al codice quando appropriato per sostituire il caricamento non elaborato delle immagini. Parametri per la restituzione di HBITMAP rispetto a HICON e HIMAGELIST in base alle esigenze.

 **Ottenere il servizio immaginiGet the image service**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Richiesta dell'immagine**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Come si aggiorna l'interfaccia utente di WinForms?
 Aggiungere quanto segue al codice quando appropriato per sostituire il caricamento non elaborato delle immagini. Cambia i valori per la restituzione di bitmap a icone in base alle esigenze.

 **Utile dichiarazione using**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Ottenere il servizio immaginiGet the image service**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Richiedi l'immagine**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Come si usano i moniker di immagini in una nuova finestra degli strumenti?
 Il modello di progetto di pacchetto VSIX è stato aggiornato per Visual Studio 2015.The VSIX package project template was updated for Visual Studio 2015. Per creare una nuova finestra degli strumenti, fare clic con il pulsante destro del mouse sul progetto VSIX e selezionare **Aggiungi** > **nuovo elemento** **(CTRL**+**MAIUSC A**+**A**). Nel nodo Extensibility per il linguaggio del progetto selezionare Finestra degli strumenti **personalizzata**, assegnare un nome alla finestra degli strumenti e premere il pulsante **Aggiungi.**

 Questi sono i luoghi chiave per utilizzare i moniker in una finestra degli strumenti. Seguire le istruzioni per ciascuno:

1. Scheda della finestra degli strumenti quando le schede sono abbastanza piccole (utilizzate anche nello switcher finestra **Ctrl**+**Tab).**

    Aggiungere questa riga al costruttore per la classe che deriva dal tipo **ToolWindowPane:**

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Comando per aprire la finestra degli strumenti.

    Nel file *vsct* per il pacchetto, modificare il pulsante di comando della finestra degli strumenti:

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

   **Come si usano i moniker di immagini in una finestra degli strumenti esistente?**

   L'aggiornamento di una finestra degli strumenti esistente per l'utilizzo di moniker di immagini è simile alla procedura per la creazione di una nuova finestra degli strumenti.

   Questi sono i luoghi chiave per utilizzare i moniker in una finestra degli strumenti. Seguire le istruzioni per ciascuno:

3. Scheda della finestra degli strumenti quando le schede sono abbastanza piccole (utilizzate anche nello switcher finestra **Ctrl**+**Tab).**

   1. Rimuovere queste righe (se esistenti) nel costruttore per la classe che deriva dal **ToolWindowPane** tipo:

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Vedere il passaggio #1 del "Come si utilizzano i moniker di immagine in una nuova finestra degli strumenti?" sezione precedente.

4. Comando per aprire la finestra degli strumenti.

   - Vedere il passaggio #2 del "Come si utilizzano i moniker di immagine in una nuova finestra degli strumenti?" sezione precedente.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Come si usano i moniker di immagini in un file vsct?
 Aggiornare il file *vsct* come indicato dalle righe commentate di seguito:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
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

 **Cosa succede se il file vsct deve essere letto anche da versioni precedenti di Visual Studio?**

 Le versioni precedenti di Visual Studio non riconoscono il flag di comando **IconIsMoniker.** È possibile usare le immagini dal servizio immagini nelle versioni di Visual Studio che lo supportano, ma continuare a usare immagini in stile precedente nelle versioni precedenti di Visual Studio.You can use images from the image service on versions of Visual Studio that support it, but continue to use old-style images on older versions of Visual Studio. A tale scopo, è necessario lasciare il file *vsct* invariato (e quindi compatibile con le versioni precedenti di Visual Studio) e creare un file CSV \<(valori delimitati da virgole) che esegue il mapping dalle coppie GUID/ID definite in bitmap di un file *vsct*> elemento per le coppie GUID/ID del moniker dell'immagine.

 Il formato del file CSV di mapping è:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Il file CSV viene distribuito con il pacchetto e il relativo percorso è specificato dalla proprietà **IconMappingFilename** dell'attributo del pacchetto **ProvideMenuResource:**

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 Il **IconMappingFilename** è un percorso relativo con radice implicita in corrispondenza $PackageFolder, come nell'esempio precedente, oppure un percorso assoluto con radice in una directory definita da una variabile di ambiente, ad esempio *"%UserProfile%"dir1"dir2"MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Come si porta il porting di un sistema di progetto?
 **Come fornire ImageMonikers per un progetto**

1. Implementare **VSHPROPID_SupportsIconMonikers** nel **linguaggio IVsHierarchy**del progetto e restituire true.

2. Implementare **VSHPROPID_IconMonikerImageList** (se il progetto originale utilizzato **VSHPROPID_IconImgList**) o **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid** **VSHPROPID_OpenFolderIconMonikerId** (se il progetto originale utilizzato **VSHPROPID_IconHandle** e **VSHPROPID_OpenFolderIconHandle**).

3. Modificare l'implementazione dei VSHPROPOV originali per le icone per creare versioni "legacy" delle icone se i punti di estensione li richiedono. **IVsImageService2** fornisce le funzionalità necessarie per ottenere tali icone

   **Requisiti aggiuntivi per i tipi di progetto VB/C**

   Implementare **VSHPROPID_SupportsIconMonikers** solo se si rileva che il progetto è il **sapore più esterno**. In caso contrario, il sapore effettivo più esterno potrebbe non supportare i moniker di immagine in realtà e il tuo sapore di base potrebbe effettivamente "nascondere" le immagini personalizzate.

   **Come si usano i moniker di immagini in CPS?**

   L'impostazione di immagini personalizzate in CPS (Common Project System) può essere eseguita manualmente o tramite un modello di elemento fornito con l'SDK di estensibilità del sistema di progetto.

   **Utilizzo dell'SDK di estensibilità del sistema di progetto**

   Seguire le istruzioni in [Fornire icone personalizzate per il tipo di progetto/elemento](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) per personalizzare le immagini CPS. Ulteriori informazioni su CPS sono disponibili nella documentazione relativa [all'estensibilità di Visual Studio Project System](https://github.com/Microsoft/VSProjectSystem)

   **Utilizzare manualmente ImageMonikers**

4. Implementare ed esportare l'interfaccia **IProjectTreeModifier** nel sistema del progetto.

5. Determinare quale **Moniker OKnownMoniker** o il moniker dell'immagine personalizzata si desidera utilizzare.

6. Nel **ApplyModifications** metodo, eseguire le operazioni seguenti in un punto qualsiasi del metodo prima di restituire il nuovo albero, simile all'esempio seguente:In the ApplyModifications method, do the following somewhere in the method before returning the new tree, similar to the below example:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Se si sta creando un nuovo albero, è possibile impostare le immagini personalizzate passando i moniker desiderati nel metodo NewTree, simile all'esempio seguente:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Come si converte da una striscia di immagini reali a una striscia di immagini basata su moniker?
 **Ho bisogno di supportare HIMAGELISTs**

 Se esiste una striscia di immagini già esistente per il codice che si desidera aggiornare per utilizzare il servizio immagini, ma si è vincolati da API che richiedono il passaggio intorno agli elenchi di immagini, è comunque possibile ottenere i vantaggi del servizio immagini. Per creare una striscia di immagini basata su moniker, attenersi alla procedura seguente per creare un manifesto da moniker esistenti.

1. Eseguire lo strumento **ManifestFromResources,** passando la striscia di immagini. Verrà generato un manifesto per la striscia.

   - Consigliato: specificare un nome non predefinito per il manifesto in base al relativo utilizzo.

2. Se si utilizzano solo **KnownMonikers**, eseguire le operazioni seguenti:

   - Sostituire \<la sezione> Immagini \<del manifesto con Immagini/>.

   - Rimuovere tutti gli URL di immagine \<secondaria (qualsiasi cosa con il nome di imagestrip>_) ).

   - Consigliato: rinominare il simbolo AssetsGuid e il simbolo della striscia di immagini in base al relativo utilizzo.

   - Sostituire ogni 's GUID di **ContainedImage**con il valore di '(ImageCatalogGuid), sostituire ogni ID 's **'containedImage**'con '(\<moniker>)e aggiungere l'attributo External 'true' a ogni **ContainedImage**

       - \<l'> del moniker deve essere sostituito con il **KnownMoniker** che corrisponde all'immagine ma con il "KnownMonikers". viene rimosso dal nome.

   - Aggiungere\\ <'import manifesto<percorso di dir di\>installazione relativo a>\*> \<.

       - Il percorso relativo è determinato dal percorso di distribuzione definito nella creazione dell'installazione per il manifesto.

3. Eseguire lo strumento **ManifestToCode** per generare wrapper in modo che il codice esistente disponga di un moniker che può essere usato per eseguire una query sul servizio immagini per la striscia di immagini.

   - Consigliato: fornire nomi non predefiniti per i wrapper e gli spazi dei nomi in base al loro utilizzo.

4. Eseguire tutte le aggiunte, la creazione/distribuzione dell'installazione e altre modifiche al codice per utilizzare il servizio immagini e i nuovi file.

   Manifesto di esempio che include immagini interne ed esterne per verificarne l'aspetto:

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

1. Determinare il set di **KnownMonikers** che corrispondono alle immagini nella striscia di immagini o creare i propri moniker per le immagini nella striscia di immagini.

2. Aggiornare qualsiasi mapping utilizzato per ottenere l'immagine in corrispondenza dell'indice richiesto nella striscia di immagini per utilizzare i moniker.

3. Aggiornare il codice per utilizzare il servizio immagini per richiedere moniker tramite il mapping aggiornato. (Questo potrebbe significare l'aggiornamento a **CrispImages** per il codice gestito o la richiesta di HBITMAP o HICON dal servizio immagini e passarli per il codice nativo.)

## <a name="testing-your-images"></a>Test delle immagini
 È possibile utilizzare lo strumento Visualizzatore libreria immagini per testare i manifesti delle immagini per assicurarsi che tutto sia stato creato correttamente. È possibile trovare lo strumento in [Visual Studio 2015 SDK](visual-studio-sdk.md). La documentazione per questo strumento e altri può essere trovata [qui](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015).

## <a name="additional-resources"></a>Risorse aggiuntive

### <a name="samples"></a>Esempi
 Molti degli esempi di Visual Studio in GitHub sono stati aggiornati per mostrare come usare il servizio immagini come parte di vari punti di estendibilità di Visual Studio.

 Verificare la disponibilità [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) dei campioni più recenti.

### <a name="tooling"></a>Strumenti
 È stato creato un set di strumenti di supporto per il servizio immagini per facilitare la creazione/aggiornamento dell'interfaccia utente che funziona con il servizio immagini. Per ulteriori informazioni su ogni strumento, consultare la documentazione fornita con gli strumenti. Gli strumenti sono inclusi come parte di [Visual Studio 2015 SDK.](visual-studio-sdk.md)

 **ManifestFromResources**

 Lo strumento Manifesto da risorse accetta un elenco di risorse immagine (PNG o XAML) e genera un file manifesto dell'immagine per l'utilizzo di tali immagini con il servizio immagini.

 **ManifestToCode**

 Lo strumento Manifesto in codice accetta un file manifesto dell'immagine e genera un file wrapper per fare riferimento ai valori del manifesto nei file di codice (C , C , o VB) o *vsct.*

 **ImageLibraryViewer (Raccolta immagini)**

 Lo strumento Visualizzatore libreria di immagini può caricare i manifesti delle immagini e consente all'utente di modificarli nello stesso modo in cui Visual Studio desidera assicurarsi che il manifesto venga creato correttamente. L'utente può modificare lo sfondo, le dimensioni, l'impostazione DPI, contrasto elevato e altre impostazioni. Visualizza inoltre le informazioni di caricamento per individuare gli errori nei manifesti e visualizza le informazioni sull'origine per ogni immagine nel manifesto.

## <a name="faq"></a>Domande frequenti

- Esistono dipendenze che è necessario \<includere durante il caricamento di riferimento Include "Microsoft.VisualStudio. Interop.14.0.DesignTime" />?

  - Impostare EmbedInteropTypes su tutte le DLL di interoperabilità.

- Come si distribuisce un manifesto dell'immagine con l'estensione?

  - Aggiungere il file *.imagemanifest* al progetto.

  - Impostare "Includi in VSIX" su True.

- Sto aggiornando il mio sistema di progetto CPS. Che cosa è successo a **ImageName** e **StockIconService**?

  - Questi sono stati rimossi quando CPS è stato aggiornato per utilizzare moniker. Non è più necessario chiamare **StockIconService**, è sufficiente passare il **KnownMoniker** desiderato al metodo o alla proprietà utilizzando il metodo di estensione **ToProjectSystemType()** nelle utilità CPS. È possibile trovare un mapping da **ImageName** a KnownMonikers di seguito:You can find a mapping from ImageName to **KnownMonikers** below:

    |||
    |-|-|
    |**ImageName**|**KnownMoniker**|
    |NomeImmagine.OfflineWebApp|KnownImageIds.Web|
    |ImageName.WebReferencesFolder|KnownImageIds.Web|
    |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName.ReferenceFolder|KnownImageIds.Reference|
    |NomeImmagine.Riferimento|KnownImageIds.Reference|
    |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder (Informazioni in lingua sconosciuta)|
    |NomeImmagine.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |NomeImmagine.Cartella|KnownImageIds.FolderClosed|
    |NomeImmagine.OpenFolder|KnownImageIds.FolderOpened|
    |NomeImmagine.ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |NomeImmagine.ApriEsclusaCartella|KnownImageIds.HiddenFolderOpened|
    |NomeImmagine.ExcludedFile|KnownImageIds.HiddenFile|
    |NomeImmagine.DependentFile|KnownImageIds.GenerateFile|
    |NomeImmagine.FileMancante|KnownImageIds.DocumentWarning|
    |NomeImmagine.WindowsForm|KnownImageIds.WindowsForm|
    |NomeImmagine.WindowsUserControl|KnownImageIds.UserControl|
    |NomeImmagine.WindowsComponente|FileKnownImageIds.ComponentFile|
    |NomeImmagine.XmlSchema|KnownImageIds.XMLSchema|
    |ImageName.XmlFile|FileKnownImageIds.XMLFile|
    |NomeImmagine.WebForm|KnownImageIds.Web|
    |NomeImmagine.WebService|KnownImageIds.WebService (ServizioImmagine KnownImageIds)|
    |NomeImmagine.WebUserControl|KnownImageIds.WebUserControl|
    |NomeImmagine.WebCustomUserControl|KnownImageIds.WebCustomControl|
    |NomeImmagine.AspPage|File KnownImageIds.ASPFile|
    |NomeImmagine.GlobalApplicationClass|FileKnownImageIds.SettingsFile|
    |NomeImmagine.WebConfig|FileNotiImageIds.ConfigurationFile|
    |NomeImmagine.HtmlPagina|File KnownImageIds.HTMLFile|
    |ImageName.StyleSheet (NomeImmagine.Foglio di stile)|KnownImageIds.StyleSheet (Foglio di visualizzazione di KnownImageIds)KnownImageIds.Style|
    |NomeImmagine.ScriptFile|KnownImageIds.JSScript|
    |ImageName.TextFile|File KnownImageIds.Document|
    |NomeImmagine.SettingsFile|KnownImageIds.Settings|
    |ImageName.Risorse|KnownImageIds.DocumentGroup (Gruppo Immagini noti)|
    |NomeImmagine.Bitmap|File KnownImageIds.Image|
    |NomeImmagine.Icona|FileKnownImageIds.IconFile|
    |NomeImmagine.Immagine|File KnownImageIds.Image|
    |ImageName.ImageMap|KnownImageIds.ImageMapFile|
    |NomeImmagine.XWorld|KnownImageIds.XWorldFile|
    |NomeImmagine.Audio|KnownImageIds.Sound|
    |NomeImmagine.Video|KnownImageIds.Media|
    |NomeImmagine.Cab|Progetto KnownImageIds.CABProject|
    |NomeImmagine.Jar|FileKnownImageIds.JARFile|
    |NomeImmagine.DataAmbiente|KnownImageIds.DataTable|
    |NomeImmagine.PreviewFile|KnownImageIds.Report|
    |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|
    |NomeImmagine.XsltFile|KnownImageIds.XSLTransform|
    |ImageName.Cursor|File KnownImageIds.CursorFile|
    |NomeImmagine.AppDesignerFolder|KnownImageIds.Property|
    |NomeImmagine.Dati|File KnownImageIds.Database|
    |NomeImmagine.Applicazione|KnownImageIds.Application|
    |NomeImmagine.DataSet|KnownImageIds.DatabaseGroup|
    |NomeImmagine.Pfx|KnownImageIds.Certificate|
    |NomeImmagine.Snk|KnownImageIds.Rule|
    |NomeImmagine.VisualBasicProject|KnownImageIds.VBProjectNode|
    |NomeImmagine.CSharpProject|KnownImageIds.CSProjectNode|
    |NomeImmagine.Vuoto|KnownImageIds.Blank|
    |NomeImmagine.CartellaMancante|KnownImageIds.FolderOffline|
    |NomeImmagine.SharedImportReference|KnownImageIds.SharedProject|
    |NomeImmagine.SharedProjectCs|KnownImageIds.CSSharedProject|
    |NomeImmagine.ProgettoShared|KnownImageIds.CPPSharedProject|
    |NomeImmagine.SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|
    |NomeImmagine.VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Sto aggiornando il mio fornitore dell'elenco di completamento. Quali **KnownMonikers** corrispondono ai vecchi valori **StandardGlyphGroup** e **StandardGlyph?**

    ||||
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassePublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClasseProtetta|
    |GlyphGroupClass|GlyphItemPrivate|ClassePrivato|
    |GlyphGroupClass|GlyphItemShortcut|ClasseAb|
    |GlyphGroupConstant (costante di GlyphGroupConstant)|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant (costante di GlyphGroupConstant)|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant (costante di GlyphGroupConstant)|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant (costante di GlyphGroupConstant)|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant (costante di GlyphGroupConstant)|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant (costante di GlyphGroupConstant)|GlyphItemShortcut|ConstantShortcut (Collegamento di costanti)|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal (Interno enumerazione)|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal (Interno enumerazione)|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut (Collegamento enumerazione)|
    |GlyphGroupEnumMembro|GlyphItemPublic|EnumerationItemPublic (proprietà)|
    |GlyphGroupEnumMembro|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMembro|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMembro|GlyphItemProtected|EnumerationItemProtected (Proprietà EnumerationItemProtected)|
    |GlyphGroupEnumMembro|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMembro|GlyphItemShortcut|EnumerationItemShortcut (collegamento di EnumerationItemShortcut)|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal (Interno evento)|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal (Interno evento)|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut (Collegamento eventi)|
    |GlyphGroupException (eccezione glisifa)|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException (eccezione glisifa)|GlyphItemInternal|EccezioneInterna|
    |GlyphGroupException (eccezione glisifa)|GlyphItemFriend|EccezioneInterna|
    |GlyphGroupException (eccezione glisifa)|GlyphItemProtected|ExceptionProtectedExceptionProtected|
    |GlyphGroupException (eccezione glisifa)|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException (eccezione glisifa)|GlyphItemShortcut|ExceptionShortcut (Collegamento eccezione)|
    |Campo Gruppo di glifi|GlyphItemPublic|CampoPubblico|
    |Campo Gruppo di glifi|GlyphItemInternal|CampoInterno|
    |Campo Gruppo di glifi|GlyphItemFriend|CampoInterno|
    |Campo Gruppo di glifi|GlyphItemProtected|CampoProtetto|
    |Campo Gruppo di glifi|GlyphItemPrivate|CampoPrivato|
    |Campo Gruppo di glifi|GlyphItemShortcut|Collegamento campo|
    |Interfaccia GlyphGroup|GlyphItemPublic|InterfacePublic (InterfacciaPublic)|
    |Interfaccia GlyphGroup|GlyphItemInternal|InterfacciaInterno|
    |Interfaccia GlyphGroup|GlyphItemFriend|InterfacciaInterno|
    |Interfaccia GlyphGroup|GlyphItemProtected|InterfaceProtected|
    |Interfaccia GlyphGroup|GlyphItemPrivate|InterfacePrivate|
    |Interfaccia GlyphGroup|GlyphItemShortcut|InterfaceShortcut (Collegamento interfaccia)|
    |GlyphGroupMacro|GlyphItemPublic|MacroPubblico|
    |GlyphGroupMacro|GlyphItemInternal|MacroInterno|
    |GlyphGroupMacro|GlyphItemFriend|MacroInterno|
    |GlyphGroupMacro|GlyphItemProtected|MacroProtetto|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivato|
    |GlyphGroupMacro|GlyphItemShortcut|Collegamento macro|
    |GlyphGroupMap|GlyphItemPublic|MappaPublic|
    |GlyphGroupMap|GlyphItemInternal|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|MapProtected|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|Collegamento mappa|
    |GlyphGroupMapItem (elemento)|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem (elemento)|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem (elemento)|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem (elemento)|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem (elemento)|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem (elemento)|GlyphItemShortcut|MapItemShortcut|
    |Metodo GlyphGroup|GlyphItemPublic|MetodoPubblico|
    |Metodo GlyphGroup|GlyphItemInternal|MetodoInterno|
    |Metodo GlyphGroup|GlyphItemFriend|MetodoInterno|
    |Metodo GlyphGroup|GlyphItemProtected|MethodProtected|
    |Metodo GlyphGroup|GlyphItemPrivate|MethodPrivate|
    |Metodo GlyphGroup|GlyphItemShortcut|MethodShortcut (Collegamento metodo)|
    |GlyphGroupOverload|GlyphItemPublic|MetodoPubblico|
    |GlyphGroupOverload|GlyphItemInternal|MetodoInterno|
    |GlyphGroupOverload|GlyphItemFriend|MetodoInterno|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut (Collegamento metodo)|
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|ModuloInterno|
    |GlyphGroupModule|GlyphItemFriend|ModuloInterno|
    |GlyphGroupModule|GlyphItemProtected|ModuloProtetto|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivato|
    |GlyphGroupModule|GlyphItemShortcut|ModuloDicollegamento|
    |Spazio dei nomi GlyphGroup|GlyphItemPublic|NamespacePublicNamespacePublic|
    |Spazio dei nomi GlyphGroup|GlyphItemInternal|NamespaceInternalNamespaceInternal|
    |Spazio dei nomi GlyphGroup|GlyphItemFriend|NamespaceInternalNamespaceInternal|
    |Spazio dei nomi GlyphGroup|GlyphItemProtected|NamespaceProtectedNamespaceProtected|
    |Spazio dei nomi GlyphGroup|GlyphItemPrivate|NamespacePrivate|
    |Spazio dei nomi GlyphGroup|GlyphItemShortcut|NamespaceShortcut (Sceltadi spazi dei nomi|
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorEInterno|
    |GlyphGroupOperator|GlyphItemFriend|OperatorEInterno|
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut (Collegamento operatore)|
    |Proprietà GlyphGroupProperty|GlyphItemPublic|ProprietàPublic|
    |Proprietà GlyphGroupProperty|GlyphItemInternal|ProprietàInterna|
    |Proprietà GlyphGroupProperty|GlyphItemFriend|ProprietàInterna|
    |Proprietà GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |Proprietà GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |Proprietà GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|
    |GlyphGroupStruct|GlyphItemInternal|StrutturaInterno|
    |GlyphGroupStruct|GlyphItemFriend|StrutturaInterno|
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut (Collegamento struttura)|
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic (Modellopubblico)|
    |GlyphGroupTemplate|GlyphItemInternal|ModelloInterno|
    |GlyphGroupTemplate|GlyphItemFriend|ModelloInterno|
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected (Modelloprotetto)|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|Collegamento di modelli|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TipoInterno|
    |GlyphGroupType|GlyphItemFriend|TipoInterno|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut (Collegamento di tipo)|
    |Unione Di glifi|GlyphItemPublic|UnionePubblico|
    |Unione Di glifi|GlyphItemInternal|UnionInternal|
    |Unione Di glifi|GlyphItemFriend|UnionInternal|
    |Unione Di glifi|GlyphItemProtected|UnionProtected|
    |Unione Di glifi|GlyphItemPrivate|UnionPrivate|
    |Unione Di glifi|GlyphItemShortcut|UnionShortcut (Abisso dell'|
    |GlyphGroupVariable|GlyphItemPublic|CampoPubblico|
    |GlyphGroupVariable|GlyphItemInternal|CampoInterno|
    |GlyphGroupVariable|GlyphItemFriend|CampoInterno|
    |GlyphGroupVariable|GlyphItemProtected|CampoProtetto|
    |GlyphGroupVariable|GlyphItemPrivate|CampoPrivato|
    |GlyphGroupVariable|GlyphItemShortcut|Collegamento campo|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut (Collegamento di ValueType)|
    |GlyphGroupIntrinsicGlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsicGlyphGroupIntrinsic|GlyphItemInternal|OggettoInterno|
    |GlyphGroupIntrinsicGlyphGroupIntrinsic|GlyphItemFriend|OggettoInterno|
    |GlyphGroupIntrinsicGlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsicGlyphGroupIntrinsic|GlyphItemPrivate|Oggetto Privato|
    |GlyphGroupIntrinsicGlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut (Collegamento oggetto)|
    |Metodo GlyphGroupJSharpMethod|GlyphItemPublic|MetodoPubblico|
    |Metodo GlyphGroupJSharpMethod|GlyphItemInternal|MetodoInterno|
    |Metodo GlyphGroupJSharpMethod|GlyphItemFriend|MetodoInterno|
    |Metodo GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |Metodo GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |Metodo GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut (Collegamento metodo)|
    |GlyphGroupJSharpField (campo di glifi)|GlyphItemPublic|CampoPubblico|
    |GlyphGroupJSharpField (campo di glifi)|GlyphItemInternal|CampoInterno|
    |GlyphGroupJSharpField (campo di glifi)|GlyphItemFriend|CampoInterno|
    |GlyphGroupJSharpField (campo di glifi)|GlyphItemProtected|CampoProtetto|
    |GlyphGroupJSharpField (campo di glifi)|GlyphItemPrivate|CampoPrivato|
    |GlyphGroupJSharpField (campo di glifi)|GlyphItemShortcut|Collegamento campo|
    |GlyphGroupJSharpClass (classe GlyphGroupJSharpClass)|GlyphItemPublic|ClassePublic|
    |GlyphGroupJSharpClass (classe GlyphGroupJSharpClass)|GlyphItemInternal|ClassInternal|
    |GlyphGroupJSharpClass (classe GlyphGroupJSharpClass)|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass (classe GlyphGroupJSharpClass)|GlyphItemProtected|ClasseProtetta|
    |GlyphGroupJSharpClass (classe GlyphGroupJSharpClass)|GlyphItemPrivate|ClassePrivato|
    |GlyphGroupJSharpClass (classe GlyphGroupJSharpClass)|GlyphItemShortcut|ClasseAb|
    |GlyphGroupJSharpNamespace (Spazio dei nomi GlyphGroupJSharpNamespace)|GlyphItemPublic|NamespacePublicNamespacePublic|
    |GlyphGroupJSharpNamespace (Spazio dei nomi GlyphGroupJSharpNamespace)|GlyphItemInternal|NamespaceInternalNamespaceInternal|
    |GlyphGroupJSharpNamespace (Spazio dei nomi GlyphGroupJSharpNamespace)|GlyphItemFriend|NamespaceInternalNamespaceInternal|
    |GlyphGroupJSharpNamespace (Spazio dei nomi GlyphGroupJSharpNamespace)|GlyphItemProtected|NamespaceProtectedNamespaceProtected|
    |GlyphGroupJSharpNamespace (Spazio dei nomi GlyphGroupJSharpNamespace)|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace (Spazio dei nomi GlyphGroupJSharpNamespace)|GlyphItemShortcut|NamespaceShortcut (Sceltadi spazi dei nomi|
    |GlyphGroupJSharpInterface (interfaccia di glyphGroupJSharpInterface)|GlyphItemPublic|InterfacePublic (InterfacciaPublic)|
    |GlyphGroupJSharpInterface (interfaccia di glyphGroupJSharpInterface)|GlyphItemInternal|InterfacciaInterno|
    |GlyphGroupJSharpInterface (interfaccia di glyphGroupJSharpInterface)|GlyphItemFriend|InterfacciaInterno|
    |GlyphGroupJSharpInterface (interfaccia di glyphGroupJSharpInterface)|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface (interfaccia di glyphGroupJSharpInterface)|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface (interfaccia di glyphGroupJSharpInterface)|GlyphItemShortcut|InterfaceShortcut (Collegamento interfaccia)|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||File Classe|
    |GlyphAssembly||Informazioni di riferimento|
    |Libreria di glifi||Libreria|
    |Progetto GlifoVBProject||VBProjectNode (VBProjectNode)|
    |GlyphCoolProject||CSProjectNode (Nodo PROGETTO)|
    |GlyphCppProject||CPPProjectNode (Nodo Progetto CPP)|
    |GlyphDialogId (Id di glyphDialog)||Finestra di dialogo|
    |GlyphOpenFolder (Cartella glifi)||Cartella aperta|
    |GlyphClosedFolder||Cartella Chiusa|
    |Freccia di glifi||Vai Avanti|
    |GlyphCSharpFile (File glyphCSharpFile)||CSFileNode (Nodo CSFileNode)|
    |GlyphCSharpExpansion||Frammento di codice|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphInformation (Informazioni sul glifo)||StatusInformation|
    |GlyphReference (riferimento a gliemi||ClassMethodReference (MetodoClass)|
    |Ricorsione glifo||Ricorsione|
    |GlyphXmlItem (elemento)||Tag|
    |Progetto GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDocument||Document|
    |Tipo GlyphForwardType||Vai Avanti|
    |GlyphCallersGraph||Servizio di chiamata|
    |GlyphCallGraph (grafo di GlyphCallGraph)||CallFrom (Informazioni in base a|
    |Avviso glifosato||StatusWarning|
    |GlyphMaybeReference (Riferimento a GlyphMaybe)||Questionmark|
    |GlyphMaybeCaller (chiamante di GlyphMaybeCaller)||Servizio di chiamata|
    |GlyphMaybeCall (Chiamata di GlyphMaybe||CallFrom (Informazioni in base a|
    |Metodo GlyphExtensionMethod||ExtensionMethod (Metodo Estensione)|
    |GlyphExtensionMethodInternal||ExtensionMethod (Metodo Estensione)|
    |GlyphExtensionMethodFriend||ExtensionMethod (Metodo Estensione)|
    |GlyphExtensionMethodProtected||ExtensionMethod (Metodo Estensione)|
    |GlyphExtensionMethodPrivate||ExtensionMethod (Metodo Estensione)|
    |GlyphExtensionMethodShortcut||ExtensionMethod (Metodo Estensione)|
    |GlyphXmlAttribute (attributo GlyphXmlAttribute)||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||XmlDescendant (Esempio XmlDescendant)|
    |Spazio glisto(GlyphXmlNamespace)||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |Controllo GlyphXmlAttribute||XmlAttributeHighConfidence (Informazioni in base al conto dei nomi Xml|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck (controllo GlyphXmlChildCheck)||XmlElementHighConfidence (Informazioni in base ai coi stati in|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |Controllo GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |Avviso di addimento||IntellisenseWarning|
