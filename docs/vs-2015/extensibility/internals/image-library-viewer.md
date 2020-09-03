---
title: Visualizzatore libreria immagini | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6423c569fd1909539de9460ab3dcde0bcf753c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532028"
---
# <a name="image-library-viewer"></a>Visualizzatore della libreria di immagini
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lo strumento Visualizzatore della libreria di immagini di Visual Studio è in grado di caricare e cercare manifesti di immagini, consentendo all'utente di manipolarli nello stesso modo in cui è possibile eseguire Visual Studio. L'utente può modificare sfondo, dimensioni, DPI, contrasto elevato e altre impostazioni. Lo strumento Visualizza anche le informazioni di caricamento per ogni manifesto dell'immagine e visualizza le informazioni sull'origine per ogni immagine nel manifesto dell'immagine. Questo strumento è utile per:  
  
1. Diagnostica degli errori  
  
2. Verifica dell'impostazione corretta degli attributi nei manifesti delle immagini personalizzate  
  
3. Ricerca di immagini nel catalogo immagini di Visual Studio in modo che un'estensione di Visual Studio possa usare immagini che soddisfano lo stile di Visual Studio  
  
   ![Immagine principale del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-hero.png "Immagine principale del visualizzatore della libreria di immagini")  
  
   **Moniker immagine**  
  
   Un moniker di immagine (o moniker per brevità) è una coppia GUID: ID che identifica in modo univoco un asset di Image asset o image list nella libreria di immagini.  
  
   **File manifesto immagine**  
  
   I file manifesto immagine (con estensione imagemanifest) sono file XML che definiscono un set di asset immagine, i moniker che rappresentano tali asset e l'immagine reale o immagini che rappresentano ogni asset. I manifesti di immagine possono definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Sono inoltre disponibili attributi che possono essere impostati sull'asset o sulle singole immagini dietro ogni asset per modificare quando e come vengono visualizzati gli asset.  
  
   **Schema manifesto immagine**  
  
   Un manifesto completo dell'immagine ha un aspetto simile al seguente:  
  
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
  
 Per facilitare la leggibilità e la manutenzione, il manifesto dell'immagine può utilizzare i simboli per i valori di attributo. I simboli sono definiti come segue:  
  
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
|Importa|Importa i simboli del file manifesto specificato per l'utilizzo nel manifesto corrente.|  
|Guid|Il simbolo rappresenta un GUID e deve corrispondere alla formattazione del GUID.|  
|ID|Il simbolo rappresenta un ID e deve essere un numero intero non negativo.|  
|string|Il simbolo rappresenta un valore stringa arbitrario.|  
  
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
|Sistema|Cartella Windows\System32|  
|WinDir|Valore della variabile di ambiente% WinDir%|  
  
 **Immagine**  
  
 L' \<Image> elemento definisce un'immagine a cui può fare riferimento un moniker. Il GUID e l'ID riuniti formano il moniker dell'immagine. Il moniker per l'immagine deve essere univoco nell'intera libreria di immagini. Se più immagini hanno un determinato moniker, il primo rilevato durante la compilazione della libreria è quello mantenuto.  
  
 Deve contenere almeno un'origine. Sebbene le origini indipendenti dalle dimensioni forniscano i migliori risultati in un'ampia gamma di dimensioni, non sono necessarie. Se al servizio viene richiesta un'immagine di una dimensione non definita nell' \<Image> elemento e non è presente un'origine indipendente dalle dimensioni, il servizio sceglierà l'origine più adatta alle dimensioni specifiche e la proporrà alla dimensione richiesta.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
    
|**Attributo**|**Definition**|  
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
  
|**Attributo**|**Definition**|  
|-|-|  
|Uri|Necessaria URI che definisce dove è possibile caricare l'immagine. I possibili valori sono i seguenti:<br /><br /> : [URI di pacchetto](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) che usa l'autorità Application:///<br /><br /> -Riferimento a una risorsa componente assoluto<br /><br /> : Percorso di un file che contiene una risorsa nativa|  
|Sfondo|Opzionale Indica il tipo di background che l'origine deve usare.<br /><br /> I possibili valori sono i seguenti:<br /><br /> - *Light*: l'origine può essere usata su uno sfondo chiaro.<br /><br /> - *Dark*: l'origine può essere usata su uno sfondo scuro.<br /><br /> - *HighContrast*: l'origine può essere usata in qualsiasi background in modalità contrasto elevato.<br /><br /> - *HighContrastLight*: l'origine può essere usata in uno sfondo chiaro in modalità contrasto elevato.<br /><br /> -*HighContrastDark*: l'origine può essere usata su uno sfondo scuro in modalità contrasto elevato.<br /><br /> Se l'attributo **background** viene omesso, l'origine può essere utilizzata in qualsiasi background.<br /><br /> Se **background** è *Light*, *Dark*, *HighContrastLight*o *HighContrastDark*, i colori dell'origine non vengono mai invertiti. Se **background** viene omesso o impostato su *HighContrast*, l'inversione dei colori dell'origine viene controllata dall'attributo **AllowColorInversion** dell'immagine.|  
  
 Un \<Source> elemento può avere esattamente uno dei sottoelementi facoltativi seguenti:  
  
|**elemento**|**Attributi (tutti necessari)**|**Definition**|  
|-|-|-|  
|\<Size>|Valore|L'origine verrà usata per le immagini con le dimensioni specificate (in unità dispositivo). L'immagine sarà quadrata.|  
|\<SizeRange>|MinSize, MaxSize|L'origine verrà usata per le immagini da MinSize a MaxSize (in unità dispositivo), inclusi. L'immagine sarà quadrata.|  
|\<Dimensions>|Larghezza, altezza|L'origine verrà usata per le immagini della larghezza e dell'altezza specificate (in unità dispositivo).|  
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|L'origine verrà usata per le immagini dalla larghezza/altezza minima alla larghezza/altezza massima (in unità dispositivo), inclusi.|  
  
 Un \<Source> elemento può anche avere un \<NativeResource> sottoelemento facoltativo, che definisce un \<Source> che viene caricato da un assembly nativo anziché da un assembly gestito.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|**Attributo**|**Definition**|  
|-|-|  
|Type|Necessaria Il tipo della risorsa nativa, ovvero XAML o PNG|  
|ID|Necessaria Parte relativa all'ID integer della risorsa nativa|  
  
 **ImageList**  
  
 L' \<ImageList> elemento definisce una raccolta di immagini che possono essere restituite in una singola striscia. Il Strip è compilato su richiesta, in base alle esigenze.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|**Attributo**|**Definition**|  
|-|-|  
|Guid|Necessaria Parte GUID del moniker dell'immagine|  
|ID|Necessaria Parte relativa all'ID del moniker dell'immagine|  
|Esterno|[Facoltativo, valore predefinito false] Indica se il moniker dell'immagine fa riferimento a un'immagine nel manifesto corrente.|  
  
 Il moniker per l'immagine contenuta non deve fare riferimento a un'immagine definita nel manifesto corrente. Se non è possibile trovare l'immagine contenuta nella libreria di immagini, al suo posto verrà utilizzata un'immagine segnaposto vuota.  
  
## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento  
 **Convalida di un manifesto dell'immagine personalizzata**  
  
 Per creare un manifesto personalizzato, è consigliabile usare lo strumento ManifestFromResources per generare automaticamente il manifesto. Per convalidare il manifesto personalizzato, avviare il Visualizzatore della libreria di immagini e selezionare file > imposta percorsi... per aprire la finestra di dialogo Cerca directory. Lo strumento userà le directory di ricerca per caricare i manifesti delle immagini, ma li userà anche per trovare i file con estensione dll che contengono le immagini in un manifesto, quindi assicurarsi di includere le directory manifest e DLL in questa finestra di dialogo.  
  
 ![Ricerca del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-search.png "Ricerca del visualizzatore della libreria di immagini")  
  
 Fare clic su **Aggiungi...** per selezionare le nuove directory di ricerca per cercare manifesti e le DLL corrispondenti. Lo strumento memorizzerà le directory di ricerca che possono essere attivate o disattivate selezionando o deselezionando una directory.  
  
 Per impostazione predefinita, lo strumento tenterà di trovare la directory di installazione di Visual Studio e di aggiungere tali directory all'elenco delle directory di ricerca. È possibile aggiungere manualmente le directory che lo strumento non trova.  
  
 Una volta caricati tutti i manifesti, è possibile usare lo strumento per impostare i colori di **sfondo** , i valori **dpi**, il **contrasto elevato**o **grayscaling** per le immagini in modo che un utente possa esaminare visivamente gli asset delle immagini per verificare che vengano visualizzati correttamente per le varie impostazioni.  
  
 ![Sfondo del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-background.png "Sfondo del visualizzatore della libreria di immagini")  
  
 Il colore di sfondo può essere impostato su chiaro, scuro o un valore personalizzato. Selezionando "Custom color", viene aperta una finestra di dialogo di selezione dei colori e il colore personalizzato viene aggiunto alla fine della casella combinata in background per richiamarlo in un secondo momento.  
  
 ![Colore personalizzato del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-custom-color.png "Colore personalizzato del visualizzatore della libreria di immagini")  
  
 Selezionando un moniker di immagine vengono visualizzate le informazioni per ogni immagine reale alla base del moniker nel riquadro Dettagli immagine a destra. Il riquadro consente inoltre agli utenti di copiare un moniker in base al nome o al valore GUID non elaborato: ID.  
  
 ![Dettagli dell'immagine del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-image-details.png "Dettagli dell'immagine del visualizzatore della libreria di immagini")  
  
 Le informazioni visualizzate per ogni origine dell'immagine includono il tipo di sfondo in base al quale visualizzarlo, se può essere a tema o se supporta Contrasto elevato, quali dimensioni sono valide per o se è indipendente dalle dimensioni e se l'immagine deriva da un assembly nativo.  
  
 ![Tema del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-can-theme.png "Tema del visualizzatore della libreria di immagini")  
  
 Quando si convalida un manifesto dell'immagine, si consiglia di distribuire il manifesto e la DLL di immagini nelle rispettive posizioni del mondo reale. In questo modo verrà verificato che i percorsi relativi funzionino correttamente e che la libreria di immagini possa trovare e caricare la DLL del manifesto e dell'immagine.  
  
 **Ricerca del catalogo immagini KnownMonikers**  
  
 Per una migliore corrispondenza con lo stile di Visual Studio, un'estensione di Visual Studio può usare le immagini nel catalogo immagini di Visual Studio invece di crearle e usarle. Questo ha il vantaggio di non dover gestire tali immagini e garantisce che l'immagine avrà un'immagine di supporto DPI elevata, in modo che sia corretta in tutte le impostazioni DPI supportate da Visual Studio.  
  
 Il Visualizzatore della libreria di immagini consente la ricerca di un manifesto, in modo che un utente possa trovare il moniker che rappresenta un asset di immagine e usare tale moniker nel codice. Per cercare le immagini, immettere il termine di ricerca desiderato nella casella di ricerca e premere INVIO. La barra di stato nella parte inferiore visualizzerà il numero di corrispondenze rilevate dalle immagini totali in tutti i manifesti.  
  
 ![Filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter.png "Filtro del visualizzatore della libreria di immagini")  
  
 Quando si cercano moniker di immagine nei manifesti esistenti, si consiglia di cercare e usare solo i moniker del catalogo immagini di Visual Studio, altri moniker accessibili pubblicamente o i moniker personalizzati. Se si usano moniker non pubblici, è possibile che l'interfaccia utente personalizzata venga interruppe o che le immagini siano state modificate in modi imprevisti se o quando tali moniker e immagini non pubblici vengono modificati o aggiornati.  
  
 Inoltre, è possibile eseguire la ricerca tramite GUID. Questo tipo di ricerca è utile per filtrare l'elenco in un singolo manifesto o una sottosezione singola di un manifesto se il manifesto contiene più GUID.  
  
 ![GUID filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID filtro del visualizzatore della libreria di immagini")  
  
 Infine, è possibile anche eseguire la ricerca in base all'ID.  
  
 ![ID filtro del visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtro del visualizzatore della libreria di immagini")  
  
## <a name="notes"></a>Note  
  
- Per impostazione predefinita, lo strumento eseguirà il pull di diversi manifesti immagine presenti nella directory di installazione di Visual Studio. L'unico con moniker utilizzabili pubblicamente è il manifesto **Microsoft. VisualStudio. ImageCatalog** . GUID: ae27a6b0-E345-4288-96df-5eaf394ee369 ( **non** eseguire l'override di questo GUID in un manifesto personalizzato) tipo: KnownMonikers  
  
- Lo strumento tenta di avviare il caricamento di tutti i manifesti di immagini trovati, quindi potrebbero essere importati alcuni secondi per visualizzare l'applicazione. Potrebbe anche essere lento o non rispondere durante il caricamento dei manifesti.  
  
## <a name="sample-output"></a>Output di esempio  
 Questo strumento non genera alcun output.
