---
title: Visualizzatore della libreria di immagini | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97d634f97eb7a13cfa54b2c0d326b19f31fb7d9d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685461"
---
# <a name="image-library-viewer"></a>Visualizzatore della libreria di immagini
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lo strumento Visualizzatore di Visual Studio Image Library è possibile caricare e cercare i manifesti dell'immagine, consentendo all'utente di modificarli in modo identico a Visual Studio. L'utente potrà modificare in background, dimensioni, DPI, contrasto elevato e altre impostazioni. Inoltre, lo strumento visualizza le informazioni di caricamento per ogni manifesto di immagini e Visualizza informazioni sull'origine per ogni immagine nel manifesto dell'immagine. Questo strumento è utile per:  
  
1. Diagnostica degli errori  
  
2. Garantire che gli attributi sono impostati in modo corretto nei manifesti immagine personalizzata  
  
3. La ricerca delle immagini dell'immagine del catalogo di Visual Studio in modo che un'estensione di Visual Studio può usare le immagini che adatta lo stile di Visual Studio  
  
   ![Immagine principale del Visualizzatore della libreria](../../extensibility/internals/media/image-library-viewer-hero.png "principale del Visualizzatore della libreria di immagini")  
  
   **Moniker di immagini**  
  
   Un moniker di immagine (o moniker breve) è una coppia GUID: ID che identifica in modo univoco un asset di immagine o un asset di elenco immagini della raccolta.  
  
   **File manifesto di immagini**  
  
   I file di immagine manifesto (.imagemanifest) sono file XML che definiscono un set di asset di immagini, i moniker che rappresentano tali asset e l'immagine reale o le immagini per rappresentare ogni asset. Manifesti dell'immagine può definire le immagini autonome o elenchi di immagini per il supporto legacy dell'interfaccia utente. Inoltre, esistono attributi che è possano impostare l'asset o le singole immagini protetti da ogni asset modificare quando e come vengono visualizzati tali asset.  
  
   **Schema del manifesto dell'immagine**  
  
   Un manifesto del completamento dell'immagine è simile alla seguente:  
  
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
|**Subelement**|**Definizione**|  
|Import|Importa i simboli del file manifesto specificato per l'uso nel manifesto corrente.|  
|GUID|Il simbolo rappresenta un GUID e deve corrispondere la formattazione di GUID.|  
|Id|Il simbolo rappresenta un ID e deve essere un numero intero non negativo.|  
|Stringa|Il simbolo rappresenta un valore di stringa arbitrario.|  
  
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
  
 Deve contenere almeno un'origine. Sebbene indipendente dalla dimensione origini fornirà i migliori risultati attraverso un'ampia gamma di dimensioni, non sono necessarie. Se il servizio è richiesto per un'immagine di dimensioni non è definita nel \<immagine > elemento ed è presente alcuna origine indipendente dalla dimensione, il servizio scegliere la migliore fonte di dimensioni specifiche e passare al piano la dimensione richiesta.  
  
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
|URI|[Obbligatorio] URI che definisce dove è possibile caricare l'immagine da. Può essere uno dei seguenti:<br /><br /> -A [URI di tipo Pack](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) utilizzando l'applicazione: / / / autorità<br /><br /> -Riferimento a una risorsa un componente assoluto<br /><br /> -Un percorso di un file contenente una risorsa nativa|  
|Sfondo|[Facoltativo] Indica l'operazione nel tipo di origine dovrà essere utilizzato in background.<br /><br /> Può essere uno dei seguenti:<br /><br /> - *Light*: L'origine può essere utilizzata su uno sfondo chiaro.<br /><br /> - *Scuro*: L'origine può essere utilizzata su uno sfondo scuro.<br /><br /> - *HighContrast*: L'origine può essere utilizzata in qualsiasi dello sfondo nella modalità a contrasto elevato.<br /><br /> - *HighContrastLight*: L'origine può essere utilizzata su uno sfondo chiaro in modalità a contrasto elevato.<br /><br /> -*HighContrastDark*: L'origine può essere utilizzata su uno sfondo scuro in modalità a contrasto elevato.<br /><br /> Se il **sfondo** attributo viene omesso, l'origine può essere usato su qualsiasi dello sfondo.<br /><br /> Se **sfondo** viene *Light*, *scuro*, *HighContrastLight*, o *HighContrastDark*, i colori dell'origine non vengono mai invertiti. Se **sfondo** viene omesso o impostato su *contrasto elevato*, l'inversione di colori dell'origine viene controllata nell'immagine **AllowColorInversion** attributo.|  
  
 Oggetto \<origine > elemento può includere esattamente uno dei sottoelementi facoltativi seguenti:  
  
||||  
|-|-|-|  
|**Elemento**|**Attributi (tutti necessari)**|**Definizione**|  
|\<Size>|Value|L'origine verrà utilizzata per le immagini della dimensione specificata (in unità di dispositivo). L'immagine sarà quadrato.|  
|\<SizeRange>|MinSize, MaxSize|L'origine verrà utilizzata per le immagini da MinSize alle dimensioni massime (in unità di dispositivo), inclusi. L'immagine sarà quadrato.|  
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
  
## <a name="how-to-use-the-tool"></a>Come usare lo strumento  
 **La convalida di un manifesto di immagini personalizzate**  
  
 Per creare un manifesto personalizzato, è consigliabile usare lo strumento ManifestFromResources per generare automaticamente il manifesto. Per convalidare il manifesto personalizzato, avviare il Visualizzatore della libreria di immagini e selezionare File > imposta percorsi... Per aprire la finestra di dialogo Directory di ricerca. Directory di ricerca viene usato per caricare i manifesti di immagine, ma lo userà anche loro di trovare i file con estensione dll che contengono le immagini in un manifesto, pertanto assicurarsi di includere sia il manifesto e le directory DLL in questa finestra di dialogo.  
  
 ![Ricerca del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-search.png "ricerca del Visualizzatore della libreria di immagini")  
  
 Fare clic su **Aggiungi...** Per selezionare nuove directory di ricerca per cercare i manifesti e le DLL corrispondenti. Lo strumento memorizzerà queste directory di ricerca e può essere attivate o disattivata, selezionare o deselezionare una directory.  
  
 Per impostazione predefinita, lo strumento tenterà di trovare la directory di installazione di Visual Studio e aggiungere tali directory all'elenco di directory di ricerca. È possibile aggiungere manualmente le directory che non viene trovato lo strumento.  
  
 Una volta che vengono caricati tutti i manifesti, lo strumento può essere usato per attivare/disattivare **sfondo** colori **DPI**, **contrasto elevato**, o **grigio** per le immagini in modo che un utente può esaminare visivamente gli asset delle immagini per verificare che viene eseguito il rendering correttamente per le varie impostazioni.  
  
 ![Immagine di sfondo del Visualizzatore della libreria](../../extensibility/internals/media/image-library-viewer-background.png "immagine di sfondo del Visualizzatore della libreria")  
  
 Chiaro, scuro, o un valore personalizzato, è possibile impostare il colore di sfondo. Selezionando "Colore personalizzato" verrà aprire una finestra di dialogo di selezione di colore e aggiungere tale colore personalizzato nella parte inferiore della casella combinata in background per essere richiamati facilmente in un secondo momento.  
  
 ![Colore personalizzato del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-custom-color.png "colore personalizzato del Visualizzatore della libreria di immagini")  
  
 La selezione di un moniker di immagini consente di visualizzare le informazioni per ogni immagine reale dietro il moniker nel riquadro dei dettagli di immagine a destra. Il riquadro consente inoltre agli utenti di copiare un moniker in base al nome o valore non elaborato coppia GUID: ID.  
  
 ![I dettagli dell'immagine del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-image-details.png "i dettagli dell'immagine del Visualizzatore della libreria di immagini")  
  
 Le informazioni visualizzate per ogni origine dell'immagine includono il tipo di sfondo per visualizzarlo, se può essere a tema o supporta a contrasto elevato, le dimensioni è valido per o se è indipendente dalla dimensione e se l'immagine proviene da un assembly nativo.  
  
 ![Visualizzatore della libreria di immagini possono tema](../../extensibility/internals/media/image-library-viewer-can-theme.png "Visualizzatore della libreria di immagini possono tema")  
  
 Durante la convalida di un manifesto di immagini, è consigliabile distribuire il manifesto e l'immagine DLL nei rispettivi percorsi reali. Ciò consente di verificare che tutti i percorsi relativi sono funzioni correttamente e che la libreria di immagini possa individuare e caricare il manifesto e l'immagine DLL.  
  
 **La ricerca per il catalogo immagine KnownMonikers**  
  
 Per meglio soddisfare lo stile di Visual Studio, un'estensione di Visual Studio può usare le immagini in Visual Studio Image catalogo anziché la creazione e con i propri. Questo ha il vantaggio di non dover gestire tali immagini e garantisce che l'immagine avrà un'immagine ad alta risoluzione, pertanto dovrebbe essere corretto in tutte le impostazioni DPI che supportano Visual Studio.  
  
 Il Visualizzatore della libreria di immagini consente un manifesto da cercare in modo che un utente può trovare il moniker che rappresenta un asset di immagine e usare tale moniker nel codice. Per cercare immagini, immettere il termine di ricerca desiderati nella casella di ricerca e premere INVIO. La barra di stato nella parte inferiore verrà visualizzato il numero di corrispondenze trovato all'esterno di immagini di totale in tutti i manifesti.  
  
 ![Filtro del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter.png "filtro del Visualizzatore della libreria di immagini")  
  
 Quando si cercano i moniker immagine nei manifesti esistenti, si consiglia di cercare e utilizzare solo i moniker di Visual Studio Image Catalog, altri moniker intenzionalmente pubblicamente accessibile o il proprio moniker personalizzato. Se si usano i moniker non pubblici, interfaccia utente personalizzata potrebbe essere interrotta o sono relative immagini stati modificati in modo imprevisto se o quando i moniker non pubblici e le immagini vengono modificate o aggiornate.  
  
 Inoltre, è possibile la ricerca dal GUID. Questo tipo di ricerca è utile per filtrare l'elenco per un manifesto singolo, o singolo sottosezione di un manifesto se tale manifesto contiene più GUID.  
  
 ![GUID filtro del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID filtro del Visualizzatore della libreria di immagini")  
  
 Infine, la ricerca per ID è possibile anche.  
  
 ![ID filtro del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtro del Visualizzatore della libreria di immagini")  
  
## <a name="notes"></a>Note  
  
- Per impostazione predefinita, lo strumento effettuerà il pull in diversi i manifesti di immagine presenti nella directory di installazione di Visual Studio. È l'unico con moniker utilizzabile pubblicamente il **Microsoft.VisualStudio.ImageCatalog** manifesto. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (effettuare **non** eseguire l'override di questo GUID in un manifesto personalizzato) digitare: KnownMonikers  
  
- Lo strumento tenta di avvio per caricare tutti i manifesti di immagine che trova, in modo che potrebbe richiedere alcuni secondi per l'applicazione viene effettivamente visualizzata. È possibile anche lenta o che non risponde durante il caricamento dei manifesti.  
  
## <a name="sample-output"></a>Esempio di output  
 Questo strumento non genera alcun output.
