---
title: Catalogo e servizio immagini | Microsoft Docs
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a098e78e8895aea72d830a88e436a06f15de6133
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584542"
---
# <a name="image-service-and-catalog"></a>Catalogo e servizio immagini
Questa guida di riferimento contiene indicazioni e procedure consigliate per l'adozione del servizio immagini di Visual Studio e del catalogo immagini introdotti in Visual Studio 2015.

 Il servizio immagini introdotto in Visual Studio 2015 consente agli sviluppatori di ottenere le immagini migliori per il dispositivo e il tema scelto dall'utente per visualizzare l'immagine, inclusa la correzione del tema per il contesto in cui vengono visualizzate. L'adozione del servizio immagini consente di eliminare i principali punti deboli correlati alla manutenzione degli asset, al ridimensionamento del HDPI e al tema.

|**Problemi attuali**|**Soluzioni**|
|-|-|
|Fusione del colore di sfondo|Fusione alfa incorporata|
|Immagini del tema (alcune)|Metadati del tema|
|Modalità Contrasto elevato|Risorse Contrasto elevato alternative|
|Sono necessarie più risorse per diverse modalità DPI|Risorse selezionabili con fallback basato su vettori|
|Immagini duplicate|Un identificatore per ogni concetto di immagine|

 Perché adottare il servizio immagini?

- Ottieni sempre l'immagine "pixel-perfect" più recente da Visual Studio

- È possibile inviare e usare immagini personalizzate

- Non è necessario testare le immagini quando Windows aggiunge la nuova scala DPI

- Risolvere gli ostacoli di architettura obsoleti nelle implementazioni

  Barra degli strumenti della shell di Visual Studio prima e dopo l'uso del servizio immagini:

  ![Servizio immagini prima e dopo](../extensibility/media/image-service-before-and-after.png "Servizio immagini prima e dopo")

## <a name="how-it-works"></a>Funzionamento
 Il servizio immagini può fornire un'immagine bitmap adatta per qualsiasi framework dell'interfaccia utente supportato:

- WPF: BitmapSource

- WinForms: System. Drawing. bitmap

- Win32: HBITMAP

  Diagramma di flusso del servizio immagini

  ![Diagramma di flusso del servizio immagini](../extensibility/media/image-service-flow-diagram.png "Diagramma di flusso del servizio immagini")

  **Moniker immagine**

  Un moniker di immagine (o moniker per brevità) è una coppia GUID/ID che identifica in modo univoco un asset immagine o un asset elenco immagini nella libreria di immagini.

  **Moniker noti**

  Set di moniker di immagini contenuti nel catalogo immagini di Visual Studio e utilizzabili pubblicamente da qualsiasi componente o estensione di Visual Studio.

  **File manifesto immagine**

  I file manifesto immagine (con*estensione imagemanifest*) sono file XML che definiscono un set di asset immagine, i moniker che rappresentano tali asset e l'immagine reale o immagini che rappresentano ogni asset. I manifesti di immagine possono definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Sono inoltre disponibili attributi che possono essere impostati sull'asset o sulle singole immagini dietro ogni asset per modificare quando e come vengono visualizzati gli asset.

  **Schema manifesto immagine**

  Un manifesto completo dell'immagine ha un aspetto simile al seguente:

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

 Per facilitare la leggibilità e la manutenzione, il manifesto dell'immagine può utilizzare i simboli per i valori di attributo. I simboli sono definiti come segue:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Sottoelemento**|**Definizione**|
|-|-|
|Importa|Importa i simboli del file manifesto specificato per l'uso nel manifesto corrente|
|Guid|Il simbolo rappresenta un GUID e deve corrispondere alla formattazione del GUID|
|ID|Il simbolo rappresenta un ID e deve essere un numero intero non negativo|
|string|Il simbolo rappresenta un valore stringa arbitrario|

 Per i simboli viene fatta distinzione tra maiuscole e minuscole e viene fatto riferimento tramite la sintassi $ (symbol-name):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Alcuni simboli sono predefiniti per tutti i manifesti. Questi possono essere usati nell'attributo URI dell' \<Source> \<Import> elemento o per fare riferimento ai percorsi nel computer locale.

|**Simbolo**|**Descrizione**|
|-|-|
|CommonProgramFiles|Valore della variabile di ambiente% CommonProgramFiles%|
|LocalAppData|Valore della variabile di ambiente% LocalAppData%|
|ManifestFolder|Cartella contenente il file manifesto|
|MyDocuments|Percorso completo della cartella documenti dell'utente corrente|
|ProgramFiles|Valore della variabile di ambiente% ProgramFiles%|
|Sistema|Cartella *Windows\System32*|
|WinDir|Valore della variabile di ambiente% WinDir%|

 **Immagine**

 L' \<Image> elemento definisce un'immagine a cui può fare riferimento un moniker. Il GUID e l'ID riuniti formano il moniker dell'immagine. Il moniker per l'immagine deve essere univoco nell'intera libreria di immagini. Se più immagini hanno un determinato moniker, il primo rilevato durante la compilazione della libreria è quello mantenuto.

 Deve contenere almeno un'origine. Le origini indipendenti dalle dimensioni forniranno i migliori risultati in un'ampia gamma di dimensioni, ma non sono necessarie. Se al servizio viene richiesta un'immagine di una dimensione non definita nell' \<Image> elemento e non è presente un'origine indipendente dalle dimensioni, il servizio sceglierà l'origine più adatta alle dimensioni specifiche e la proporrà alla dimensione richiesta.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Attributo**|**Definizione**|
|-|-|
|Guid|Necessaria Parte GUID del moniker dell'immagine|
|ID|Necessaria Parte relativa all'ID del moniker dell'immagine|
|AllowColorInversion|[Facoltativo, valore predefinito true] Indica se i colori dell'immagine possono essere invertiti a livello di codice quando vengono utilizzati in uno sfondo scuro.|

 **Origine**

 L' \<Source> elemento definisce una singola risorsa di origine dell'immagine (XAML e png).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Attributo**|**Definizione**|
|-|-|
|Uri|Necessaria URI che definisce dove è possibile caricare l'immagine. I possibili valori sono i seguenti:<br /><br /> : [URI di pacchetto](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) che usa l'autorità Application:///<br />-Riferimento a una risorsa componente assoluto<br />: Percorso di un file che contiene una risorsa nativa|
|Background|Opzionale Indica il tipo di background che l'origine deve usare.<br /><br /> I possibili valori sono i seguenti:<br /><br /> *Chiaro:* L'origine può essere utilizzata su uno sfondo chiaro.<br /><br /> *Scuro:* L'origine può essere utilizzata su uno sfondo scuro.<br /><br /> *HighContrast:* L'origine può essere utilizzata in qualsiasi background in modalità Contrasto elevato.<br /><br /> *HighContrastLight:* L'origine può essere utilizzata su uno sfondo chiaro in modalità Contrasto elevato.<br /><br /> *HighContrastDark:* L'origine può essere utilizzata su uno sfondo scuro in modalità Contrasto elevato.<br /><br /> Se l'attributo background viene omesso, l'origine può essere utilizzata in qualsiasi background.<br /><br /> Se background è *Light*, *Dark*, *HighContrastLight*o *HighContrastDark*, i colori dell'origine non vengono mai invertiti. Se background viene omesso o impostato su *HighContrast*, l'inversione dei colori dell'origine viene controllata dall'attributo **AllowColorInversion** dell'immagine.|

Un \<Source> elemento può avere esattamente uno dei sottoelementi facoltativi seguenti:

|**elemento**|**Attributi (tutti necessari)**|**Definizione**|
|-|-|-|
|\<Size>|Valore|L'origine verrà usata per le immagini con le dimensioni specificate (in unità dispositivo). L'immagine sarà quadrata.|
|\<SizeRange>|MinSize, MaxSize|L'origine verrà usata per le immagini da MinSize a MaxSize (in unità dispositivo), inclusi. L'immagine sarà quadrata.|
|\<Dimensions>|Larghezza, altezza|L'origine verrà usata per le immagini della larghezza e dell'altezza specificate (in unità dispositivo).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|L'origine verrà usata per le immagini dalla larghezza/altezza minima alla larghezza/altezza massima (in unità dispositivo), inclusi.|

 Un \<Source> elemento può anche avere un \<NativeResource> sottoelemento facoltativo, che definisce un \<Source> che viene caricato da un assembly nativo anziché da un assembly gestito.

```xml
<NativeResource Type="type" ID="int" />
```

|**Attributo**|**Definizione**|
|-|-|
|Tipo|Necessaria Il tipo della risorsa nativa, ovvero XAML o PNG|
|ID|Necessaria Parte relativa all'ID integer della risorsa nativa|

 **ImageList**

 L' \<ImageList> elemento definisce una raccolta di immagini che possono essere restituite in una singola striscia. Il Strip è compilato su richiesta, in base alle esigenze.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Attributo**|**Definizione**|
|-|-|
|Guid|Necessaria Parte GUID del moniker dell'immagine|
|ID|Necessaria Parte relativa all'ID del moniker dell'immagine|
|Esterno|[Facoltativo, valore predefinito false] Indica se il moniker dell'immagine fa riferimento a un'immagine nel manifesto corrente.|

 Il moniker per l'immagine contenuta non deve fare riferimento a un'immagine definita nel manifesto corrente. Se non è possibile trovare l'immagine contenuta nella libreria di immagini, al suo posto verrà utilizzata un'immagine segnaposto vuota.

## <a name="using-the-image-service"></a>Uso del servizio immagini

### <a name="first-steps-managed"></a>Primi passaggi (gestiti)
 Per usare il servizio immagini, è necessario aggiungere al progetto i riferimenti ad alcuni o a tutti gli assembly seguenti:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Obbligatorio se si usa il catalogo immagini predefinito **KnownMonikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Obbligatorio se si usano **CrispImage** e **ImageThemingUtilities** nell'interfaccia utente WPF.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Obbligatorio se si usano i tipi **ImageMoniker** e **ImageAttributes** .

  - **EmbedInteropTypes** deve essere impostato su true.

- *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime*

  - Obbligatorio se si usa il tipo **IVsImageService2** .

  - **EmbedInteropTypes** deve essere impostato su true.

- *Microsoft.VisualStudio.Utilities.dll*

  - Obbligatorio se si usa **BrushToColorConverter** per **ImageThemingUtilities. ImageBackgroundColor** nell'interfaccia utente WPF.

- *Microsoft. VisualStudio. Shell. \<VSVersion> . 0*

  - Obbligatorio se si usa il tipo **IVsUIObject** .

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Obbligatorio se si usano gli helper dell'interfaccia utente correlati a WinForms.

  - **EmbedInteropTypes** deve essere impostato su true

### <a name="first-steps-native"></a>Primi passaggi (nativi)
 Per usare il servizio immagini, è necessario includere nel progetto alcune o tutte le intestazioni seguenti:

- **KnownImageIds. h**

  - Obbligatorio se si usa il catalogo immagini predefinito **KnownMonikers**, ma non è possibile usare il tipo **ImageMoniker** , ad esempio quando si restituiscono valori da **IVsHierarchy GetGuidProperty** o chiamate **GetProperty** .

- **KnownMonikers. h**

  - Obbligatorio se si usa il catalogo immagini predefinito **KnownMonikers**.

- **ImageParameters140. h**

  - Obbligatorio se si usano i tipi **ImageMoniker** e **ImageAttributes** .

- **VSShell140. h**

  - Obbligatorio se si usa il tipo **IVsImageService2** .

- **ImageThemingUtilities. h**

  - Obbligatorio se non si è in grado di consentire al servizio immagini di gestire l'utente.

  - Non usare questa intestazione se il servizio immagini è in grado di gestire le immagini.

::: moniker range="vs-2017"
- **VSUIDPIHelper. h**

  - Obbligatorio se si usano gli helper DPI per ottenere il valore DPI corrente.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness. h**

  - Obbligatorio se si usano gli helper di sensibilizzazione DPI per ottenere il valore DPI corrente.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Ricerca per categorie scrivere una nuova interfaccia utente WPF?

1. Per iniziare, aggiungere al progetto i riferimenti agli assembly necessari nella sezione passaggi precedenti. Non è necessario aggiungerli tutti, quindi aggiungere solo i riferimenti necessari. Nota: se si usa o si ha accesso a **colori** invece che a **pennelli**, è possibile ignorare il riferimento alle **utilità**, perché il convertitore non sarà necessario.

2. Selezionare l'immagine desiderata e ottenere il relativo moniker. Usare un **KnownMoniker**o usare il proprio se si dispone di immagini e moniker personalizzati.

3. Aggiungere **CrispImages** al codice XAML. (Vedere l'esempio seguente).

4. Impostare la proprietà **ImageThemingUtilities. ImageBackgroundColor** nella gerarchia dell'interfaccia utente. (Deve essere impostato nella posizione in cui il colore di sfondo è noto, non necessariamente in **CrispImage**). (Vedere l'esempio seguente).

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

 **Ricerca per categorie aggiornare l'interfaccia utente WPF esistente?**

 L'aggiornamento dell'interfaccia utente WPF esistente è un processo relativamente semplice costituito da tre passaggi di base:

1. Sostituire tutti \<Image> gli elementi dell'interfaccia utente con \<CrispImage> gli elementi.

2. Modificare tutti gli attributi di origine in attributi moniker.

    - Se l'immagine non cambia mai e si usa **KnownMonikers**, associare in modo statico tale proprietà a **KnownMoniker**. (Vedere l'esempio precedente).

    - Se l'immagine non cambia mai e si usa un'immagine personalizzata, associare in modo statico il proprio moniker.

    - Se l'immagine può essere modificata, associare l'attributo del moniker a una proprietà del codice che invia una notifica sulle modifiche delle proprietà.

3. In un punto qualsiasi della gerarchia dell'interfaccia utente impostare **ImageThemingUtilities. ImageBackgroundColor** per assicurarsi che il colore Inversion funzioni correttamente.

    - Questa operazione potrebbe richiedere l'uso della classe **BrushToColorConverter** . (Vedere l'esempio precedente).

## <a name="how-do-i-update-win32-ui"></a>Ricerca per categorie aggiornare l'interfaccia utente Win32?
 Aggiungere quanto segue al codice laddove appropriato per sostituire il caricamento non elaborato delle immagini. Cambiare i valori per restituire HBITMAPs rispetto a HICONs e HIMAGELIST in base alle esigenze.

 **Ottenere il servizio immagini**

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

## <a name="how-do-i-update-winforms-ui"></a>Ricerca per categorie aggiornare l'interfaccia utente di WinForms?
 Aggiungere quanto segue al codice laddove appropriato per sostituire il caricamento non elaborato delle immagini. Modificare i valori per restituire bitmap e icone in base alle esigenze.

 **Istruzione using utile**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Ottenere il servizio immagini**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Ricerca per categorie usare i moniker di immagine in una nuova finestra degli strumenti?
 Il modello di progetto di pacchetto VSIX è stato aggiornato per Visual Studio 2015. Per creare una nuova finestra degli strumenti, fare clic con il pulsante destro del mouse sul progetto VSIX e scegliere **Aggiungi**  >  **nuovo elemento** (**CTRL** + **MAIUSC** + **a**). Nel nodo estendibilità per il linguaggio del progetto selezionare **finestra degli strumenti personalizzata**, assegnare un nome alla finestra degli strumenti e premere il pulsante **Aggiungi** .

 Questi sono i punti chiave per usare i moniker in una finestra degli strumenti. Seguire le istruzioni per ogni:

1. Scheda della finestra degli strumenti quando le schede sono sufficientemente piccole (usate anche nello **Ctrl**strumento di selezione della finestra della + **scheda** CTRL).

    Aggiungere questa riga al costruttore per la classe che deriva dal tipo **ToolWindowPane** :

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Comando per aprire la finestra degli strumenti.

    Nel file con *estensione vsct* per il pacchetto modificare il pulsante di comando della finestra degli strumenti:

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

   **Ricerca per categorie usare moniker di immagine in una finestra degli strumenti esistente?**

   L'aggiornamento di una finestra degli strumenti esistente per l'utilizzo dei moniker di immagine è simile alla procedura per la creazione di una nuova finestra degli strumenti.

   Questi sono i punti chiave per usare i moniker in una finestra degli strumenti. Seguire le istruzioni per ogni:

3. Scheda della finestra degli strumenti quando le schede sono sufficientemente piccole (usate anche nello **Ctrl**strumento di selezione della finestra della + **scheda** CTRL).

   1. Rimuovere queste righe (se esistenti) nel costruttore della classe che deriva dal tipo **ToolWindowPane** :

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Vedere Step #1 of the "Ricerca per categorie use image monikers in an New tool window?" precedente.

4. Comando per aprire la finestra degli strumenti.

   - Vedere Step #2 of the "Ricerca per categorie use image monikers in an New tool window?" precedente.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Ricerca per categorie usare moniker di immagine in un file con estensione vsct?
 Aggiornare il file con *estensione vsct* come indicato dalle righe commentate sotto:

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

 **Cosa accade se il file. vsct deve essere letto anche da versioni precedenti di Visual Studio?**

 Le versioni precedenti di Visual Studio non riconoscono il flag di comando **IconIsMoniker** . È possibile usare le immagini del servizio immagini nelle versioni di Visual Studio che la supportano, ma continuare a usare immagini obsolete nelle versioni precedenti di Visual Studio. A tale scopo, è necessario lasciare invariato il file con *estensione vsct* (e quindi compatibile con le versioni precedenti di Visual Studio) e creare un file CSV (valori delimitati da virgole) che esegue il mapping da coppie GUID/ID definite nell'elemento di un file con *estensione vsct* \<Bitmaps> alle coppie GUID/ID del moniker di immagine.

 Il formato del file CSV di mapping è il seguente:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Il file CSV viene distribuito con il pacchetto e il relativo percorso viene specificato dalla proprietà **IconMappingFilename** dell'attributo del pacchetto **ProvideMenuResource** :

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** è un percorso relativo con una radice implicita in $PackageFolder $ (come nell'esempio precedente) o un percorso assoluto con radice esplicita in una directory definita da una variabile di ambiente, ad esempio *@ "% UserProfile% \dir1\dir2\MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Ricerca per categorie porta un sistema di progetto?
 **Come fornire ImageMonikers per un progetto**

1. Implementare **VSHPROPID_SupportsIconMonikers** in **IVsHierarchy**del progetto e restituire true.

2. Implementare **VSHPROPID_IconMonikerImageList** (se il progetto originale usava **VSHPROPID_IconImgList**) o **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (se il progetto originale usava **VSHPROPID_IconHandle** e **VSHPROPID_OpenFolderIconHandle**).

3. Modificare l'implementazione del VSHPROPIDs originale per le icone per creare versioni "Legacy" delle icone se i punti di estensione li richiedono. **IVsImageService2** fornisce le funzionalità necessarie per ottenere tali icone

   **Requisiti aggiuntivi per le versioni dei progetti VB/C#**

   Implementare **VSHPROPID_SupportsIconMonikers** solo se si rileva che il progetto è la versione più **esterna**. In caso contrario, la versione più esterna effettiva potrebbe non supportare i moniker dell'immagine in realtà e la versione di base potrebbe "nascondere" immagini personalizzate.

   **Ricerca per categorie usare i moniker di immagine in CPS?**

   L'impostazione di immagini personalizzate in CPS (Common Project System) può essere eseguita manualmente o tramite un modello di elemento incluso in Project System Extensibility SDK.

   **Uso di Project System Extensibility SDK**

   Per personalizzare le immagini CPS, seguire le istruzioni [fornite in fornire icone personalizzate per il tipo di progetto/tipo di elemento](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) . Altre informazioni su CPS sono disponibili nella [documentazione sull'estendibilità del sistema di progetto di Visual Studio](https://github.com/Microsoft/VSProjectSystem)

   **Usare manualmente ImageMonikers**

4. Implementare ed esportare l'interfaccia **IProjectTreeModifier** nel sistema del progetto.

5. Determinare quale **KnownMoniker** o moniker dell'immagine personalizzata si vuole usare.

6. Nel metodo **ApplyModifications** , eseguire le operazioni seguenti nel metodo prima di restituire il nuovo albero, in modo simile all'esempio seguente:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Se si sta creando un nuovo albero, è possibile impostare le immagini personalizzate passando i moniker desiderati nel metodo viene NewTree, in modo simile all'esempio seguente:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Ricerca per categorie convertire da un'immagine reale a una striscia di immagini basata su moniker?
 **È necessario supportare HIMAGELISTs**

 Se è presente una striscia di immagine già esistente per il codice che si vuole aggiornare per usare il servizio immagini, ma si è vincolati da API che richiedono il passaggio di elenchi di immagini, è comunque possibile usufruire dei vantaggi del servizio immagini. Per creare un'immagine basata su moniker, attenersi alla procedura seguente per creare un manifesto da moniker esistenti.

1. Eseguire lo strumento **ManifestFromResources** e passargli l'elenco di immagini. Verrà generato un manifesto per la striscia.

   - Consigliato: specificare un nome non predefinito per il manifesto per adattarlo all'utilizzo.

2. Se si usa solo **KnownMonikers**, eseguire le operazioni seguenti:

   - Sostituire la \<Images> sezione del manifesto con \<Images/> .

   - Rimuovere tutti gli ID di immagine (qualsiasi elemento con \<imagestrip name> _ # #).

   - Consigliato: rinominare il simbolo di AssetsGuid e il simbolo della striscia dell'immagine in base all'utilizzo.

   - Sostituire ogni GUID di **ContainedImage**con $ (ImageCatalogGuid), sostituire l'ID di ogni **ContainedImage**con $ ( \<moniker> ) e aggiungere l'attributo External = "true" a ogni **ContainedImage**

       - \<moniker> deve essere sostituito con **KnownMoniker** che corrisponde all'immagine ma con "KnownMonikers". rimosso dal nome.

   - Aggiungere <Import manifest = "$ (ManifestFolder) \\<percorso dir di installazione relativo a * \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest"/ \*> nella parte superiore della \<Symbols> sezione.

       - Il percorso relativo è determinato dal percorso di distribuzione definito nella creazione dell'installazione per il manifesto.

3. Eseguire lo strumento **ManifestToCode** per generare wrapper in modo che il codice esistente disponga di un moniker che può usare per eseguire una query sul servizio immagini per l'elenco di immagini.

   - Consigliato: specificare nomi non predefiniti per i wrapper e gli spazi dei nomi per adattarne l'utilizzo.

4. Eseguire tutte le operazioni di aggiunta, creazione/distribuzione del programma di installazione e altre modifiche al codice per lavorare con il servizio immagini e i nuovi file.

   Manifesto di esempio che include immagini sia interne che esterne per vedere come dovrebbe apparire:

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

1. Determinare il set di **KnownMonikers** che corrispondono alle immagini nell'elenco di immagini oppure creare moniker personalizzati per le immagini nell'elenco di immagini.

2. Aggiornare il mapping usato per ottenere l'immagine in corrispondenza dell'indice richiesto nell'elenco di immagini per usare invece i moniker.

3. Aggiornare il codice per usare il servizio immagini per richiedere moniker tramite il mapping aggiornato. Questo potrebbe significare l'aggiornamento a **CrispImages** per il codice gestito o la richiesta di HBITMAPs o HICONs dal servizio immagini e il relativo passaggio per il codice nativo.

## <a name="testing-your-images"></a>Test delle immagini
 È possibile utilizzare lo strumento Visualizzatore libreria immagini per testare i manifesti dell'immagine per assicurarsi che tutti gli elementi vengano creati correttamente. È possibile trovare lo strumento in [Visual Studio 2015 SDK](visual-studio-sdk.md). La documentazione per questo strumento e altre informazioni sono disponibili [qui](./internals/vssdk-utilities.md?view=vs-2015&preserve-view=true).

## <a name="additional-resources"></a>Risorse aggiuntive

### <a name="samples"></a>Esempi
 Molti degli esempi di Visual Studio su GitHub sono stati aggiornati per illustrare come usare il servizio immagini come parte dei diversi punti di estendibilità di Visual Studio.

 Controllare [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) gli esempi più recenti.

### <a name="tooling"></a>Strumenti
 È stato creato un set di strumenti di supporto per il servizio immagini per semplificare la creazione o l'aggiornamento dell'interfaccia utente che interagisce con il servizio immagini. Per ulteriori informazioni su ogni strumento, consultare la documentazione fornita con gli strumenti di. Gli strumenti sono inclusi in [Visual Studio 2015 SDK](visual-studio-sdk.md).

 **ManifestFromResources**

 Lo strumento Manifest from Resources accetta un elenco di risorse immagine (PNG o XAML) e genera un file manifesto di immagine per l'uso di tali immagini con il servizio immagini.

 **ManifestToCode**

 Lo strumento Manifest to Code accetta un file manifesto di immagine e genera un file wrapper per fare riferimento ai valori del manifesto nei file di codice (C++, C# o VB) o *vsct* .

 **ImageLibraryViewer**

 Lo strumento Visualizzatore libreria immagini consente di caricare manifesti di immagini e di modificarli nello stesso modo in cui Visual Studio può verificare che il manifesto venga creato correttamente. L'utente può modificare sfondo, dimensioni, impostazioni DPI, Contrasto elevato e altre impostazioni. Vengono inoltre visualizzate le informazioni di caricamento per individuare gli errori nei manifesti e vengono visualizzate le informazioni sull'origine per ogni immagine nel manifesto.

## <a name="faq"></a>Domande frequenti

- Sono presenti dipendenze che è necessario includere durante il caricamento \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> ?

  - Impostare EmbedInteropTypes = "true" in tutte le DLL di interoperabilità.

- Ricerca per categorie distribuire un manifesto immagine con l'estensione?

  - Aggiungere il file con *estensione imagemanifest* al progetto.

  - Impostare "Includi in VSIX" su true.

- Sto aggiornando il sistema del progetto CPS. Cosa è successo a **ImageName** e **StockIconService**?

  - Questi sono stati rimossi quando CPS è stato aggiornato per l'uso dei moniker. Non è più necessario chiamare **StockIconService**, è sufficiente passare il **KnownMoniker** desiderato al metodo o alla proprietà usando il metodo di estensione **TOPROJECTSYSTEMTYPE ()** nelle utilità CPS. È possibile trovare un mapping da **ImageName** a **KnownMonikers** di seguito:

    |**ImageName**|**KnownMoniker**|
    |-|-|
    |ImageName. OfflineWebApp|KnownImageIds. Web|
    |ImageName. WebReferencesFolder|KnownImageIds. Web|
    |ImageName. OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName. ReferenceFolder|KnownImageIds. Reference|
    |ImageName. Reference|KnownImageIds. Reference|
    |ImageName. SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName. DiscoWebReference|KnownImageIds. DynamicDiscoveryDocument|
    |ImageName. Folder|KnownImageIds.FolderClosed|
    |ImageName. OpenFolder|KnownImageIds.FolderOpened|
    |ImageName. ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |ImageName. OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ImageName. ExcludedFile|KnownImageIds.HiddenFile|
    |ImageName. DependentFile|KnownImageIds.GenerateFile|
    |ImageName. MissingFile|KnownImageIds.DocumentWarning|
    |ImageName. WindowsForm|KnownImageIds. WindowsForm|
    |ImageName. WindowsUserControl|KnownImageIds. UserControl|
    |ImageName. WindowsComponent|KnownImageIds.ComponentFile|
    |Schema ImageName.Xml|Schema KnownImageIds.XML|
    |File ImageName.Xml|File KnownImageIds.XML|
    |ImageName. WebForm|KnownImageIds. Web|
    |ImageName. WebService|KnownImageIds. WebService|
    |ImageName. webusercontrol|KnownImageIds. webusercontrol|
    |ImageName. WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName. AspPage|KnownImageIds.ASPFile|
    |ImageName. GlobalApplicationClass|KnownImageIds. SettingsFile|
    |ImageName. webConfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName. StyleSheet|KnownImageIds. StyleSheet|
    |ImageName. ScriptFile|Script di KnownImageIds.JS|
    |ImageName. TextFile|KnownImageIds.Document|
    |ImageName. SettingsFile|KnownImageIds. Settings|
    |ImageName. resources|KnownImageIds.DocumentGroup|
    |ImageName. bitmap|KnownImageIds. image|
    |ImageName. Icon|KnownImageIds. IconFile|
    |ImageName. image|KnownImageIds. image|
    |ImageName. ImageMap|KnownImageIds.ImageMapFile|
    |ImageName. XWorld|KnownImageIds.XWorldFile|
    |ImageName. audio|KnownImageIds. Sound|
    |ImageName. video|KnownImageIds. Media|
    |ImageName.Cab|Progetto KnownImageIds.CAB|
    |ImageName. jar|KnownImageIds. JARFile|
    |ImageName. DataEnvironment|KnownImageIds. DataTable|
    |ImageName. PreviewFile|KnownImageIds. report|
    |ImageName. DanglingReference|KnownImageIds.ReferenceWarning|
    |ImageName. XsltFile|KnownImageIds. XSLTransform|
    |ImageName. Cursor|KnownImageIds. CursorFile|
    |ImageName. AppDesignerFolder|KnownImageIds. Property|
    |ImageName. Data|KnownImageIds. database|
    |ImageName. Application|KnownImageIds. Application|
    |ImageName. DataSet|KnownImageIds.DatabaseGroup|
    |ImageName. pfx|KnownImageIds. Certificate|
    |ImageName. snk|KnownImageIds. Rule|
    |ImageName. VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName. CSharpProject|KnownImageIds.CSProjectNode|
    |ImageName. Empty|KnownImageIds. blank|
    |ImageName. MissingFolder|KnownImageIds.FolderOffline|
    |ImageName. SharedImportReference|KnownImageIds.SharedProject|
    |ImageName. SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName. SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName. SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName. CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName. VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Sto aggiornando il provider dell'elenco di completamento. Quali **KnownMonikers** corrispondono ai valori **StandardGlyphGroup** e **StandardGlyph** precedenti?

    |Nome|Nome|Nome|
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
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
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
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
    |GlyphAssembly||Informazioni di riferimento|
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
    |GlyphJSharpDocument||Documento|
    |GlyphForwardType||GoToNext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||CallFrom|
    |GlyphWarning||StatusWarning|
    |GlyphMaybeReference||QuestionMark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||Xmldescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|