---
title: Servizio immagini e catalogo | Microsoft Docs
description: Questo articolo contiene indicazioni e procedure consigliate per l'adozione del Visual Studio Image Service e del Catalogo immagini.
ms.custom: SEO-VS-2020
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 78c029fc6b010d53d819d4b3c91efff714717699
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626201"
---
# <a name="image-service-and-catalog"></a>Servizio immagini e catalogo
Questo manuale contiene indicazioni e procedure consigliate per l'adozione del servizio Visual Studio e del catalogo immagini introdotto nel Visual Studio 2015.

 Il servizio immagini introdotto in Visual Studio 2015 consente agli sviluppatori di ottenere le immagini migliori per il dispositivo e il tema scelto dall'utente per visualizzare l'immagine, incluso il tema corretto per il contesto in cui vengono visualizzate. L'adozione del servizio immagini consente di eliminare i principali problemi relativi alla manutenzione degli asset, al ridimensionamento HDPI e ai relativi argomenti.

|**Problemi attuali**|**Soluzioni**|
|-|-|
|Fusione dei colori di sfondo|Fusione alfa incorporata|
|Immagini a sfondo (alcune)|Metadati del tema|
|Contrasto elevato modalità|Risorse Contrasto elevato alternative|
|Sono necessarie più risorse per modalità DPI diverse|Risorse selezionabili con fallback basato su vettori|
|Duplicare le immagini|Un identificatore per ogni concetto di immagine|

 Perché adottare il servizio immagini?

- Ottenere sempre l'immagine più recente "pixel-perfect" da Visual Studio

- È possibile inviare e usare immagini personalizzate

- Non è necessario testare le immagini quando Windows nuovo ridimensionamento DPI

- Risolvere i vecchi ostacoli dell'architettura nelle implementazioni

  La barra Visual Studio della shell prima e dopo l'uso del servizio immagini:

  ![Servizio immagini prima e dopo](../extensibility/media/image-service-before-and-after.png "Servizio immagini prima e dopo")

## <a name="how-it-works"></a>Funzionamento
 Il servizio immagini può fornire un'immagine bitmap adatta a qualsiasi framework dell'interfaccia utente supportato:

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Diagramma di flusso del servizio immagini

  ![Diagramma di flusso del servizio immagini](../extensibility/media/image-service-flow-diagram.png "Diagramma di flusso del servizio immagini")

  **Moniker di immagine**

  Un moniker di immagine (o moniker breve) è una coppia GUID/ID che identifica in modo univoco un asset di immagine o un asset dell'elenco immagini nella raccolta immagini.

  **Moniker noti**

  Set di moniker di immagine contenuti nel Visual Studio Image Catalog e utilizzabili pubblicamente da qualsiasi Visual Studio componente o estensione.

  **File manifesto dell'immagine**

  I file manifesto dell'immagine (con estensione *imagemanifest)* sono file XML che definiscono un set di asset di immagine, i moniker che rappresentano tali asset e l'immagine o le immagini reali che rappresentano ogni asset. I manifesti di immagini possono definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Sono inoltre disponibili attributi che possono essere impostati sull'asset o sulle singole immagini dietro ogni asset per modificare quando e come tali asset vengono visualizzati.

  **Schema del manifesto dell'immagine**

  Un manifesto completo dell'immagine è simile al seguente:

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

 Come supporto per la leggibilità e la manutenzione, il manifesto dell'immagine può usare simboli per i valori degli attributi. I simboli sono definiti nel modo seguente:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Sottoelemento**|**Definition**|
|-|-|
|Importa|Importa i simboli del file manifesto specificato da usare nel manifesto corrente|
|Guid|Il simbolo rappresenta un GUID e deve corrispondere alla formattazione GUID|
|ID|Il simbolo rappresenta un ID e deve essere un numero intero non negativo|
|string|Il simbolo rappresenta un valore stringa arbitrario|

 Ai simboli viene fatto distinzione tra maiuscole e minuscole e viene fatto riferimento tramite la sintassi $(symbol-name):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Alcuni simboli sono predefiniti per tutti i manifesti. Possono essere usati nell'attributo URI dell'elemento o per fare riferimento \<Source> ai percorsi nel computer \<Import> locale.

|**Simbolo**|**Descrizione**|
|-|-|
|CommonProgramFiles|Valore della variabile di ambiente %CommonProgramFiles%|
|Localappdata|Valore della variabile di ambiente %LocalAppData%|
|ManifestFolder|Cartella contenente il file manifesto|
|Mydocuments|Percorso completo della cartella Documenti dell'utente corrente|
|ProgramFiles|Valore della variabile di ambiente %ProgramFiles%|
|Sistema|Cartella *Windows\System32*|
|Windir|Valore della variabile di ambiente %WinDir%|

 **Immagine**

 \<Image>L'elemento definisce un'immagine a cui un moniker può fare riferimento. Il GUID e l'ID insieme formano il moniker dell'immagine. Il moniker per l'immagine deve essere univoco nell'intera raccolta immagini. Se più immagini hanno un moniker specificato, la prima rilevata durante la compilazione della libreria è quella mantenuta.

 Deve contenere almeno un'origine. Le origini indipendenti dalla dimensione offrono risultati ottimali in un'ampia gamma di dimensioni, ma non sono necessarie. Se al servizio viene richiesta un'immagine di dimensioni non definite nell'elemento e non esiste un'origine indipendente dalla dimensione, il servizio sceglierà l'origine specifica delle dimensioni migliori e la scalerà fino alle dimensioni \<Image> richieste.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Attributo**|**Definition**|
|-|-|
|Guid|[Obbligatorio] Parte GUID del moniker dell'immagine|
|ID|[Obbligatorio] Parte ID del moniker dell'immagine|
|AllowColorInversion|[Facoltativo, valore predefinito true] Indica se i colori dell'immagine possono essere invertiti a livello di codice quando vengono usati su uno sfondo scuro.|

 **Origine**

 \<Source>L'elemento definisce un singolo asset di origine dell'immagine (XAML e PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Attributo**|**Definition**|
|-|-|
|Uri|[Obbligatorio] URI che definisce la posizione da cui è possibile caricare l'immagine. I possibili valori sono i seguenti:<br /><br /> - URI [di tipo Pack](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) che usa l'application:/// locale<br />- Riferimento assoluto alle risorse del componente<br />- Percorso di un file contenente una risorsa nativa|
|Sfondo|[Facoltativo] Indica il tipo di sfondo che l'origine deve usare.<br /><br /> I possibili valori sono i seguenti:<br /><br /> *Luce:* L'origine può essere usata su uno sfondo chiaro.<br /><br /> *Scuro:* L'origine può essere usata su uno sfondo scuro.<br /><br /> *HighContrast:* L'origine può essere usata in qualsiasi sfondo in Contrasto elevato predefinita.<br /><br /> *HighContrastLight:* L'origine può essere usata su uno sfondo chiaro in Contrasto elevato predefinita.<br /><br /> *HighContrastDark:* L'origine può essere usata su uno sfondo scuro in Contrasto elevato predefinita.<br /><br /> Se l'attributo Background viene omesso, l'origine può essere usata in qualsiasi sfondo.<br /><br /> Se Background è *Light,* *Dark,* *HighContrastLight* o *HighContrastDark,* i colori dell'origine non vengono mai invertiti. Se Background viene omesso o impostato su *HighContrast,* l'inversione dei colori dell'origine è controllata **dall'attributo AllowColorInversion** dell'immagine.|

Un \<Source> elemento può avere esattamente uno dei sottoelementi facoltativi seguenti:

|**elemento**|**Attributi (tutti obbligatori)**|**Definition**|
|-|-|-|
|\<Size>|Valore|L'origine verrà usata per le immagini delle dimensioni specificate (in unità dispositivo). L'immagine sarà quadrata.|
|\<SizeRange>|MinSize, MaxSize|L'origine verrà usata per le immagini da MinSize a MaxSize (in unità dispositivo) in modo inclusivo. L'immagine sarà quadrata.|
|\<Dimensions>|Larghezza, altezza|L'origine verrà usata per le immagini della larghezza e dell'altezza specificate (in unità dispositivo).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|L'origine verrà usata per le immagini dalla larghezza/altezza minima alla larghezza/altezza massima (in unità dispositivo) in modo inclusivo.|

 Un \<Source> elemento può anche avere un sottoelemento facoltativo, che definisce un che viene caricato da un assembly nativo \<NativeResource> anziché da un assembly \<Source> gestito.

```xml
<NativeResource Type="type" ID="int" />
```

|**Attributo**|**Definition**|
|-|-|
|Tipo|[Obbligatorio] Tipo della risorsa nativa, XAML o PNG|
|ID|[Obbligatorio] Parte dell'ID intero della risorsa nativa|

 **Imagelist**

 \<ImageList>L'elemento definisce una raccolta di immagini che possono essere restituite in una singola striscia. La striscia viene compilata su richiesta, in base alle esigenze.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Attributo**|**Definition**|
|-|-|
|Guid|[Obbligatorio] Parte GUID del moniker dell'immagine|
|ID|[Obbligatorio] Parte ID del moniker dell'immagine|
|Esterno|[Facoltativo, valore predefinito false] Indica se il moniker dell'immagine fa riferimento a un'immagine nel manifesto corrente.|

 Il moniker per l'immagine contenuta non deve fare riferimento a un'immagine definita nel manifesto corrente. Se non è possibile trovare l'immagine contenuta nella raccolta immagini, al suo posto verrà usata un'immagine segnaposto vuota.

## <a name="using-the-image-service"></a>Uso del servizio immagini

### <a name="first-steps-managed"></a>Primi passaggi (gestiti)
 Per usare il servizio immagini, è necessario aggiungere al progetto riferimenti ad alcuni o a tutti gli assembly seguenti:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Obbligatorio se si usa il catalogo immagini incorporato **KnownMonikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Obbligatorio se si **usanoImage e** **ImageThemingUtilities nell'interfaccia** utente WPF.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Obbligatorio se si usano **i tipi ImageMoniker** **e ImageAttributes.**

  - **EmbedInteropTypes** deve essere impostato su true.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Obbligatorio se si usa il **tipo IVsImageService2.**

  - **EmbedInteropTypes** deve essere impostato su true.

- *Microsoft.VisualStudio.Utilities.dll*

  - Obbligatorio se si usa **BrushToColorConverter per** **ImageThemingUtilities.ImageBackgroundColor** nell'interfaccia utente WPF.

- *Microsoft.VisualStudio.Shell. \<VSVersion> . 0*

  - Obbligatorio se si usa il **tipo IVsUIObject.**

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Obbligatorio se si usano gli helper dell'interfaccia utente correlati a WinForms.

  - **EmbedInteropTypes** deve essere impostato su true

### <a name="first-steps-native"></a>Primi passaggi (nativi)
 Per usare il servizio immagini, è necessario includere alcune o tutte le intestazioni seguenti nel progetto:

- **KnownImageIds.h**

  - Obbligatorio se si usa il catalogo immagini predefinito **KnownMonikers**, ma non è possibile usare il tipo **ImageMoniker,** ad esempio quando si restituiscono valori da **chiamate IVsHierarchy GetGuidProperty** o **GetProperty.**

- **KnownMonikers.h**

  - Obbligatorio se si usa il catalogo immagini incorporato **KnownMonikers**.

- **ImageParameters140.h**

  - Obbligatorio se si usano **i tipi ImageMoniker** **e ImageAttributes.**

- **VSShell140.h**

  - Obbligatorio se si usa il **tipo IVsImageService2.**

- **ImageThemingUtilities.h**

  - Obbligatorio se non è possibile consentire al servizio immagini di gestire i loro dati.

  - Non usare questa intestazione se il servizio immagini è in grado di gestire il testo dell'immagine.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Obbligatorio se si usano gli helper DPI per ottenere il valore DPI corrente.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Obbligatorio se si usano gli helper di riconoscimento DPI per ottenere il valore DPI corrente.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Ricerca per categorie scrivere una nuova interfaccia utente WPF?

1. Per iniziare, aggiungere al progetto i riferimenti all'assembly necessari nella sezione dei primi passaggi precedenti. Non è necessario aggiungerli tutti, quindi aggiungere solo i riferimenti necessari. Nota: se si usa o si ha accesso a **Colori** invece di Pennelli **,** è possibile ignorare il riferimento a **Utilità**, poiché non sarà necessario il convertitore.

2. Selezionare l'immagine desiderata e ottenere il relativo moniker. Usare un **oggetto KnownMoniker** oppure usare il proprio se si dispone di immagini e moniker personalizzati.

3. **AggiungereImages a** XAML. Vedere l'esempio seguente.

4. Impostare la **proprietà ImageThemingUtilities.ImageBackgroundColor** nella gerarchia dell'interfaccia utente. Questa proprietà deve essere impostata nella posizione in cui è noto il colore di sfondo, non necessariamente **inImageImage.** Vedere l'esempio seguente.

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

 **Ricerca per categorie'interfaccia utente WPF esistente?**

 L'aggiornamento dell'interfaccia utente WPF esistente è un processo relativamente semplice costituito da tre passaggi di base:

1. Sostituire tutti \<Image> gli elementi nell'interfaccia utente con \<CrispImage> elementi .

2. Modificare tutti gli attributi source in Attributi moniker.

    - Se l'immagine non cambia mai e si usa **KnownMonikers,** associare in modo statico tale proprietà a **KnownMoniker**. Vedere l'esempio precedente.

    - Se l'immagine non cambia mai e si usa un'immagine personalizzata, eseguire l'associazione statica al moniker personale.

    - Se l'immagine può cambiare, associare l'attributo Moniker a una proprietà di codice che notifica le modifiche alle proprietà.

3. In un punto qualsiasi della gerarchia dell'interfaccia utente impostare **ImageThemingUtilities.ImageBackgroundColor** per assicurarsi che l'inversione del colore funzioni correttamente.

    - Questa operazione potrebbe richiedere l'uso della **classe BrushToColorConverter.** Vedere l'esempio precedente.

## <a name="how-do-i-update-win32-ui"></a>Ricerca per categorie'interfaccia utente Win32?
 Aggiungere quanto segue al codice, laddove appropriato, per sostituire il caricamento non elaborato delle immagini. Impostare i valori per la restituzione di HBITMAP rispetto a HICON e HIMAGELIST in base alle esigenze.

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

## <a name="how-do-i-update-winforms-ui"></a>Ricerca per categorie'interfaccia utente di WinForms?
 Aggiungere quanto segue al codice, laddove appropriato, per sostituire il caricamento non elaborato delle immagini. Impostare i valori per restituire bitmap e icone in base alle esigenze.

 **Istruzione using utile**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Ottenere il servizio immagini**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Richiedere l'immagine**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Ricerca per categorie usare moniker di immagine in una nuova finestra degli strumenti?
 Il modello di progetto pacchetto VSIX è stato aggiornato per Visual Studio 2015. Per creare una nuova finestra degli strumenti, fare clic con il pulsante destro del mouse sul progetto VSIX e scegliere **Aggiungi**  >  **nuovo elemento** (**CTRL** + **MAIUSC** + **A**). Nel nodo Estendibilità per il linguaggio del progetto selezionare **Finestra degli** strumenti personalizzata, assegnare un nome alla finestra degli strumenti e premere il **pulsante** Aggiungi.

 Questi sono i punti chiave in cui usare i moniker in una finestra degli strumenti. Seguire le istruzioni per ogni:

1. La scheda della finestra degli strumenti quando le schede sono sufficientemente piccole (usate anche nel commutatore della finestra **CTRL** +  TAB).

    Aggiungere questa riga al costruttore per la classe che deriva dal **tipo ToolWindowPane:**

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Comando per aprire la finestra degli strumenti.

    Nel file *con estensione vsct* per il pacchetto modificare il pulsante di comando della finestra degli strumenti:

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

   L'aggiornamento di una finestra degli strumenti esistente per l'uso dei moniker delle immagini è simile alla procedura per la creazione di una nuova finestra degli strumenti.

   Questi sono i punti chiave in cui usare i moniker in una finestra degli strumenti. Seguire le istruzioni per ogni:

3. La scheda della finestra degli strumenti quando le schede sono sufficientemente piccole (usate anche nel commutatore della finestra **CTRL** +  TAB).

   1. Rimuovere queste righe (se presenti) nel costruttore per la classe che deriva dal **tipo ToolWindowPane:**

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Vedere il passaggio #1 "Usare Ricerca per categorie moniker di immagine in una nuova finestra degli strumenti?" precedente.

4. Comando per aprire la finestra degli strumenti.

   - Vedere il passaggio #2 "Usare Ricerca per categorie moniker immagine in una nuova finestra degli strumenti?" precedente.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Ricerca per categorie usare moniker di immagine in un file con estensione vsct?
 Aggiornare il file *con estensione vsct* come indicato dalle righe commentate seguenti:

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

 **Cosa succede se il file con estensione vsct deve essere letto anche dalle versioni precedenti di Visual Studio?**

 Le versioni precedenti Visual Studio non riconoscono il flag **di comando IconIsMoniker.** È possibile usare le immagini del servizio immagini nelle versioni di Visual Studio che lo supportano, ma continuare a usare immagini di vecchio stile nelle versioni precedenti di Visual Studio. A tale scopo, è necessario lasciare invariato il file con estensione *vsct* (e quindi compatibile con le versioni precedenti di Visual Studio) e creare un file CSV (valori delimitati da virgole) che esegue il mapping da coppie GUID/ID definite nell'elemento di un file *vsct* alle coppie \<Bitmaps> GUID/ID del moniker di immagini.

 Il formato del file CSV di mapping è:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Il file CSV viene distribuito con il pacchetto e il relativo percorso viene specificato dalla **proprietà IconMappingFilename** dell'attributo del pacchetto **ProvideMenuResource:**

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** è un percorso relativo con radice implicita in $PackageFolder$ (come nell'esempio precedente) o un percorso assoluto con radice esplicita in una directory definita da una variabile di ambiente, ad esempio *@"%UserProfile%\dir1\dir2\MyMappingFile.csv".*

## <a name="how-do-i-port-a-project-system"></a>Ricerca per categorie un sistema di progetto?
 **Come fornire ImageMonikers per un progetto**

1. Implementare **VSHPROPID_SupportsIconMonikers** su **IVsHierarchy del progetto** e restituire true.

2. Implementare **VSHPROPID_IconMonikerImageList** (se il progetto originale usava **VSHPROPID_IconImgList**) o **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (se  il progetto originale usava VSHPROPID_IconHandle **e VSHPROPID_OpenFolderIconHandle**).

3. Modificare l'implementazione dei VSHPROPID originali per le icone per creare versioni "legacy" delle icone se i punti di estensione le richiedono. **IVsImageService2 offre** le funzionalità necessarie per ottenere tali icone

   **Requisiti aggiuntivi per VB/C# di progetto**

   Implementare **VSHPROPID_SupportsIconMonikers** solo se si rileva che il progetto è il **gusto più esterno.** In caso contrario, la flavor più esterna effettiva potrebbe non supportare i moniker delle immagini in realtà e il gusto di base potrebbe effettivamente "nascondere" le immagini personalizzate.

   **Ricerca per categorie usare moniker di immagine in CPS?**

   L'impostazione di immagini personalizzate in CPS (Common Project System) può essere eseguita manualmente o tramite un modello di elemento fornito con Project System Extensibility SDK.

   **Uso di Project SDK di estendibilità del sistema**

   Seguire le istruzioni in [Specificare icone personalizzate per il tipo Project/elemento](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) per personalizzare le immagini CPS. Altre informazioni su CPS sono disponibili nella Visual Studio Project [di estendibilità del sistema](https://github.com/Microsoft/VSProjectSystem)

   **Usare manualmente ImageMonikers**

4. Implementare ed esportare **l'interfaccia IProjectTreeModifier** nel sistema del progetto.

5. Determinare **quale moniker di** immagini knownmoniker o personalizzato si vuole usare.

6. Nel metodo **ApplyModifications** eseguire le operazioni seguenti in un punto qualsiasi del metodo prima di restituire il nuovo albero, come nell'esempio seguente:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Se si crea un nuovo albero, è possibile impostare le immagini personalizzate passando i moniker desiderati al metodo NewTree, simile all'esempio seguente:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Ricerca per categorie da una striscia di immagini reale a una striscia di immagini basata su moniker?
 **È necessario supportare HIMAGELISTs**

 Se è già presente una striscia di immagini per il codice che si vuole aggiornare per usare il servizio immagini, ma si è vincolati da API che richiedono il passaggio di elenchi di immagini, è comunque possibile ottenere i vantaggi del servizio immagini. Per creare una striscia di immagini basata su moniker, seguire questa procedura per creare un manifesto da moniker esistenti.

1. Eseguire lo **strumento ManifestFromResources** passandolo alla striscia di immagini. Verrà generato un manifesto per la striscia.

   - Consigliato: specificare un nome non predefinito per il manifesto in base al relativo utilizzo.

2. Se si usa solo **KnownMonikers,** eseguire le operazioni seguenti:

   - Sostituire la \<Images> sezione del manifesto con \<Images/> .

   - Rimuovere tutti gli ID immagine secondaria (qualsiasi elemento \<imagestrip name> con _##).

   - Consigliato: rinominare il simbolo AssetsGuid e il simbolo della striscia di immagini in base al relativo utilizzo.

   - Sostituire ogni GUID di **ContainedImage** con $(ImageCatalogGuid), sostituire ogni ID di **ContainedImage** con $( ) e aggiungere l'attributo \<moniker> External="true" a ogni **ContainedImage**

       - \<moniker> deve essere sostituito con **KnownMoniker che** corrisponde all'immagine, ma con "KnownMonikers". rimosso dal nome.

   - Aggiungere <Import Manifest="$(ManifestFolder) \\<Relative install dir path to * \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest" /> all'inizio \* della \<Symbols> sezione.

       - Il percorso relativo è determinato dal percorso di distribuzione definito nella creazione del programma di installazione per il manifesto.

3. Eseguire lo **strumento ManifestToCode** per generare wrapper in modo che il codice esistente abbia un moniker che può usare per eseguire query sul servizio immagini per la striscia di immagini.

   - Consigliato: specificare nomi non predefiniti per i wrapper e gli spazi dei nomi in base al relativo utilizzo.

4. Eseguire tutte le operazioni di aggiunta, creazione/distribuzione e altre modifiche del codice per usare il servizio immagini e i nuovi file.

   Manifesto di esempio che include immagini interne ed esterne per vedere come dovrebbe apparire:

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

1. Determinare il set **di oggetti KnownMonikers** che corrispondono alle immagini nella striscia di immagini oppure creare moniker personalizzati per le immagini nella striscia immagini.

2. Aggiornare il mapping usato per ottenere l'immagine in corrispondenza dell'indice richiesto nella striscia di immagini per usare invece i moniker.

3. Aggiornare il codice per usare il servizio immagini per richiedere moniker tramite il mapping aggiornato. Ciò potrebbe significare l'aggiornamento a **CrispImages** per il codice gestito o la richiesta di HBITMAP o HICON dal servizio immagini e il passaggio di tali immagini per il codice nativo.

## <a name="testing-your-images"></a>Test delle immagini
 È possibile usare lo strumento Visualizzatore libreria di immagini per testare i manifesti dell'immagine per assicurarsi che tutto sia stato creato correttamente. È possibile trovare lo strumento in [Visual Studio 2015 SDK.](visual-studio-sdk.md) La documentazione per questo strumento e altri strumenti è disponibile [qui.](./internals/vssdk-utilities.md?view=vs-2015&preserve-view=true)

## <a name="additional-resources"></a>Risorse aggiuntive

### <a name="samples"></a>Esempi
 Diversi esempi di Visual Studio su GitHub sono stati aggiornati per illustrare come usare il servizio immagini come parte di vari Visual Studio punti di estendibilità.

 Controllare [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) gli esempi più recenti.

### <a name="tooling"></a>Strumenti
 È stato creato un set di strumenti di supporto per Il servizio immagini per facilitare la creazione/aggiornamento dell'interfaccia utente che funziona con Il servizio immagini. Per altre informazioni su ogni strumento, vedere la documentazione fornita con gli strumenti. Gli strumenti sono inclusi nell'SDK [Visual Studio 2015.](visual-studio-sdk.md)

 **ManifestFromResources**

 Lo Manifest from Resources usa un elenco di risorse immagine (PNG o XAML) e genera un file manifesto dell'immagine per l'uso di tali immagini con il servizio immagini.

 **ManifestToCode**

 Lo strumento Manifest to Code accetta un file manifesto dell'immagine e genera un file wrapper per fare riferimento ai valori del manifesto nel codice (C++, C# o VB) o nei file con estensione *vsct.*

 **ImageLibraryViewer**

 Lo strumento Visualizzatore libreria di immagini può caricare i manifesti delle immagini e consente all'utente di modificarli nello stesso modo Visual Studio per assicurarsi che il manifesto venga creato correttamente. L'utente può modificare lo sfondo, le dimensioni, l'impostazione DPI, Contrasto elevato e altre impostazioni. Visualizza anche le informazioni di caricamento per trovare gli errori nei manifesti e le informazioni sull'origine per ogni immagine nel manifesto.

## <a name="faq"></a>Domande frequenti

- Sono presenti dipendenze che è necessario includere durante il caricamento \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> di ?

  - Impostare EmbedInteropTypes="true" in tutte le DLL di interoperabilità.

- Ricerca per categorie distribuire un manifesto dell'immagine con l'estensione?

  - Aggiungere il file *con estensione imagemanifest* al progetto.

  - Impostare "Includi in VSIX" su True.

- È in corso l'aggiornamento di CPS Project System. Cosa è successo **a ImageName** **e StockIconService?**

  - Questi sono stati rimossi quando CPS è stato aggiornato per l'uso dei moniker. Non è più necessario chiamare **StockIconService**, è sufficiente passare il **KnownMoniker** desiderato al metodo o alla proprietà usando il metodo di estensione **ToProjectSystemType()** nelle utilità CPS. È possibile trovare un mapping da **ImageName** a **KnownMonikers di** seguito:

    |**ImageName**|**KnownMoniker**|
    |-|-|
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
    |ImageName.SettingsFile|KnownImageIds. Impostazioni|
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

  - È in corso l'aggiornamento del provider dell'elenco di completamento. Quali **oggetti KnownMonikers** corrispondono ai valori **standard StandardGlyphGroup** e **StandardGlyph?**

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
    |Eccezione GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |Eccezione GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |Eccezione GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |Eccezione GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |Eccezione GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |Eccezione GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInternal|InterfacciaInternal|
    |GlyphGroupInterface|GlyphItemFriend|InterfacciaInternal|
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
    |GlyphGroupMethod|GlyphItemPublic|MetodoPublic|
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupMethod|GlyphItemShortcut|MetodoShortcut|
    |GlyphGroupOverload|GlyphItemPublic|MetodoPublic|
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
    |GlyphGroupNamespace|GlyphItemInternal|Spazio dei nomiInternal|
    |GlyphGroupNamespace|GlyphItemFriend|Spazio dei nomiInternal|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|Spazio dei nomiShortcut|
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
    |GlyphGroupStruct|GlyphItemInternal|StrutturaInternal|
    |GlyphGroupStruct|GlyphItemFriend|StrutturaInternal|
    |GlyphGroupStruct|GlyphItemProtected|StrutturaProtezione|
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
    |GlyphGroupJSharpMethod|GlyphItemPublic|MetodoPublic|
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
    |GlyphGroupJSharpNamespace|GlyphItemInternal|Spazio dei nomiInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|Spazio dei nomiInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|Spazio dei nomiShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfacciaInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfacciaInternal|
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||Riferimento|
    |GlyphLibrary||Libreria|
    |GlyphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Finestra di dialogo|
    |GlyphOpenFolder||FolderOpened|
    |GlyphClosedFolder||FolderClosed|
    |GlifoArrow||GoToNext|
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
    |GlyphMaybeReference||Questionmark|
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
    |GlifoXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|
