---
title: Modelli compositi per Visual Studio | Microsoft Docs
description: Informazioni sui modelli compositi importanti per la coerenza in Visual Studio. I modelli compositi combinano elementi di interazione e progettazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8ac314a2ec49b805fc87badf6b63a719b8511e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952096"
---
# <a name="composite-patterns-for-visual-studio"></a>Modelli compositi per Visual Studio
I modelli compositi combinano elementi di interazione e progettazione in configurazioni distinte. Alcuni dei più importanti modelli compositi in Visual Studio rispetto alla coerenza includono:

- [Visualizzazione dei dati](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfaccia utente e visualizzazione in oggetto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistenza e salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualizzazione dei dati

### <a name="overview"></a>Panoramica
 I grafici rappresentano un modo visivo per aggregare e visualizzare i dati allo scopo di migliorare il processo decisionale. Possono aiutare gli utenti a occuparsi di una grande quantità di dati, ma poco significative vedono cosa merita attenzione e cosa potrebbe richiedere un'azione.

 L'utente trarrà vantaggio da un grafico se si verifica una delle condizioni seguenti:

- Il grafico consentirà agli utenti di identificare le attività su cui possono agire?

- Il grafico consentirà agli utenti di prevedere le conseguenze di potenziali modifiche?

- Il grafico consente agli utenti di individuare le tendenze e identificare i modelli?

- Il grafico consentirà agli utenti di prendere decisioni migliori?

- Il grafico aiuterà a rispondere a una domanda specifica che gli utenti possono avere nel contesto specificato?

#### <a name="general-rules-for-charts"></a>Regole generali per i grafici

- Etichettare chiaramente i dati. Le illustrazioni senza spiegazione sono semplicemente belle.

- Avviare gli assi da zero per evitare l'inclinazione delle proporzioni. La lunghezza delle righe e le dimensioni della barra sono indicatori visivi importanti per comprendere le relazioni tra i punti dati.

- Creare grafici, non infografica. Le infografica sono rappresentazioni artistiche dei dati e il loro obiettivo principale è la narrativa visiva. I grafici possono (e dovrebbero) essere visivamente accattivanti, ma lasciare che i dati parlino per se stesso.

- Evitare skeumorphism, grafici a barre pittoriche, hashmark di contrasto e altri tocchi di infografica.

- Non usare effetti 3D come elementi decorativi. È possibile usarli solo se sono effettivamente parte integrante della capacità dell'utente di comprendere le informazioni.

- Evitare di utilizzare più righe e riempimenti, poiché più di due colori possono rendere difficile la lettura e l'interpretazione di questo tipo di grafico.

- Non utilizzare un grafico (o qualsiasi illustrazione) come unico mezzo per comprendere un concetto o interagire con i dati. Questa operazione presenta difficoltà per gli utenti con problemi visivi.

- Non usare i grafici come elementi gratuiti o decorativi in una pagina. In altre parole, se un grafico non aggiunge alcun valore o aiuta gli utenti a risolvere un problema, non usarlo.

### <a name="chart-types"></a>Tipi di grafico
 I tipi di grafici utilizzati in Visual Studio includono grafici a barre, grafici a linee, un grafico a torta modificato noto come grafico ad anello o "grafico ad anello", sequenze temporali, grafici a dispersione (detti anche "grafici del cluster") e grafici di Gantt. Ogni tipo di grafico è utile per la comunicazione di un tipo diverso di informazioni.

### <a name="other-charting-considerations"></a>Altre considerazioni sui grafici

#### <a name="color"></a>Colore
 In Visual Studio è disponibile una tavolozza specifica dei colori grafici definiti per l'utilizzo. La tavolozza è accessibile per i tipi principali di cecità dei colori e i colori possono essere differenziati anche quando vengono usati come sezioni molto strette di colore. È possibile usare questi colori in qualsiasi combinazione per qualsiasi tipo di grafico o grafico nell'interfaccia utente. Non è necessario usare tutti i sette colori se non sono necessari molti colori distinti. Questi colori non sono stati progettati per essere usati con alcun elemento in primo piano, quindi non inserire testo o glifi su questi colori. Queste tonalità devono essere hardcoded ed essere esposte alla personalizzazione dell'utente in **strumenti > opzioni** (vedere [esposizione dei colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Campione|Hex|RGB|
|------------|---------|---------|
|![Campione 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113178, 82|
|![Campione BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191, 63, 0|
|![Campione FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252183, 20|
|![Campione 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144, 63139|
|![Campione 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17.122.209|
|![Campione 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121.215.242|
|![Campione B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181.181.181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interfaccia utente e visualizzazione in oggetto
 Questa sezione fornisce il contesto per la lettura, nota anche come visualizzazione di anteprima del codice, un tipo di interfaccia utente in oggetto univoco per Visual Studio.

### <a name="overview"></a>Panoramica

- L'interfaccia utente di un oggetto deve fornire all'utente ulteriori informazioni o interattività senza ritirare dalla propria attività principale.

- Il modello principale per l'interfaccia utente di un oggetto in Visual Studio è noto come "informazioni sul punto di attenzione".

- L'interfaccia utente di un oggetto in Visual Studio può essere inline o mobile e durevole o temporaneo.

  - La visualizzazione del codice, un tipo di interfaccia utente su oggetto in Visual Studio, è inline e durevole.

  - CodeLens, un tipo di interfaccia utente su oggetto in Visual Studio, è mobile e temporaneo

  Per comprendere il funzionamento di una porzione di codice o la ricerca di dettagli su tale codice, spesso è necessario che lo sviluppatore Commuti il contesto e vada ad altro contenuto o a un'altra finestra. Questi cambi di contesto possono compromettere, perché gli utenti possono perdere lo stato attivo sulla propria attività originale se lasciano la finestra principale. Inoltre, il recupero di un contesto originale può essere difficile, soprattutto se il cambio di codice ha causato l'offuscamento del codice originale da parte di un'altra interfaccia utente.

  L'interfaccia utente di un oggetto segue un modello denominato "Information at The Point of attention". Questi messaggi, le finestre popup e le finestre di dialogo forniscono agli utenti informazioni aggiuntive rilevanti che aggiungono chiarimenti o interattività senza perdere lo stato attivo sulla propria attività principale. Esempi di interfaccia utente su oggetto includono finestre popup visualizzate quando un utente posiziona il puntatore del mouse su un'icona nell'area di notifica, il zigzag rosso sotto una parola digitata in modo errato e la visualizzazione di anteprima introdotta in Visual Studio 2013.

### <a name="decision-points"></a>Punti decisionali
 All'interno di Visual Studio, esistono diversi modi per usare questo modello di informazioni al punto di attenzione. Scegliere il meccanismo appropriato e implementarlo in modo coerente e prevedibile è essenziale per l'esperienza complessiva. In caso contrario, gli utenti potrebbero presentare un'esperienza confusa o incoerente che detrae lo stato attivo dal contenuto stesso.

#### <a name="relationships-between-master-and-detail-content"></a>Relazioni tra il contenuto master e quello dettagliato
 Le informazioni sul punto di attenzione vengono usate per visualizzare una relazione tra il contenuto su cui l'utente è concentrato (il contenuto "Master") e il contenuto correlato aggiuntivo (contenuto "dettaglio"). In questo modello, il contenuto dettagliato è chiaramente correlato al contenuto utilizzato dall'utente e può essere visualizzato vicino al contenuto principale. Le informazioni aggiuntive o le informazioni che non possono essere riepilogate senza sovraccaricare il contenuto master devono seguire un altro modello, ad esempio una finestra degli strumenti.

- Visualizza **sempre** il contenuto del dettaglio in prossimità del contenuto principale.

- Assicurarsi **sempre** che il contenuto del dettaglio consenta comunque a un utente di rimanere concentrato sul contenuto master. Il modo migliore per ottenere questo risultato è spesso quello di eseguire il rendering del contenuto dettaglio il più vicino possibile al contenuto master. Per eseguire questa operazione, è possibile eseguire il rendering del contenuto del dettaglio in una finestra popup accanto al contenuto master oppure eseguendo il rendering del contenuto dettaglio inline sotto il contenuto del master.

- **Non usare mai** le informazioni nel punto di attenzione che allontana l'utente dal contenuto principale. Se gli utenti devono visualizzare il contenuto del dettaglio separatamente, esporre un'azione esplicita che consenta all'utente di eseguire questa operazione.

#### <a name="design-details"></a>Dettagli progettazione
 Una volta stabilito che l'interfaccia utente on-Object è la scelta corretta, sono disponibili quattro considerazioni di progettazione principali:

1. **Persistenza:** il contenuto dovrebbe essere durevole o temporaneo?
   Si vuole che gli utenti mantengano visibili le informazioni per fare riferimento o interagire? In alternativa, gli utenti vogliono visualizzare rapidamente le informazioni e continuare con l'attività principale?

2. **Tipo di contenuto:** il contenuto può essere informativo, praticabile o di spostamento?
   L'utente necessita di ulteriori dettagli sul contenuto Master? L'utente deve completare un'attività che influisca sul contenuto Master? O l'utente deve essere reindirizzato a un'altra risorsa?

3. **Tipo di indicatore:** è opportuno avere un indicatore di ambiente?
   Le informazioni possono essere riepilogate in modo utile e visualizzate senza sovraccaricare il contenuto Master?

4. **Movimenti:** quali movimenti verranno usati per richiamare e chiudere l'interfaccia utente?
   In che modo l'utente Visualizza il contenuto del dettaglio e lo invia? È presente un valore per aggiungere un movimento, ad esempio il blocco, per passare tra gli stati temporanei e durevoli?

   Ognuno di questi quattro punti decisionali avrà un effetto sui componenti principali dell'interfaccia utente di un oggetto.

### <a name="on-object-ui-components"></a>Componenti dell'interfaccia utente in oggetto

1. Tipo di contenitore (Content Presenter)

    - Virgola mobile

    - Inline

2. Tipo di contenuto

    - Informativo: dati che potrebbero essere statici o dinamici

    - Azionebile: comandi che modificano il contenuto Master

    - Spostamento: collegamenti che consentono all'utente di passare a un'altra finestra o a un'altra applicazione, ad esempio MSDN

3. Movimenti

    - Chiamata

    - Licenziamento

    - Aggiunta

    - Altre interazioni

4. Persistenza e modello di commit

    - Temporaneo

    - Durable

    - Automatico

    - Su richiesta

5. Indicatori di ambiente (facoltativo)

    - Sottolineatura zigzag

    - Icona Smart Tag

    - Altri indicatori di ambiente

#### <a name="container-content-presenter-type"></a>Tipo di contenitore (Content Presenter)
 Sono disponibili due opzioni principali per presentare il contenuto al punto di attenzione:

1. **Inline:** un presentatore inline, ad esempio la visualizzazione di visualizzazione introdotta nell'editor di codice Visual Studio 2013, rende disponibile spazio per il nuovo contenuto spostando il contenuto esistente.

    - **Preferire** i presentatori inline se si prevede che gli utenti vogliano dedicare una quantità significativa di tempo che fa riferimento o interagisca con il contenuto presente.

    - **Evitare** i presentatori inline se si prevede che gli utenti desiderino visualizzare le informazioni presenti, quindi continuare con l'attività principale con un'interferenza minima.

2. **Mobile:** un presentatore mobile è posizionato il più vicino possibile al contenuto selezionato, ma non modifica il layout del contenuto esistente. È possibile utilizzare diverse strategie, ad esempio la visualizzazione di un pannello di contenuto mobile sullo spazio vuoto più vicino al simbolo selezionato.

    - **Preferisci** i presentatori mobili se si prevede che gli utenti desiderino visualizzare le informazioni presenti, quindi continuare con l'attività principale con un'interferenza minima.

    - **Evitare** i presentatori mobili se si prevede che gli utenti vogliano dedicare una quantità significativa di tempo che fa riferimento o interagisca con il contenuto presente.

#### <a name="content-type"></a>Tipo di contenuto
 Sono disponibili tre tipi principali di contenuto che possono essere visualizzati all'interno di qualsiasi contenitore dell'interfaccia utente in un oggetto. È possibile visualizzare qualsiasi combinazione di questi tipi di informazioni. I tre tipi sono:

1. **Informativo:** la maggior parte dei contenitori dell'interfaccia utente in oggetto visualizzerà un tipo di contenuto informativo. Il contenuto può rappresentare informazioni sullo stato attuale dell'ambiente oppure può rappresentare informazioni su un potenziale stato futuro dell'ambiente. Ad esempio, può essere usato per mostrare l'effetto di un particolare comando, ad esempio un refactoring, sul codice esistente.

    - Usare **sempre** la rappresentazione canonica delle informazioni visualizzate. Ad esempio, il codice dovrebbe essere simile al codice, completare con l'evidenziazione della sintassi e rispettare qualsiasi tipo di carattere e altre impostazioni di ambiente impostate dall'utente.

    - Considerare **sempre** il supporto di qualsiasi azione sul contenuto informativo che sarebbe possibile se le stesse informazioni venissero presentate come contenuto master. Se ad esempio si presenta codice esistente all'interno di un contenitore dell'interfaccia utente su un oggetto, è consigliabile supportare la possibilità di esplorare e modificare tale codice.

    - Considerare **sempre** l'uso di un colore di sfondo diverso se si presenta contenuto informativo che rappresenta un potenziale stato futuro.

2. Praticabile: alcuni contenitori dell'interfaccia utente su oggetti offrono la possibilità di eseguire un'azione sul contenuto Master, ad esempio l'esecuzione di un'operazione di refactoring.

    - Posizionare **sempre** i comandi eseguibili separatamente dal contenuto informativo.

    - Abilitare e disabilitare **sempre** le azioni quando appropriato.

    - Fare **sempre** riferimento alle linee guida standard per rappresentare i comandi all'interno delle finestre di dialogo.

    - Mantenete **sempre** il numero di azioni che vengono esposte in un contenitore dell'interfaccia utente su un oggetto per un valore minimo assoluto. L'interazione con l'interfaccia utente on-Object dovrebbe essere un'esperienza semplice e rapida. L'utente non deve spendere energia nella gestione del contenitore dell'interfaccia utente on-Object.

    - Considerare **sempre** come e quando un contenitore dell'interfaccia utente su un oggetto verrà chiuso o eliminato. Come procedura consigliata, qualsiasi azione che concluda la finestra di dialogo tra il contenuto master e i dettagli deve chiudere anche il contenitore dell'interfaccia utente su un oggetto quando viene richiamata l'azione.

3. **Spostamento:** alcuni contenitori dell'interfaccia utente in oggetto includono collegamenti che consentono all'utente di passare a un'altra finestra o applicazione, ad esempio l'apertura di un articolo di MSDN nel Web browser dell'utente.

    - Anteporre **sempre** qualsiasi collegamento di navigazione con "Open", in modo che gli utenti non siano sorpresi dall'esplorazione di altri contenuti.

    - Separa **sempre** i collegamenti di navigazione da collegamenti interoperabili.

#### <a name="ambient-indicators-optional"></a>Indicatori di ambiente (facoltativo)
 Gli indicatori di ambiente possono essere delicati, incluso il testo presentato in un colore a contrasto dal resto del codice, o ovvio, inclusi i simboli del solletico, ad esempio sottolineature zigzag e icone smart tag. Gli indicatori di ambiente comunicano la disponibilità di informazioni aggiuntive pertinenti. Idealmente, forniscono informazioni utili anche senza richiedere all'utente di interagire con loro.

- Posizionare **sempre** un indicatore di ambiente in modo che non venga distratto o sovraccaricato dall'utente. Se è impossibile posizionare un indicatore di ambiente in questo modo, prendere in considerazione un'altra soluzione.

- Posizionare **sempre** l'indicatore di ambiente il più vicino possibile al contenuto a cui è correlato.

- Provare **sempre** a creare un indicatore che riepiloga le informazioni che rende disponibili. È consigliabile fornire un conteggio del numero di elementi di dati disponibili (ad esempio, "3 Riferimenti" anziché semplicemente "Riferimenti") o pensare a un altro modo per riepilogare i dati.

  - Nei casi in cui i dati di un indicatore non possono essere sempre calcolati e visualizzati, è opportuno fornire un feedback progressivo quando vengono calcolati i valori. Si consideri, ad esempio, un'animazione delle modifiche che riflettono gli aggiornamenti ai dati disponibili, in modo analogo al modo in cui il riquadro live della posta elettronica Windows Phone viene aggiornato man mano che aumenta il numero di messaggi di posta elettronica non letti.

- **Non aggiungere mai** più indicatori che un utente può ragionevolmente assumere per un determinato contenuto. Gli indicatori di ambiente devono essere utili senza richiedere alcuna interazione da parte dell'utente. Gli indicatori perdono il proprio ambiente se richiedono overflow e altri controlli di gestione per visualizzarli.

#### <a name="gestures"></a>Movimenti
 Un aspetto fondamentale per consentire all'utente di mantenere lo stato attivo sul contenuto principale consiste nel supportare i movimenti corretti per aprire e ignorare il contenuto di dettagli aggiuntivi.

- È **sempre** necessario che l'utente esegua un movimento esplicito per aprire il contenuto aggiuntivo. I movimenti aperti comuni includono:

  - **Hover:** descrizioni comandi o contenuti informativi non interattivi

  - **Comando esplicito:** Presenter inline

  - **Fare doppio clic sull'indicatore di ambiente:** Finestra popup di CodeLens

- Ignorare **sempre** il contenuto del dettaglio ogni volta che l'utente preme il tasto ESC.

- Considerare **sempre** il contesto dell'interfaccia utente di un oggetto. Per i presentatori di contenuto che consentono l'interazione all'interno del contenitore, valutare con attenzione se visualizzare informazioni aggiuntive sul passaggio del mouse, il che potrebbe compromettere il flusso di lavoro dell'utente.

- **Non visualizzare mai** il contenuto al passaggio del mouse che risulta modificabile o invita l'interazione dell'utente. Questo comportamento può vanificare gli utenti se tentano di spostare il cursore sul contenuto del dettaglio, perché il comportamento standard di una descrizione comando è quello di ignorare immediatamente quando il cursore non si trova più sul contenuto master che lo ha prodotto.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modelli di selezione

### <a name="overview"></a>Panoramica
 Un modello di selezione è il meccanismo usato per indicare e confermare le operazioni su uno o più oggetti di interesse all'interno dell'interfaccia utente. In questo argomento vengono illustrati i modelli di interazione della selezione all'interno degli editor di documenti di Visual Studio: editor di testo, aree di progettazione e superfici di modellazione.

 Gli utenti devono avere un modo per indicare a Visual Studio cosa stanno lavorando e Visual Studio deve rispondere in modo prevedibile con commenti e suggerimenti agli utenti sul funzionamento. Le differenze o una comunicazione non conforme tra l'utente e l'interfaccia utente possono comportare la mancata presenza di un'azione da parte dell'utente, che può provocare conseguenze impreviste. Spesso l'errore non viene rilevato fino a quando l'utente non rileva che un elemento è mancante o è stato modificato. I modelli di selezione sono pertanto una delle parti più importanti della progettazione dell'interfaccia utente. Sebbene i modelli di selezione in Visual Studio siano coerenti con Windows, le variazioni sono minime.

 In Visual Studio, come in Windows, i modelli di selezione variano a seconda del contesto in cui si verifica l'interazione. Le selezioni possono essere eseguite in quattro tipi di oggetti:

- Testo

- Oggetti grafici

- Elenchi e alberi

- Griglie

  All'interno di questi oggetti sono disponibili tre tipi di selezione:

- Contigui

- Disgiunto

- Region

#### <a name="scope"></a>Ambito
 Il componente più importante della selezione è garantire che l'utente sia in grado di riconoscere la finestra che sta funzionando (attivazione) e la posizione dello stato attivo (selezione). Visual Studio estende la funzionalità di gestione delle finestre in Windows, ma lo schema di attivazione è lo stesso: l'interazione con una finestra porta lo stato attivo sulla finestra. Visual Studio include due indicatori per l'attivazione: uno per le finestre dei documenti e uno per le finestre degli strumenti.

 Per le finestre dei documenti, la finestra attiva è indicata da una scheda della finestra del documento in primo piano e modificando il colore di sfondo:

 ![Selezione della scheda attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Selezione scheda attiva**

 Per le finestre degli strumenti, la finestra attiva è indicata da una modifica apportata al colore dell'area della barra del titolo della finestra degli strumenti:

 ![Selezione della finestra degli strumenti attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Finestra degli strumenti attiva che mostra la selezione principale di un nodo**

 ![Selezione della finestra degli strumenti inattiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Finestra degli strumenti inattiva che mostra la selezione latente del nodo**

 Quando una finestra è attiva, la relativa messa a fuoco è indicata in base ai modelli di selezione descritti in questa sezione delle linee guida.

#### <a name="context"></a>Context
 Visual Studio è stato progettato per mantenere un concetto forte di contesto, tenendo traccia della posizione di lavoro dell'utente. È attiva una sola finestra, sia che si tratti di uno strumento o di una finestra del documento. Tuttavia, la finestra del documento in primo piano mantiene sempre una selezione latente. Sebbene lo stato attivo possa trovarsi in una finestra degli strumenti, la finestra del documento che era l'ultima attiva Visualizza una selezione, anche in uno stato inattivo. Questa operazione viene eseguita per mantenere il contesto dell'utente nel documento in cui sono state apportate modifiche, mostrando che Visual Studio ha mantenuto il proprio stato in modo che possano tornare e passare senza interruzioni tra le finestre degli strumenti e i documenti.

### <a name="text-selection"></a>Selezione testo
 Gli editor di Visual Studio che sono strettamente testuali, ad esempio l'editor di testo incorporato, utilizzano lo stesso modello di selezione di testo e l'aspetto descritti nella pagina [mouse e puntatori](/windows/desktop/uxguide/inter-mouse) delle linee guida sull'interazione dell'esperienza utente di Windows su MSDN. Lo stato attivo per l'input nell'editor di testo è indicato da una barra verticale denominata punto di inserimento. Il punto di inserimento è un singolo pixel di spessore e colorato come l'inverso di tutto ciò che viene visualizzato dietro di esso. Lampeggia in base alla frequenza impostata dall'impostazione della velocità di **lampeggio del cursore** nella scheda **velocità** dell'applet della **tastiera** nel pannello di controllo.

#### <a name="contiguous-and-disjoint-selection"></a>Selezione contigua e non contigua
 La selezione all'interno dell'editor di testo è solo contigua. Le selezioni di testo non contigue non sono consentite, ma devono essere risolte negli editor di oggetti grafici. Quando il puntatore del mouse dell'utente è posizionato su un'area di testo, il cursore cambia in un I-Beam. Un singolo clic posiziona il punto di inserimento nell'editor di testo in corrispondenza della posizione di clic. Tenendo premuto il pulsante del mouse, viene avviata un'evidenziazione di selezione e il pulsante del mouse termina l'evidenziazione della selezione.

#### <a name="region-selection-box-selection"></a>Selezione area (selezione casella)
 Visual Studio supporta le selezioni dell'area nell'editor di testo e questa operazione è denominata selezione box. La selezione della casella consente all'utente di selezionare un'area di testo che non segue il normale flusso di testo. Come per la selezione di testo standard, la selezione deve essere contigua. La selezione della casella viene avviata tenendo premuto il tasto ALT mentre si trascina con il mouse. La selezione della casella può essere avviata anche tenendo premuto ALT e MAIUSC mentre si utilizzano i tasti di direzione per indicare l'area di selezione. Selezione Box usa la selezione normale evidenziata e Mostra il cursore del punto di inserimento che lampeggia alla fine dell'area di selezione.

 ![Selezione&#41; casella di &#40;regionali in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Selezione area (box) in Visual Studio**

#### <a name="text-selection-appearance"></a>Aspetto selezione testo
 I colori utilizzati per la selezione attiva e inattiva nell'editor possono essere personalizzati. Per personalizzare l'aspetto visivo dell'editor, un utente può passare a **strumenti > opzioni** e quindi cercare in **ambiente > tipi di carattere e colori > editor di testo**.

### <a name="graphical-selection"></a>Selezione grafica

#### <a name="interaction"></a>Interazione
 La selezione di oggetti grafici può essere complessa e dipende da diversi fattori:

- **Modello di selezione principale dell'editor.** Gli editor che contengono oggetti grafici possono essere utilizzati anche per modificare testo o griglie. Ad esempio, l'editor potrebbe essere un editor basato su testo che supporta anche la posizione di oggetti grafici, ad esempio la finestra di progettazione XAML di Visual Studio. Il supporto di più tipi di oggetto può influire sul modo in cui l'utente seleziona i gruppi composti da diversi tipi di oggetti.

- **Supporto per gli Stati di selezione primaria e secondaria.** Un editor può fornire stati di selezione primari e secondari, in modo che gli oggetti possano essere modificati all'unisono, allineati l'uno con l'altro, ridimensionati insieme e così via.

- **Supporto per la modifica sul posto.** Gli editor possono inoltre consentire la modifica del contenuto degli oggetti grafici. Ad esempio, una forma rettangolo potrebbe contenere anche testo all'interno che può essere modificato dall'utente. Inoltre, il testo potrebbe essere centrato o giustificato. La modifica sul posto comporta un livello più dettagliato di interazione dell'utente e pertanto richiede un insieme appropriato di segnali visivi per la presentazione delle informazioni sullo stato all'utente.

#### <a name="mouse-interaction"></a>Interazione con il mouse

|Input|Risultato|
|-----------|------------|
|Fare clic su un oggetto non selezionato|Seleziona l'oggetto e visualizza una linea tratteggiata e gli handle di selezione, se l'oggetto è ridimensionabile.|
|Fare clic su un oggetto selezionato|Attiva la modifica sul posto se l'oggetto lo supporta. Quando si fa clic all'esterno dell'oggetto, viene disattivata la modalità di modifica sul posto.|
|Fare doppio clic su un oggetto|Apre il codice sottostante l'oggetto per la modifica e potrebbe inserire un gestore eventi predefinito, se appropriato.|
|Puntare a un oggetto|Imposta il puntatore sul cursore di spostamento. L'aspetto dell'oggetto, ad esempio la luminosità o il colore, potrebbe cambiare.|
|Puntare a un handle di selezione|Imposta il puntatore sul cursore di ridimensionamento. Per gli oggetti che supportano la rotazione, è possibile che alcuni handle di selezione modifichino il puntatore su un cursore ruota, perché il puntatore è posizionato in modo diverso (ad esempio, spostato più a lontano) rispetto all'handle di selezione.|
|Trascinamento|Anche se l'oggetto non è selezionato in precedenza, imposta il puntatore sul cursore di spostamento e sposta l'oggetto.|
|L'editor perde lo stato attivo|Disattiva la modalità di modifica sul posto, sebbene l'oggetto mantenga il contenuto e l'aspetto che aveva durante l'ultima operazione o lo stato di selezione.|
|Selezione oggetti|Indicato da un bordo, da una linea tratteggiata o da un altro trattamento visivo distinto per evidenziare il limite dell'oggetto.|
|Ridimensionare un oggetto selezionato|Indicato dagli handle di selezione.<br /><br /> Un oggetto ridimensionabile dispone di otto handle, che rappresentano ogni direzione in cui può essere ridimensionato. Se l'oggetto può essere ridimensionato solo in determinate direzioni, è possibile utilizzare un minor numero di handle. Quando l'utente ridimensiona un oggetto fino a quando otto handle non sono interattivi, è possibile usare quattro handle. Le dimensioni dell'handle devono essere associate al bordo della finestra e alle metriche perimetrali con la funzione API **GetSystemMetrics** per ridimensionare la risoluzione dello schermo.<br /><br /> ![Quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Ruotare un oggetto selezionato|![Punti di manipolazione di rotazione](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interazione con la tastiera

|Input|Risultato|
|-----------|------------|
|Scheda|Sposta l'indicatore di stato attivo tra l'ordine logico degli oggetti nell'editor. Questo può essere da sinistra a destra o dall'alto verso il basso a seconda del valore della proprietà **TabIndex** (o equivalente), dell'ordine di creazione dell'oggetto e dello scopo generale dell'editor. MAIUSC + TAB inverte la direzione dell'indicatore di stato attivo.|
|BARRA SPAZIATRICE|Attiva la modalità panning mentre viene mantenuta la sequenza di tasti. Per eseguire il panning della posizione del viewport, è necessario un ulteriore input del mouse.|
|CTRL+BARRA SPAZIATRICE|Attiva la modalità di zoom mentre viene mantenuta la sequenza di tasti. Per aumentare e ridurre il fattore di zoom, è necessario un ulteriore input del mouse.|
|CTRL + ALT + segno meno|Riduce il fattore di zoom di un livello.|
|CTRL + ALT + segno di addizione|Aumenta il fattore di zoom di un livello.|
|MAIUSC o CTRL|Aggiunge l'oggetto al gruppo di selezione. CTRL consente inoltre di rimuovere gli oggetti singolarmente dal gruppo di selezione.|
|Immettere|Esegue il comando predefinito per l'oggetto (in genere Open o Edit).|
|F2|Attiva la modifica sul posto per l'oggetto.|
|Tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto freccia premuto, in piccoli incrementi (ad esempio, 1 pixel alla volta)|
|CTRL + tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto freccia premuto, in incrementi maggiori (ad esempio, 10 pixel alla volta)|
|MAIUSC + tasti di direzione|Ridimensiona gli oggetti selezionati nella rispettiva direzione, in piccoli incrementi (ad esempio, 1 pixel alla volta)|
|CTRL + MAIUSC + tasti di direzione|Ridimensiona gli oggetti selezionati nella rispettiva direzione, con incrementi maggiori, ad esempio 10 pixel alla volta.|

 Quando gli utenti modificano i controlli sul posto, potrebbe essere utile che gli oggetti vengano ridimensionati automaticamente con l'input dell'utente. Se, ad esempio, l'utente modifica un controllo etichetta, l'etichetta dovrebbe espandersi per visualizzare il testo appena digitato dall'utente. Se questa operazione non viene eseguita, l'utente deve ridimensionare il controllo manualmente dopo aver modificato il testo. Se l'utente dispone di un numero elevato di controlli, questo diventa un'attività a Rote e non produttiva.

#### <a name="graphical-containers"></a>Contenitori grafici
 In alcuni casi, gli editor grafici forniscono contenitori per altri oggetti grafici, ad esempio il controllo pannello Windows Form o il controllo layout griglia nella finestra di progettazione HTML. Se l'editor fornisce contenitori per altri oggetti grafici, è necessario usare il modello di selezione seguente solo per il contenitore (gli oggetti all'interno del contenitore seguono il modello standard come descritto in precedenza):

|Input|Risultato|
|-----------|------------|
|Fai clic sul contenitore|Seleziona l'oggetto contenitore senza selezionare direttamente uno degli oggetti contenuti. Il contenitore può essere spostato e/o ridimensionato con il mouse e l'input della tastiera standard (come descritto in precedenza). Gli oggetti contenuti vengono spostati in relazione al contenitore, ma gli oggetti contenuti non vengono ridimensionati a meno che non siano anche selezionati direttamente.|
|Passare il mouse sull'area limite del contenitore|Converte il mouse nel cursore di spostamento, a indicare che è possibile spostare il contenitore.|
|Trascinare l'area limite del contenitore|Imposta il mouse sul cursore di spostamento e sposta il contenitore e gli oggetti contenuti all'interno di. Non è possibile spostare il contenitore senza prima selezionare con un solo clic.|
|Fare clic su un oggetto all'interno del contenitore|Deseleziona il contenitore (se selezionato) e seleziona solo l'oggetto selezionato.|
|Premere MAIUSC + clic o CTRL + clic su un oggetto contenuto e/o su un contenitore|Aggiunge l'oggetto selezionato a una selezione o a un gruppo di selezione esistente. Se l'oggetto selezionato è già membro del gruppo di selezione, viene rimosso dal gruppo di selezione.|

 Gli oggetti contenuti devono essere conformi al modello di selezione di base, come descritto nella sezione precedente. Dal test di usabilità della finestra di progettazione Windows Form, gli utenti aspettavano l'accesso trasparente agli oggetti contenuti senza passaggi (imposti dall'oggetto di contenimento).

#### <a name="disjoint-and-region-selections"></a>Selezioni non contigue e Region
 Gli editor di oggetti grafici devono supportare le selezioni non contigue. Si noti che questo grafico non Mostra l'aspetto del controllo per Visual Studio. Per le specifiche visive dettagliate, vedere [aspetto della selezione degli oggetti grafici](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) .

 ![Selettori di elementi non contigui e di aree](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Selezione non contigua**

 Gli editor grafici devono anche fornire selezioni di area con un indicatore di selezione del tipo Marquee. Se l'editor grafico supporta altri tipi di oggetti, ad esempio il testo, le selezioni dell'area potrebbero non essere possibili a seconda dei vincoli degli altri tipi di oggetto.

 ![Selezione di testo scorrevole](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Selezione di testo scorrevole**

#### <a name="primary-and-secondary-selections"></a>Selezioni primarie e secondarie
 Alcuni editor di oggetti grafici consentono all'utente di modificare o allineare gli oggetti nei gruppi. In questo caso, è necessario introdurre il concetto di selezioni primarie e secondarie. La selezione principale è l'oggetto a cui tutti gli altri oggetti rispondono per le operazioni di gruppo. L'oggetto che l'utente seleziona per primo diventa il controllo principale e le selezioni successive diventano le selezioni secondarie. La selezione primaria presenta un trattamento visivo distinto dalle selezioni secondarie per indicare quale oggetto è primario:

 ![Selezione primaria e secondaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Selezione primaria con due selezioni secondarie**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Aspetto selezione oggetto grafico
 Gli handle di selezione sono quadrati disegnati in un modello rettangolare intorno al rettangolo di selezione dell'oggetto. Il grafico seguente mostra esempi dei vari Stati che un oggetto grafico può avere con handle, ridimensionamento e aspetto di modifica sul posto. Le dimensioni degli handle devono essere associate al bordo della finestra e alle metriche perimetrali usando l'API **GetSystemMetrics** .

| State | Aspetto | Dettagli visivi |
|-------------------------|---------------| - |
| **Deselezionato** | Predefinito | ![Stato del pulsante predefinito](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Selezione primaria** | Ridimensionabile | ![Selezione primaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Selezione primaria** | Non ridimensionabile | ![Selezione primaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Selezione primaria** | Bloccato | ![Selezione primaria bloccata](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Selezione secondaria** | Ridimensionabile | ![Selezione secondaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Selezione secondaria** | Non ridimensionabile | ![Selezione secondaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Selezione secondaria** | Bloccato | ![Selezione secondaria bloccata](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Interfaccia utente attiva** | Predefinito | ![Stato attivo dell'interfaccia utente](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Visualizza modelli di selezione

#### <a name="tree-view"></a>Visualizzazione struttura
 La selezione in una visualizzazione albero viene visualizzata con un'evidenziazione semplice. Se l'utente fa clic sul nome di un nodo o sull'icona di un nodo, il nodo viene selezionato. Il glifo triangolare a sinistra del nodo espande o contrae il controllo albero ma non influisce sulla selezione dell'utente, con un'eccezione: quando si comprime un nodo padre quando la selezione si trova in un figlio di tale nodo, la selezione viene spostata nell'elemento padre.

 ![Visualizzazione albero tipica in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Visualizzazione albero tipica in Visual Studio**

 Le visualizzazioni albero possono supportare selezioni contigue e non contigue, anche su più livelli nell'albero. È necessario effettuare selezioni multiple contigue o non contigue sui nodi della struttura ad albero visibili. Se un nodo è compresso, la selezione non contigua viene persa e il nodo compresso ottiene la selezione. In questo modo, l'utente può visualizzare i nodi che saranno interessati da un'operazione. Quando i nodi vengono compressi, diventa poco chiaro i nodi che potrebbero essere interessati.

 Quando viene selezionato un nodo padre, l'operazione deve essere applicata all'elemento padre, anche se in alcuni casi è opportuno che un'operazione venga applicata all'elemento padre e a tutti i relativi elementi figlio. In questo caso, fornire un'interfaccia utente aggiuntiva durante l'operazione, ad esempio una finestra di dialogo di conferma o una casella di controllo per rendere esplicita l'opzione "applica a tutti gli elementi figlio".

##### <a name="renaming"></a>Ridenominazione
 Se i nodi dell'albero supportano la ridenominazione, è necessario eseguire la ridenominazione. L'operazione sul posto deve essere lo standard in tutti i controlli albero in Visual Studio. Fornire un comando Rinomina che attiva immediatamente la modalità di modifica sul posto, con la selezione di testo che copre l'intero nome del nodo, pronto ad accettare l'input dell'utente. Se il nodo rappresenta un file, il nome file deve contenere l'estensione. L'evidenziazione della selezione deve includere solo il corpo del nome file e non l'estensione.

|Input|Risultato|
|-----------|------------|
|INVIO (tasto)|Esegui il commit dell'operazione di ridenominazione|
|Tasto ESC|Annulla l'operazione di ridenominazione|
|Clic all'esterno dell'area di modifica sul posto|Esegui il commit dell'operazione di ridenominazione|
|Annulla|Fornire un'operazione di annullamento semplice per annullare l'operazione di ridenominazione|

#### <a name="selection-within-lists-and-grid-controls"></a>Selezione all'interno di elenchi e controlli griglia
 Il concetto chiave per la selezione dell'elenco è che è basato su righe, vale a dire che, quando viene effettuata una selezione, l'intera riga viene selezionata come unità. Al contrario, le griglie possono consentire la selezione di celle specifiche senza influire su altri aspetti della riga. Le griglie possono anche contenere una gerarchia di righe annidate, ad esempio in un TreeGrid, che consentono di selezionare e deselezionare interi rami della gerarchia interagendo con le righe padre. La selezione negli elenchi è indicata da un semplice colore di evidenziazione sull'intera riga di dati. Lo stato attivo viene visualizzato da un bordo punteggiato a un singolo pixel intorno alla riga o alla cella modificabile corrente (riga se tutte le celle sono di sola lettura).

> [!NOTE]
> Lo **stato attivo** e la **selezione** sono concetti diversi. Lo stato *attivo* indica che l'elemento dell'interfaccia utente è destinato a ricevere input non indirizzato in modo esplicito a un altro oggetto, mentre la *selezione* fa riferimento allo stato dell'inclusione di un oggetto in un set di oggetti in cui potrebbero verificarsi le operazioni successive.

 Le selezioni negli elenchi possono essere contigue, non contigue o di regione. Quando sono consentite più selezioni, la selezione contigua e non contigua deve sempre essere supportata, mentre il supporto per le selezioni di area (box) è facoltativo. Le selezioni dell'area vengono avviate trascinando nello spazio vuoto del corpo dell'elenco.

| Oggetto | Selezione |
|--------|------------|
| Elenco | Contigui |
| Elenco | Disgiunto |
| Elenco | Region |

 Facendo clic una volta su un elenco, viene selezionata la riga in cui si è verificato il clic. Se l'utente fa clic in una cella di elenco che supporta la modifica sul posto, viene attivata immediatamente anche la cella per la modifica sul posto. In caso contrario, l'intera riga viene immediatamente selezionata e Mostra un'evidenziazione.

 Il trascinamento del corpo dell'elenco esegue una delle tre operazioni seguenti:

- Avvia una selezione dell'area se l'elenco lo supporta e il mouse è nello spazio vuoto

- Avvia un'operazione di trascinamento della selezione se la cella o la riga dell'elenco supporta l'origine di trascinamento

- Seleziona la riga corrente

##### <a name="in-place-editing"></a>Modifica sul posto
 Quando è consentita la modifica sul posto, sono disponibili due modelli di base: controllo di modifica semplice e selezione proprietà. Con un semplice controllo di modifica, il contenuto viene evidenziato e pronto per l'input dell'utente non appena viene attivata la modifica sul posto. Quando viene implementata una selezione proprietà, il pulsante che richiama la selezione proprietà viene visualizzato una volta attivata la modalità di modifica sul posto e la selezione corrente non è evidenziata. Il pulsante di selezione deve essere giustificato a destra nella cella. Per esempi di modifica sul posto, vedere la **finestra Proprietà** e **elenco attività** in Visual Studio.

##### <a name="keyboard-support"></a>Supporto per la tastiera
 Il supporto della tastiera per la selezione negli elenchi e nelle griglie segue le convenzioni standard di Windows:

- Tasti di direzione spostarsi nell'elenco, selezionando ogni riga/cella mentre lo stato attivo viene spostato.

- MAIUSC + freccia esegue una selezione contigua nella direzione dei tasti di direzione.

- CTRL + freccia seguita dalla barra spaziatrice Alterna l'aggiunta e la rimozione di elementi dell'elenco dalla selezione, creando una selezione non contigua.

- Per le griglie che contengono gerarchie annidate, il tasto freccia destra espande una riga padre e il tasto freccia sinistra ne comprime uno.

- Il tasto TAB sposta lo stato attivo tra le celle nella riga corrente se le celle sono modificabili.

- Il tasto invio esegue il comando predefinito nell'elemento dell'elenco (spesso **aperto**).

- Il tasto F2 attiva la modifica sul posto per la cella attualmente selezionata.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistenza e salvataggio delle impostazioni

### <a name="overview"></a>Panoramica
 Sebbene ogni componente software in Visual Studio sia in genere responsabile per lo stato e la persistenza, Visual Studio salva automaticamente le impostazioni in alcuni casi, ad esempio con le dimensioni e le posizioni delle finestre. La tabella seguente è costituita da una combinazione di impostazioni salvate automaticamente e da impostazioni che richiedono l'uso di un utente esplicito o di un'azione programmata.

|Oggetto|Cosa salvare|Quando salvare|Dove salvare|
|------------|------------------|------------------|-------------------|
|Oggetto selezionabile (ad esempio, una riga di codice)|Un punto di interruzione in una riga di codice<br /><br /> Un collegamento utente associato alla riga di codice|Quando il progetto viene salvato|File delle **Opzioni utente (con estensione suo)** per il progetto|
|Finestra di dialogo|Posizione della finestra di dialogo, se è stata spostata<br /><br /> Visualizzazione usata dall'utente nella finestra di dialogo|Alla chiusura della finestra di dialogo<br /><br /> Al termine della sessione di Visual Studio|In memoria<br /><br /> Registro di sistema in **HKEY_CURRENT_USER**|
|Finestra|Le dimensioni e la posizione della finestra|Alla chiusura della finestra<br /><br /> Quando cambia la modalità di Visual Studio<br /><br /> Al termine della sessione di Visual Studio|File delle **Opzioni utente (con estensione suo)** per il progetto<br /><br /> File di opzioni personalizzate per le impostazioni della finestra|
|Documento|Selezione corrente nel documento.<br /><br /> Visualizzazione del documento<br /><br /> Ultime diverse posizioni visitate dall'utente|Quando il documento viene salvato|File delle **Opzioni utente (con estensione suo)** per il progetto|
|Project|Riferimenti a file<br /><br /> Riferimenti alle directory su disco<br /><br /> Riferimenti ad altri software<br /><br /> Componenti<br /><br /> Informazioni sullo stato del progetto stesso|Quando il progetto viene salvato|File di progetto|
|Soluzione|Riferimenti ai progetti<br /><br /> Riferimenti a file|Quando il progetto o la soluzione viene salvata|File della **soluzione (. sln)**|
|Impostazioni in **strumenti > opzioni**|Personalizzazioni della tastiera<br /><br /> Personalizzazioni della barra degli strumenti<br /><br /> Combinazioni di colori|Quando si chiude la finestra di dialogo **strumenti > opzioni**<br /><br /> Al termine della sessione di Visual Studio|Registro di sistema in **HKEY_CURRENT_USER**|

 Cosa sta facendo l'utente e, quando si esegue questa operazione, determina se un'impostazione viene salvata in memoria (durante la sessione), salvata su disco (tra le sessioni come impostazione del registro di sistema), come parte del file del progetto o della soluzione, come parte del file delle **Opzioni di soluzione (con estensione suo)** o come un file di impostazioni personalizzato che solo il componente software è La tabella precedente mostra diversi eventi in cui è possibile salvare le impostazioni. In altri casi, tuttavia, potrebbe essere necessario salvare lo stato:

- Quando l'utente cambia posizione all'interno di una finestra di dialogo o di una finestra

- Quando l'utente trasferisce lo stato attivo a un'altra finestra

- Quando l'utente passa dalla progettazione alla modalità di debug

- Quando l'utente disconnette il proprio account

- Quando il computer entra in stato di ibernazione o si arresta

- Quando il computer o il disco rigido sta per essere riformattato e configurato nuovamente

### <a name="window-configurations"></a>Configurazioni di finestre
 Una configurazione di finestra è la presentazione di base dell'ambiente di sviluppo, ovvero uno schema costituito dall'elenco delle finestre degli strumenti presenti e dal modo in cui sono disposte. Per Windows gestito dall'IDE (finestre IDE), le informazioni sul layout sono rese permanente per ogni utente, pertanto quando un utente avvia l'IDE, il layout della finestra viene visualizzato come quando l'ultimo è terminato Visual Studio. Lo stato e la posizione delle finestre IDE vengono mantenuti in un file di opzioni personalizzate in formato XML. Le finestre degli strumenti create dai pacchetti caricati nell'IDE rendono permanente le informazioni sullo stato nel registro di sistema e possono essere o meno per utente.

#### <a name="profile-specific-layouts"></a>Layout specifici del profilo
 Ogni profilo include layout della finestra degli strumenti, organizzati in modo familiare a specifici utenti di sviluppatori (Visual C++ gli sviluppatori si aspettano di visualizzare i **Esplora soluzioni** sul lato sinistro dell'IDE, mentre gli sviluppatori C# si aspettano di vedere i **Esplora soluzioni** a destra). I layout di finestra specifici del profilo vengono caricati dopo che l'utente sceglie un profilo all'avvio. L'autore di un pacchetto deve determinare il layout della finestra più adatto all'esperienza del cliente, sapendo che le modifiche apportate dall'utente alla configurazione della finestra verranno rese permanente.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Input tocco
 Gli utenti stanno sempre usando i prodotti di sviluppo Microsoft nei dispositivi touch. Tuttavia, esistono barriere che rendono difficile usare gli strumenti di sviluppo nei dispositivi touch. Gli utenti si aspettano che i prodotti forniscano un'esperienza di tocco affidabile e precisa. Lo scopo di queste linee guida è informare le decisioni sulle funzionalità di tocco da incorporare e per favorire un'esperienza di tocco coerente tra Visual Studio e i prodotti correlati.

### <a name="levels-of-experience"></a>Livelli di esperienza
 I livelli di esperienza seguenti sono destinati a servire come guida per aiutare i team a decidere quali funzionalità di tocco offrire in base al livello desiderato di interesse di investimento in touch.

- L' **esperienza di base** è destinata ai team che desiderano fornire funzionalità di tocco, in modo che non ci siano vicoli inattivi per tutto il lavoro.

- L' **esperienza ottimizzata** è destinata ai team che desiderano fornire le funzionalità di tocco più comuni, ad esempio quelle disponibili in genere nelle applicazioni del browser Internet.

- L' **esperienza elevata** è destinata ai team che desiderano aggiungere funzionalità, ad esempio movimenti o altre funzionalità facoltative che possono rendere la loro applicazione intuitiva.

||Esperienza di base|Esperienza ottimizzata|Esperienza elevata|
|-|----------------------|--------------------------|-------------------------|
|**Consente agli utenti di...**|Correzione del codice e della lettura a livello di progetto e soluzione senza terminazioni non recapitabili|Eseguire attività di manutenzione, refactoring e navigazione|Utilizza un'esperienza coerente, intuitiva e fluida in tutta sicurezza|
|**Editor**|Panoramica e selezione del tocco<br /><br /> Tocco della barra di scorrimento per saltare e premere + trascina|Zoom a pizzico<br /><br /> Scorrimento rapido<br /><br /> Selezione<br /><br /> Facile utilizzo del menu di scelta rapida||
|**Finestre degli strumenti principali**|Panoramica dell'elenco<br /><br /> Selezione degli elementi<br /><br /> Tocco della barra di scorrimento per saltare e premere + trascina|Scorrimento e selezione semplici degli elementi||
|**Windowing**||Ridimensiona finestra<br /><br /> Barra di accesso rapido||
|**Documento**||Navigazione semplice tra file aperti||
|**Movimenti**||Assicurare il funzionamento dei movimenti comuni nell'IDE|Azioni basate su movimenti<br /><br /> Supportare il trascinamento della selezione e le finestre di progettazione|
|**Altre considerazioni**|||Tastiera personalizzata sullo schermo|

#### <a name="gestures"></a>Movimenti
 I movimenti forniscono agli utenti un collegamento ai comandi che potrebbero altrimenti richiedere un'interazione più complicata. Vedere le linee guida di Windows sui [movimenti di tocco comuni per le applicazioni desktop](/windows/desktop/wintouch/windows-touch-gestures-overview)e seguire queste linee guida per la maggior parte dei movimenti, inclusi i semplici movimenti come la panoramica e lo zoom.
