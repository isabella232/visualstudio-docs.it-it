---
title: Visualizzatore raccolta immagini | Microsoft Docs
description: Informazioni sullo strumento Visual Studio Image Library Viewer che carica ed esegue ricerche nei manifesti delle immagini, consentendo di visualizzare e modificare gli attributi delle immagini.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ee92f235bc973d0929e89ceae8d24f8ca77b9865
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710277"
---
# <a name="image-library-viewer"></a>Visualizzatore della libreria di immagini
Lo strumento Visual Studio Image Library Viewer può caricare ed eseguire ricerche nei manifesti delle immagini, consentendo all'utente di modificarli nello stesso modo Visual Studio possibile. L'utente può modificare sfondo, dimensioni, DPI, contrasto elevato e altre impostazioni. Lo strumento visualizza anche le informazioni di caricamento per ogni manifesto dell'immagine e le informazioni sull'origine per ogni immagine nel manifesto dell'immagine. Questo strumento è utile per:

1. Diagnostica degli errori

2. Verifica della corretta impostazione degli attributi nei manifesti di immagini personalizzati

3. Ricerca di immagini nel Catalogo Visual Studio immagini in modo che un'estensione Visual Studio possa usare immagini che si adattano allo stile di Visual Studio

   ![Immagine principale del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-hero.png "Immagine principale del visualizzatore della libreria di immagini")

   **Moniker immagine**

   Un moniker immagine (o moniker breve) è una coppia GUID:ID che identifica in modo univoco un asset immagine o un asset elenco immagini nella raccolta immagini.

   **File manifesto dell'immagine**

   I file manifesto dell'immagine (con estensione imagemanifest) sono file XML che definiscono un set di asset di immagini, i moniker che rappresentano tali asset e l'immagine o le immagini reali che rappresentano ogni asset. I manifesti di immagini possono definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Sono inoltre disponibili attributi che possono essere impostati nell'asset o nelle singole immagini dietro ogni asset per modificare quando e come tali asset vengono visualizzati.

   **Schema del manifesto dell'immagine**

   Un manifesto completo dell'immagine è simile al seguente:

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

 Per facilitare la leggibilità e la manutenzione, il manifesto dell'immagine può usare i simboli per i valori degli attributi. I simboli sono definiti nel modo seguente:

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
|Importa|Importa i simboli del file manifesto specificato per l'uso nel manifesto corrente.|
|Guid|Il simbolo rappresenta un GUID e deve corrispondere alla formattazione GUID.|
|ID|Il simbolo rappresenta un ID e deve essere un numero intero non negativo.|
|string|Il simbolo rappresenta un valore stringa arbitrario.|

 Ai simboli viene fatto distinzione tra maiuscole e minuscole e viene fatto riferimento tramite la sintassi $(symbol-name):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Alcuni simboli sono predefiniti per tutti i manifesti. Possono essere usati nell'attributo Uri \<Source> dell'elemento o per fare riferimento ai percorsi nel computer \<Import> locale.

|**Simbolo**|**Descrizione**|
|-|-|
|CommonProgramFiles|Valore della variabile di ambiente %CommonProgramFiles%|
|Localappdata|Valore della variabile di ambiente %LocalAppData%|
|Cartella ManifestFolder|Cartella contenente il file manifesto|
|Mydocuments|Percorso completo della cartella Documenti dell'utente corrente|
|ProgramFiles|Valore della variabile di ambiente %ProgramFiles%|
|Sistema|Cartella Windows\System32|
|Windir|Valore della variabile di ambiente %WinDir%|

 **Immagine**

 \<Image>L'elemento definisce un'immagine a cui può fare riferimento un moniker. Il GUID e l'ID insieme formano il moniker dell'immagine. Il moniker per l'immagine deve essere univoco nell'intera raccolta immagini. Se più immagini hanno un moniker specificato, la prima rilevata durante la compilazione della libreria è quella mantenuta.

 Deve contenere almeno un'origine. Anche se le origini indipendenti dalla dimensione offrono risultati ottimali in un'ampia gamma di dimensioni, non sono necessarie. Se al servizio viene richiesta un'immagine di una dimensione non definita nell'elemento e non esiste un'origine indipendente dalla dimensione, il servizio sceglierà l'origine specifica delle dimensioni migliori e la scalerà in base alle dimensioni \<Image> richieste.

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
|Uri|[Obbligatorio] URI che definisce la posizione da cui è possibile caricare l'immagine. I possibili valori sono i seguenti:<br /><br /> - URI [di tipo pack](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) che usa l application:/// autorità<br /><br /> - Riferimento alla risorsa componente assoluto<br /><br /> - Percorso di un file contenente una risorsa nativa|
|Sfondo|[Facoltativo] Indica il tipo di sfondo che l'origine deve usare.<br /><br /> I possibili valori sono i seguenti:<br /><br /> - *Chiaro:* la sorgente può essere usata su uno sfondo chiaro.<br /><br /> - *Scuro:* l'origine può essere usata su uno sfondo scuro.<br /><br /> - *HighContrast:* l'origine può essere usata in qualsiasi background in Contrasto elevato modalità.<br /><br /> - *HighContrastLight:* l'origine può essere usata su uno sfondo chiaro Contrasto elevato modalità.<br /><br /> -*HighContrastDark:* l'origine può essere usata su uno sfondo scuro in Contrasto elevato predefinita.<br /><br /> Se **l'attributo Background** viene omesso, l'origine può essere usata in qualsiasi sfondo.<br /><br /> Se **Background** è *Light,* *Dark,* *HighContrastLight* o *HighContrastDark,* i colori dell'origine non vengono mai invertiti. Se **Background** viene omesso o impostato su *HighContrast,* l'inversione dei colori dell'origine è controllata dall'attributo **AllowColorInversion** dell'immagine.|

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

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 **Convalida di un manifesto dell'immagine personalizzato**

 Per creare un manifesto personalizzato, è consigliabile usare lo strumento ManifestFromResources per rigenerare automaticamente il manifesto. Per convalidare il manifesto personalizzato, avviare il Visualizzatore libreria di immagini e selezionare File > Imposta percorsi... per aprire la finestra di dialogo Directory di ricerca. Lo strumento userà le directory di ricerca per caricare i manifesti delle immagini, ma li userà anche per trovare i file .dll che contengono le immagini in un manifesto, quindi assicurarsi di includere sia il manifesto che le directory DLL in questa finestra di dialogo.

 ![Ricerca del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-search.png "Ricerca del visualizzatore della libreria di immagini")

 Fare **clic su** Aggiungi per selezionare nuove directory di ricerca per cercare i manifesti e le DLL corrispondenti. Lo strumento memorizza queste directory di ricerca e può essere attivata o disattivata selezionando o deselezionando una directory.

 Per impostazione predefinita, lo strumento tenterà di trovare Visual Studio directory di installazione e di aggiungere tali directory all'elenco delle directory di ricerca. È possibile aggiungere manualmente le directory che lo strumento non trova.

 Dopo aver caricato tutti i manifesti, lo  strumento può essere usato per  attivare o disattivare i colori di sfondo, **IDPI,** il contrasto elevato o la scala di grigi per le immagini, in modo che un utente possa esaminare visivamente gli asset delle immagini per verificare che il rendering venga eseguito correttamente per diverse impostazioni. 

 ![Sfondo del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-background.png "Sfondo del visualizzatore della libreria di immagini")

 Il colore di sfondo può essere impostato su Chiaro, Scuro o su un valore personalizzato. Se si seleziona "Colore personalizzato", verrà aperta una finestra di dialogo di selezione dei colori e tale colore personalizzato verrà aggiunto nella parte inferiore della casella combinata di sfondo per un facile richiamo in un secondo momento.

 ![Colore personalizzato del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-custom-color.png "Colore personalizzato del visualizzatore della libreria di immagini")

 La selezione di un moniker di immagine visualizza le informazioni per ogni immagine reale dietro tale moniker nel riquadro Dettagli immagine a destra. Il riquadro consente inoltre agli utenti di copiare un moniker in base al nome o al valore GUID:ID non elaborato.

 ![Dettagli dell'immagine del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-image-details.png "Dettagli dell'immagine del visualizzatore della libreria di immagini")

 Le informazioni visualizzate per ogni origine dell'immagine includono il tipo di sfondo su cui visualizzarla, se può essere a base di testo o supporta Contrasto elevato, per quali dimensioni è valida o se è indipendente dalle dimensioni e se l'immagine proviene da un assembly nativo.

 ![Tema del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-can-theme.png "Tema del visualizzatore della libreria di immagini")

 Quando si convalida un manifesto dell'immagine, è consigliabile distribuire il manifesto e la DLL dell'immagine nelle rispettive posizioni reali. In questo modo si verificherà che tutti i percorsi relativi funzionino correttamente e che la libreria di immagini sia in grado di trovare e caricare il manifesto e la DLL dell'immagine.

 **Ricerca del catalogo immagini KnownMonikers**

 Per ottenere una corrispondenza migliore Visual Studio stile, un'estensione Visual Studio può usare immagini nel catalogo immagini Visual Studio anziché creare e usare immagini proprie. Questo ha il vantaggio di non dover mantenere tali immagini e garantisce che l'immagine avrà un'immagine di supporto con valori DPI elevati, quindi dovrebbe essere corretta in tutte le impostazioni DPI supportate da Visual Studio.

 Il visualizzatore della libreria di immagini consente di cercare un manifesto in modo che un utente possa trovare il moniker che rappresenta un asset di immagine e usarlo nel codice. Per cercare immagini, immettere il termine di ricerca desiderato nella casella di ricerca e premere INVIO. La barra di stato nella parte inferiore visualizza il numero di corrispondenze trovate tra le immagini totali in tutti i manifesti.

 ![Filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter.png "Filtro del visualizzatore della libreria di immagini")

 Quando si cercano moniker di immagini nei manifesti esistenti, è consigliabile cercare e usare solo i moniker del Catalogo immagini di Visual Studio, altri moniker intenzionalmente accessibili pubblicamente o moniker personalizzati. Se si usano moniker non pubblico, è possibile che l'interfaccia utente personalizzata venga interrotta o che le immagini cambino in modo imprevisto se o quando tali moniker e immagini non pubblico vengono modificati o aggiornati.

 È anche possibile eseguire la ricerca in base al GUID. Questo tipo di ricerca è utile per filtrare l'elenco in base a un singolo manifesto o a una singola sottosezione di un manifesto se tale manifesto contiene più GUID.

 ![GUID filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID filtro del visualizzatore della libreria di immagini")

 Infine, è anche possibile eseguire la ricerca in base all'ID.

 ![ID filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtro del visualizzatore della libreria di immagini")

## <a name="notes"></a>Note

- Per impostazione predefinita, lo strumento estrae diversi manifesti immagine presenti nella directory Visual Studio di installazione. L'unico che dispone di moniker utilizzabili pubblicamente è il **manifesto Microsoft.VisualStudio.ImageCatalog.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369  (non eseguire l'override di questo GUID in un manifesto personalizzato) Tipo: KnownMonikers

- Lo strumento tenta all'avvio di caricare tutti i manifesti dell'immagine trovati, quindi potrebbero essere disponibili alcuni secondi prima che l'applicazione venga effettivamente visualizzata. Potrebbe anche essere lenta o non rispondere durante il caricamento dei manifesti.

## <a name="sample-output"></a>Output di esempio
 Questo strumento non genera alcun output.
