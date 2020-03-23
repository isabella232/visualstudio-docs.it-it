---
title: Immagini e icone per Visual Studio . Documenti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303197"
---
# <a name="images-and-icons-for-visual-studio"></a>Immagini e icone per Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Utilizzo dell'immagine in Visual StudioImage use in Visual Studio
 Prima di creare la grafica, è consigliabile utilizzare più di 1.000 immagini nella libreria di immagini di [Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Tipi di immagini

- **Icone**. Piccole immagini visualizzate in comandi, gerarchie, modelli e così via. La dimensione predefinita dell'icona utilizzata in Visual Studio è un file PNG 16x16.The default icon size used in Visual Studio is a 16x16 PNG. Le icone prodotte dal servizio immagini generano automaticamente il formato XAML per il supporto HDPI.

    > [!NOTE]
    > Mentre le immagini vengono utilizzate nel sistema di menu, non è necessario creare un'icona per ogni comando. Consultare [i menu e i comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) per verificare se il comando deve ottenere un'icona.

- **Miniature.** Immagini utilizzate nell'area di anteprima di una finestra di dialogo, ad esempio la finestra di dialogo Nuovo progetto.

- **Immagini della finestra di dialogo.** Immagini visualizzate nelle finestre di dialogo o nelle procedure guidate, come elementi grafici descrittivi o indicatori di messaggio. Utilizzare raramente e solo quando necessario per illustrare un concetto difficile o ottenere l'attenzione dell'utente (avviso, avviso).

- **Immagini animate.** Utilizzato negli indicatori di stato, nelle barre di stato e nelle finestre di dialogo delle operazioni.

- **Cursori.** Utilizzato per indicare se un'operazione è consentita utilizzando il mouse, dove un oggetto può essere rilasciato e così via.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Design delle icone

### <a name="overview"></a>Panoramica
 Visual Studio usa icone di tipo moderno, che hanno una geometria pulita e un equilibrio 50/50 di positivo/negativo (luce/scuro) e usano metafore dirette e comprensibili. I punti di progettazione delle icone cruciali sono incentrati su chiarezza, semplificazione e contesto.

- **Chiarezza:** concentrarsi sulla metafora di base che dà a un'icona il suo significato e la sua individualità.

- **Semplificazione:** ridurre l'icona al suo significato principale - ottenere il tema attraverso con solo gli elementi necessari (s) e senza fronzoli.

- **Contesto:** considerare tutti gli aspetti del ruolo di un'icona durante lo sviluppo del concetto, che è fondamentale quando si decide quali elementi costituiscono la metafora principale dell'icona.

  Con le icone, ci sono una serie di punti di progettazione da evitare:

- Non usare icone che indicano elementi dell'interfaccia utente tranne quando appropriato. Scegliere un approccio più astratto o simbolico quando l'elemento dell'interfaccia utente non è comune, evidente né univoco.

- Non usare eccessivamente elementi comuni come documenti, cartelle, frecce e la lente di ingrandimento. Utilizzare tali elementi solo quando è essenziale per il significato dell'icona. Ad esempio, la lente di ingrandimento rivolta a destra deve indicare solo Cerca, Sfoglia e Trova.

- Anche se alcuni elementi icona legacy mantengono l'uso della prospettiva, non creare nuove icone con prospettiva a meno che l'elemento non manchi di chiarezza senza di esso.

- Non inserire troppe informazioni in un'icona. Un'immagine semplice che può essere facilmente riconosciuta o appresa come simbolo riconoscibile è molto più utile di un'immagine eccessivamente complessa. Un'icona non può raccontare tutta la storia.

### <a name="icon-creation"></a>Creazione delle icone

#### <a name="concept-development"></a>Sviluppo del concetto
 Visual Studio ha all'interno della propria interfaccia utente un'ampia gamma di tipi di icona. Considerare attentamente il tipo di icona durante lo sviluppo. Non usare oggetti dell'interfaccia utente non chiari o non comuni per gli elementi icona. In questi casi, optare per il simbolo, ad esempio con l'icona Smart Tag. Si noti che il significato del tag astratto a sinistra è più evidente della versione vaga basata sull'interfaccia utente a destra:

|||
|-|-|
|**Uso corretto delle immagini simboliche**|**Uso non corretto di immagini simboliche**|
|![Icona smart tag corretta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icona smart tag non corretta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Esistono casi in cui gli elementi dell'interfaccia utente standard e facilmente riconoscibili funzionano bene per le icone. Aggiungi finestra è uno di questi esempi:Add Window is one such example:

|||
|-|-|
|**Correggere l'elemento dell'interfaccia utente in un'iconaCorrect UI element in an icon**|**Elemento dell'interfaccia utente non corretto in un'icona**|
|![Icona Aggiungi finestra corretta](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icona Aggiungi finestra non corretta](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Non usare un documento come elemento di base a meno che non sia essenziale per il significato dell'icona. Senza l'elemento documento in Aggiungi documento (sotto) il significato viene perso, mentre con Aggiorna l'elemento documento non è necessario comunicare il significato.

|||
|-|-|
|**Uso corretto dell'icona del documento**|**Utilizzo non corretto dell'icona del documento**|
|![Icona Documento corretta](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icona Documento non corretta](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Il concetto di "show" deve essere rappresentato dall'icona che meglio illustra ciò che viene visualizzato, ad esempio con l'esempio Mostra tutti i file. Una metafora dell'obiettivo può essere usata per indicare il concetto di "vista", se necessario, ad esempio con l'esempio di Visualizzazione risorse.

|||
|-|-|
|**"Mostra"**|**"Visualizza"**|
|![Icona Mostra](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icona Visualizza](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 L'icona della lente di ingrandimento rivolta a destra deve rappresentare solo Cerca, Trova e Sfoglia. La variante rivolta a sinistra con il segno più o meno deve rappresentare solo lo zoom avanti o indietro.

|||
|-|-|
|**"Cerca"**|**"Ingrandisci"**|
|![icona Cerca](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icona Zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Nelle viste ad albero, non utilizzare sia l'icona della cartella che un modificatore. Se disponibile, utilizzare solo il modificatore.

|||
|-|-|
|**Correggere le icone della vista ad albero**|**Icone della vista ad albero non corrette**|
|![Correggere l'icona](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") della vista ad albero &#40;1&#41;corretta icona della ![vista ad albero &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icona](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") della vista ad albero non corretta &#40;1&#41;icona della vista ad albero non corretta &#40;2 ![&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Dettagli stile

#### <a name="layout"></a>Layout
 Impilare gli elementi come illustrato per le icone standard 16x16:

 ![Stack di layout per icone 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Stack di layout per icone 16x16

 Gli elementi di notifica dello stato sono meglio utilizzati come icone autonome. Esistono contesti, tuttavia, in cui una notifica deve essere impilata sull'elemento di base, ad esempio con l'icona Completamento attività:There are contexts, however, in which a notification should be stacked on the base element, such as with the Task Complete icon:

 ![Notifiche autonome in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Icone di notifica autonome

 ![Icona Attività completata](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icona Attività completata

 Le icone del progetto sono in genere file con estensione ico che contengono più dimensioni. La maggior parte delle icone 16x16 contengono gli stessi elementi. Le versioni 32x32 hanno maggiori dettagli, incluso il tipo di progetto, se applicabile.

 ![Icone di progetto in Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Icone del progetto della libreria di controlli Windows VB, 16x16 e 32x32

 Centra un'icona all'interno del relativo fotogramma pixel. Se ciò non è possibile, allineare l'icona alla parte superiore e/o destra della cornice.

 ![Icona centrata nel frame di pixel](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icona centrata nel frame di pixel

 ![Icona allineata al lato superiore destro del frame di pixel](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icona allineata in alto a destra della cornice

 ![Icona centrata e allineata al lato superiore del frame di pixel](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icona centrata e allineata alla parte superiore della cornice

 Per ottenere l'allineamento e l'equilibrio ideali, evitate di ostruire l'elemento di base dell'icona con i glifi delle azioni. Posizionate il glifo nella parte superiore sinistra dell'elemento di base. Quando si aggiunge un elemento aggiuntivo, considerare l'allineamento e il bilanciamento dell'icona.

|||
|-|-|
|**Corretto allineamento e bilanciamento**|**Allineamento e bilanciamento errati**|
|![Equilibrio e allineamento corretti dell'icona](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Equilibrio e allineamento non corretti dell'icona](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Garantire la parità delle dimensioni per le icone che condividono elementi e vengono utilizzate nei set. Si noti che nell'associazione errata, il cerchio e la freccia sono sovradimensionati e non corrispondono.

|||
|-|-|
|**Parità di dimensioni corretta**|**Parità di dimensioni non corretta**|
|![Dimensioni e parità corrette dell'icona](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Dimensioni e parità non corrette dell'icona](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Utilizzare spessori di linea e visivi coerenti. Valutare il confronto tra l'icona che si sta creando e altre icone utilizzando un confronto affiancato. Non utilizzare mai l'intero telaio 16x16, utilizzare 15x15 o più piccolo. Il rapporto negativo-positivo (da scuro a chiaro) deve essere 50/50.

|||
|-|-|
|**Corretto rapporto negativo-positivo**|**Rapporto negativo-positivo errato**|
|![Peso visivo corretto per le icone &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Peso visivo corretto per le icone &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Peso visivo corretto per le icone &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Impatto visivo non corretto per le icone](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Usa forme semplici e comparabili e angoli complementari per costruire i tuoi elementi senza sacrificare l'integrità degli elementi. Se possibile, utilizzare angoli di 45 o 90 o 90 gradi.

 ![Angoli corretti per le icone](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Prospettiva
 Mantenere l'icona chiara e comprensibile. Usa la prospettiva e una fonte di luce solo quando necessario. Anche se l'uso della prospettiva sugli elementi icona deve essere evitato, alcuni elementi non sono riconoscibili senza di esso. In questi casi, una prospettiva stilizzata comunica la chiarezza dell'elemento.

 ![Prospettiva a tre punti](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Prospettiva a tre punti

 ![Prospettiva a un punto](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Prospettiva a un punto

 La maggior parte degli elementi deve essere rivolta o inclinata verso destra:

 ![Icone con angolazione corretta](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Utilizzare le sorgenti luminose solo quando si aggiunge la chiarezza necessaria a un oggetto.

|||
|-|-|
|**Sorgente luminosa corretta**|**Sorgente luminosa errata**|
|![Sorgenti di luce corrette per le icone](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Sorgenti di luce non corrette per le icone](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Utilizzare i contorni solo per migliorare la leggibilità o per comunicare meglio la metafora. Il saldo negativo-positivo (chiaro-scuro) deve essere 50/50.

|||
|-|-|
|**Uso corretto dei contorni**|**Uso non corretto dei contorni**|
|![Strutture corrette](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Strutture non corrette](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipi di icone
 **Le** icone della shell e della barra dei comandi sono costituite da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone della shell e della barra dei comandi](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Esempi di icone della shell e della barra dei comandi

 **Le** icone della barra dei comandi della finestra degli strumenti sono costituite da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone della barra dei comandi della finestra degli strumenti](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Esempi di icone della barra dei comandi della finestra degli strumenti

 Le icone di **disambiguatore** della visualizzazione albero sono costituite da non più di tre degli elementi seguenti: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone di disambiguatore della visualizzazione struttura](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Esempi di icone di disambiguatore della visualizzazione struttura

 Le icone di **tassonomia** dei valori basati sullo stato sono presenti nei seguenti stati: attivo, attivo disabilitato e inattivo disabilitato.

 ![Esempi di icone di tassonomia dei valori basata sullo stato](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Esempi di icone di tassonomia dei valori basata sullo stato

 Le icone **IntelliSense** sono costituite da non più di tre dei seguenti elementi: una base, un modificatore e uno stato.

 ![Esempi di icone IntelliSenseExamples of IntelliSense icons](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Esempi di icone IntelliSenseExamples of IntelliSense icons

 Le icone **di progetto piccole (16x16)** non devono avere più di due elementi: una base e un modificatore.

 ![Esempi di icone di progetto di piccole dimensioni (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") icona progetto ![16x16 icona](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") del progetto &#40;2&#41;icona del ![progetto 16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Esempi di icone di progetto di piccole dimensioni (16x16)

 Le icone di **progetto grandi (32x32)** sono costituite da non più di quattro dei seguenti elementi: una base, uno o due modificatori e una sovrapposizione di linguaggio.

 ![Esempi di icone di progetto di grandi dimensioni (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Esempi di icone di progetto di grandi dimensioni (32x32)

### <a name="production-details"></a>Dettagli di produzione
 Tutti i nuovi elementi dell'interfaccia utente devono essere creati utilizzando Windows Presentation Foundation (WPF) e tutte le nuove icone per WPF devono essere in formato PNG a 32 bit. Il formato PNG a 24 bit è un formato legacy che non supporta la trasparenza e pertanto non è consigliato per le icone.

 Salvare la risoluzione a 96 DPI.

#### <a name="file-types"></a>Tipi di file

- PNG a **32 bit:** il formato preferito per le icone. Formato di file di compressione dei dati senza perdita di dati in grado di archiviare una singola immagine raster (pixel). I file PNG a 32 bit supportano la trasparenza del canale alfa, la correzione gamma e l'interlacciamento.

- **BMP a 32 bit:** per controlli non WPF. Chiamato anche XP o a colori alti, BMP a 32 bit è un formato di immagine RGB/A, un'immagine a colori reali con una trasparenza alfa-canale. Il canale alfa è un livello di trasparenza designato in Adobe Photoshop che viene quindi salvato all'interno della bitmap come canale di colore aggiuntivo (quarto). Uno sfondo nero viene aggiunto durante la produzione di grafica a tutti i file BMP a 32 bit per fornire un rapido segnale visivo sulla profondità del colore. Questo sfondo nero rappresenta l'area da mascherare nell'interfaccia utente.

- ICO a **32 bit:** per le icone di progetto e Aggiungi elemento. Tutti i file ICO sono a 32 bit di colore reale con trasparenza alfa-canale (RGB/A). Poiché i file ICO possono memorizzare più dimensioni e profondità di colore, le icone di Vista sono spesso in un formato ICO contenente dimensioni di immagine 16x16, 32x32, 48x48 e 256x256. Per poter essere visualizzati correttamente in Esplora risorse, i file ICO devono essere salvati a profondità di colore a 24 e 8 bit per ogni dimensione dell'immagine.

- **XAML:** per le aree di progettazione e gli strumenti decorativi di Windows. Le icone XAML sono file di immagine basati su vettori che supportano il ridimensionamento, la rotazione, l'archiviazione e la trasparenza. Non sono comuni in Visual Studio oggi, ma stanno diventando sempre più popolari a causa della loro flessibilità.

- **SVG**

- **BMP a 24 bit:** per la barra dei comandi di Visual Studio. Un formato di immagine RGB a colori reali, BMP a 24 bit è una convenzione di icona che crea un livello di trasparenza utilizzando magenta (R.255, G-0, B-255) come chiave di colore per un livello di trasparenza knock-out. In un BMP a 24 bit, tutte le superfici magenta vengono visualizzate utilizzando il colore di sfondo.

- GIF a **24 bit:** per la barra dei comandi di Visual Studio. Formato di immagine RGB a colori che supporta la trasparenza. I file GIF vengono spesso utilizzati nella grafica della procedura guidata e nelle animazioni GIF.

### <a name="icon-construction"></a>Costruzione di icone
 La dimensione dell'icona più piccola in Visual Studio è 16x16.The smallest icon size in Visual Studio is 16x16. Il più grande di uso comune è 32x32. Tenere presente di non riempire l'intero riquadro 16x16, 24x24 o 32x32 durante la progettazione di un'icona. La costruzione uniforme e leggibile delle icone è essenziale per il riconoscimento da parte dell'utente. Attenersi ai seguenti punti durante la creazione di icone.

- Le icone devono essere chiare, comprensibili e coerenti.

- È preferibile utilizzare gli elementi di notifica dello stato come icone singole e non impilarli sopra un elemento di base dell'icona. In alcuni contesti, l'interfaccia utente potrebbe richiedere l'elemento status da associare a un elemento di base.

- Le icone del progetto sono in genere file con estensione ico che contengono diverse dimensioni. È in corso l'aggiornamento solo delle icone 16x16, 24x24 e 32x32. La maggior parte delle icone 16x16 e 24x24 conterrà gli stessi elementi. Le icone 32x32 contengono ulteriori dettagli, incluso il tipo di linguaggio del progetto, se applicabile.

- Per le icone 32x32, gli elementi di base hanno in genere uno spessore di linea di 2 pixel. Per gli elementi di dettaglio è possibile utilizzare uno spessore di linea di 1 o 2 pixel. Usa il tuo giudizio migliore per determinare quale è più adatto.

- Avere una spaziatura di almeno 1 pixel tra gli elementi per le icone 16x16 e 24x24. Per le icone 32x32, utilizzare la spaziatura di 2 pixel tra gli elementi e tra il modificatore e l'elemento di base.

  ![Spaziatura degli elementi per icone di dimensioni 16x16, 24x24 e 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Spaziatura degli elementi per icone di dimensioni 16x16, 24x24 e 32x32

#### <a name="color-and-accessibility"></a>Colore e accessibilità
 Le linee guida per la conformità di Visual Studio richiedono che tutte le icone nel prodotto superino i requisiti di accessibilità per colore e contrasto. Ciò si ottiene tramite l'inversione dell'icona e, quando si progetta, è necessario tenere presente che verranno invertiti a livello di codice nel prodotto.

 Per ulteriori informazioni sull'utilizzo del colore nelle icone di Visual Studio, consultate [Utilizzo del colore nelle immagini.](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Uso del colore nelle immagini

### <a name="overview"></a>Panoramica
 Le icone in Visual Studio sono principalmente monocromatiche. Il colore è riservato per trasmettere informazioni specifiche e mai per la decorazione. Viene utilizzato il colore:

- per indicare un'azione

- per avvisare l'utente di una notifica di stato

- per designare l'affiliazione linguistica

- per differenziare gli elementi all'interno di IntelliSense

### <a name="accessibility"></a>Accessibilità
 Le linee guida per la conformità di Visual Studio richiedono che tutte le icone archiviate nel prodotto superino i requisiti di accessibilità per colore e contrasto. I colori nella tavolozza della lingua visiva sono stati testati e soddisfano questi requisiti.

#### <a name="color-inversion-for-dark-themes"></a>Inversione colore per temi scuri
 Per fare in modo che le icone vengano visualizzate con il rapporto di contrasto corretto nel tema scuro di Visual Studio, viene applicata un'inversione a livello di codice. I colori di questa guida sono stati scelti in parte in modo che si invertano correttamente. Limitare l'uso del colore a questa tavolozza, o si otterrà risultati imprevedibili quando viene applicata l'inversione.

 ![Esempi di icone i cui colori sono stati invertiti](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Esempi di icone i cui colori sono stati invertiti

### <a name="base-palette"></a>Tavolozza di base
 Tutte le icone standard contengono tre colori di base. Le icone non contengono sfumature o ombreggiature, con una o due eccezioni per le icone dello strumento 3D.

|Uso|Nome|Valore (tema chiaro)|Swatch|Esempio|
|-----------|----------|---------------------------|------------|-------------|
|Sfondo/Scuro|VS BG|424242 / 66,66,66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Esempio di tavolozza di base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Primo piano/Luce|VS FG|F0EFF1 / 240.239.241|![Campione F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Riquadro|VS Out|F6F6F6 / 246.246.246|![Campione F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Oltre ai colori di base, ogni icona può contenere un colore aggiuntivo dalla tavolozza estesa.

### <a name="extended-palette"></a>Tavolozza estesa

#### <a name="action-modifiers"></a>Modificatori di azione
 I quattro colori seguenti indicano i tipi di azioni richiesti dai modificatori di azione:

|Uso|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|Positive|VS Azione Verde|388A34 / 56.138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negative|VS Azione Rosso|A1260D / 161,38,13|![Campione A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutralità|VS Azione Blu|00539C / 0,83,156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Crea/Nuovo|VS Azione Arancione|C27D1A / 194.156,26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Esempi
 Il verde viene utilizzato per i modificatori di azione positiva come "Aggiungi", "Esegui", "Riproduci" e "Convalida".

|||||
|-|-|-|-|
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Esegui|![Icona Esegui query](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Eseguire la query|![Icona Riproduci tutti i passi](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Riproduci tutti i passaggi|![Icona Aggiungi controllo](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Aggiungi controllo|

 Il rosso viene utilizzato per i modificatori di azione negativi come "Elimina", "Stop", "Annulla" e "Chiudi".

|||||
|-|-|-|-|
|![Icona Elimina relazioni](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />Eliminare la relazione|![Icona Elimina colonna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Elimina colonna|![Icona Interrompi query](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Interrompi query|![Icona Connessione offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Connessione non in linea|

 Il blu viene applicato ai modificatori di azione neutra più comunemente rappresentati come frecce, ad esempio "Aperto", "Avanti", "Precedente", "Importa" ed "Esporta".

|||||
|-|-|-|-|
|![Icona Vai al campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Vai al campo|![Icona&#45;di controllo in batch](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Archiviazione in batch|![Icona Editor di indirizzo](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Editor indirizzi|![Icona Editor di associazione](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />Editor dell'associazione|

 L'oro scuro viene utilizzato principalmente per il modificatore "Nuovo".

|||||
|-|-|-|-|
|![Icona Nuovo progetto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Nuovo progetto|![Icona Crea Nuovo grafico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Crea nuovo grafico|![Icona Nuovo Unit test](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Nuovo unit test|![Icona Nuova voce di elenco](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Nuova voce di elenco|

#### <a name="special-cases"></a>Casi speciali
 In casi speciali, un modificatore di azione colorato può essere utilizzato in modo indipendente come icona autonoma. Il colore utilizzato per l'icona riflette le azioni a cui è associata l'icona. Questo utilizzo è limitato a un piccolo sottoinsieme di icone, tra cui:

||||||
|-|-|-|-|-|
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Esegui|![Icona Interrompi](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Arresto|![Icona Elimina](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />Delete|![Icona Salva](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Salvare|![Icona Esplora indietro](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Esplora indietro|

### <a name="code-hierarchy-palette"></a>Tavolozza della gerarchia del codice

#### <a name="folder"></a>Cartella

|Uso|Nome|Valore (tutti i temi)|Swatch|Esempio|
|-----------|----------|--------------------------|------------|-------------|
|Cartelle|Cartella|DCB67A / 220.182.122|![Campione DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icona del colore della cartella](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Lingue di Visual Studio
 Ognuno dei linguaggi o piattaforme comuni disponibili in Visual Studio ha un colore associato. Questi colori vengono utilizzati sull'icona di base o sui modificatori di lingua visualizzati nell'angolo superiore destro delle icone composte.

|Uso|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|BLU WPF HTML ASP|0095D7 / 0,149.215|![Campione 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP Viola|9B4F96 / 155.79.150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Green (VS Action Green)|388A34 / 56.138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|Rosso CSS|BD1E2D / 189,30,45|![Campione BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS Viola|672878 / 103,40,120|![Campione 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Arancione|F16421 / 241,100,33|![Campione F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blu (VS Action Blue)|00539C / 0,83,156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Arancione|E04C06 / 224,76,6|![Campione E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|VERDE PY|879636 / 135,150,54|![Campione 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Esempi di icone con modificatori di linguaggio

|||||||
|-|-|-|-|-|-|
|![Icona di Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![C icona&#35;](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C icona di&#43;&#43; ](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; icona](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![Icona di JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Icona di Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![Icona di HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Icona di WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Icona di ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Icona di CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Icona di TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Le icone IntelliSense utilizzano una tavolozza di colori esclusiva. Questi colori vengono utilizzati per consentire agli utenti di distinguere rapidamente tra i diversi elementi nell'elenco popup IntelliSense.These colors are used to help users quickly distinguish between the different items in the IntelliSense popup list.

|Uso|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|Classe, Evento|VS Azione Arancione|C27D1A / 194.125,26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metodo di estensione, metodo, modulo, delegato|VS Azione Viola|652D90 / 101.45.144|![Campione 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Campo, Elemento enum, Macro, Struttura, Tipo di valore Unione, Operatore, Interfaccia|VS Azione Blu|00539C / 0,83,156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Oggetto|VS Azione Verde|388A34 / 56.138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Costante, Eccezione, Elemento enum, Mappa, Elemento mappa, Spazio dei nomi, Modello, Definizione del tipo|Sfondo (VS BG)|424242 / 66,66,66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Esempi di icone IntelliSenseExamples of IntelliSense icons

||||||
|-|-|-|-|-|
|![Icona della classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Classe|![Icona dell'evento privato IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Evento privato|![Icona del delegato IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />Delegato|![Icona descrittiva del metodo IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Metodo Amico|![Icona del campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Campo|
|![Icona dell'elemento enum protetto IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Elemento enum protetto|![Icona dell'oggetto IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Oggetto|![Icona del modello IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Modello|![Icona del collegamento all'eccezione IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Scelta rapida eccezione||

### <a name="notifications"></a>Notifiche
 Le notifiche in Visual Studio vengono utilizzate per indicare lo stato. La tavolozza delle notifiche utilizza i seguenti quattro colori, nonché le opzioni di riempimento in primo piano in bianco o nero, per definire le notifiche con i seguenti livelli di stato.

|Uso|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|Stato: neutro|Notifica Blu (VS Blue)|1BA1E2 / 27.161.226|![Campione 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stato: positivo|Verde notifica (VS Verde)|339933 / 51,153,51|![Campione 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stato: negativo|Rosso notifica (VS Red)|E51400 / 229,20,0|![Campione E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stato: avviso|Notifica Giallo (VS Arancione)|FFCC00 / 255.204,0|![Campione FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Riempimento in primo piano|Notifica Nera (Nero)|000000 / 0,0,0|![&#35;di swatch 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Riempimento in primo piano|Notifica Bianco (Bianco)|FFFFFF / 255.255.255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Esempi di icone di notifica

|||||
|-|-|-|-|
|![Icona di avviso](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Avviso|![Icona avviso](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Avviso|![Icona Completato](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Operazione completata|![Icona Interrompi](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Arresto|

### <a name="visual-studio-online"></a>Visual Studio Online
 In generale, Visual Studio Online è costituito da funzionalità ospitate in un browser. Il colore varia in ambienti diversi, ma lo stile rimane lo stesso.

|Gruppo|Uso|Nome|Valore (tutti i temi)|Swatch|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Background|TFSO BG|656565/ 101, 101, 101|![Campione 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Riquadro|TFSO OUT|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Background|bianco|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Principato di Monaco|Background|bianco|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Background|bianco|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normale|F12 Grey_Primary|555555 / 85, 85, 85|![Campione 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Passaggio del mouse|F12 Blue_Hover|2279BF / 34.121.191|![Campione 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Disabled|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Campione ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Sfondo al passaggio del mouse|Hover bg|D9EBF7 / 217.235.247|![Campione D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Sfondo premuto|Premuto bg|B2D7F0 / 178.215.240|![Campione B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Riquadro|VS OUT|F6F6F6 / 246.246.246|![Campione F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Informazioni|Informazioni|00BCF2 / 0,188.242|![Campione 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Avviso|Avviso|F28300 / 242.131,0|![Campione F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Errore / Negativo|Error_Negative|E81123 / 232,17,35|![Campione E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Inizio / Positivo|Start_Positive|009E49 / 0,158,73|![Campione 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Tipo di interruzione|Tipo di interruzione|9B4F96 / 155.79.150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Contrassegno evento|Contrassegno evento|A51F00 / 165,31,0|![Campione A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Contrassegno utente|Contrassegno utente|F16220 / 241,98,32|![Campione F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Esempi di icone di Visual Studio Online

|TFS Online||||
|----------------|-|-|-|
|![Icona team di TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Online Team|![Icona di informazioni TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />Informazioni|![Icona della cronologia di TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Cronologia|![Icona del branch TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Ramo|

|Napa||||
|----------|-|-|-|
|![Icona del contenuto Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Contenuto|![Icona della posta di Office Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Posta di Office|![Icona di SharePoint Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Icona del riquadro attività Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Riquadro attività|

|Principato di Monaco||||
|------------|-|-|-|
|![Icona dei file Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />File|![Icona Git Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Icona di ricerca Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Ricerca|![Icona di testo Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Text|

|F12|||
|---------|-|-|
|![Icona codice Pretty F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Codice Pretty|![Icona di avviso F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Avviso|![Icona di emulazione F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Emulare|