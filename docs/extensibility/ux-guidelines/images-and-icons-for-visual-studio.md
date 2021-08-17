---
title: Immagini e icone per Visual Studio | Microsoft Docs
description: Informazioni sui concetti di progettazione usati per creare le immagini e le icone per Visual Studio.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ca7eea3b88b6cfe38bd0d1be568b9aeaf5e329ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028930"
---
# <a name="images-and-icons-for-visual-studio"></a>Immagini e icone per Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Uso delle immagini in Visual Studio
 Prima di creare un disegno, è consigliabile usare più di 1.000 immagini nella raccolta Visual Studio [immagini.](https://www.microsoft.com/download/details.aspx?id=35825)

### <a name="types-of-images"></a>Tipi di immagini

- **Icone**. Immagini di piccole dimensioni che vengono visualizzate in comandi, gerarchie, modelli e così via. La dimensione predefinita dell'icona usata Visual Studio è un PNG 16x16. Le icone generate dal servizio immagini generano automaticamente il formato XAML per il supporto HDPI.

    > [!NOTE]
    > Mentre le immagini vengono usate nel sistema di menu, non è consigliabile creare un'icona per ogni comando. Consultare [Menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) vedere se il comando deve ottenere un'icona.

- **Miniature.** Immagini usate nell'area di anteprima di una finestra di dialogo, ad esempio la finestra di dialogo Project dialogo.

- **Immagini della finestra di dialogo.** Immagini visualizzate nelle finestre di dialogo o nelle procedure guidate, come grafica descrittiva o indicatori di messaggio. Usare raramente e solo quando necessario per illustrare un concetto difficile o ottenere l'attenzione dell'utente (avviso, avviso).

- **Immagini animate.** Usato negli indicatori di stato, nelle barre di stato e nelle finestre di dialogo delle operazioni.

- **Cursori.** Utilizzato per indicare se un'operazione è consentita usando il mouse, dove un oggetto può essere eliminato e così via.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Progettazione delle icone

### <a name="overview"></a>Panoramica
 Visual Studio usa icone di stile moderno, che hanno una geometria pulita e un equilibrio 50/50 di positivo/negativo (chiaro/scuro) e usano metafore dirette e comprensibili. I punti di progettazione delle icone cruciali sono al centro di chiarezza, semplificazione e contesto.

- **Chiarezza:** concentrarsi sulla metafora principale che dà a un'icona il significato e l'individualità.

- **Semplificazione: ridurre** l'icona al significato principale: ottenere il tema con solo gli elementi necessari e senza frondoli.

- **Contesto: prendere** in considerazione tutti gli aspetti del ruolo di un'icona durante lo sviluppo del concetto, che è fondamentale quando si decide quali elementi costituiscono la metafora principale dell'icona.

  Con le icone, esistono diversi punti di progettazione da evitare:

- Non usare icone che significano elementi dell'interfaccia utente tranne quando appropriato. Scegliere un approccio più astratto o simbolico quando l'elemento dell'interfaccia utente non è comune, evidente o univoco.

- Non utilizzare in modo eccessivo elementi comuni come documenti, cartelle, frecce e la lente di ingrandimento. Usare questi elementi solo quando sono essenziali per il significato dell'icona. Ad esempio, la lente di ingrandimento rivolta a destra deve indicare solo Cerca, Sfoglia e Trova.

- Anche se alcuni elementi icona legacy mantengono l'uso della prospettiva, non creare nuove icone con prospettiva a meno che l'elemento non sia privo di chiarezza.

- Non creare troppe informazioni in un'icona. Un'immagine semplice che può essere facilmente riconosciuta o appresa come simbolo riconoscibile è molto più utile di un'immagine troppo complessa. Un'icona non può raccontare l'intera storia.

### <a name="icon-creation"></a>Creazione dell'icona

#### <a name="concept-development"></a>Sviluppo di concetti
 Visual Studio ha all'interno dell'interfaccia utente un'ampia gamma di tipi di icona. Considerare attentamente il tipo di icona durante lo sviluppo. Non usare oggetti dell'interfaccia utente poco chiari o non comuni per gli elementi icona. Scegliere il simbolo simbolico in questi casi, ad esempio con l'icona Smart tag. Si noti che il significato del tag astratto a sinistra è più ovvio della versione vaga basata sull'interfaccia utente a destra:

|**Uso corretto delle immagini simboliche**|**Uso non corretto di immagini simboliche**|
|-|-|
|![Icona smart tag corretta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icona smart tag non corretta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Esistono istanze in cui gli elementi dell'interfaccia utente standard e facilmente riconoscibili funzionano bene per le icone. Aggiungi finestra è un esempio di questo tipo:

|**Elemento corretto dell'interfaccia utente in un'icona**|**Elemento dell'interfaccia utente non corretto in un'icona**|
|-|-|
|![Icona Aggiungi finestra corretta](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icona Aggiungi finestra non corretta](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Non usare un documento come elemento di base a meno che non sia essenziale per il significato dell'icona. Senza l'elemento documento in Aggiungi documento (sotto) il significato viene perso, mentre con Aggiorna l'elemento del documento non è necessario comunicarlo.

|**Uso corretto dell'icona del documento**|**Uso non corretto dell'icona del documento**|
|-|-|
|![Icona Documento corretta](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icona Documento non corretta](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Il concetto di "show" deve essere rappresentato dall'icona che illustra meglio ciò che viene visualizzato, ad esempio con l'esempio Mostra tutti i file. Una metafora dell'obiettivo può essere usata per indicare il concetto di "vista" se necessario, ad esempio con l'Visualizzazione risorse esempio.

|**"Mostra"**|**"Visualizza"**|
|-|-|
|![Icona Mostra](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icona Visualizza](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 L'icona a forma di lente di ingrandimento rivolta a destra deve rappresentare solo Cerca, Trova e Sfoglia. La variante rivolta a sinistra con il segno più o meno deve rappresentare solo lo zoom avanti/indietro.

|**"Cerca"**|**"Zoom"**|
|-|-|
|![icona Cerca](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icona Zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Nelle visualizzazioni albero non usare sia l'icona della cartella che un modificatore. Se disponibile, usare solo il modificatore .

|**Icone corrette della visualizzazione albero**|**Icone della visualizzazione albero non corrette**|
|-|-|
|![Icona corretta della visualizzazione albero &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") icona corretta della visualizzazione ![albero &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icona visualizzazione albero non corretta &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") icona visualizzazione albero ![non corretta &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Dettagli dello stile

#### <a name="layout"></a>Layout
 Impilare gli elementi come illustrato per le icone standard 16x16:

 ![Stack di layout per icone 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Stack di layout per icone 16x16

 Gli elementi di notifica dello stato vengono usati meglio come icone autonome. Esistono tuttavia contesti in cui una notifica deve essere impilata sull'elemento di base, ad esempio con l'icona Completamento attività:

 ![Notifiche autonome in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Icone di notifica autonome

 ![Icona Attività completata](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icona Completamento attività

 Project icone sono in genere file con estensione ico che contengono più dimensioni. La maggior parte delle icone 16x16 contiene gli stessi elementi. Le versioni 32x32 includono altri dettagli, incluso il tipo di progetto, se applicabile.

 ![Icone di progetto in Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB Windows control library Project icone, 16x16 e 32x32

 Centrare un'icona all'interno del relativo frame in pixel. Se ciò non è possibile, allineare l'icona alla parte superiore e/o destra del frame.

 ![Icona centrata nel frame di pixel](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icona centrata nel frame di pixel

 ![Icona allineata al lato superiore destro del frame di pixel](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icona allineata in alto a destra nel frame

 ![Icona centrata e allineata al lato superiore del frame di pixel](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icona centrata e allineata alla parte superiore del frame

 Per ottenere l'allineamento e il bilanciamento ideali, evitare di ostruire l'elemento di base dell'icona con glifi di azione. Posizionare il glifo nella parte superiore sinistra dell'elemento di base. Quando si aggiunge un elemento aggiuntivo, considerare l'allineamento e il bilanciamento dell'icona.

|**Allineamento e bilanciamento corretti**|**Allineamento e bilanciamento non corretti**|
|-|-|
|![Equilibrio e allineamento corretti dell'icona](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Equilibrio e allineamento non corretti dell'icona](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Verificare la parità delle dimensioni per le icone che condividono elementi e vengono usate nei set. Si noti che nell'associazione non corretta il cerchio e la freccia sono di dimensioni troppo grande e non corrispondono.

|**Correttezza della parità delle dimensioni**|**Parità delle dimensioni non corretta**|
|-|-|
|![Dimensioni e parità corrette dell'icona](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Dimensioni e parità non corrette dell'icona](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Usare pesi coerenti per linee e oggetti visivi. Valutare il confronto tra l'icona che si sta creando e le altre icone usando un confronto affiancato. Non usare mai l'intero frame 16x16, usare 15x15 o un valore inferiore. Il rapporto tra negativo e positivo (scuro-chiaro) deve essere 50/50.

|**Correggere il rapporto negativo-positivo**|**Rapporto negativo-positivo non corretto**|
|-|-|
|![Correggere lo spessore visivo per le icone &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Correzione dello spessore visivo per le icone &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Correzione dello spessore visivo per le icone &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Impatto visivo non corretto per le icone](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Usa forme semplici e simili e angoli complementari per creare gli elementi senza compromettere l'integrità degli elementi. Usare angolazioni di 45° o 90°, se possibile.

 ![Angoli corretti per le icone](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Prospettiva
 Mantenere l'icona chiara e comprensibile. Usare la prospettiva e una sorgente di luce solo quando necessario. Anche se è consigliabile evitare l'uso della prospettiva sugli elementi icona, alcuni elementi non sono riconoscibili senza di essa. In questi casi, una prospettiva stilizzata comunica la chiarezza dell'elemento.

 ![Prospettiva a tre punti](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Prospettiva a tre punti

 ![Prospettiva a un punto](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Prospettiva a un punto

 La maggior parte degli elementi deve essere rivolta verso destra o angolata:

 ![Icone con angolazione corretta](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Usare le sorgenti di luce solo quando si aggiunge chiarezza necessaria a un oggetto.

|**Correggere la sorgente di luce**|**Sorgente di luce non corretta**|
|-|-|
|![Sorgenti di luce corrette per le icone](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Sorgenti di luce non corrette per le icone](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Usare i contorni solo per migliorare la leggibilità o per comunicare meglio la metafora. Il saldo positivo negativo (chiaro scuro) deve essere 50/50.

|**Uso corretto delle strutture**|**Uso non corretto delle strutture**|
|-|-|
|![Strutture corrette](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Strutture non corrette](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipi di icona
 **Le icone della shell e della** barra dei comandi sono costituite da non più di tre degli elementi seguenti: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone della shell e della barra dei comandi](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Esempi di icone della shell e della barra dei comandi

 **Le icone della barra dei comandi** della finestra degli strumenti sono costituite da non più di tre degli elementi seguenti: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone della barra dei comandi della finestra degli strumenti](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Esempi di icone della barra dei comandi della finestra degli strumenti

 **Le icone di disambiguatore** della visualizzazione albero sono costituite da non più di tre degli elementi seguenti: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone di disambiguazione della visualizzazione albero](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Esempi di icone di disambiguazione della visualizzazione albero

 **Le icone di tassonomia dei valori** basati sullo stato esistono negli stati seguenti: attiva, attiva disabilitata e inattiva disabilitata.

 ![Esempi di icone di tassonomia dei valori basati sullo stato](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Esempi di icone di tassonomia dei valori basati sullo stato

 **Le icone intelliSense** sono costituite da non più di tre degli elementi seguenti: una base, un modificatore e uno stato.

 ![Esempi di icone IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Esempi di icone IntelliSense

 **Le icone di progetto piccole (16x16)** non devono avere più di due elementi: un modificatore di base e uno.

 Esempi di icone di progetto piccole ![(16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") icona del progetto ![16x16](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") &#40;2&#41;![16x16](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3") icona del progetto &#40;3&#41;<br />Esempi di icone di progetto piccole (16x16)

 Le icone di progetto grandi **(32x32)** sono costituite da non più di quattro degli elementi seguenti: una base, uno o due modificatori e una sovrimpressione del linguaggio.

 ![Esempi di icone di progetto di grandi dimensioni (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Esempi di icone di progetto di grandi dimensioni (32x32)

### <a name="production-details"></a>Dettagli di produzione
 Tutti i nuovi elementi dell'interfaccia utente devono essere creati usando Windows Presentation Foundation (WPF) e tutte le nuove icone per WPF devono essere in formato PNG a 32 bit. Il formato PNG a 24 bit è un formato legacy che non supporta la trasparenza e pertanto non è consigliato per le icone.

 Salvare la risoluzione a 96 DPI.

#### <a name="file-types"></a>Tipi di file

- **PNG a 32 bit: formato** preferito per le icone. Formato di file di compressione dei dati senza perdita di dati in grado di archiviare una singola immagine raster (pixel). I file PNG a 32 bit supportano la trasparenza del canale alfa, la correzione gamma e l'interlacciamento.

- **BMP a 32 bit: per** i controlli non WPF. Detto anche XP o colore elevato, BMP a 32 bit è un formato di immagine RGB/A, un'immagine di colore reale con trasparenza del canale alfa. Il canale alfa è un livello di trasparenza designato in Adobe Photoshop che viene quindi salvato all'interno della bitmap come canale di colore aggiuntivo (quarto). Durante la produzione della grafica viene aggiunto uno sfondo nero a tutti i file BMP a 32 bit per fornire un segnale visivo rapido sulla profondità del colore. Questo sfondo nero rappresenta l'area da mascherare nell'interfaccia utente.

- **ICO a 32 bit: per** Project e Aggiungi elemento. Tutti i file ICO sono di colore reale a 32 bit con trasparenza del canale alfa (RGB/A). Poiché i file ICO possono archiviare più dimensioni e profondità dei colori, le icone di Vista sono spesso in un formato ICO contenente dimensioni di immagine 16x16, 32x32, 48x48 e 256x256. Per essere visualizzati correttamente in Windows Explorer, i file ICO devono essere salvati fino a 24 bit e a 8 bit di profondità dei colori per ogni dimensione dell'immagine.

- **XAML: per** aree di progettazione e Windows strumenti decorativi. Le icone XAML sono file di immagine basati su vettori che supportano il ridimensionamento, la rotazione, l'archiviazione e la trasparenza. Attualmente non sono comuni in Visual Studio, ma stanno diventando più popolari grazie alla loro flessibilità.

- **SVG**

- **BMP a 24 bit: per** la Visual Studio comandi. Un formato di immagine RGB a colori reale, BMP a 24 bit è una convenzione di icona che crea un livello di trasparenza usando magenta (R=255, G=0, B=255) come chiave di colore per un livello di trasparenza in fase di invertirsi. In un BMP a 24 bit tutte le superfici magenta vengono visualizzate usando il colore di sfondo.

- **GIF a 24 bit: per** la Visual Studio comandi. Un formato di immagine RGB di colore reale che supporta la trasparenza. I file GIF vengono spesso usati nelle illustrazioni delle procedure guidate e nelle animazioni GIF.

### <a name="icon-construction"></a>Costruzione di icone
 La dimensione dell'icona più piccola Visual Studio è 16x16. Il più grande in uso comune è 32x32. Tenere presente di non riempire l'intero frame 16x16, 24x24 o 32x32 durante la progettazione di un'icona. La costruzione di icone leggibili e uniformi è essenziale per il riconoscimento dell'utente. Quando si compilano icone, attenersi ai punti seguenti.

- Le icone devono essere chiare, comprensibili e coerenti.

- È meglio usare gli elementi di notifica dello stato come singole icone e non impilarli sopra un elemento di base icona. In alcuni contesti, l'interfaccia utente potrebbe richiedere l'associazione dell'elemento di stato a un elemento di base.

- Project icone sono in genere file con estensione ico che contengono diverse dimensioni. Vengono aggiornate solo le icone 16x16, 24x24 e 32x32. La maggior parte delle icone 16x16 e 24x24 conterrà gli stessi elementi. Le icone 32x32 contengono altri dettagli, incluso il tipo di linguaggio del progetto, se applicabile.

- Per le icone 32x32, gli elementi di base hanno in genere uno spessore di linea di 2 pixel. Per gli elementi di dettaglio è possibile usare uno spessore di linea di 1 o 2 pixel. Usare il giudizio migliore per determinare quale sia più adatto.

- Avere almeno una spaziatura di 1 pixel tra gli elementi per le icone 16x16 e 24x24. Per le icone 32x32, usare la spaziatura di 2 pixel tra gli elementi e tra il modificatore e l'elemento di base.

  ![Spaziatura degli elementi per le icone con dimensioni 16x16, 24x24 e 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Spaziatura degli elementi per le icone con dimensioni 16x16, 24x24 e 32x32

#### <a name="color-and-accessibility"></a>Colore e accessibilità
 Visual Studio di conformità richiedono che tutte le icone nel prodotto superino i requisiti di accessibilità per il colore e il contrasto. Questa operazione viene ottenuta tramite l'inversione dell'icona e, durante la progettazione, è necessario tenere presente che verranno invertiti a livello di codice nel prodotto.

 Per altre informazioni sull'uso del colore nelle icone Visual Studio, vedere [Uso del colore nelle immagini](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Uso del colore nelle immagini

### <a name="overview"></a>Panoramica
 Le icone Visual Studio sono principalmente monocromatiche. Il colore è riservato per trasmettere informazioni specifiche e mai per la decorazione. Viene usato il colore:

- per indicare un'azione

- per avvisare l'utente di una notifica di stato

- per designare l'affiliazione linguistica

- per differenziare gli elementi all'interno di IntelliSense

### <a name="accessibility"></a>Accessibilità
 Visual Studio di conformità richiedono che tutte le icone archiviate nel prodotto superino i requisiti di accessibilità per il colore e il contrasto. I colori nella tavolozza del linguaggio visivo sono stati testati e soddisfano questi requisiti.

#### <a name="color-inversion-for-dark-themes"></a>Inversione del colore per i temi scuri
 Per fare in modo che le icone vengano visualizzate con il rapporto di contrasto corretto nel tema Visual Studio scuro, viene applicata un'inversione a livello di codice. I colori di questa guida sono stati scelti in parte in modo che vengano invertiti correttamente. Limitare l'uso del colore a questa tavolozza oppure si otterrà risultati imprevedibili quando viene applicata l'inversione.

 ![Esempi di icone con i colori invertiti](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Esempi di icone con i colori invertiti

### <a name="base-palette"></a>Riquadro di base
 Tutte le icone standard contengono tre colori di base. Le icone non contengono sfumature o ombreggiature, con una o due eccezioni per le icone degli strumenti 3D.

|Utilizzo|Nome|Valore (tema Chiaro)|Swatch|Esempio|
|-----------|----------|---------------------------|------------|-------------|
|Sfondo/Scuro|VS BG|424242 / 66,66,66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Esempio di tavolozza di base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Primo piano/Chiaro|VS FG|F0EFF1 / 240.239.241|![Campione F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Riquadro|VS Out|F6F6F6 / 246.246.246|![Campione F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Oltre ai colori di base, ogni icona può contenere un colore aggiuntivo dalla tavolozza estesa.

### <a name="extended-palette"></a>Riquadro esteso

#### <a name="action-modifiers"></a>Modificatori di azione
 I quattro colori seguenti indicano i tipi di azioni richieste dai modificatori di azione:

|Utilizzo|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|Positivo|Verde azione di Visual Studio|388A34 / 56.138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negativo|Visual Studio Action Red|A1260D / 161,38,13|![Campione A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutralità|Visual Studio Action Blue|00539C / 0,83,156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Crea/Nuovo|VS Action Orange|C27D1A / 194.156.26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Esempio
 Il verde viene usato per i modificatori di azione positivi, ad esempio "Add", "Run", "Play" e "Validate".

|Esegui|Eseguire la query|Riproduci tutti i passaggi|Aggiungere un controllo|
|-|-|-|-|
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Icona Esegui query](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Icona Riproduci tutti i passi](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Icona Aggiungi controllo](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Red viene usato per i modificatori di azione negativi, ad esempio "Delete", "Stop", "Cancel" e "Close".

|Eliminare la relazione|Elimina colonna|Interrompi query|Connessione offline|
|-|-|-|-|
|![Icona Elimina relazioni](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Icona Elimina colonna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Icona Interrompi query](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Icona Connessione offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Il blu viene applicato ai modificatori di azione neutri più comunemente rappresentati come frecce, ad esempio "Apri", "Avanti", "Precedente", "Importa" ed "Esporta".

|Vai al campo|Batch Check-In|Editor indirizzi|Editor associazioni|
|-|-|-|-|
|![Icona Vai al campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Icona&#45;controllo in batch](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Icona Editor di indirizzo](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![Icona Editor di associazione](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 L'oro scuro viene usato principalmente per il modificatore "New".

|Nuovo progetto|Creare una nuova Graph|Nuovo unit test|Nuovo elemento elenco|
|-|-|-|-|
|![Icona Nuovo progetto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Icona Crea Nuovo grafico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Icona Nuovo Unit test](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Icona Nuova voce di elenco](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Casi speciali
 In casi speciali, un modificatore di azione colorato può essere usato in modo indipendente come icona autonoma. Il colore usato per l'icona riflette le azioni a cui è associata l'icona. Questo uso è limitato a un piccolo subset di icone, tra cui:

|Esegui|Interrompere|Elimina|Salva|Esplora indietro|
|-|-|-|-|-|
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Icona di arresto : quadrato rosso tinta unita.](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Icona Elimina](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Icona Salva](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Icona Esplora indietro](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Riquadro gerarchia del codice

#### <a name="folder"></a>Cartella

|Utilizzo|Nome|Valore (tutti i temi)|Swatch|Esempio|
|-----------|----------|--------------------------|------------|-------------|
|Cartelle|Cartella|DCB67A / 220.182.122|![Campione DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icona del colore della cartella](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio lingue
 A ogni linguaggio o piattaforma comune disponibile in Visual Studio è associato un colore. Questi colori vengono usati sull'icona di base o sui modificatori del linguaggio visualizzati nell'angolo superiore destro delle icone composte.

|Utilizzo|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blu|0095D7 / 0,149,215|![Campione 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|Viola CPP|9B4F96 / 155.79.150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Green (VS Action Green)|388A34 / 56.138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS Red|BD1E2D / 189,30,45|![Campione BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS Viola|672878 / 103,40,120|![Campione 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![Campione F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blu (VS Action Blue)|00539C / 0,83,156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Arancione TS|E04C06 / 224.76,6|![Campione E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Verde|879636 / 135,150,54|![Campione 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Esempi di icone con modificatori di linguaggio

|VB|C#|C++|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Icona di Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![Icona&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![Icona&#43;&#43; C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![F&#35; icona](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![Icona di JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Icona di Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|
|![Icona di HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Icona di WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Icona di ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Icona di CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Icona di TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript|

#### <a name="intellisense"></a>IntelliSense
 Le icone IntelliSense usano una tavolozza dei colori esclusiva. Questi colori vengono usati per consentire agli utenti di distinguere rapidamente tra i diversi elementi nell'elenco popup di IntelliSense.

|Utilizzo|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|Classe, evento|VS Action Orange|C27D1A / 194,125,26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metodo di estensione, metodo, modulo, delegato|Viola di VS Action|652D90 / 101,45,144|![Campione 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Field, Enum Item, Macro, Structure, Union Value Type, Operator, Interface|Visual Studio Action Blue|00539C / 0,83,156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Oggetto|Verde azione di Visual Studio|388A34 / 56.138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constant, Exception, Enum Item, Map, Map Item, Namespace, Template, Type Definition|Background (VS BG)|424242 / 66,66,66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Esempi di icone IntelliSense

|Classe|Evento privato|Delegato|Friend del metodo|Campo|
|-|-|-|-|-|
|![Icona della classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![Icona dell'evento privato IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![Icona del delegato IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Icona descrittiva del metodo IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Icona del campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Elemento Enum protetto|Oggetto|Modello|Collegamento all'eccezione|
|-|-|-|-|
|![Icona dell'elemento enum protetto IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![Icona dell'oggetto IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![Icona del modello IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![Icona del collegamento all'eccezione IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Notifiche
 Le notifiche in Visual Studio vengono usate per indicare lo stato. La tavolozza delle notifiche usa i quattro colori seguenti, nonché le opzioni di riempimento in primo piano bianco o nero, per definire le notifiche con i livelli di stato seguenti.

|Utilizzo|Nome|Valore (tutti i temi)|Swatch|
|-----------|----------|--------------------------|------------|
|Stato: neutro|Notification Blue (VS Blue)|1BA1E2 /27.161.226|![Campione 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stato: positivo|Verde notifica (VS Verde)|339933 / 51,153,51|![Campione 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stato: negativo|Notifica rossa (VS Red)|E51400 / 229,20,0|![Campione E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stato: avviso|Giallo notifica (VS Orange)|FFCC00 / 255.204.0|![Campione FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Riempimento in primo piano|Notifica nera (nera)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Riempimento in primo piano|Bianco notifica (bianco)|FFFFFF/ 255.255.255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Esempi di icone di notifica

|Avviso|Avviso|Operazione completata|Interrompere|
|-|-|-|-|
|![Icona di avviso](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Icona avviso](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Icona Completato](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Icona di arresto : cerchio rosso a tinta unita con un quadrato bianco al centro.](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|