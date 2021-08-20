---
title: Editor immagini
description: Informazioni su come usare l'editor Visual Studio immagini per visualizzare e modificare le risorse trama e immagine usate nello sviluppo di app DirectX.
ms.custom: SEO-VS-2020
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 47bcc37f0fe000066f8e2585098601b71e606a12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133549"
---
# <a name="image-editor"></a>Editor immagini

Questo articolo descrive come usare l'**editor di immagini** di Visual Studio per visualizzare e modificare la trama e le risorse di immagine.

Con l'**editor di immagini** è possibile usare i tipi di formati avanzati per trame e immagini, che vengono impiegati nello sviluppo di app DirectX. Nell'editor è incluso il supporto per formati di file di immagine e codifiche dei colori comuni, per funzionalità come i canali alfa e il mapping MIP e per molti dei formati di trama con accelerazione hardware e ad alta compressione supportati da DirectX.

## <a name="supported-formats"></a>Formati supportati

L'**editor di immagini** supporta i formati di immagine seguenti:

|Nome del formato|Estensione del file|
|-----------------| - |
|Portable Network Graphics|*PNG*|
|JPEG|*.jpg*, *jpeg,* *jpe,* *jfif*|
|Direct Draw Surface|*.dds*|
|Graphics Interchange Format|*.gif*|
|Bitmap|*.bmp*, *.dib*|
|TIFF (Tagged Image File Format)|*.tif,* *.tiff*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Introduzione

Questa sezione descrive come aggiungere un'immagine al progetto Visual Studio e configurarla in base ai propri requisiti.

### <a name="add-an-image-to-your-project"></a>Aggiungere un'immagine al progetto

1. In **Esplora soluzioni** aprire il menu di scelta rapida del progetto a cui si vuole aggiungere l'immagine e scegliere **Aggiungi** > **Nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento**, in **Installato**, selezionare **Grafica** e quindi selezionare un formato di file appropriato per l'immagine.

   > [!NOTE]
   > Se non viene visualizzata la categoria **Grafica** nella finestra di dialogo **Aggiungi nuovo elemento**, potrebbe essere necessario installare il componente **Editor di immagini e modelli 3D**. Chiudere la finestra di dialogo **e** quindi selezionare Strumenti Ottieni strumenti e funzionalità dalla barra dei menu per aprire il Programma di installazione di Visual Studio  >   . Selezionare la scheda **Singoli componenti** e il componente **Editor di immagini e modelli 3D** nella categoria **Giochi e grafica**. Selezionare **Modifica**.
   >
   > ![Componente Editor di immagini e modelli 3D](media/image-3d-model-editors-component.png)

   Per informazioni su come scegliere un formato di file in base ai requisiti, vedere la sezione [Scelta del formato dell'immagine](#choose-the-image-format).

3. Specificare il **nome** del file di immagine e **il percorso** in cui deve essere creato.

4. Fare clic sul pulsante **Aggiungi**.

### <a name="choose-the-image-format"></a>Scelta del formato dell'immagine

A seconda di come si prevede di usare l'immagine, alcuni formati di file possono essere più appropriati di altri. Alcuni formati, ad esempio, potrebbero non supportare una funzionalità necessaria, quali il formato trasparenza o un formato di colore specifico. Alcuni formati potrebbero non offrire la compressione adatta per il tipo di contenuto dell'immagine pianificata.

Le informazioni seguenti possono essere utili per scegliere un formato di immagine adatto alle proprie esigenze:

**Immagine bitmap (estensione bmp)**

Formato dell'immagine bitmap. Un formato di immagine non compresso che supporta colori a 24 bit. Il formato bitmap non supporta la trasparenza.

**Immagine GIF (estensione gif)**

Formato di immagine GIF (Graphics Interchange Format). Un formato di immagine senza perdita di dati con compressione LZW che supporta fino a 256 colori. Non è adatto a fotografie e immagini con una quantità significativa di dettagli di colore, ma offre dei buoni rapporti di compressione per le immagini con un numero limitato di colori che hanno un alto livello di coerenza nei colori.

**Immagine JPG (estensione jpg)**

Formato di immagine JPEG (Joint Photographic Experts Group). Un formato di immagine a elevata compressione e con perdita di dati che supporta colori a 24 bit ed è adatto alla compressione per scopi generici di immagini che hanno un alto livello di coerenza nei colori.

**Immagine PNG (estensione png)**

Formato di immagine PNG (Portable Network Graphics). Un formato di immagine con compressione moderata e senza perdita di dati che supporta colori a 24 bit e trasparenza alfa. È adatto alle immagini naturali e artificiali, ma non fornisce buoni rapporti di compressione come i formati con perdita di dati quali JPG o GIF.

**Immagine TIFF (estensione tif)**

Formato di immagine TIFF o TIF (Tagged Image File Format). Un formato di immagine flessibile che supporta diversi schemi di compressione.

**Trama DDS (estensione dds)**

Formato di trama DDS (DirectDraw Surface). Un formato di trama a elevata compressione e con perdita di dati che supporta colori a 24 bit e trasparenza alfa. I rapporti di compressione possono essere al massimo di 8:1. Si basa sulla tecnologia di compressione S3 Texture Compression, che può essere decompressa nell'hardware grafico.

**Immagine TGA (estensione tga)**

Formato di immagine TGA (Truevision Graphics Adapter), noto anche come Targa. Un formato di immagine senza perdita di dati con compressione RLE che supporta sia immagini con colori mappati (tavolozza dei colori) sia immagini con colori diretti, con colori fino a 24 bit e trasparenza alfa. Non è adatto a fotografie e immagini con una quantità significativa di dettagli di colore, ma offre dei buoni rapporti di compressione per le immagini con ampi intervalli di colori identici.

### <a name="configure-the-image"></a>Configurazione dell'immagine

Prima di iniziare a lavorare all'immagine creata, è possibile modificarne la configurazione predefinita. È ad esempio possibile modificare le dimensioni o il formato di colore usato. Per informazioni su come configurare queste e altre proprietà dell'immagine, vedere [Proprietà dell'immagine](#image-properties).

> [!NOTE]
> Prima di salvare il lavoro, assicurarsi di impostare la proprietà **Formato colore** se si vuole usare un formato di colore specifico. Se il formato del file supporta la compressione, è possibile modificare le impostazioni di compressione quando si salva il file per la prima volta oppure quando si sceglie **Salva con nome**.

## <a name="work-with-the-image-editor"></a>Uso dell'editor di immagini

Questa sezione descrive come usare **l'editor di immagini** per modificare trame e immagini.

I comandi che influiscono sullo stato **dell'editor di** immagini si trovano sulla barra degli strumenti modalità **editor** di immagini insieme ai comandi avanzati. La barra degli strumenti si trova lungo il bordo superiore dell'area **di progettazione dell'editor** di immagini. Gli strumenti di disegno si trovano sulla barra **degli strumenti dell'editor** di immagini lungo il bordo più a sinistra dell'area **di progettazione dell'editor** di immagini.

### <a name="image-editor-mode-toolbar"></a>Barra degli strumenti della modalità dell'editor di immagini

![Barra degli strumenti della modalità dell'editor di immagini in Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

La tabella seguente descrive gli elementi nella barra degli strumenti della **modalità dell'editor di immagini**, elencati nell'ordine di visualizzazione da sinistra verso destra:

|Elemento della barra degli strumenti|Descrizione|
|------------------|-----------------|
|**Select**|Consente di selezionare un'area rettangolare di un'immagine. Dopo aver selezionato un'area, è possibile tagliarla, copiarla, spostarla, ridimensionarla, ruotarla, capovolgerla o eliminarla. In presenza di una selezione attiva, gli strumenti di disegno influiscono solo sull'area selezionata.|
|**Selezione irregolare**|Consente di selezionare un'area non regolare di un'immagine. Dopo aver selezionato un'area, è possibile tagliarla, copiarla, spostarla, ridimensionarla, ruotarla, capovolgerla o eliminarla. In presenza di una selezione attiva, gli strumenti di disegno influiscono solo sull'area selezionata.|
|**Selezione con bacchetta magica**|Consente di selezionare un'area con colori simili all'interno di un'immagine. È possibile configurare la *tolleranza*, ovvero la differenza massima tra colori adiacenti entro la quale sono considerati simili, per includere una gamma più ampia o più ristretta di colori simili. Dopo aver selezionato un'area, è possibile tagliarla, copiarla, spostarla, ridimensionarla, ruotarla, capovolgerla o eliminarla. In presenza di una selezione attiva, gli strumenti di disegno influiscono solo sull'area selezionata.|
|**Dettaglio**|Consente di spostare l'immagine in relazione alla cornice della finestra. In modalità **Panoramica** selezionare un punto nell'immagine e quindi spostarlo in qualsiasi direzione.<br /><br /> È possibile attivare temporaneamente la **modalità Panoramica** premendo e tenendo premuto **CTRL.**|
|**Zoom**|Consente di visualizzare una quantità maggiore o minore di dettagli dell'immagine in relazione alla cornice della finestra. In modalità **Zoom** selezionare un punto nell'immagine e quindi spostarlo a destra o in basso per fare zoom avanti oppure a sinistra o in alto per fare zoom indietro.<br /><br /> È possibile eseguire lo zoom avanti o indietro tenendo premuto **CTRL** mentre si usa la rotellina del mouse o si preme il segno più ( ) o **+** il segno meno ( **-** ).|
|**Zoom a dimensioni effettive**|Visualizza l'immagine usando una relazione 1:1 tra i pixel dell'immagine e quelli dello schermo.|
|**Adatta alla finestra**|Visualizza l'immagine completa nella cornice della finestra.|
|**Adatta larghezza**|Visualizza l'ampiezza completa dell'immagine nella cornice della finestra.|
|**Pannello Grid**|Abilita o disabilita la griglia che indica i limiti dei pixel. È possibile che la griglia non venga visualizzata finché non si ingrandisce l'immagine con lo zoom.|
|**Visualizzazione livello MIP successivo**|Attiva il successivo livello MIP più grande in una catena di mapping MIP. Il livello MIP attivo è visualizzato nell'area di progettazione. Questo elemento è disponibile solo per le trame con livelli MIP.|
|**Visualizzazione livello MIP precedente**|Attiva il successivo livello MIP più piccolo in una catena di mapping MIP. Il livello MIP attivo è visualizzato nell'area di progettazione. Questo elemento è disponibile solo per le trame con livelli MIP.|
|**Canale rosso**<br /><br /> **Canale verde**<br /><br /> **Canale blu**<br /><br /> **Canale alfa**|Abilita o disabilita il canale di colore specifico. **Nota:** abilitando o disabilitando in modo sistematico i canali dei colori, è possibile isolare i problemi correlati a uno o più canali. Ad esempio, è possibile identificare la trasparenza alpha non corretta.|
|**Background**|Abilita o disabilita la visualizzazione dello sfondo attraverso parti trasparenti dell'immagine. È possibile configurare la modalità di visualizzazione dello sfondo scegliendo tra le opzioni seguenti:<br /><br /> **Scacchi**<br /> Usa il colore verde insieme al colore di sfondo specificato per visualizzare lo sfondo con un motivo a scacchiera. È possibile usare questa opzione per rendere più evidenti le parti trasparenti dell'immagine.<br /><br /> Sfondo bianco<br /> Usa il bianco per visualizzare lo sfondo.<br /><br /> Sfondo nero<br /> Usa il nero per visualizzare lo sfondo.<br /><br /> Anima sfondo<br /> Esegue lentamente una panoramica del modello a scacchiera. È possibile usare questa opzione per rendere più evidenti le parti trasparenti dell'immagine.|
|**Proprietà**|Apre o chiude alternativamente la finestra **Proprietà**.|
|**Funzionalità avanzate**|Contiene opzioni e comandi aggiuntivi.<br /><br /> **Filtri**<br /><br /> Fornisce vari filtri di immagine comuni: **Bianco e nero**, **Sfocatura**, **Luminosità**, **Scurimento**, **Rilevamento bordi**, **Rilievo**, **Inverti colori**, **Increspatura**, **Tono seppia** e **Nitidezza**.<br /><br /> **Motori grafica**<br /><br /> **Rendering con D3D11**<br /> Usa Direct3D 11 per eseguire il rendering **dell'area di progettazione dell'editor** di immagini.<br /><br /> **Rendering con D3D11WARP**<br /> Usa Direct3D 11 Windows Advanced Rasterization Platform (WARP) per eseguire il rendering dell'area di **progettazione dell'editor** di immagini.<br /><br /> **Strumenti**<br /><br /> **Capovolgi orizzontalmente**<br /> Traspone l'immagine attorno all'asse orizzontale, o asse X.<br /><br /> **Capovolgi verticalmente**<br /> Traspone l'immagine attorno all'asse verticale, o asse Y.<br /><br /> **Genera MIP**<br /> Genera i livelli MIP per un'immagine. Se i livelli MIP sono già presenti, vengono ricreati dal livello MIP più grande. Le modifiche apportate ai livelli MIP più piccoli vengono perse. Per salvare i livelli MIP generati, è necessario usare il formato *DDS* per salvare l'immagine.<br /><br /> **Visualizzazione**<br /><br /> **Frequenza fotogrammi**<br /> Quanto è abilitata, consente di visualizzare la frequenza dei fotogrammi nell'angolo superiore destro dell'area di progettazione. La frequenza dei fotogrammi è il numero di fotogrammi disegnati al secondo. **Suggerimento:** È possibile scegliere il **pulsante** Avanzate per eseguire nuovamente l'ultimo comando.|

### <a name="image-editor-toolbar"></a>Barra degli strumenti dell'editor di immagini

![Barra degli strumenti dell'editor di immagini](../designers/media/digit-tre-toolbar.png)

La tabella seguente descrive gli elementi sulla barra degli strumenti **dell'editor** di immagini, elencati nell'ordine in cui vengono visualizzati dall'alto verso il basso:

|Elemento della barra degli strumenti|Descrizione|
|------------------|-----------------|
|**Matita**|Usa la selezione di colore attiva per disegnare un tratto con aliasing. È possibile impostare il colore e lo spessore del tratto nella finestra **Proprietà**.|
|**Brush**|Usa la selezione di colore attiva per disegnare un tratto con anti-aliasing. È possibile impostare il colore e lo spessore del tratto nella finestra **Proprietà**.|
|**Aerografo**|Usa la selezione di colore attiva per disegnare un tratto con anti-aliasing che si fonde insieme all'immagine e diventa più saturo in funzione del tempo. È possibile impostare il colore e lo spessore del tratto nella finestra **Proprietà**.|
|**Eyedropper**|Imposta la selezione di colore attiva in base al colore del pixel selezionato.|
|**Fill**|Usa la selezione di colore attiva per riempire un'area dell'immagine. L'area interessata include il pixel a cui viene applicato il riempimento e ogni pixel dello stesso colore che sia connesso al primo tramite pixel dello stesso colore. Se il riempimento viene applicato all'interno di una selezione attiva, l'area interessata sarà vincolata dalla selezione.<br /><br /> Per impostazione predefinita, la selezione di colore attiva viene fusa insieme all'area interessata dell'immagine in base alla componente alfa. Per usare la selezione colori attiva per sovrascrivere l'area interessata, tenere premuto **MAIUSC** quando si usa lo strumento riempimento.|
|**Gomma**|Imposta i pixel sul colore completamente trasparente se l'immagine supporta un canale alfa. In caso contrario, imposta i pixel sul colore di sfondo attivo.|
|**Linea**, **Rettangolo**, **Rettangolo arrotondato**, **Ellisse**|Disegna una forma in un'immagine. È possibile impostare il colore e lo spessore del contorno nella finestra **Proprietà**.<br /><br /> Per disegnare una primitiva con larghezza e altezza uguali, tenere premuto **MAIUSC** mentre si disegna.|
|**Text**|Usa la selezione del colore di primo piano per tracciare del testo. Il colore di sfondo è determinato dalla selezione del colore di sfondo. Per uno sfondo trasparente, il valore alfa della selezione del colore di sfondo deve essere 0. Mentre l'area di testo è attiva, è possibile specificare se il testo viene tracciato usando un tratto con anti-aliasing ed è possibile impostare per il testo le opzioni **Valore**, **Tipo di carattere** e **Dimensione** e lo stile **Grassetto**, **Corsivo** o **Sottolineato** nella finestra **Proprietà**. Il contenuto e l'aspetto del testo viene completato quando l'area di testo non è più attiva.|
|**Ruota**|Ruota l'immagine di 90 gradi in senso orario.|
|**Tagliare**|Taglia l'immagine in base alla selezione attiva.|

### <a name="work-with-mip-levels"></a>Uso dei livelli MIP

Alcuni formati di immagine, ad esempio il formato con estensione *DDS*, DirectDraw Surface, supportano i livelli MIP per il livello di dettaglio dello spazio della trama. Per informazioni su come generare e usare i livelli MIP, vedere [Procedura: Creare e modificare i livelli MIP](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Uso della trasparenza

Alcuni formati di immagine, ad esempio i formati con estensione *DDS*, DirectDraw Surface, supportano la trasparenza. Esistono diversi modi di usare la trasparenza, a seconda dello strumento in uso. Per specificare il livello di trasparenza per una selezione di colore, nella finestra **Proprietà** impostare la componente **A** (alpha) di tale selezione di colore.

La tabella seguente descrive come i diversi tipi di strumenti controllano la modalità di applicazione della trasparenza:

|Strumento|Descrizione|
|----------|-----------------|
|**Matita**, **Pennello**, **Aerografo**, **Linea**, **Rettangolo**, **Rettangolo arrotondato**, **Ellisse**, **Testo**|Per fondere la selezione di colore attiva insieme all'immagine, nella finestra **Proprietà** espandere il gruppo di proprietà **Canali** e impostare la casella di controllo **Disegno** per il canale **Alfa** e quindi disegnare normalmente.<br /><br /> Per disegnare usando la selezione di colore attiva e lasciare invariato il valore alfa dell'immagine, deselezionare la casella di controllo **Disegno** per il canale **Alfa** e quindi disegnare normalmente.|
|**Fill**|Per fondere la selezione di colore attiva insieme all'immagine, basta scegliere l'area da riempire.<br /><br /> Per usare la selezione colori attiva, incluso il valore del canale alfa, per sovrascrivere l'immagine, tenere premuto **MAIUSC** e quindi scegliere l'area da riempire.|

### <a name="image-properties"></a>Proprietà dell'immagine

È possibile usare la finestra **Proprietà** per specificare varie proprietà dell'immagine, ad esempio impostare le proprietà Larghezza e Altezza per ridimensionare l'immagine.

La tabella seguente descrive le proprietà dell'immagine:

|Proprietà|Descrizione|
|--------------|-----------------|
|Larghezza|Larghezza dell'immagine.|
|Altezza|Altezza dell'immagine.|
|Bit per pixel|Numero di bit che rappresentano ogni pixel. Il valore di questa proprietà dipende dal valore di **Formato colore** dell'immagine.|
|Selezione trasparente|**True** per fondere il livello di selezione insieme all'immagine principale, in base al valore alfa del livello di selezione; in caso contrario, **False**. Questo elemento è disponibile solo per le immagini che supportano la componente alfa.|
|Formato|Formato di colore dell'immagine. È possibile specificare diversi formati di colore, a seconda del formato dell'immagine. Il formato di colore definisce il numero e il tipo di canali di colore inclusi nell'immagine e anche la dimensione e la codifica di vari canali.|
|Livello MIP|Livello MIP attivo. Questo elemento è disponibile solo per le trame con livelli MIP.|
|Conteggio livelli MIP|Numero totale di livelli MIP nell'immagine. Questo elemento è disponibile solo per le trame con livelli MIP.|
|Conteggio frame|Numero totale di frame nell'immagine. Questo elemento è disponibile solo per le immagini che supportano le matrici di trame.|
|Frame|Frame corrente. Solo il primo frame può essere visualizzato. Tutti gli altri frame vengono persi quando l'immagine viene salvata.|
|Conteggio sezioni di profondità|Numero totale di sezioni di profondità nell'immagine. Questo elemento è disponibile solo per le immagini che supportano le trame di volume.|
|Sezione di profondità|Sezione di profondità corrente. Solo la prima sezione può essere visualizzata. Tutte le altre sezioni vengono perse quando l'immagine viene salvata.|

> [!NOTE]
> Poiché la proprietà **Rotazione di** si applica a tutti gli strumenti e alle aree selezionate, viene sempre visualizzata nella parte inferiore della finestra **Proprietà** insieme ad altre proprietà degli strumenti. **Rotazione di** viene sempre visualizzata perché l'intera immagine è implicitamente selezionata quando non sono attivi altri strumenti o selezioni. Per altre informazioni sulla proprietà **Rotate by,** vedere [Proprietà dello strumento](#tool -properties).

### <a name="resize-images"></a>Ridimensionamento delle immagini

Esistono due modi per ridimensionare un'immagine. In entrambi i casi, **l'editor di immagini** usa l'interpolazione bilineare per ricampionare l'immagine.

- Nella finestra **Proprietà** specificare nuovi valori per le proprietà **Larghezza** e **Altezza**.

- Selezionare l'intera immagine e usare i marcatori del bordo per ridimensionarla.

### <a name="selected-regions"></a>Aree selezionate

Le selezioni nell'**editor di immagini** definiscono le aree dell'immagine attive. Gli strumenti e le trasformazioni influenzano le aree attive. Se è presente una selezione attiva, le aree esterne all'area selezionata non sono interessate dalla maggior parte degli strumenti e delle trasformazioni. Se invece non è presente una selezione attiva, l'intera immagine è attiva.

La maggior parte degli strumenti, come **Matita**, **Pennello**, **Aerografo**, **Riempimento**, **Gomma** e primitive 2D, e delle trasformazioni, come **Ruota**, **Taglia**, **Inverti colori**, **Capovolgi orizzontalmente** e **Capovolgi verticalmente**, è vincolata o definita dalla selezione attiva. Tuttavia, alcuni strumenti, quali **Contagocce** e **Testo**, e trasformazioni, quali **Genera MIP**, non sono interessati dalle selezioni attive. Questi strumenti si comportano sempre come se l'intera immagine corrisponda alla selezione attiva.

Mentre si seleziona un'area, è possibile tenere premuto **MAIUSC** per eseguire una selezione proporzionale, ovvero quadrata. In caso contrario, la selezione non è vincolata.

#### <a name="resize-selections"></a>Ridimensionamento delle selezioni

Dopo aver selezionato un'area, è possibile ridimensionarla o ridimensionarne i contenuti di immagine modificando le dimensioni del marcatore di selezione. Quando si ridimensiona l'area selezionata, è possibile usare i tasti di modifica seguenti per modificare il comportamento dell'area selezionata durante il ridimensionamento:

**CTRL**: copia il contenuto dell'area selezionata prima che venga ridimensionata. In questo modo, l'immagine originale rimane invariata mentre la copia viene ridimensionata.

**MAIUSC**: ridimensiona l'area selezionata proporzionalmente alle dimensioni originali.

**ALT**: modifica le dimensioni dell'area selezionata. In questo modo, l'immagine rimane invariata.

La tabella seguente illustra le combinazioni di tasti di modifica valide:

|CTRL|MAIUSC|ALT|Descrizione|
|----------|-----------|---------|-----------------|
||||Ridimensiona il contenuto dell'area selezionata.|
||**Maiusc**||Ridimensiona in modo proporzionale il contenuto dell'area selezionata.|
|||**Alt**|Ridimensiona l'area selezionata. In questo modo viene definita una nuova area di selezione.|
||**Maiusc**|**Alt**|Ridimensiona in modo proporzionale l'area selezionata. In questo modo viene definita una nuova area di selezione.|
|**Ctrl**|||Copia e quindi ridimensiona il contenuto dell'area selezionata.|
|**Ctrl**|**Maiusc**||Copia e quindi ridimensiona in modo proporzionale il contenuto dell'area selezionata.|

### <a name="tool-properties"></a>Proprietà degli strumenti

Quando è selezionato uno strumento, è possibile usare la finestra **Proprietà** per specificare i dettagli su come questo deve agire sull'immagine. Ad esempio, è possibile impostare lo spessore dello strumento **Matita** o il colore dello strumento **Pennello**.

È inoltre possibile impostare sia un colore di primo piano sia un colore di sfondo. Entrambi supportano un canale alfa per fornire l'opacità definita dall'utente. Le impostazioni si applicano a tutti gli strumenti. Se si usa il mouse, il pulsante sinistro corrisponde al colore di primo piano e quello destro corrisponde al colore di sfondo.

La tabella seguente descrive le proprietà degli strumenti:

|Strumento|Proprietà|
|----------|----------------|
|Tutti gli strumenti e le selezioni|**Rotazione di**<br /> Definisce il numero di gradi, in senso orario, in base al quale viene ruotato lo strumento o la selezione.|
|**Matita**, **Pennello**, **Aerografo**, **Gomma**|**Thickness**<br /> Definisce le dimensioni dell'area interessata dallo strumento.|
|**Text**|**Anti-alias**<br /> Traccia il testo usando bordi con anti-aliasing. In questo modo il testo assume un aspetto più uniforme.<br /><br /> **Valore**<br /> Testo da tracciare.<br /><br /> **Font**<br /> Tipo di carattere usato per tracciare il testo.<br /><br /> **Dimensioni**<br /> Dimensione del testo.<br /><br /> **Grassetto**<br /> Applica il grassetto.<br /><br /> **Corsivo**<br /> Applica il corsivo.<br /><br /> **Sottolineato**<br /> Applica la sottolineatura.|
|**Primitiva 2D**|**Anti-alias**<br /> Disegna le primitive usando bordi con anti-aliasing. In questo modo, le primitive assumono un aspetto più uniforme.<br /><br /> **Thickness**<br /> Definisce lo spessore della linea che forma il contorno della primitiva.<br /><br /> **Raggio X**<br /> (Solo rettangolo arrotondato) Definisce il raggio di arrotondamento per i bordi superiore e inferiore della primitiva.<br /><br /> **Raggio Y**<br /> (Solo rettangolo arrotondato) Definisce il raggio di arrotondamento per i bordi destro e sinistro della primitiva.|
|**Matita**, **Pennello**, **Aerografo**, **Primitiva 2D**|**Canali**<br /> Abilita o disabilita i canali di colore specifici per la visualizzazione e il disegno. Se per un canale di colore specifico è impostata l'opzione **Visualizzazione**, tale canale è visibile nell'immagine. In caso contrario, non è visibile. Se per un canale di colore specifico è impostata l'opzione **Disegno**, tale canale è interessato dalle operazioni di disegno. In caso contrario, non lo è.|
|**Selezione con bacchetta magica**, **Riempimento**|**Tolleranza**<br /> Definisce la differenza massima tra i colori adiacenti considerati simili, in modo da includere un numero minore o maggiore di colori simili nell'area interessata o selezionata. Per impostazione predefinita, il valore è 32. In questo modo, i pixel adiacenti in 32 tonalità (più chiare o più scure) del colore originale vengono considerati come parte dell'area.|

## <a name="keyboard-shortcuts"></a>Scelte rapide da tastiera

|Comando|Scelte rapide da tastiera|
|-------------| - |
|Passare alla modalità **Seleziona**|**S**|
|Passare alla modalità **Zoom**|**Z**|
|Passare alla modalità **Panoramica**|**K**|
|Seleziona tutto|**CTRL** + **A**|
|Eliminare la selezione corrente|**Elimina**|
|Annullare la selezione corrente|**ESC** (escape)|
|Zoom avanti|**CTRL** + **Rotellina del mouse in avanti**<br /><br /> **CTRL** + **PageUp**<br /><br /> Segno più ( **+** )|
|Zoom indietro|**CTRL** - **Rotellina del mouse indietro**<br /><br /> **CTRL** - **Pagina alla rovescia**<br /><br /> Segno meno ( **-** )|
|Fare una panoramica dell'immagine verso l'alto|**Rotellina del mouse indietro**<br /><br /> **PGGIÙ**|
|Fare una panoramica dell'immagine verso il basso|**Rotellina del mouse avanti**<br /><br /> **PGSU**|
|Fare una panoramica dell'immagine verso sinistra|**MAIUSC** + **Rotellina del mouse indietro**<br /><br /> **Rotellina del mouse a sinistra**<br /><br /> **MAIUSC** + **Pagina alla rovescia**|
|Fare una panoramica dell'immagine verso destra|**MAIUSC** + **Rotellina del mouse in avanti**<br /><br /> **Rotellina del mouse verso destra**<br /><br /> **MAIUSC** + **PageUp**|
|Fare zoom in base alla dimensione effettiva|**CTRL** + **0** (zero)|
|Adattare l'immagine alla finestra|**CTRL** + **G**, **CTRL** + **F**|
|Adattare l'immagine alla larghezza della finestra|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **I**|
|Attivare o disattivare la griglia|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **G**|
|Ritagliare l'immagine in base alla selezione corrente|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **C**|
|Visualizzare il livello MIP successivo (maggiore dettaglio)|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **6**|
|Visualizzare il livello MIP precedente (minore dettaglio)|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **7**|
|Attivare o disattivare il canale del colore rosso|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **1**|
|Attivare o disattivare il canale del colore verde|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **2**|
|Attivare o disattivare il canale del colore blu|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **3**|
|Attivare o disattivare il canale alfa (trasparenza)|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **4**|
|Attivare o disattivare il motivo a scacchi alfa|**CTRL+FRECCIA DESTRA** + **G**, **CTRL** + **B**|
|Attivare lo strumento per la selezione irregolare|**L**|
|Attivare lo strumento per la selezione con bacchetta magica|**M**|
|Attivare lo strumento Matita|**P**|
|Attivare lo strumento Pennello|**B**|
|Attivare lo strumento Riempimento|**F**|
|Attivare lo strumento Gomma|**E**|
|Attivare lo strumento Testo|**T**|
|Attivare lo strumento di selezione del colore (contagocce)|**Ho**|
|Spostare la selezione attiva e il relativo contenuto|**Tasti di** direzione.|
|Ridimensionare la selezione attiva e il relativo contenuto|**CTRL+FRECCIA DESTRA** + **Tasti di** direzione|
|Spostare la selezione attiva, ma non il relativo contenuto|**MAIUSC** + **Tasti di** direzione|
|Ridimensionare la selezione attiva, ma non il relativo contenuto|**MAIUSC** + **CTRL** + **Tasti di** direzione|
|Eseguire il commit del livello corrente|**Ritorno**|
|Ridurre lo spessore dello strumento|**[**|
|Aumentare lo spessore dello strumento|**]**|

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Uso di asset 3D per giochi e app](../designers/working-with-3-d-assets-for-games-and-apps.md)|Fornisce informazioni generali sugli strumenti disponibili in Visual Studio per usare gli asset grafici come trame, immagini, modelli 3D ed effetti shader.|
|[Editor dei modelli](../designers/model-editor.md)|Descrive come usare l'editor dei modelli di Visual Studio per lavorare con i modelli 3D.|
|[Finestra di progettazione shader](../designers/shader-designer.md)|Descrive come usare la progettazione shader di Visual Studio per lavorare con gli shader.|
