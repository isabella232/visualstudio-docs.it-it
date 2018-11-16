---
title: Immagini e icone per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ab668678a0ec867112f461b7978962d941bcdc8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749174"
---
# <a name="images-and-icons-for-visual-studio"></a>Immagini e icone per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_ImageUseInVisualStudio"></a> Uso di immagini in Visual Studio  
 Prima di creare la grafica, è consigliabile rendere utilizzo delle immagini oltre 1.000 nel [Visual Studio Image Library](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Tipi di immagini  
  
-   **Le icone**. Immagini di piccole dimensioni che vengono visualizzati nei comandi, le gerarchie, modelli e così via. La dimensione di icona predefinita utilizzata in Visual Studio è un file 16x16 PNG. Icone generate automaticamente dal servizio image generano il formato XAML per il supporto HDPI.  
  
     **Nota:** mentre le immagini vengono usate nel sistema di menu, non è necessario creare un'icona per ogni comando. Consultare [menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) per vedere se il comando deve visualizzare un'icona.  
  
-   **Anteprime.** Immagini usate nell'area di anteprima di una finestra di dialogo, ad esempio la finestra di dialogo Nuovo progetto.  
  
-   **Immagini di finestra di dialogo.** Immagini visualizzate nelle finestre di dialogo o le procedure guidate, come grafica descrittiva o gli indicatori di messaggio. Usare raramente e solo quando necessario, per illustrare un concetto piuttosto complesso o per ottenere l'attenzione dell'utente (avviso, avviso).  
  
-   **Immagini animate.** Utilizzata per gli indicatori di stato, barre di stato e le finestre di dialogo di operazione.  
  
-   **Cursori.** Utilizzato per indicare se un'operazione è consentita l'uso del mouse, in cui potrebbero essere interrotte, un oggetto e così via.  
  
##  <a name="BKMK_IconDesign"></a> Progettazione di icona  
  
### <a name="overview"></a>Panoramica  
 Visual Studio Usa icone in stile moderno, che dispongono di geometria pulita e un saldo 50/50 pari positivo/negativo (chiaro o scuro) e quindi metafore dirette e comprensibile. Icona fondamentale progettazione punti sono incentrate maggiore chiarezza, semplificazione e il contesto.  
  
- **Maggiore chiarezza:** concentrare la metafora di core che offre un'icona relativo significato e la tua personalità.  
  
- **Semplificazione:** ridurre l'icona al relativo significato core: consente di ottenere il tema con solo gli elementi necessari e non increspature.  
  
- **Contesto:** prendere in considerazione tutti gli aspetti del ruolo dell'icona durante lo sviluppo di verifica, è fondamentale per decidere quali elementi costituiscono metafora di core dell'icona.  
  
  Con le icone, sono presenti un numero di punti di progettazione per evitare di:  
  
- Non usare le icone che indicano gli elementi dell'interfaccia utente, ad eccezione di quando appropriato. Scegliere un approccio più astratto o simbolico quando l'elemento dell'interfaccia utente non è comune, evidente, né univoco.  
  
- Non utilizzo eccessivo di elementi comuni, ad esempio documenti, cartelle, frecce e la lente di ingrandimento. Usare questi elementi solo quando è essenziale per il significato dell'icona. Ad esempio, la lente di ingrandimento rivolta verso destra deve indicare solo Cerca, Sfoglia e individuare.  
  
- Anche se alcuni elementi legacy icona gestiscono l'utilizzo del punto di vista, non creare nuove icone con punto di vista, a meno che l'elemento non dispone di chiarezza senza di essa.  
  
- Non cram troppe informazioni in un'icona. Una semplice immagine che può essere facilmente riconosciuta o appreso come simbolo di riconoscibile è molto più utile rispetto a un'immagine eccessivamente complessa. Un'icona non è esauriente.  
  
### <a name="icon-creation"></a>Creazione di icone  
  
#### <a name="concept-development"></a>Sviluppo di concetto  
 Visual Studio include all'interno dell'interfaccia utente di un'ampia gamma di tipi di icone. Valutare attentamente il tipo di icona durante lo sviluppo. Non usare oggetti dell'interfaccia utente non comuni o poco chiaro per gli elementi di icona. Scegliere il collegamento simbolico in questi casi, ad esempio con l'icona Smart Tag. Si noti che il significato del tag astratto a sinistra è più evidente rispetto alla versione vaga, basato sull'interfaccia utente a destra:  
  
|||  
|-|-|  
|**Utilizzo corretto delle immagini simbolico**|**Uso non corretto di immagini simbolico**|  
|![Icona Smart Tag corretta](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404 01_SmartTagCorrect")|![Icona Smart Tag non corretta](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404 02_SmartTagIncorrect")|  
  
 Sono presenti istanze in cui gli elementi dell'interfaccia utente standard e facilmente riconoscibili funzionano anche per le icone. Aggiungi che finestra è uno di questi esempi:  
  
|||  
|-|-|  
|**Corretto elemento dell'interfaccia utente in un'icona**|**Elemento dell'interfaccia utente non corretto in un'icona**|  
|![Icona Aggiungi finestra corretta](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404 03_AddWindowCorrect")|![Icona Aggiungi finestra corretta](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404 04_AddWindowIncorrect")|  
  
 Non usare un documento come elemento di base, a meno che non è essenziale significato dell'icona. Senza il documento elemento nel documento aggiungere (sotto) il significato è andato perso, mentre con l'aggiornamento dell'elemento del documento non è necessario comunicare il significato.  
  
|||  
|-|-|  
|**Utilizzo corretto delle icone documento**|**Uso non corretto dell'icona del documento**|  
|![Icona documento corretta](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404 05_DocumentIconCorrect")|![Icona documento corretta](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404 06_DocumentIconIncorrect")|  
  
 Il concetto di "Mostra" deve essere rappresentato dall'icona di cui illustra al meglio ciò che viene visualizzato, ad esempio come con l'esempio mostra tutti i file. Una metafora dell'obiettivo può essere utilizzata per indicare il concetto di "visualizzazione", se necessario, ad esempio con l'esempio di visualizzazione di risorse.  
  
|||  
|-|-|  
|**"Show"**|**"View"**|  
|![Mostra l'icona](../../extensibility/ux-guidelines/media/0404-07-show.png "0404 07_Show")|![Icona di visualizzazione](../../extensibility/ux-guidelines/media/0404-08-view.png "0404 08_View")|  
  
 Il rivolta verso destra sottorappresentata sull'icona a forma deve rappresentare solo eseguire la ricerca, trovare e Sfoglia. La variante rivolta verso sinistra con il segno più o meno (-) deve rappresentare solo zoom avanti / zoom indietro.  
  
|||  
|-|-|  
|**"Ricerca"**|**Eseguire lo zoom "Avanti"**|  
|![Icona di ricerca](../../extensibility/ux-guidelines/media/0404-09-search.png "0404 09_Search")|![Icona dello zoom](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404 10_Zoom")|  
  
 Nelle visualizzazioni albero, non usare l'icona della cartella sia un modificatore. Quando è disponibile, usare solo il modificatore.  
  
|||  
|-|-|  
|**Icone di visualizzazione albero corretto**|**Icone di visualizzazione albero non corretta**|  
|![Icona visualizzazione albero corretta &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![icona visualizzazione albero corretta &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![Icona visualizzazione albero non corretta &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![icona visualizzazione albero non corretta &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404 14_ TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Dettagli di stile  
  
#### <a name="layout"></a>Layout  
 Elementi dello stack come illustrato per 16x16 icone standard:  
  
 ![Stack di layout per 16x16 icone](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404 15_LayoutStack")  
  
 **Stack di layout per 16x16 icone**  
  
 Elementi di notifica di stato sono più usati come icone autonomo. Sono disponibili contesti, tuttavia, in cui una notifica deve essere impilata sull'elemento di base, ad esempio con l'icona attività completata:  
  
 ![Notifiche autonome in Visual Studio](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")  
  
 **Icone di notifica autonomo**  
  
 ![Icona attività completata](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404 17_TaskComplete")  
  
 **Icona attività completata**  
  
 Icone di progetto sono in genere i file con estensione ico che contengono più dimensioni. La maggior parte delle 16x16 icone contengono gli stessi elementi. Le versioni di 32 x 32 includono informazioni dettagliate, incluso il tipo di progetto quando applicabile.  
  
 ![Icone in Visual Studio del progetto](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")  
  
 **Icone di progetto libreria di controlli Windows VB, 16 x 16 e 32 x 32**  
  
 Centro di un'icona all'interno della cornice di pixel. Se ciò non è possibile, allineare l'icona nella parte superiore e/o a destra del frame.  
  
 ![Icona centrata nel frame di pixel](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404 19_IconCentered")  
  
 **Icona centrata nel frame di pixel**  
  
 ![Icona allineata in alto a destra del frame di pixel](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404 20_IconTopRight")  
  
 **Icona allineata alla parte superiore destra del frame**  
  
 ![Icona centrata e allineata al lato superiore del frame di pixel](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404 21_IconTopAlign")  
  
 **Icona centrata e allineata alla parte superiore del frame**  
  
 Per raggiungere un equilibrio e allineamento ideale, evitare ostruendo elementi di base dell'icona con i glifi di azione. Posizionare il glifo nella parte superiore sinistra dell'elemento di base. Quando si aggiunge un ulteriore elemento, prendere in considerazione l'allineamento e saldo dell'icona.  
  
|||  
|-|-|  
|**Equilibrio e allineamento corretto**|**Equilibrio e allineamento non corretto**|  
|![Correggere icona equilibrio e allineamento](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![Icona corretto equilibrio e allineamento](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|  
  
 Verificare la parità di dimensioni per le icone che condividono elementi e vengono usati nel set. Si noti che nell'associazione non corretta, il cerchio e freccia sono di grandi dimensioni e non corrispondono.  
  
|||  
|-|-|  
|**Parità di dimensioni corrette**|**Parità di dimensioni non corrette**|  
|![Correggere le dimensioni delle icone e parità](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404 24_SizeParityCorrect")|![Dimensioni dell'icona non corretto e parità](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404 25_SizeParityIncorrect")|  
  
 Usare riga coerente e pesi visual. Valutare come l'icona che si sta compilando Confronta ad altre icone tramite un confronto side-by-side. Usare l'intero 16x16 fotogramma, non utilizzare mai 15 x 15 o più piccole. Il rapporto tra (dark-a-light) negativo-per-positivo deve essere 50/50.  
  
|||  
|-|-|  
|**Corrette proporzioni negativo-per-positivo**|**Corretto rapporto negativo-per-positivo**|  
|![Correggere l'impatto visivo per le icone &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![Correggere l'impatto visivo per le icone &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![Correggere l'impatto visivo per le icone &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![Impatto visivo non corretto per le icone](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404 29_VisualWeightIncorrect")|  
  
 Usare le forme confrontabili, semplice e angoli complementare per compilare gli elementi senza compromettere l'integrità di elemento. Usare gli angoli ° 45 o 90° laddove possibile.  
  
 ![Correggere gli angoli di icona](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404 30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Prospettiva  
 Mantenere l'icona chiaro e comprensibile. Usare prospettiva e una sorgente di luce solo quando necessario. Sebbene tramite prospettiva sugli elementi di icona deve essere evitata, alcuni elementi sono non riconoscibile senza di essa. In questi casi, una prospettiva con stili comunica chiarezza dell'elemento.  
  
 ![3&#45;scegliere una prospettiva](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404 31_3PointPerspective")  
  
 **prospettiva di 3 punto**  
  
 ![1&#45;scegliere una prospettiva](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404 32_1PointPerspective")  
  
 **prospettiva di 1 punto**  
  
 La maggior parte degli elementi devono essere rivolto o con angolazione verso destra.  
  
 ![Le icone con angolazione corretta](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404 33_AngledRight")  
  
 Usare sorgenti di luce solo quando si aggiunge la chiarezza necessaria a un oggetto.  
  
|||  
|-|-|  
|**Sorgente di luce corrette**|**Sorgente di luce non corretto**|  
|![Correggere le sorgenti di luce per le icone](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![Sorgenti di luce non corretti per le icone](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|  
  
 Utilizza le strutture solo per migliorare la leggibilità o a comunicare meglio la metafora. Il saldo (chiaro-scuro) positivo a negativo deve essere 50/50.  
  
|||  
|-|-|  
|**Utilizzo corretto delle strutture**|**Uso non corretto di strutture**|  
|![Correggere i contorni](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404 36_OutlinesCorrect")|![Strutture non corrette](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404 37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Tipi di icone  
 **La shell e sulla barra dei comandi** icone sono costituiti da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.  
  
 ![La shell e comando della barra di icone](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404 38_ShellIcons")  
  
 **Esempi di comando della barra delle icone e shell**  
  
 **Barra di comando finestra degli strumenti** icone sono costituiti da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.  
  
 ![Strumento icone della finestra comando barra](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")  
  
 **Esempi di icone della barra degli strumenti finestra comando**  
  
 **Disambiguatore visualizzazione struttura ad albero** icone sono costituiti da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.  
  
 ![Icone del disambiguatore della visualizzazione albero](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404 40_TreeViewIcons")  
  
 **Esempi di struttura ad albero visualizzare icone del disambiguatore**  
  
 **Tassonomia basati sullo stato valore** icone esistono nei seguenti stati: attivo, disabilitato attivo e inattivo disabilitato.  
  
 ![Stato&#45;tassonomia valore icone basate sui](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")  
  
 **Esempi di icone di tassonomia basati sullo stato di valore**  
  
 **IntelliSense** icone sono costituiti da non più di tre dei seguenti elementi: una base, uno modificatore e uno stato.  
  
 ![Icone per IntelliSense](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404 42_IntelliSenseIcons")  
  
 **Esempi di icone per IntelliSense**  
  
 **Piccola (16 x 16) progetto** icone devono avere non più di due elementi: una base e un modificatore.  
  
 ![icona di 16x16 progetto &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404 43_16x16Project1") ![icona di 16x16 progetto &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404 44_16x16Project2") ![icona di 16x16 progetto &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404 45_16x16Project3")  
  
 **Esempi di piccole icone di progetto (16 x 16)**  
  
 **Progetto di grandi dimensioni (32x32)** icone sono costituiti da non più di quattro elementi seguenti: una base, uno o due modificatori e una delle lingue della sovrimpressione.  
  
 ![icone di 32x32 progetto](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404 46_32x32Project")  
  
 **Esempi di grandi dimensioni icone di progetto (32x32)**  
  
### <a name="production-details"></a>Dettagli di produzione  
 Tutti i nuovi elementi dell'interfaccia utente devono essere creati usando Windows Presentation Foundation (WPF) e tutte le nuove icone per WPF devono essere nel formato PNG a 32 bit. Il file PNG 24 bit è un formato legacy che non supporta la trasparenza e pertanto non è consigliato per le icone.  
  
 Salvare la risoluzione a 96 DPI.  
  
#### <a name="file-types"></a>Tipi di file  
  
-   **PNG a 32 bit:** nel formato preferito per le icone. Un formato di file compressione senza perdita di dati che può archiviare un'immagine raster single (pixel). file PNG a 32 bit supportano la trasparenza di canale alfa, la correzione gamma e interlacciamento.  
  
-   **32 bit BMP:** per i controlli non WPF. Noto anche come XP o colori, 32 bit BMP è un formato di immagine RGB/A, un'immagine del true-color con trasparenza una canale alfa. Il canale alfa è un livello di trasparenza designata in Adobe Photoshop che verranno poi salvati in bitmap come un aggiuntiva (quarta) il canale del colore. Durante la produzione di opere a tutti i file BMP 32 bit per fornire un'indicazione visiva rapida sulla profondità di colore viene aggiunto un sfondo nero. Lo sfondo nero rappresenta l'area a cui applicare nell'interfaccia utente.  
  
-   **32 bit ICO:** per le icone di progetto e Aggiungi elemento. Tutti i file ICO sono true colori a 32 bit con la trasparenza di canale alfa (RGB/A). Poiché i file ICO possono archiviare più formati e intensità di colore, le icone Vista sono spesso in formato ICO contenente 16x16, 32x32, 48 x 48 e dimensioni delle immagini di 256 x 256. Per visualizzare correttamente in Windows Explorer, i file ICO devono essere salvati a discesa per intensità di colore a 24 bit e a 8 bit per ogni dimensione dell'immagine.  
  
-   **XAML:** per le aree di progettazione e gli strumenti decorativi visuali di Windows. Le icone XAML sono file di immagine basato su vettore che supportano la scalabilità, la rotazione, archiviazione e la trasparenza. Non sono comuni in Visual Studio oggi stesso, ma stanno diventando più popolari a causa delle loro flessibilità.  
  
-   **SVG**  
  
-   **24 bit BMP:** per la barra dei comandi di Visual Studio. Un formato di immagine true-color: RGB(0, 24 bit BMP è una convenzione di icona che crea un livello di trasparenza come chiave di colore per un livello di trasparenza orizzontale knock tramite magenta (255 = R, G = 0, B = 255). In un'immagine BMP 24 bit, tutte le superfici magenta vengono visualizzate utilizzando il colore di sfondo.  
  
-   **GIF 24 bit:** per la barra dei comandi di Visual Studio. Un formato di immagine RGB true-color che supporta la trasparenza. File GIF vengono spesso usati in opere di procedura guidata e animazioni GIF.  
  
### <a name="icon-construction"></a>Costruzione di icona  
 Le dimensioni dell'icona in Visual Studio più piccola sono 16x16. La più grande in comune usare è 32x32. Tenere a mente non per riempire l'intero fotogramma 16 x 16, 24 x 24 o 32 x 32 quando si progetta un'icona. Costruzione di icona leggibili, uniform è essenziale per riconoscimento degli utenti. Rispettare quanto riportato di seguito durante la creazione di icone.  
  
- Le icone devono essere chiaro comprensibile e coerente.  
  
- È consigliabile usare gli elementi di notifica di stato sotto forma di icone singole e non a sovrapporli all'inizio di un elemento di base sull'icona. In determinati contesti, l'interfaccia utente potrebbe richiedere l'elemento di stato per poter essere associati con un elemento di base.  
  
- Icone di progetto sono in genere i file con estensione ico che contengono diverse dimensioni. Vengono aggiornate solo le icone 16x16, 24x24 e 32x32. La maggior parte delle icone 16x16 e 24x24 conterrà gli stessi elementi. Le icone di 32 x 32 contengono informazioni più dettagliate, incluso il tipo di linguaggio di progetto quando applicabile.  
  
- Per le icone di 32 x 32, elementi di base in genere hanno uno spessore di linea 2 pixel. Uno spessore di linea 1 o 2 pixel può essere utilizzato per elementi di dettaglio. Usare giudizio per determinare che è più adatto.  
  
- Disporre di almeno un 1 pixel la spaziatura tra gli elementi per 16 x 16 e le icone di 24 x 24. Per le icone di 32 x 32, usare 2 pixel spaziatura tra gli elementi e tra il modificatore ed elemento di base.  
  
  ![Spaziatura elementi per icone 16x16, 24x24 e 32x32](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404 47_ElementSpacing")  
  
  **Spaziatura elementi per le icone di dimensioni pari a 16x16, 24x24 e 32x32**  
  
#### <a name="color-and-accessibility"></a>Colore e l'accessibilità  
 Linee guida per la conformità di Visual Studio richiedono che tutte le icone all'interno del prodotto passare i requisiti di accessibilità per colore e a contrasto elevato. Questo risultato viene ottenuto tramite inversione icona e durante la progettazione, è necessario essere consapevoli che verrà invertiti a livello di codice all'interno del prodotto.  
  
 Per altre informazioni sull'utilizzo dei colori nelle icone di Visual Studio, vedere [con colore nelle immagini](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a> Utilizzando colore nelle immagini  
  
### <a name="overview"></a>Panoramica  
 Le icone in Visual Studio sono principalmente monocromatica. Colore è riservato per comunicare informazioni specifiche e mai per effetto. Colore viene usato:  
  
-   per indicare un'azione  
  
-   Per ricevere un avviso all'utente una notifica sullo stato  
  
-   Per definire un'affiliazione di linguaggio  
  
-   per distinguere gli elementi all'interno di IntelliSense  
  
### <a name="accessibility"></a>Accessibilità  
 Linee guida per la conformità di Visual Studio richiedono che tutte le icone selezionata nel passaggio di prodotti i requisiti di accessibilità per colore e a contrasto elevato. Colori della tavolozza del linguaggio visivo sono stati testati e soddisfano questi requisiti.  
  
#### <a name="color-inversion-for-dark-themes"></a>Inversione di colore per i temi scuri  
 Per visualizzare le icone con il contrasto corretto con tema scuro di Visual Studio, un'inversione viene applicata a livello di codice. I colori in questa guida sono stati scelti in parte in modo che essi Inverti correttamente. Limitare l'uso del colore per questo riquadro o si otterranno risultati imprevedibili quando viene applicato l'inversione.  
  
 ![Esempi di icone i cui colori sono stati invertiti](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405 01_DarkThemeInversion")  
  
 **Esempi di icone di cui si sono verificati i colori invertiti**  
  
### <a name="base-palette"></a>Tavolozza di base  
 Tutte le icone standard contengono tre colori di base. Le icone non contengono alcun sfumature o ombreggiature, con una o due eccezioni per le icone dello strumento di 3D.  
  
|Utilizzo|nome|Valore (con tema chiaro)|Campione|Esempio|  
|-----------|----------|---------------------------|------------|-------------|  
|Sfondo/scuro|VS BG|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Esempio di tavolozza di base](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405 02_BasePaletteExample")|  
|In primo piano/leggera|VS FG|F0EFF1 / 240,239,241|![Campione F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||  
|Struttura|Visual Studio Out|F6F6F6 / 246,246,246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||  
  
 Oltre ai colori di base, ogni icona può contenere un aggiuntivo colore dalla tavolozza estesa.  
  
### <a name="extended-palette"></a>Tavolozza estesa  
  
#### <a name="action-modifiers"></a>Modificatori di azione  
 I quattro colori riportato di seguito indicano i tipi di azioni necessarie per i modificatori di azione:  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|Positivo|Visual Studio azione verde|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|  
|Negativo|Visual Studio azione rosso|A1260D / 161,38,13|![Campione A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|  
|Lingua di sistema|Visual Studio azione blu|00539C / 0,83,156|![Campione 00539c](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|  
|Crea/nuovo|Visual Studio azione arancione|C27D1A / 194,156,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Esempi  
 Verde viene usato per i modificatori di azione positiva, ad esempio "Add", "Esegui", "Play" e "Convalida".  
  
|||||  
|-|-|-|-|  
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405 03_ActionModifierRun") **eseguire**|![Icona query Execute](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405 04_ExecuteQuery") **Esegui Query**|![Tutti i passaggi icona Riproduci](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405 05_PlayAllSteps") **Riproduci tutti i passaggi**|![Aggiungi icona del controllo](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405 06_AddControl") **Aggiungi controllo**|  
  
 Rosso viene usato per i modificatori di azione negativo, ad esempio "Elimina," "Stop", "Annullamento" e "Chiudi".  
  
|||||  
|-|-|-|-|  
|![Icona Elimina relazioni](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405 07_DeleteRelationship") **Elimina relazione**|![Icona Elimina colonna](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405 08_DeleteColumn") **Elimina colonna**|![Icona query Arresta](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405 09_StopQuery") **arresta Query**|![Icona connessione offline](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405 10_ConnectionOffline") **non in linea di connessione**|  
  
 Blu viene applicata all'azione neutro modificatori più comunemente rappresentate come frecce, ad esempio "Aperta", "Avanti", "Indietro", "Importa" e "Esporta".  
  
|||||  
|-|-|-|-|  
|![Andare all'icona di campo](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405 11_GoToField") **passare al campo**|![In batch di controllo&#45;icona](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405 12_BatchedCheckIn") **controllo aggiuntivo in batch**|![Icona editor di indirizzo](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405 13_AddressEditor") **Editor di indirizzo**|![Icona editor di associazione](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405 14_AssociationEditor") **Editor di associazione**|  
  
 Oro scuro viene usata principalmente per il modificatore "Nuovo".  
  
|||||  
|-|-|-|-|  
|![Icona Nuovo progetto](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405 15_NewProject") **nuovo progetto**|![Crea nuova icona di grafo](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405 16_CreateNewGraph") **creare nuovo grafico**|![Icona nuovo unit test](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405 17_NewUnitTest") **nuovi Unit Test**|![Icona Nuovo elemento di elenco](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405 18_NewListItem") **nuovo elemento elenco**|  
  
#### <a name="special-cases"></a>Casi speciali  
 In casi particolari, azione colorato può possibile usare un modificatore in modo indipendente come icona autonomo. Il colore utilizzato per l'icona riflette le azioni che è associata l'icona. Questo utilizzo è limitato a un piccolo subset delle icone, tra cui:  
  
||||||  
|-|-|-|-|-|  
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405 03_ActionModifierRun") **eseguire**|![Icona Arresta](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405 19_Stop") **arrestare**|![Icona di eliminazione](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405 20_Delete") **Delete**|![Icona Salva](../../extensibility/ux-guidelines/media/0405-21-save.png "0405 21_Save") **Salva**|![Icona Indietro Navigate](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405 22_NavigateBack") **Esplora indietro**|  
  
### <a name="code-hierarchy-palette"></a>Riquadro gerarchia code  
  
#### <a name="folder"></a>Cartella  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|Esempio|  
|-----------|----------|--------------------------|------------|-------------|  
|Cartelle|Cartella|DCB67A / 220,182,122|![Swatch DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Icona della cartella colore](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405 23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Linguaggi di Visual Studio  
 Ogni i comuni linguaggi o piattaforme disponibili in Visual Studio è associato alcun colore. Vengono usati questi colori sull'icona di base, o sui modificatori di linguaggio che vengono visualizzati nell'angolo superiore destro delle icone composte.  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF blu|0095D7 / 0,149,215|![Campione 0095d7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|  
|C++|Viola CPP|9B4F96 / 155,79,150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|  
|C#|CS verde (verde azione di Visual Studio)|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|  
|CSS|Red CSS|BD1E2D / 189,30,45|![Swatch BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|  
|F#|FS viola|672878 / 103,40,120|![Swatch 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|  
|JavaScript|JS arancione|F16421 / 241,100,33|![Campione F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|  
|VB|VB Blue (blu azione di Visual Studio)|00539C / 0,83,156|![Campione 00539c](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|  
|TypeScript|Servizi terminal arancione|E04C06 / 224,76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|  
|Python|PIA verde|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Esempi di icone con i modificatori di linguaggio  
  
|||||||  
|-|-|-|-|-|-|  
|![Icona di Visual Basic](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405 25_VB") **VB**|![C&#35; icona](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405 26_CSharp")**C#**|![C&#43; &#43; sull'icona](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405 27_CPlusPlus") **C++**|![F&#35; icona](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405 28_FSharp")**F#**|![Icona di JavaScript](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405 29_JavaScript") **JavaScript**|![Icona di Python](../../extensibility/ux-guidelines/media/0405-30-python.png "0405 30_Python") **Python**|  
|![Icona HTML](../../extensibility/ux-guidelines/media/0405-31-html.png "0405 31_HTML") **HTML**|![Icona di WPF](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405 32_WPF") **WPF**|![Icona di ASP](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405 33_ASP") **ASP**|![Icona di CSS](../../extensibility/ux-guidelines/media/0405-34-css.png "0405 34_CSS") **CSS**|![Icona di TypeScript](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405 35_TypeScript") **TypeScript**||  
  
#### <a name="intellisense"></a>IntelliSense  
 Icone per IntelliSense utilizzano una tavolozza dei colori esclusivo. Tali colori vengono utilizzati per consentire agli utenti di distinguere rapidamente tra i diversi elementi nell'elenco popup di IntelliSense.  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|Classe di evento,|Visual Studio azione arancione|C27D1A / 194,125,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|  
|Metodo di estensione, metodo, modulo, delegato|Visual Studio azione viola|652 90 D / 101,45,144|![Campione 652d90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|  
|Campo, elemento di enumerazione, Macro, struttura, tipo di valore di unione, operatore, interfaccia|Visual Studio azione blu|00539C / 0,83,156|![Campione 00539c](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|  
|Object|Visual Studio azione verde|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|  
|Costante, eccezioni, elemento di enumerazione, mappa, elemento della mappa, Namespace, modello di definizione dei tipi|In background (BG Visual Studio)|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Esempi di icone per IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Icona della classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405 36_IntelliSenseClass") **classe**|![Icona dell'evento privato IntelliSense](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent") **evento privato**|![Icona del delegato IntelliSense](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405 38_IntelliSenseDelegate") **delegato**|![Icona descrittiva del metodo IntelliSense](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend") **Friend (metodo)**|![Icona del campo](../../extensibility/ux-guidelines/media/0405-40-field.png "0405 40_Field") **campo**|  
|![IntelliSense protetti icona dell'elemento enum](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem") **elemento Enum protetto**|![Icona dell'oggetto IntelliSense](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405 42_IntelliSenseObject") **oggetto**|![Icona del modello IntelliSense](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405 43_IntelliSenseTemplate") **modello**|![Icona di collegamento eccezione IntelliSense](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut") **scelta rapida di eccezione**||  
  
### <a name="notifications"></a>Notifiche  
 Le notifiche in Visual Studio vengono usate per indicare lo stato. La tavolozza di notifica utilizza i seguenti quattro colori, nonché le opzioni di riempimento colore nero o bianco in primo piano, per definire le notifiche con i seguenti livelli di stato.  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|Stato: neutro|Notifica Blue (blu di Visual Studio)|1BA1E2 / 27,161,226|![Campione 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|  
|Stato: positiva|Notifica verde (verde Visual Studio)|339933 / 51,153,51|![Campione 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|  
|Stato: negativa|Notifica Red (rosso di Visual Studio)|E51400 / 229,20,0|![Swatch E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|  
|Stato: avviso|Notifica giallo (arancione Visual Studio)|FFCC00 / 255,204,0|![Campione FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|  
|Riempimento di primo piano|Notifica nero (nero)|000000 / 0,0,0|![Campione &#35;000000](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|  
|Riempimento di primo piano|Notifica White (bianco)|FFFFFF / 255,255,255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Esempi di icone di notifica  
  
|||||  
|-|-|-|-|  
|![Icona di avviso](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405 45_Alert") **avviso**|![Icona di avviso](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405 48_Warning") **avviso**|![Icona completato](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405 46_Complete") **completa**|![Icona Arresta](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405 47_Stop") **arrestare**|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 In generale, Visual Studio Online include funzionalità ospitate in un browser. Il colore varia in ambienti diversi, ma lo stile rimane invariato.  
  
|Raggruppa|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Sfondo|TFSO BG|656565/ 101, 101, 101|![Campione 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|  
|TFS|Struttura|TFSO OUT|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|Napa|Sfondo|Bianco|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|Monaco|Sfondo|Bianco|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|F12|Sfondo|Bianco|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|F12|Normale|Grey_Primary F12|555555 / 85, 85, 85|![Campione 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|  
|F12|Passaggio del mouse|F12 Blue_Hover|2279BF / 34,121,191|![Swatch 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|  
|F12|Disabilitato|LtGrey_Disabled F12|ABABAC / 171,171,172|![Swatch ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|  
|F12|Dello sfondo al passaggio del mouse|Passare il mouse bg|D9EBF7 / 217,235,247|![Swatch D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|  
|F12|Sfondo premuta|Bg premuto|B2D7F0 / 178,215,240|![Swatch B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|  
|F12|Struttura|VISUAL STUDIO OUT|F6F6F6 / 246,246,246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|  
|F12|Informazioni|Informazioni|00BCF2 / 0,188,242|![Campione 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|  
|F12|Avviso|Avviso|F28300 / 242,131,0|![Campione F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|  
|F12|Errore / Negative|Error_Negative|E81123 / 232,17,35|![Campione E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|  
|F12|Avviare / positivo|Start_Positive|009E49 / 0,158,73|![Campione 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|  
|F12|Tipo di interruzione|Tipo di interruzione|9B4F96 / 155,79,150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|  
|F12|Contrassegno di eventi|Contrassegno di eventi|A51F00 / 165,31,0|![Swatch A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|  
|F12|Contrassegno utente|Contrassegno utente|F16220 / 241,98,32|![Campione F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Esempi di icone di Visual Studio Online  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Icona team TFS Online](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405 49_TFSOnlineTeam") **Team Online**|![Icona di informazioni TFS](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405 50_TFSInformation") **informazioni**|![Icona cronologia TFS](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405 51_TFSHistory") **cronologia**|![Icona del branch TFS](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405 52_TFSBranch") **ramo**|  
  
|Napa||||  
|----------|-|-|-|  
|![Icona del contenuto Napa](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405 53_NapaContent") **contenuto**|![Icona posta elettronica di office Napa](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405 54_NapaOfficeMail") **posta elettronica di Office**|![Icona di SharePoint Napa](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405 55_NapaSharePoint") **SharePoint**|![Icona del riquadro attività Napa](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405 56_NapaTaskPane") **riquadro attività**|  
  
|Monaco||||  
|------------|-|-|-|  
|![Icona dei file Monaco](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405 57_MonacoFiles") **file**|![Icona Git Monaco](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405 58_MonacoGit") **Git**|![Icona di ricerca Monaco](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405 59_MonacoSearch") **ricerca**|![Icona di testo Monaco](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405 60_MonacoText") **testo**|  
  
|F12||||  
|---------|-|-|-|  
|![Icona codice pretty F12](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405 61_F12PrettyCode") **molto codice**|![Icona di avviso F12](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405 62_F12Warning") **avviso**|![Icona di emulazione F12](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405 63_F12Emulate") **Emulate**|

