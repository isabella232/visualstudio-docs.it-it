---
title: Visualizzatore della libreria di immagini - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707741"
---
# <a name="image-library-viewer"></a>Visualizzatore della libreria di immagini
Lo strumento Visualizzatore libreria di immagini di Visual Studio può caricare ed eseguire ricerche nei manifesti delle immagini, consentendo all'utente di modificarli nello stesso modo in cui farebbe Visual Studio. L'utente può modificare lo sfondo, le dimensioni, dPI, contrasto elevato e altre impostazioni. Lo strumento visualizza anche le informazioni di caricamento per ogni manifesto dell'immagine e visualizza le informazioni sull'origine per ogni immagine nel manifesto dell'immagine. Questo strumento è utile per:

1. Diagnostica degli errori

2. Verifica della corretta impostazione degli attributi nei manifesti immagine personalizzatiEnsuring attributes are set correctly in custom image manifests

3. Ricerca di immagini nel Catalogo immagini di Visual Studio in modo che un'estensione di Visual Studio possa usare immagini che si adattano allo stile di Visual StudioSearching for images in the Visual Studio Image Catalog so that a Visual Studio extension can use images that fit the style of Visual Studio

   ![Immagine principale del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-hero.png "Immagine principale del visualizzatore della libreria di immagini")

   **Moniker immagine**

   Un moniker di immagini (o moniker in breve) è una coppia GUID:ID che identifica in modo univoco una risorsa immagine o un asset di immagini nella raccolta immagini.

   **File manifesto immagine**

   I file manifesto dell'immagine (con estensione imagemanifest) sono file XML che definiscono un set di risorse immagine, i moniker che rappresentano tali risorse e l'immagine o le immagini reali che rappresentano ogni risorsa. I manifesti immagine possono definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Inoltre, ci sono attributi che possono essere impostati sulla risorsa o sulle singole immagini dietro ogni risorsa per modificare quando e come tali risorse vengono visualizzate.

   **Schema del manifesto dell'immagine**

   Un manifesto completo dell'immagine è simile al seguente:A complete image manifest looks like this:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
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
|Importa|Importa i simboli del file manifesto specificato per l'utilizzo nel manifesto corrente.|
|Guid|Il simbolo rappresenta un GUID e deve corrispondere alla formattazione GUID.|
|ID|Il simbolo rappresenta un ID e deve essere un numero intero non negativo.|
|string|Il simbolo rappresenta un valore stringa arbitrario.|

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
|System|La cartella Windows-System32|
|Windir|Il valore della variabile di ambiente %WinDir%|

 **Immagine**

 L'elemento \<> Image definisce un'immagine a cui fa riferimento un moniker. Il GUID e l'ID presi insieme formano il moniker dell'immagine. Il moniker per l'immagine deve essere univoco nell'intera libreria di immagini. Se più di un'immagine ha un dato moniker, la prima rilevata durante la creazione della libreria è quella che viene mantenuta.

 Deve contenere almeno una fonte. Anche se le sorgenti neutre di dimensione daranno i migliori risultati in un'ampia gamma di dimensioni, non sono necessarie. Se al servizio viene richiesta un'immagine di \<una dimensione non definita nell'elemento Image> e non esiste un'origine neutra per le dimensioni, il servizio sceglierà la fonte specifica per le dimensioni migliori e la scalerà in base alle dimensioni richieste.

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
|Uri|[Obbligatorio] URI che definisce la posizione da cui è il caricamento dell'immagine. I possibili valori sono i seguenti:<br /><br /> - Un [URI di tipo Pack](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) che utilizza l'autorità application:///<br /><br /> - Un riferimento di risorsa componente assoluto- An absolute component resource reference<br /><br /> - Un percorso a un file contenente una risorsa nativa- A path to a file containing a native resource|
|Background|[Facoltativo] Indica il tipo di sfondo in cui deve essere utilizzata l'origine.<br /><br /> I possibili valori sono i seguenti:<br /><br /> - *Luce*: La sorgente può essere utilizzata su uno sfondo chiaro.<br /><br /> - *Scuro*: La sorgente può essere utilizzata su uno sfondo scuro.<br /><br /> - *HighContrast*: La sorgente può essere utilizzata su qualsiasi sfondo in modalità Contrasto elevato.<br /><br /> - *HighContrastLight*: La sorgente può essere utilizzata su uno sfondo chiaro in modalità Contrasto elevato.<br /><br /> -*HighContrastDark*: La sorgente può essere utilizzata su uno sfondo scuro in modalità Contrasto elevato.<br /><br /> Se l'attributo **Background** viene omesso, l'origine può essere utilizzata in qualsiasi sfondo.<br /><br /> Se **Sfondo** è *Chiaro*, *Scuro*, *HighContrastLight*o *HighContrastDark*, i colori della sorgente non vengono mai invertiti. Se **Sfondo** viene omesso o impostato su *HighContrast*, l'inversione dei colori dell'origine è controllata dall'attributo **AllowColorInversion** dell'immagine.|

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

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 **Convalida di un manifesto dell'immagine personalizzatoValidating a custom image manifest**

 Per creare un manifesto personalizzato, è consigliabile usare lo strumento ManifestFromResources per generare automaticamente il manifesto. Per convalidare il manifesto personalizzato, avviare il Visualizzatore raccolta immagini e selezionare Percorsi > file... per aprire la finestra di dialogo Directory di ricerca. Lo strumento utilizzerà le directory di ricerca per caricare i manifesti di immagine, ma li utilizzerà anche per trovare i file DLL che contengono le immagini in un manifesto, quindi assicurarsi di includere le directory manifesto e DLL in questa finestra di dialogo.

 ![Ricerca del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-search.png "Ricerca del visualizzatore della libreria di immagini")

 Fare clic su **Aggiungi...** per selezionare nuove directory di ricerca in cui cercare i manifesti e le DLL corrispondenti. Lo strumento ricorderà queste directory di ricerca e possono essere attivate o disattivate selezionando o deselezionando una directory.

 Per impostazione predefinita, lo strumento tenterà di trovare la directory di installazione di Visual Studio e aggiungere tali directory all'elenco delle directory di ricerca. È possibile aggiungere manualmente le directory che lo strumento non trova.

 Una volta caricati tutti i manifesti, lo strumento può essere utilizzato per attivare o disattivare i colori di **sfondo,** **DPI,** **contrasto elevato**o **grayscaling** per le immagini in modo che un utente possa ispezionare visivamente le risorse immagine per verificare che il rendering venga eseguito correttamente per varie impostazioni.

 ![Sfondo del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-background.png "Sfondo del visualizzatore della libreria di immagini")

 Il colore di sfondo può essere impostato su Chiaro, Scuro o su un valore personalizzato. Selezionando "Colore personalizzato" si aprirà una finestra di dialogo di selezione del colore e aggiungere quel colore personalizzato nella parte inferiore della casella combinata di sfondo per un facile richiamo in un secondo momento.

 ![Colore personalizzato del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-custom-color.png "Colore personalizzato del visualizzatore della libreria di immagini")

 Selezionando un moniker di immagine vengono visualizzate le informazioni per ogni immagine reale dietro il moniker nel riquadro Dettagli immagine a destra. Il riquadro consente inoltre agli utenti di copiare un moniker in base al nome o al valore GUID:ID non elaborato.

 ![Dettagli dell'immagine del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-image-details.png "Dettagli dell'immagine del visualizzatore della libreria di immagini")

 Le informazioni visualizzate per ogni origine dell'immagine includono il tipo di sfondo su cui visualizzarla, se può essere a tema o supporta Contrasto elevato, quali dimensioni è valida per o se è indipendente dalle dimensioni e se proviene da un assembly nativo.

 ![Tema del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-can-theme.png "Tema del visualizzatore della libreria di immagini")

 Quando si convalida un manifesto dell'immagine, è consigliabile distribuire il manifesto e la DLL dell'immagine nelle relative posizioni reali. In questo modo verrà verificato che tutti i percorsi relativi funzionino correttamente e che la libreria di immagini sia in grado di trovare e caricare il manifesto e la DLL dell'immagine.

 **Ricerca del catalogo immagini KnownMonikers**

 Per abbinare meglio lo stile di Visual Studio, un'estensione di Visual Studio può usare le immagini nel catalogo immagini di Visual Studio anziché creare e usare il proprio. Questo ha il vantaggio di non dover gestire tali immagini e garantisce che l'immagine avrà un'immagine di backup ad alta risoluzione in modo che dovrebbe apparire corretta in tutte le impostazioni DPI che supporta Visual Studio.

 Il visualizzatore della libreria di immagini consente di cercare un manifesto in modo che un utente possa trovare il moniker che rappresenta un asset di immagine e usare tale moniker nel codice. Per cercare immagini, immettere il termine di ricerca desiderato nella casella di ricerca e premere INVIO. La barra di stato in basso mostrerà quante corrispondenze sono state trovate dalle immagini totali in tutti i manifesti.

 ![Filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter.png "Filtro del visualizzatore della libreria di immagini")

 Quando si cercano moniker di immagini nei manifesti esistenti, è consigliabile cercare e utilizzare solo i moniker di Visual Studio Image Catalog, altri moniker accessibili intenzionalmente pubblicamente o i propri moniker personalizzati. Se utilizzi i moniker non pubblici, l'interfaccia utente personalizzata potrebbe essere interrotta o le sue immagini potrebbero essere modificate in modi imprevisti se o quando tali moniker e immagini non pubblici vengono modificati o aggiornati.

 Inoltre, la ricerca in base al GUID è possibile. Questo tipo di ricerca è utile per filtrare l'elenco in base a un singolo manifesto o a una singola sottosezione di un manifesto se tale manifesto contiene più GUID.

 ![GUID filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID filtro del visualizzatore della libreria di immagini")

 Infine, è possibile anche la ricerca in base all'ID.

 ![ID filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtro del visualizzatore della libreria di immagini")

## <a name="notes"></a>Note

- Per impostazione predefinita, lo strumento estrarrà diversi manifesti di immagine presenti nella directory di installazione di Visual Studio.By default, the tool will pull in several image manifests present in the Visual Studio install directory. L'unico che dispone di moniker consumabili pubblicamente è il manifesto **Microsoft.VisualStudio.ImageCatalog.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 **(non** eseguire l'override di questo GUID in un manifesto personalizzato) Tipo: KnownMonikers

- Lo strumento tenta all'avvio di caricare tutti i manifesti dell'immagine trovati, pertanto potrebbero essere stati applicati alcuni secondi prima che l'applicazione venga effettivamente visualizzata. Potrebbe anche essere lento o non risponde durante il caricamento dei manifesti.

## <a name="sample-output"></a>Output di esempio
 Questo strumento non genera alcun output.
