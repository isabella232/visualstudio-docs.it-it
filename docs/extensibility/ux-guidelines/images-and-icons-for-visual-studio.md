---
title: Immagini e icone per Visual Studio | Microsoft Docs
description: Informazioni sui concetti di progettazione usati per creare immagini e icone per Visual Studio.
ms.date: 04/26/2017
ms.topic: overview
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c7bc09147c2c9a6cf36a1a967241219df9e9bce
ms.sourcegitcommit: 20f546a0b13b56e7b0da21abab291d42a5ba5928
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104884161"
---
# <a name="images-and-icons-for-visual-studio"></a>Immagini e icone per Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Uso delle immagini in Visual Studio
 Prima di creare grafica, provare a usare le immagini 1000 + nella [libreria di immagini di Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Tipi di immagini

- **Icone**. Immagini piccole visualizzate in comandi, gerarchie, modelli e così via. Le dimensioni dell'icona predefinite usate in Visual Studio sono 16x16 PNG. Le icone prodotte dal servizio immagini generano automaticamente il formato XAML per il supporto di HDPI.

    > [!NOTE]
    > Mentre le immagini vengono utilizzate nel sistema di menu, è consigliabile non creare un'icona per ogni comando. Per verificare se il comando deve ottenere un'icona, consultare i [menu e i comandi di Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) .

- **Anteprime.** Immagini utilizzate nell'area di anteprima di una finestra di dialogo, ad esempio la finestra di dialogo nuovo progetto.

- **Immagini della finestra di dialogo.** Immagini visualizzate nelle finestre di dialogo o nelle procedure guidate, come elementi grafici descrittivi o indicatori di messaggio. Usare raramente e solo quando necessario per illustrare un concetto difficile o ottenere l'attenzione dell'utente (avviso, avviso).

- **Immagini animate.** Utilizzato negli indicatori di stato, nelle barre di stato e nelle finestre di dialogo delle operazioni.

- **Cursori.** Utilizzato per indicare se un'operazione è consentita utilizzando il mouse, in cui un oggetto può essere eliminato e così via.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Progettazione dell'icona

### <a name="overview"></a>Panoramica
 Visual Studio USA icone in stile moderno, con geometria pulita e un saldo 50/50 positivo/negativo (chiaro/scuro) e usa metafore dirette e comprensibili. Icona cruciale punti di progettazione Centra intorno a chiarezza, semplificazione e contesto.

- **Chiarezza:** concentrarsi sulla metafora di base che fornisce a un'icona il significato e la singolarità.

- **Semplificazione:** ridurre l'icona con il significato principale, ovvero ottenere il tema tra i soli elementi necessari e senza fronzoli.

- **Contesto:** considerare tutti gli aspetti del ruolo di un'icona durante lo sviluppo del concetto, che è fondamentale quando si definiscono gli elementi che costituiscono la metafora principale dell'icona.

  Con le icone è possibile evitare diversi punti di progettazione:

- Non usare icone che indicano gli elementi dell'interfaccia utente tranne quando appropriato. Scegliere un approccio più astratto o simbolico quando l'elemento dell'interfaccia utente non è né comune, chiaro né univoco.

- Non esagerare gli elementi comuni, ad esempio documenti, cartelle, frecce e lente di ingrandimento. Usare tali elementi solo quando è essenziale per il significato dell'icona. Ad esempio, la lente di ingrandimento a destra deve indicare solo ricerca, Sfoglia e trova.

- Sebbene alcuni elementi dell'icona legacy mantengano l'uso della prospettiva, non creare nuove icone con la prospettiva, a meno che l'elemento non sia chiaro senza di esso.

- Non stipare troppe informazioni in un'icona. Un'immagine semplice che può essere facilmente riconosciuta o appresa come simbolo riconoscibile è molto più utile di un'immagine eccessivamente complessa. Un'icona non può raccontare tutta la storia.

### <a name="icon-creation"></a>Creazione di icone

#### <a name="concept-development"></a>Sviluppo di concetti
 Visual Studio dispone di un'ampia gamma di tipi di icone nell'interfaccia utente. Considerare attentamente il tipo di icona durante lo sviluppo. Non usare oggetti dell'interfaccia utente non chiari o non comuni per gli elementi dell'icona. Optare per il simbolico in questi casi, ad esempio con l'icona Smart tag. Si noti che il significato del tag astratto a sinistra è più ovvio della versione vaga basata sull'interfaccia utente a destra:

|**Utilizzo corretto di immagini simboliche**|**Uso errato di immagini simboliche**|
|-|-|
|![Icona smart tag corretta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icona smart tag non corretta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Sono presenti istanze in cui gli elementi dell'interfaccia utente standard e facilmente riconoscibili funzionano correttamente per le icone. Aggiungi finestra è un esempio di questo tipo:

|**Correggi elemento dell'interfaccia utente in un'icona**|**Elemento dell'interfaccia utente non corretto in un'icona**|
|-|-|
|![Icona Aggiungi finestra corretta](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icona Aggiungi finestra non corretta](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Non usare un documento come elemento di base, a meno che non sia essenziale per il significato dell'icona. Senza l'elemento documento in Aggiungi documento (sotto) il significato viene perso, mentre con refresh l'elemento del documento non è necessario per comunicare il significato.

|**Icona di utilizzo corretto dell'icona del documento**|**Uso errato dell'icona del documento**|
|-|-|
|![Icona Documento corretta](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icona Documento non corretta](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Il concetto di "Mostra" deve essere rappresentato dall'icona che illustra meglio gli elementi visualizzati, ad esempio con l'esempio Mostra tutti i file. Una metafora Lens può essere usata per indicare il concetto di "View", se necessario, ad esempio con il Visualizzazione risorse esempio.

|**Visualizza**|**Visualizzare**|
|-|-|
|![Icona Mostra](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icona Visualizza](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 L'icona a forma di lente di ingrandimento a destra deve rappresentare solo ricerca, trova e Sfoglia. La variante a sinistra con il segno più o il segno meno deve rappresentare solo lo zoom avanti/Zoom indietro.

|**Ricerca**|**Zoom**|
|-|-|
|![icona Cerca](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icona Zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Nelle visualizzazioni ad albero non usare sia l'icona della cartella che un modificatore. Se disponibile, usare solo il modificatore.

|**Icone visualizzazione albero corrette**|**Icone visualizzazione albero non corrette**|
|-|-|
|![Icona visualizzazione albero corretta &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![icona visualizzazione albero corretta &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icona visualizzazione albero non corretta &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![icona visualizzazione albero non corretta &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Dettagli stile

#### <a name="layout"></a>Layout
 Elementi dello stack come illustrato per le icone 16x16 standard:

 ![Stack di layout per icone 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Stack di layout per icone 16x16

 Gli elementi di notifica di stato sono meglio usati come icone autonome. Tuttavia, esistono contesti in cui una notifica deve essere impilata nell'elemento di base, ad esempio con l'icona di completamento dell'attività:

 ![Notifiche autonome in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Icone di notifica autonome

 ![Icona Attività completata](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icona di completamento attività

 Le icone di progetto sono in genere file con estensione ico che contengono più dimensioni. La maggior parte delle icone 16x16 contiene gli stessi elementi. Le versioni di 32x32 offrono maggiori dettagli, incluso il tipo di progetto quando applicabile.

 ![Icone di progetto in Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Icone del progetto di libreria di controlli Windows VB, 16x16 e 32x32

 Centrare un'icona all'interno del relativo frame pixel. Se ciò non è possibile, allineare l'icona alla parte superiore e/o a destra del frame.

 ![Icona centrata nel frame di pixel](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icona centrata nel frame di pixel

 ![Icona allineata al lato superiore destro del frame di pixel](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icona allineata alla parte superiore destra del frame

 ![Icona centrata e allineata al lato superiore del frame di pixel](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icona centrata e allineata alla parte superiore del frame

 Per ottenere l'allineamento e il bilanciamento ideali, evitare di ostacolare l'elemento di base dell'icona con i glifi dell'azione. Posizionare il glifo vicino alla parte superiore sinistra dell'elemento di base. Quando si aggiunge un elemento aggiuntivo, prendere in considerazione l'allineamento e il saldo dell'icona.

|**Allineamento e bilanciamento corretti**|**Allineamento e bilanciamento non corretti**|
|-|-|
|![Equilibrio e allineamento corretti dell'icona](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Equilibrio e allineamento non corretti dell'icona](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Verificare la parità delle dimensioni per le icone che condividono gli elementi e vengono usate nei set. Si noti che nell'associazione non corretta, il cerchio e la freccia sono sovradimensionati e non corrispondono.

|**Parità di dimensioni corrette**|**Parità dimensioni non corrette**|
|-|-|
|![Dimensioni e parità corrette dell'icona](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Dimensioni e parità non corrette dell'icona](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Usare i pesi lineari e visivi coerenti. Valutare il modo in cui l'icona compilata viene confrontata con altre icone usando un confronto affiancato. Non usare mai l'intero frame 16x16, usare 15x15 o una dimensione inferiore. Il rapporto da negativo a positivo (scuro a chiaro) dovrebbe essere 50/50.

|**Rapporto tra negativo e positivo corretto**|**Rapporto negativo a positivo errato**|
|-|-|
|![Spessore visivo corretto per le icone &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Spessore visivo corretto per le icone &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Spessore visivo corretto per le icone &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Impatto visivo non corretto per le icone](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 USA forme semplici e confrontabili e angoli complementari per creare gli elementi senza sacrificare l'integrità degli elementi. Usare gli angoli 45 ° o 90 ° laddove possibile.

 ![Angoli corretti per le icone](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Prospettiva
 Tenere l'icona chiara e comprensibile. Usare la prospettiva e una fonte di luce solo quando è necessario. Sebbene sia consigliabile evitare l'uso della prospettiva sugli elementi Icon, alcuni elementi non sono riconoscibili senza di essa. In questi casi, una prospettiva stilizzata comunica la chiarezza dell'elemento.

 ![Prospettiva a tre punti](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Prospettiva a tre punti

 ![Prospettiva a un punto](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Prospettiva a un punto

 La maggior parte degli elementi deve essere rivolti o inclinati a destra:

 ![Icone con angolazione corretta](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Usare le fonti di luce solo quando si aggiunge la chiarezza necessaria a un oggetto.

|**Sorgente di luce corretta**|**Sorgente di luce non corretta**|
|-|-|
|![Sorgenti di luce corrette per le icone](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Sorgenti di luce non corrette per le icone](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Usare le strutture solo per migliorare la leggibilità o per comunicare meglio la metafora. Il saldo negativo positivo (luce scura) dovrebbe essere 50/50.

|**Utilizzo corretto di strutture**|**Uso non corretto di strutture**|
|-|-|
|![Strutture corrette](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Strutture non corrette](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipi di icone
 Le icone della **Shell e della barra dei comandi** non sono più di tre degli elementi seguenti: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone della shell e della barra dei comandi](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Esempi di icone della shell e della barra dei comandi

 Le icone della **barra dei comandi della finestra degli strumenti** non sono più di tre degli elementi seguenti: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone della barra dei comandi della finestra degli strumenti](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Esempi di icone della barra dei comandi della finestra degli strumenti

 Le icone **ambiguità selezionando della visualizzazione albero** sono costituite da non più di tre degli elementi seguenti: una base, un modificatore, un'azione o uno stato.

 ![Esempi di icone ambiguità selezionando di visualizzazione albero](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Esempi di icone ambiguità selezionando di visualizzazione albero

 Le icone di **Tassonomia del valore basato sullo stato** esistono negli Stati seguenti: attivo, attivo disabilitato e inattivo disabilitato.

 ![Esempi di icone di tassonomia del valore basato sullo stato](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Esempi di icone di tassonomia del valore basato sullo stato

 Le icone di **IntelliSense** non sono costituite da più di tre degli elementi seguenti: una base, un modificatore e uno stato.

 ![Esempi di icone IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Esempi di icone IntelliSense

 Le icone di **progetto Small (16x16)** non devono avere più di due elementi: uno di base e un modificatore.

 ![Esempi di icone di progetto Small (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 icona del progetto &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![icona del progetto 16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Esempi di icone di progetto Small (16x16)

 Le icone di **progetto di grandi dimensioni (32x32)** non sono costituite da più di quattro degli elementi seguenti: una base, uno a due modificatori e una sovrapposizione della lingua.

 ![Esempi di icone di progetto di grandi dimensioni (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Esempi di icone di progetto di grandi dimensioni (32x32)

### <a name="production-details"></a>Dettagli di produzione
 Tutti i nuovi elementi dell'interfaccia utente devono essere creati usando Windows Presentation Foundation (WPF) e tutte le nuove icone per WPF devono essere in formato PNG a 32 bit. Il formato PNG a 24 bit è un formato legacy che non supporta la trasparenza ed è quindi sconsigliato per le icone.

 Salvare la risoluzione a 96 DPI.

#### <a name="file-types"></a>Tipi di file

- **png a 32 bit:** il formato preferito per le icone. Formato di file di compressione dati senza perdita di dati in grado di archiviare un'immagine raster (pixel) singola. i file PNG a 32 bit supportano la trasparenza del canale alfa, la correzione gamma e l'interlacciamento.

- **BMP a 32 bit:** per i controlli non WPF. Detto anche XP o High Color, BMP a 32 bit è un formato di immagine RGB/A, un'immagine a colori veri con una trasparenza del canale alfa. Il canale alfa è un livello di trasparenza designato in Adobe Photoshop che viene quindi salvato nella bitmap come canale di colore aggiuntivo (quarto). Viene aggiunto uno sfondo nero durante la produzione della grafica a tutti i file BMP a 32 bit per fornire un segnale visivo rapido sulla profondità dei colori. Questo sfondo nero rappresenta l'area da nascondere nell'interfaccia utente.

- **ICO a 32 bit:** per le icone di progetto e per l'aggiunta di elementi. Tutti i file ICO sono di colore true a 32 bit con trasparenza del canale alfa (RGB/A). Poiché i file ICO possono archiviare più dimensioni e profondità dei colori, le icone di vista sono spesso in un formato ICO che contiene le dimensioni delle immagini 16x16, 32x32, 48x48 e 256x256. Per visualizzare correttamente in Esplora risorse, i file ICO devono essere salvati fino a una profondità di colore a 24 bit e a 8 bit per ogni dimensione di immagine.

- **XAML:** per le aree di progettazione e gli strumenti decorativi di Windows. Le icone XAML sono file di immagine basati su vettori che supportano il ridimensionamento, la rotazione, l'archiviazione e la trasparenza. Attualmente non sono comuni in Visual Studio, ma sono sempre più diffusi grazie alla loro flessibilità.

- **SVG**

- **BMP a 24 bit:** per la barra dei comandi di Visual Studio. Un formato di immagine RGB true-color, BMP a 24 bit è una convenzione di icona che crea un livello di trasparenza usando Magenta (R = 255, G = 0, B = 255) come chiave di colore per un livello di trasparenza di knock-out. In un BMP a 24 bit tutte le superfici Magenta vengono visualizzate utilizzando il colore di sfondo.

- **gif a 24 bit:** per la barra dei comandi di Visual Studio. Formato di immagine RGB True-Color che supporta la trasparenza. I file GIF vengono spesso usati nelle creazioni guidate e nelle animazioni GIF.

### <a name="icon-construction"></a>Costruzione di icone
 La dimensione più piccola dell'icona in Visual Studio è 16x16. Il più grande utilizzo comune è 32x32. Tenere presente che non si riempie l'intero frame 16x16, 24x24 o 32x32 quando si progetta un'icona. La costruzione di icone uniforme e leggibile è essenziale per il riconoscimento degli utenti. Quando si compilano le icone, attenersi ai punti seguenti.

- Le icone dovrebbero essere chiare, comprensibili e coerenti.

- È preferibile usare gli elementi di notifica di stato come icone singole e non impilarli sopra un elemento icona di base. In determinati contesti, l'interfaccia utente potrebbe richiedere che l'elemento status venga associato a un elemento di base.

- Le icone di progetto sono in genere file con estensione ico che contengono diverse dimensioni. Verranno aggiornate solo le icone 16x16, 24x24 e 32x32. La maggior parte delle icone 16x16 e 24x24 conterrà gli stessi elementi. Le icone 32x32 contengono ulteriori dettagli, incluso il tipo di lingua del progetto, quando applicabile.

- Per le icone 32x32, gli elementi di base in genere hanno un peso di linea da 2 pixel. Per gli elementi dettaglio è possibile utilizzare un peso di riga di 1 o 2 pixel. Usare il giudizio migliore per determinare quale sia più adatto.

- Avere almeno una spaziatura di 1 pixel tra gli elementi per le icone 16x16 e 24x24. Per le icone 32x32, usare la spaziatura tra due pixel tra gli elementi e tra il modificatore e l'elemento di base.

  ![Spaziatura elementi per icone di dimensioni 16x16, 24x24 e 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Spaziatura elementi per icone di dimensioni 16x16, 24x24 e 32x32

#### <a name="color-and-accessibility"></a>Colore e accessibilità
 Le linee guida di conformità di Visual Studio richiedono che tutte le icone del prodotto superino i requisiti di accessibilità per il colore e il contrasto. Questa operazione viene eseguita tramite inversione dell'icona e, quando si progetta, è necessario tenere presente che saranno invertite a livello di codice nel prodotto.

 Per altre informazioni sull'uso del colore nelle icone di Visual Studio, vedere [uso dei colori nelle immagini](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Uso del colore nelle immagini

### <a name="overview"></a>Panoramica
 Le icone in Visual Studio sono principalmente monocromatiche. Il colore è riservato per fornire informazioni specifiche e mai per la decorazione. Viene usato il colore:

- per indicare un'azione

- per segnalare all'utente una notifica di stato

- per designare l'affiliazione alla lingua

- per distinguere gli elementi all'interno di IntelliSense

### <a name="accessibility"></a>Accessibilità
 Le linee guida di conformità di Visual Studio richiedono che tutte le icone controllate nel prodotto superino i requisiti di accessibilità per il colore e il contrasto. I colori nella tavolozza della lingua visiva sono stati testati e soddisfano questi requisiti.

#### <a name="color-inversion-for-dark-themes"></a>Inversione dei colori per temi scuri
 Per far apparire le icone con il giusto rapporto di contrasto nel tema scuro di Visual Studio, viene applicata un'inversione a livello di codice. I colori in questa guida sono stati scelti in parte, in modo che vengano invertiti correttamente. Limitare l'uso del colore a questa tavolozza oppure si otterranno risultati imprevedibili quando si applica l'inversione.

 ![Esempi di icone con colori invertiti](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Esempi di icone con colori invertiti

### <a name="base-palette"></a>Tavolozza di base
 Tutte le icone standard contengono tre colori di base. Le icone non contengono gradienti o ombreggiatura, con una o due eccezioni per le icone degli strumenti 3D.

|Utilizzo|Nome|Valore (tema chiaro)|Campione|Esempio|
|-----------|----------|---------------------------|------------|-------------|
|Sfondo/scuro|VS BG|424242/66, 66, 66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Esempio di tavolozza di base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Primo piano/chiaro|VS FG|F0EFF1/240.239.241|![Campione F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Riquadro|Visual Studio|F6F6F6/246.246.246|![Campione F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Oltre ai colori di base, ogni icona può contenere un colore aggiuntivo dalla tavolozza estesa.

### <a name="extended-palette"></a>Tavolozza estesa

#### <a name="action-modifiers"></a>Modificatori di azione
 I quattro colori seguenti indicano i tipi di azioni richiesti dai modificatori di azione:

|Utilizzo|Nome|Valore (tutti i temi)|Campione|
|-----------|----------|--------------------------|------------|
|Positivo|Verde azione VS|388A34/56138, 52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negativo|Rosso azione VS|A1260D/161, 38, 13|![Campione A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutralità|Blu azione VS|00539C/0, 83156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Crea/nuovo|Arancio azione VS|C27D1A/194156, 26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Esempio
 Il verde viene usato per i modificatori di azione positivi, come "Add", "Run", "Play" e "Validate".

|Esegui|Eseguire la query|Esegui tutti i passaggi|Aggiungi controllo|
|-|-|-|-|
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Icona Esegui query](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Icona Riproduci tutti i passi](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Icona Aggiungi controllo](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Il rosso viene usato per i modificatori di azione negativi come "Delete", "Stop", "Cancel" e "close".

|Eliminare la relazione|Elimina colonna|Interrompi query|Connessione offline|
|-|-|-|-|
|![Icona Elimina relazioni](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Icona Elimina colonna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Icona Interrompi query](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Icona Connessione offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Il blu viene applicato ai modificatori di azione neutri rappresentati più di frequente come frecce, ad esempio "Apri", "Avanti", "precedente", "importazione" ed "esportazione".

|Vai al campo|Check-In in batch|Editor indirizzi|Editor associazione|
|-|-|-|-|
|![Icona Vai al campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Icona di controllo&#45;in batch nell'icona](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Icona Editor di indirizzo](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![Icona Editor di associazione](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 Oro scuro viene usato principalmente per il modificatore "New".

|Nuovo progetto|Crea nuovo grafico|Nuovo unit test|Nuovo elemento elenco|
|-|-|-|-|
|![Icona Nuovo progetto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Icona Crea Nuovo grafico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Icona Nuovo Unit test](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Icona Nuova voce di elenco](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Casi speciali
 In casi speciali, un modificatore di azione colorato può essere usato in modo indipendente come icona autonoma. Il colore utilizzato per l'icona riflette le azioni a cui è associata l'icona. Questo utilizzo è limitato a un piccolo subset di icone, tra cui:

|Esegui|Interrompere|Elimina|Salva|Esplora indietro|
|-|-|-|-|-|
|![Icona Esegui](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Icona Arresta il quadrato rosso a tinta unita.](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Icona Elimina](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Icona Salva](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Icona Esplora indietro](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Tavolozza gerarchia del codice

#### <a name="folder"></a>Cartella

|Utilizzo|Nome|Valore (tutti i temi)|Campione|Esempio|
|-----------|----------|--------------------------|------------|-------------|
|Cartelle|Cartella|DCB67A/220.182.122|![Campione DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icona del colore della cartella](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Linguaggi di Visual Studio
 A ogni linguaggio o piattaforma comune disponibile in Visual Studio è associato un colore. Questi colori vengono utilizzati sull'icona di base o sui modificatori di linguaggio visualizzati nell'angolo superiore destro delle icone composte.

|Utilizzo|Nome|Valore (tutti i temi)|Campione|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP.NET HTML WPF blu|0095D7/0149.215|![Campione 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP viola|9B4F96/155, 79150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS verde (Visual Studio Action verde)|388A34/56138, 52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS rosso|BD1E2D/189, 30, 45|![Campione BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|Viola FS|672878/103, 40120|![Campione 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|Arancione JS|F16421/241100, 33|![Campione F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB blu (VS Action Blue)|00539C/0, 83156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Arancione Servizi terminal|E04C06/224, 76, 6|![Campione E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|Verde PY|879636/135150, 54|![Campione 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Esempi di icone con modificatori di linguaggio

|VB|C#|C++|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Icona di Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![Icona di&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![Icona di&#43;&#43; C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![Icona&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![Icona di JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Icona di Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|
|![Icona di HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Icona di WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Icona di ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Icona di CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Icona di TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript|

#### <a name="intellisense"></a>IntelliSense
 Le icone IntelliSense usano una tavolozza dei colori esclusiva. Questi colori vengono usati per aiutare gli utenti a distinguere rapidamente tra i diversi elementi nell'elenco popup di IntelliSense.

|Utilizzo|Nome|Valore (tutti i temi)|Campione|
|-----------|----------|--------------------------|------------|
|Classe, evento|Arancio azione VS|C27D1A/194125, 26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metodo di estensione, metodo, modulo, delegato|Viola azione VS|652D90/101, 45144|![Campione 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Campo, elemento enum, macro, struttura, tipo valore Unione, operatore, interfaccia|Blu azione VS|00539C/0, 83156|![Campione 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Oggetto|Verde azione VS|388A34/56138, 52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Costante, eccezione, elemento enum, mappa, elemento della mappa, spazio dei nomi, modello, definizione del tipo|Sfondo (VS BG)|424242/66, 66, 66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Esempi di icone IntelliSense

|Classe|Evento privato|Delegato|Friend metodo|Campo|
|-|-|-|-|-|
|![Icona della classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![Icona dell'evento privato IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![Icona del delegato IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Icona descrittiva del metodo IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Icona campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Elemento enum protetto|Oggetto|Modello|Collegamento eccezione|
|-|-|-|-|
|![Icona dell'elemento enum protetto IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![Icona dell'oggetto IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![Icona del modello IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![Icona del collegamento all'eccezione IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Notifiche
 Le notifiche in Visual Studio vengono usate per indicare lo stato. La tavolozza delle notifiche usa i quattro colori seguenti, nonché le opzioni di riempimento in primo piano nero o bianco, per definire le notifiche con i livelli di stato seguenti.

|Utilizzo|Nome|Valore (tutti i temi)|Campione|
|-----------|----------|--------------------------|------------|
|Stato: neutro|Notifica blu (VS blu)|1BA1E2/27.161.226|![Campione 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stato: positivo|Verde delle notifiche (VS verde)|339933/51153, 51|![Campione 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stato: negativo|Notifica rossa (VS rosso)|E51400/229, 20, 0|![Campione E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stato: avviso|Notifiche gialle (VS arancione)|FFCC00/255204, 0|![Campione FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Riempimento in primo piano|Notifica nero (nero)|000000/0, 0, 0|![Campione &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Riempimento in primo piano|Notifica bianco (bianco)|FFFFFF/255.255.255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Esempi di icone di notifica

|Avviso|Avviso|Operazione completata|Interrompere|
|-|-|-|-|
|![Icona di avviso](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Icona avviso](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Icona Completato](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Arresta il cerchio rosso con icona a tinta unita con un quadrato bianco al centro.](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|