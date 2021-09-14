---
title: Finestra di progettazione shader
description: Informazioni su come usare la finestra Visual Studio Shader per creare, modificare ed esportare effetti visivi personalizzati noti come shader.
ms.custom: SEO-VS-2020
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 02b59924a2b2020d6c5855f5e91f41615601a19d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710365"
---
# <a name="shader-designer"></a>Finestra di progettazione shader

Questo documento descrive come usare la **finestra di progettazione shader** di Visual Studio per creare, modificare ed esportare effetti visivi personalizzati noti come *shader*.

È possibile usare la **finestra di progettazione shader** per creare effetti visivi personalizzati per un gioco o un'app anche se non si conosce il linguaggio di programmazione HLSL (High-Level Shader Language). Per creare uno shader nella **finestra di progettazione shader**, si definisce il layout in forma di grafico. A questo scopo, si aggiungono all'area di progettazione *nodi* che rappresentano i dati e le operazioni, quindi si creano connessioni tra di essi per definire il modo in cui le operazioni elaborano i dati. Per ogni nodo dell'operazione viene fornita un'anteprima dell'effetto prodotto fino a quel momento in modo da poterne visualizzare il risultato. I dati passano attraverso i nodi verso un nodo finale che rappresenta l'output dello shader.

## <a name="supported-formats"></a>Formati supportati

La **finestra di progettazione shader** supporta questi formati di shader:

|Nome del formato|Estensione nome del file|Operazioni supportate (visualizzazione, modifica, esportazione)|
|-----------------| - | - |
|Directed Graph Shader Language|*.dgsl*|Visualizzazione, modifica|
|Shader HLSL (codice sorgente)|*.hlsl*|Esportazione|
|Shader HLSL (bytecode)|*.cso*|Esportazione|
|Intestazione C++ (matrice di bytecode HLSL)|*H*|Esportazione|

## <a name="get-started"></a>Introduzione

In questa sezione viene descritto come aggiungere uno shader DGSL al progetto Visual Studio C++ e vengono fornite informazioni introduttive di base.

> [!NOTE]
> L'integrazione della compilazione automatica degli elementi grafici, come i grafici shader (file con estensione dgsl) è supportata solo per i progetti C++.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Per aggiungere uno shader DGSL al progetto

1. Assicurarsi di avere a disposizione il componente di Visual Studio richiesto installato necessario per usare gli elementi grafici. Questo componente è denominato **Editor di immagini e modelli 3D**.

   Per installarlo, aprire Programma di installazione di Visual Studio selezionando Strumenti Ottieni strumenti e funzionalità dalla barra dei menu e quindi selezionare la scheda Singoli componenti. Selezionare il componente Editor di modelli immagine e  >   **3D**  nella categoria Giochi e grafica e quindi selezionare **Modifica**. 

   ![Componente Editor di immagini e modelli 3D](media/image-3d-model-editors-component.png)

2. In **Esplora soluzioni** aprire il menu di scelta rapida del progetto C++ a cui si vuole aggiungere lo shader e quindi scegliere **Aggiungi** > **Nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento**, in **Installato**, selezionare **Grafica** e quindi selezionare **Visual Effect Graph (.dgsl)**.

   > [!NOTE]
   > Se non viene visualizzata la categoria **Grafica** nella finestra di dialogo **Aggiungi nuovo elemento** e il componente **Editor di immagini e modelli 3D** è installato, gli elementi grafici non sono supportati per il tipo di progetto.

4. Specificare il **Nome** del file shader e il **percorso** in cui crearlo.

5. Fare clic sul pulsante **Aggiungi**.

### <a name="the-default-shader"></a>Shader predefinito

Ogni volta che si crea uno shader DGSL, viene inizialmente definito come uno shader minimo con un solo nodo **Colore punto** collegato al nodo **Colore finale**. Sebbene questo shader sia completo e funzionale, non fa molto. Per creare uno shader funzionante, quindi, come primo passaggio è spesso necessario eliminare il nodo **Colore punto** o scollegarlo dal nodo **Colore finale** per fare spazio ad altri nodi.

## <a name="work-with-the-shader-designer"></a>Uso della finestra di progettazione shader

Nelle sezioni seguenti viene descritto come utilizzare Progettazione shader per utilizzare shader personalizzati.

### <a name="shader-designer-toolbars"></a>Barre degli strumenti della finestra di progettazione shader

Le barre degli strumenti della finestra di progettazione shader contengono comandi che consentono di usare grafici di shader DGSL.

I comandi che influiscono sullo stato della finestra di progettazione shader si trovano nella barra degli strumenti **Modalità progettazione shader** della finestra principale di Visual Studio. Gli strumenti e i comandi di progettazione si trovano nella barra degli strumenti della **finestra di progettazione shader** disponibile nell'area di progettazione.

Di seguito è illustrata la barra degli strumenti **Modalità progettazione shader**.

![Barra degli strumenti modale progettazione shader.](../designers/media/digit-dsd-modal-toolbar.png)

Questa tabella descrive gli elementi disponibili nella barra degli strumenti **Modalità progettazione shader**, elencati nell'ordine di visualizzazione da sinistra verso destra.

|Elemento della barra degli strumenti|Descrizione|
|------------------|-----------------|
|**Select**|Consente l'interazione con i nodi e i bordi nel grafico. In questa modalità è possibile selezionare nodi per spostarli o eliminarli, nonché definire bordi o interromperli.|
|**Dettaglio**|Consente lo spostamento di un grafico shader relativo alla cornice della finestra. Per visualizzare una panoramica, selezionare un punto nell'area di progettazione e spostarlo nell'area circostante.<br /><br /> In **modalità** Selezione è possibile premere e tenere premuto **CTRL** per attivare **temporaneamente** la modalità Panoramica.|
|**Zoom**|Consente la visualizzazione di un numero maggiore o minore di dettagli del grafico shader relativo alla cornice della finestra. In modalità **Zoom** selezionare un punto nell'area di progettazione e spostarlo a destra o in basso per eseguire lo zoom avanti oppure a sinistra o in alto per eseguire lo zoom indietro.<br /><br /> In modalità **Seleziona** è possibile tenere premuto **CTRL** per eseguire lo zoom avanti o indietro usando la rotellina del mouse.|
|**Zoom per adattare**|Consente di visualizzare il grafico shader completo nella cornice della finestra.|
|**Modalità rendering in tempo reale**|Se è abilitato il rendering in tempo reale, Visual Studio ridisegna l'area di progettazione, anche se non viene eseguita alcuna azione da parte dell'utente. Questa modalità è utile se si utilizzano shader mutevoli nel tempo.|
|**Anteprima con sfera**|Se abilitata, viene usato un modello di sfera per visualizzare in anteprima lo shader. È possibile abilitare una sola forma di anteprima alla volta.|
|**Anteprima con cubo**|Se abilitata, viene usato un modello di cubo per visualizzare in anteprima lo shader. È possibile abilitare una sola forma di anteprima alla volta.|
|**Anteprima con cilindro**|Se abilitata, viene usato un modello di cilindro per visualizzare in anteprima lo shader. È possibile abilitare una sola forma di anteprima alla volta.|
|**Anteprima con cono**|Se abilitata, viene usato un modello di cono per visualizzare in anteprima lo shader. È possibile abilitare una sola forma di anteprima alla volta.|
|**Anteprima con teiera**|Se abilitata, viene usato un modello di teiera per visualizzare in anteprima lo shader. È possibile abilitare una sola forma di anteprima alla volta.|
|**Anteprima con teiera**|Se abilitata, viene usato un modello di teiera per visualizzare in anteprima lo shader. È possibile abilitare una sola forma di anteprima alla volta.|
|**Casella degli strumenti**|Consente di visualizzare o nascondere la **casella degli strumenti**.|
|**Proprietà**|Consente di visualizzare o nascondere la finestra **Proprietà**.|
|**Funzionalità avanzate**|Contiene opzioni e comandi avanzati.<br /><br /> **Esporta**: consente l'esportazione di uno shader in diversi formati.<br /><br /> **Esporta come**: esporta lo shader come codice sorgente HLSL o come bytecode shader compilato. Per altre informazioni su come esportare gli shader, vedere [Procedura: Esportare uno shader.](../designers/how-to-export-a-shader.md)<br /><br /> **Motori grafica**: consente la selezione del renderer usato per visualizzare l'area di progettazione.<br /><br /> **Rendering con D3D11**: usa Direct3D 11 per eseguire il rendering dell'area di progettazione della finestra di progettazione shader.<br /><br /> **Rendering con D3D11**: usa la piattaforma WARP (Windows Advanced Rasterization Platform) di Direct3D 11 per il rendering dell'area di progettazione della finestra di progettazione shader.<br /><br /> **Visualizza**: consente la selezione di informazioni aggiuntive sulla finestra di progettazione shader.<br /><br /> **Frequenza dei fotogrammi**: se abilitata, consente di visualizzare la frequenza dei fotogrammi corrente nell'angolo superiore destro dell'area di progettazione. La frequenza dei fotogrammi è il numero di fotogrammi disegnati al secondo. Questa opzione è utile quando si abilita l'opzione **Modalità rendering in tempo reale**.|

> [!TIP]
> È possibile scegliere il pulsante **Avanzate** per eseguire nuovamente l'ultimo comando.

### <a name="work-with-nodes-and-connections"></a>Uso di nodi e connessioni

Usare la modalità **Seleziona** per aggiungere, rimuovere, riposizionare, connettere e configurare i nodi. Di seguito viene illustrato come eseguire queste operazioni di base.

#### <a name="to-perform-basic-operations-in-select-mode"></a>Per eseguire operazioni di base in modalità Seleziona

- Ecco come:

  - Per aggiungere un nodo al grafico, selezionarlo nella **casella degli strumenti** e spostarlo nell'area di progettazione.

  - Per rimuovere un nodo dal grafico, selezionarlo e premere **CANC**.

  - Per riposizionare un nodo, selezionarlo e spostarlo in una nuova posizione.

  - Per collegare due nodi, spostare un terminale di output di un nodo in un terminale di input dell'altro nodo. Possono essere collegati solo terminali con tipi compatibili. Una linea tra i terminali mostra la connessione.

  - Per rimuovere una connessione, scegliere **Interrompi collegamenti** dal menu di scelta rapida di uno dei terminali connessi.

  - Per configurare le proprietà di un nodo, selezionare il nodo e nella finestra **Proprietà** specificare nuovi valori per le proprietà.

### <a name="preview-shaders"></a>Anteprima degli shader

Per capire come uno shader apparirà nell'app, è possibile configurare il modo in cui l'effetto viene visualizzato in anteprima. Per approssimare la creazione di un'app, è possibile scegliere una forma di cui eseguire il rendering, configurare le trame e altri parametri di materiale, attivare l'animazione degli effetti basati sul tempo ed esaminare l'anteprima da angolature diverse.

#### <a name="shapes"></a>Forme

Nella finestra di progettazione shader sono disponibili sei forme, una sfera, un cubo, un cilindro, un cono, una teiera e un piano, che è possibile usare per visualizzare in anteprima lo shader. A seconda del tipo di shader, alcune forme potrebbero offrire un'anteprima migliore.

Per scegliere una forma da visualizzare in anteprima, nella barra degli strumenti **Modalità progettazione shader** scegliere la forma desiderata.

#### <a name="textures-and-material-parameters"></a>Trame e parametri di materiale

Molti shader si basano su trame e proprietà di materiali per produrre un aspetto univoco per ogni tipo di oggetto nell'app. Per vedere l'aspetto che avrà lo shader nell'app, è possibile impostare le trame e le proprietà di materiali usate per il rendering dell'anteprima per trovare una corrispondenza con le trame e i parametri che possono essere usati nell'app.

Per associare una trama diversa a un registro di trama o modificare altri parametri di materiali:

1. In modalità **Seleziona** selezionare un'area vuota dell'area di progettazione. Nella finestra **Proprietà** vengono visualizzate le proprietà globali dello shader.

2. Nella finestra **Proprietà** specificare nuovi valori per le proprietà di trama e parametri che si vuole modificare.

La tabella seguente riporta i parametri di shader che è possibile modificare:

|Parametro|Proprietà|
|---------------|----------------|
|**Trama 1**  -  **Trama 8**|**Accesso**:                             **pubblico per** consentire l'impostazione della proprietà dall'Editor modelli. in caso contrario, **Private**.<br /><br /> **Nome file**: percorso completo del file della trama associato a questo registro di trama.|
|**Ambiente materiale**|**Accesso**:                             **pubblico per** consentire l'impostazione della proprietà dall'Editor modelli. in caso contrario, **Private**.<br /><br /> **Valore**: colore diffuso del pixel corrente dovuto all'illuminazione indiretta o ambientale.|
|**Materiale diffuso**|**Accesso**: **Pubblico** per consentire l'impostazione della proprietà dall'editor dei modelli. **Privato** in caso contrario.<br /><br /> **Value**: colore che descrive il modo in cui il pixel corrente diffonde l'illuminazione diretta.|
|**Materiale emissivo**|**Accesso**:                              **pubblico per** consentire l'impostazione della proprietà dall'Editor modelli. in caso contrario, **Private**.<br /><br /> **Valore**: contributo di colore del pixel corrente, in base all'illuminazione autofornita.|
|**Materiale speculare**|**Accesso**:                              **pubblico per** consentire l'impostazione della proprietà dall'Editor modelli. in caso contrario, **Private**.<br /><br /> **Valore**: colore che descrive il modo in cui l'illuminazione diretta viene riflessa dal pixel corrente.|
|**Materiale potenza speculare**|**Accesso**:                             **pubblico per** consentire l'impostazione della proprietà dall'Editor modelli. in caso contrario, **Private**.<br /><br /> **Valore**: esponente che definisce l'intensità delle evidenziazioni speculari nel pixel corrente.|

#### <a name="time-based-effects"></a>Effetti basati sul tempo

Alcuni shader hanno un componente temporale che anima l'effetto. Per vedere come apparirà l'effetto, è necessario aggiornare l'anteprima più volte al secondo. Per impostazione predefinita, l'anteprima viene aggiornata solo quando lo shader viene modificato; per modificare questo comportamento in modo da poter visualizzare gli effetti basati sul tempo, è necessario abilitare il rendering in tempo reale.

Per abilitare il rendering in tempo reale, nella barra degli strumenti della finestra di progettazione Shader scegliere **Modalità rendering in tempo reale**.

#### <a name="examine-the-effect"></a>Esaminare l'effetto

Molti shader sono interessati da variabili come l'angolo di visualizzazione o l'illuminazione direzionale. Per esaminare il modo in cui l'effetto reagisce alla variazione di queste variabili, è possibile ruotare liberamente la forma di anteprima e osservare il comportamento dello shader.

Per ruotare la forma, tenendo premuto **ALT**, selezionare un punto qualsiasi nell'area di progettazione e spostarlo.

### <a name="export-shaders"></a>Esportazione degli shader

Prima di poter usare uno shader nell'app, è necessario esportarlo in un formato supportato da DirectX.

È possibile esportare gli shader come codice sorgente HLSL o come bytecode shader compilato. Il codice sorgente HLSL viene esportato in un file di testo con estensione *hlsl.* Il bytecode dello shader può essere esportato in un file binario non elaborato con estensione *cso* o in un file di intestazione C++ (con estensione *h*) che codifica il bytecode dello shader in una matrice.

Per altre informazioni su come esportare gli shader, vedere [Procedura: Esportare uno shader.](../designers/how-to-export-a-shader.md)

## <a name="keyboard-shortcuts"></a>Tasti di scelta rapida

|Comando|Tasti di scelta rapida|
|-------------| - |
|Passare alla modalità **Seleziona**|**CTRL** + **G**, **CTRL** + **Q**<br /><br /> **S**|
|Passare alla modalità **Zoom**|**CTRL** + **G**, **CTRL** + **Z**<br /><br /> **Z**|
|Passare alla modalità **Panoramica**|**CTRL** + **G**, **CTRL** + **P**<br /><br /> **K**|
|Seleziona tutto|**CTRL** + **Oggetto**|
|Eliminare la selezione corrente|**Elimina**|
|Annullare la selezione corrente|**ESCAPE** (**ESC**)|
|Zoom avanti|**CTRL** + **Rotellina del mouse in avanti**<br /><br /> Segno più ( **+** )|
|Zoom indietro|**CTRL** + **Rotellina del mouse all'indietro**<br /><br /> Segno meno ( **-** )|
|Fare una panoramica dell'area di progettazione verso l'alto|**Rotellina del mouse indietro**<br /><br /> **PGGIÙ**|
|Fare una panoramica dell'area di progettazione verso il basso|**Rotellina del mouse avanti**<br /><br /> **PGSU**|
|Fare una panoramica dell'area di progettazione verso sinistra|**MAIUSC** + **Rotellina del mouse all'indietro**<br /><br /> **Rotellina del mouse a sinistra**<br /><br /> **MAIUSC** + **PageDown**|
|Fare una panoramica dell'area di progettazione verso destra|**MAIUSC** + **Rotellina del mouse in avanti**<br /><br /> **Rotellina del mouse verso destra**<br /><br /> **MAIUSC** + **PageUp**|
|Sposta lo stato attivo della tastiera su un altro nodo|Tasti **freccia**|
|Selezionare il nodo con lo stato attivo della tastiera (aggiunge il nodo al gruppo di selezione)|**MAIUSC** + **BARRA SPAZIATRICE**|
|Attivare o disattivare la selezione del nodo con lo stato attivo|**CTRL** + **BARRA SPAZIATRICE**|
|Attivare o disattivare la selezione corrente (se non è selezionato alcun nodo, selezionare il nodo con lo stato attivo)|**BARRA SPAZIATRICE**|
|Spostare in alto la selezione corrente|**MAIUSC** + **Freccia SU**|
|Spostare in basso la selezione corrente|**MAIUSC** + **Freccia GIÙ**|
|Spostare a sinistra la selezione corrente|**MAIUSC** + **Freccia SINISTRA**|
|Spostare a destra la selezione corrente|**MAIUSC** + **Freccia DESTRA**.|

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Uso di asset 3D per giochi e app](../designers/working-with-3-d-assets-for-games-and-apps.md)|Fornisce una panoramica degli strumenti di Visual Studio a cui attingere per poter usare trame e immagini, modelli 3D ed effetti shader.|
|[Editor di immagini](../designers/image-editor.md)|Descrive come usare l'editor di immagini di Visual Studio con trame e immagini.|
|[Editor di modelli](../designers/model-editor.md)|Descrive come usare l'editor dei modelli di Visual Studio per lavorare con i modelli 3D.|
