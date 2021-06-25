---
title: Modelli compositi per Visual Studio | Microsoft Docs
description: Informazioni sui modelli compositi importanti per la coerenza Visual Studio. I modelli compositi combinano l'interazione e gli elementi di progettazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8b84baa7be7449b8edb6241e415fc90c9acd594
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901422"
---
# <a name="composite-patterns-for-visual-studio"></a>Modelli compositi per Visual Studio
I modelli compositi combinano l'interazione e gli elementi di progettazione in configurazioni distinte. Di seguito sono riportati alcuni dei modelli compositi più Visual Studio per quanto riguarda la coerenza:

- [Visualizzazione dei dati](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfaccia utente su oggetto e visualizzazione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistenza e salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualizzazione dei dati

### <a name="overview"></a>Panoramica
 I grafici sono un modo visivo per aggregare e visualizzare i dati per migliorare il processo decisionale. Possono aiutare gli utenti a dover affrontare una grande quantità di dati, ma un significato poco significato per vedere ciò che richiede attenzione e ciò che potrebbe richiedere un'azione.

 L'utente trarrà vantaggio da un grafico se si verifica una delle condizioni seguenti:

- Il grafico consente agli utenti di identificare le attività su cui possono agire?

- Il grafico consentirà agli utenti di prevedere le conseguenze di potenziali modifiche?

- Il grafico consente agli utenti di individuare le tendenze e identificare i modelli?

- Il grafico consentirà agli utenti di prendere decisioni migliori?

- Il grafico consente di rispondere a una domanda specifica che gli utenti possono avere nel contesto specificato?

#### <a name="general-rules-for-charts"></a>Regole generali per i grafici

- Etichettare chiaramente i dati. Le illustrazioni senza spiegazione sono solo immagini di grande qualità.

- Iniziare gli assi da zero per evitare proporzioni di inclinazione. La lunghezza della riga e le dimensioni della barra sono segnali visivi importanti per comprendere le relazioni tra i punti dati.

- Creare grafici, non infografiche. Le infografiche sono rappresentazioni rappresentative dei dati e il loro obiettivo principale è la narrazione visiva. I grafici possono (e devono) essere visivamente accattivanti, ma consentono ai dati di parlare per se stessi.

- Evitare lo skeumorfismo, i grafici a barre grafici, i segni hash di contrasto e altri tocchi infografici.

- Non usare gli effetti 3D come elemento decorativo. Usarli solo se sono realmente parte integrante della capacità dell'utente di comprendere le informazioni.

- Evitare di usare più linee e riempimenti, poiché più di due colori possono rendere questo tipo di grafico difficile da leggere e interpretare correttamente.

- Non usare un grafico (o alcuna illustrazione) come unico mezzo per comprendere un concetto o interagire con i dati. Ciò presenta difficoltà per gli utenti con problemi visivi.

- Non usare i grafici come elementi decorativi o gratuito in una pagina. In altre parole, se un grafico non aggiunge alcun valore o aiuta gli utenti a risolvere un problema, non usarlo.

### <a name="chart-types"></a>Tipi di grafico
 I tipi di grafici usati in Visual Studio includono grafici a barre, grafici a linee, un grafico a torta modificato noto come grafico ad anello o "grafico ad anello", sequenze temporali, grafici a dispersione (detti anche "grafici a cluster") e grafici a dispersione. Ogni tipo di grafico è utile per comunicare un tipo diverso di informazioni.

### <a name="other-charting-considerations"></a>Altre considerazioni sulla creazione di grafici

#### <a name="color"></a>Color
 È disponibile una tavolozza specifica di colori dei grafici da usare in Visual Studio. La tavolozza è accessibile per i principali tipi di daltonismo e i colori possono essere differenziati anche se usati come sezioni di colore molto ristrette. È possibile usare questi colori in qualsiasi combinazione per qualsiasi tipo di grafico o grafico nell'interfaccia utente. Non è necessario usare tutti e sette i colori se non sono necessari molti colori distinti. Questi colori non sono stati progettati per essere usati con elementi in primo piano, quindi non posizionare testo o glifi sopra questi colori. Queste tonalità devono essere hard coded ed esposte alla personalizzazione dell'utente in Strumenti **> Opzioni** (vedere Esposizione dei colori per gli [utenti finali).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Swatch|Hex|RGB|
|------------|---------|---------|
|![Campione 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Campione BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Campione FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Campione 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Campione 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Campione 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Campione B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interfaccia utente su oggetto e visualizzazione
 Questa sezione fornisce il contesto per l'anteprima, nota anche come visualizzazione di anteprima del codice, un tipo di interfaccia utente su oggetti univoca per Visual Studio.

### <a name="overview"></a>Panoramica

- L'interfaccia utente su oggetto deve fornire all'utente altre informazioni o interattività senza distogliere dall'attività principale.

- Il modello principale per l'interfaccia utente su oggetti Visual Studio è noto come "informazioni al momento dell'attenzione".

- L'interfaccia utente su oggetto Visual Studio è inline o mobile e durevole o temporanea.

  - La visualizzazione anteprima codice, un tipo di interfaccia utente su oggetti in Visual Studio, è inline e durevole.

  - CodeLens, un tipo di interfaccia utente su oggetto in Visual Studio, è mobile e temporaneo

  Per comprendere il funzionamento di un frammento di codice o per trovare informazioni dettagliate su tale codice, spesso uno sviluppatore deve cambiare contesto e passare ad altro contenuto o a un'altra finestra. Questi cambiamenti di contesto possono essere dirompenti, perché gli utenti possono perdere lo stato attivo sull'attività originale se lasciano la finestra principale. Inoltre, il recupero del contesto originale può essere difficile, soprattutto se il passaggio da una finestra all'altra ha causato l'offuscamento del codice originale da parte di un'altra interfaccia utente.

  L'interfaccia utente su oggetto segue un modello denominato "informazioni al momento dell'attenzione". Questi messaggi, finestre popup e finestre di dialogo offrono agli utenti informazioni aggiuntive e rilevanti che aggiungono chiarimenti o interattività senza perdere lo stato attivo sull'attività principale. Esempi di interfaccia utente su oggetti includono le finestre popup che vengono visualizzate quando un utente passa il puntatore del mouse su un'icona nell'area di notifica, la linea onnisolata rossa sotto una parola con errori di ortografia e la visualizzazione di anteprima introdotta in Visual Studio 2013.

### <a name="decision-points"></a>Punti decisionali
 In Visual Studio, esistono diversi modi per usare questo modello di informazioni al momento dell'attenzione. Scegliere il meccanismo giusto e implementarlo in modo coerente e prevedibile è essenziale per l'esperienza complessiva. In caso contrario, gli utenti potrebbero presentare un'esperienza confusa o incoerente che distode lo stato attivo dal contenuto stesso.

#### <a name="relationships-between-master-and-detail-content"></a>Relazioni tra il contenuto master e il contenuto dettagliato
 Le informazioni al momento dell'attenzione vengono usate per visualizzare una relazione tra il contenuto su cui l'utente è incentrato (il contenuto "master") e il contenuto correlato aggiuntivo (il contenuto "dettagliato"). In questo modello, il contenuto dei dettagli è chiaramente correlato al contenuto che l'utente sta lavorando e può essere visualizzato vicino al contenuto master. Le informazioni supplementari o le informazioni che non possono essere riepilogate senza travolgere il contenuto master devono seguire un altro modello, ad esempio una finestra degli strumenti.

- **Visualizzare** sempre il contenuto dei dettagli in prossimità del contenuto master.

- **Assicurarsi** sempre che il contenuto dei dettagli consenta comunque a un utente di rimanere incentrato sul contenuto master. Spesso, il modo migliore per ottenere questo risultato è eseguire il rendering del contenuto dei dettagli il più vicino possibile al contenuto master. A tale scopo, è possibile eseguire il rendering del contenuto dei dettagli in una finestra popup accanto al contenuto master oppure eseguire il rendering del contenuto dei dettagli inline sotto il contenuto master.

- **Non** usare mai informazioni al momento dell'attenzione che allontanano l'utente dal contenuto master. Se gli utenti devono visualizzare il contenuto dei dettagli separatamente, esporre un'azione esplicita che consente all'utente di eseguire questa operazione.

#### <a name="design-details"></a>Dettagli della progettazione
 Dopo aver determinato che l'interfaccia utente in un oggetto è la scelta giusta, è necessario tenere presenti quattro considerazioni di progettazione principali:

1. **Persistenza:** il contenuto deve essere durevole o temporaneo?
   Gli utenti vogliono mantenere le informazioni visibili per fare riferimento o interagire con loro? Oppure gli utenti vogliono visualizzare rapidamente le informazioni e quindi continuare con l'attività principale?

2. **Tipo di contenuto:** il contenuto sarà informativo, utilizzabile o di navigazione?
   L'utente ha bisogno di dettagli aggiuntivi sul contenuto master? L'utente deve completare un'attività che influisce sul contenuto master? O l'utente deve essere indirizzato a un'altra risorsa?

3. **Tipo di indicatore:** un indicatore di ambiente ha senso?
   È possibile riepilogare le informazioni in modo utile e visualizzarle senza travolgerlo?

4. **Movimenti: quali** movimenti verranno usati per richiamare e chiudere l'interfaccia utente?
   In che modo l'utente può visualizzare il contenuto dei dettagli e inviarlo? È importante aggiungere un movimento, ad esempio il blocco, per passare da uno stato temporaneo a uno durevole?

   Ognuno di questi quattro punti decisionali avrà un impatto sui componenti principali dell'interfaccia utente sull'oggetto.

### <a name="on-object-ui-components"></a>Componenti dell'interfaccia utente su oggetti

1. Tipo di contenitore (presentatore di contenuto)

    - Virgola mobile

    - Inline

2. Tipo di contenuto

    - Informativo: dati che potrebbero essere statici o dinamici

    - Azione: comandi che modificano il contenuto master

    - Navigazione: collegamenti che consezionano l'utente a un'altra finestra o applicazione, ad esempio MSDN

3. Movimenti

    - Chiamata

    - Licenziamento

    - Aggiunta

    - Altre interazioni

4. Modello di persistenza e commit

    - Temporaneo

    - Durable

    - Automatico

    - Su richiesta

5. Indicatori di ambiente (facoltativo)

    - Sottolineatura a sottolineatura ondulata

    - Icona smart tag

    - Altri indicatori di ambiente

#### <a name="container-content-presenter-type"></a>Tipo di contenitore (presentatore di contenuto)
 Sono disponibili due opzioni principali per presentare il contenuto al momento dell'attenzione:

1. **Inline:** un presentatore inline, ad esempio la visualizzazione di anteprima introdotta nell'editor di codice Visual Studio 2013, crea spazio per il nuovo contenuto spostando il contenuto esistente.

    - **Preferire** i relatori inline se si prevede che gli utenti vorranno dedicare una quantità significativa di tempo facendo riferimento o interagendo con il contenuto presente.

    - **Evitare** i relatori inline se si prevede che gli utenti vogliano visualizzare le informazioni presenti, quindi continuare con l'attività principale con un'interruzione minima.

2. **Mobile:** un presentatore mobile viene posizionato il più vicino possibile al contenuto selezionato, ma non modifica il layout del contenuto esistente. È possibile usare diverse strategie, ad esempio la visualizzazione di un pannello di contenuto mobile sopra lo spazio vuoto disponibile più vicino al simbolo selezionato.

    - **Preferire** i relatori mobili se si prevede che gli utenti vogliano dare un'occhiata alle informazioni presenti, quindi continuare con l'attività principale con un'interruzione minima.

    - **Evitare** relatori mobili se si prevede che gli utenti vorranno dedicare una quantità significativa di tempo facendo riferimento o interagendo con il contenuto presente.

#### <a name="content-type"></a>Tipo di contenuto
 Esistono tre tipi principali di contenuto che possono essere visualizzati all'interno di qualsiasi contenitore dell'interfaccia utente su oggetti. È possibile visualizzare qualsiasi combinazione di questi tipi di informazioni. I tre tipi sono:

1. **Informativo: la** maggior parte dei contenitori dell'interfaccia utente sugli oggetti visualizza un tipo di contenuto informativo. Il contenuto può rappresentare informazioni sullo stato attuale dell'ambiente oppure può rappresentare informazioni su un potenziale stato futuro dell'ambiente. Ad esempio, può essere usato per mostrare l'effetto di un comando specifico, ad esempio un refactoring, sul codice esistente.

    - **Usare** sempre la rappresentazione canonica delle informazioni visualizzate. Ad esempio, il codice dovrebbe essere simile al codice, completo di evidenziazione della sintassi e deve rispettare qualsiasi tipo di carattere e altre impostazioni di ambiente impostate dall'utente.

    - **Valutare** sempre la possibilità di supportare qualsiasi azione sul contenuto informativo che sarebbe possibile se le stesse informazioni vengono presentate come contenuto master. Ad esempio, se si presenta codice esistente all'interno di un contenitore dell'interfaccia utente in un oggetto, è consigliabile supportare la possibilità di esplorare e modificare tale codice.

    - **Prendere** sempre in considerazione l'uso di un colore di sfondo diverso se si presenta contenuto informativo che rappresenta un potenziale stato futuro.

2. Fattibile: alcuni contenitori dell'interfaccia utente in oggetti offrono la possibilità di eseguire un'azione sul contenuto master, ad esempio l'esecuzione di un'operazione di refactoring.

    - **Posizionare** sempre i comandi utilizzabili separatamente dal contenuto informativo.

    - **Abilitare** e disabilitare sempre le azioni quando appropriato.

    - **Fare** sempre riferimento alle linee guida standard per la rappresentazione dei comandi all'interno delle finestre di dialogo.

    - **Mantenere** sempre il numero di azioni esposte in un contenitore dell'interfaccia utente in un oggetto al minimo assoluto. L'interazione con l'interfaccia utente su oggetti deve essere un'esperienza leggera e veloce. L'utente non deve expend energia per la gestione del contenitore dell'interfaccia utente nell'oggetto stesso.

    - **Considerare** sempre come e quando un contenitore dell'interfaccia utente in un oggetto verrà chiuso o ignorato. Come procedura consigliata, qualsiasi azione che termina la finestra di dialogo tra il contenuto master e il contenuto dei dettagli deve chiudere anche il contenitore dell'interfaccia utente nell'oggetto quando tale azione viene richiamata.

3. **Navigazione: alcuni** contenitori dell'interfaccia utente su oggetti includono collegamenti che connettono l'utente a un'altra finestra o applicazione, ad esempio l'apertura di un articolo MSDN nel Web browser dell'utente.

    - **Anteporre** sempre qualsiasi collegamento di navigazione con "Apri" in modo che gli utenti non siano sorprese dallo spostamento ad altri contenuti.

    - **Separare** sempre i collegamenti di navigazione dai collegamenti utilizzabili.

#### <a name="ambient-indicators-optional"></a>Indicatori di ambiente (facoltativo)
 Gli indicatori di ambiente possono essere sottili, incluso il testo presentato in un colore a contrasto rispetto al resto del codice o ovvio, inclusi i simboli tickler, ad esempio sottolineature a sottolineatura ondulata e icone smart tag. Gli indicatori di ambiente comunicano la disponibilità di informazioni aggiuntive e rilevanti. Idealmente, forniscono informazioni utili anche senza richiedere all'utente di interagire con essi.

- **Posizionare** sempre un indicatore di ambiente in modo che non distragga o sovraccarici l'utente. Se non è possibile posizionare un indicatore di ambiente in questo modo, prendere in considerazione un'altra soluzione.

- **Posizionare** sempre l'indicatore di ambiente il più vicino possibile al contenuto a cui è correlato.

- **Provare** sempre a creare un indicatore che riepiloga le informazioni che rende disponibili. Valutare la possibilità di fornire un conteggio del numero di elementi di dati disponibili (ad esempio, "3 riferimenti" anziché semplicemente "Riferimenti") o pensare a un altro modo per riepilogare i dati.

  - Nei casi in cui i dati per un indicatore non possono sempre essere calcolati e visualizzati, valutare immediatamente la possibilità di fornire feedback progressivo quando vengono calcolati i valori. Ad esempio, è consigliabile animare le modifiche che riflettono gli aggiornamenti ai dati disponibili, in modo simile al modo in cui il riquadro animato del messaggio di posta elettronica Windows Phone viene aggiornato con l'aumentare del numero di messaggi di posta elettronica non letti.

- **Non** aggiungere mai più indicatori di quanto un utente possa ragionevolmente assumere per una determinata parte di contenuto. Gli indicatori di ambiente devono essere utili senza richiedere alcuna interazione da parte dell'utente. Gli indicatori perdono l'ambiente se richiedono overflow e altri controlli di gestione per visualizzarli.

#### <a name="gestures"></a>Movimenti
 Un aspetto chiave di consentire all'utente di mantenere lo stato attivo sul contenuto master è il supporto dei movimenti per aprire e ignorare il contenuto di dettaglio aggiuntivo.

- **Richiedere** sempre all'utente di eseguire un movimento esplicito per aprire il contenuto aggiuntivo. I movimenti aperti comuni includono:

  - **Passaggio del mouse:** descrizioni comando o contenuto informativo non interattivo

  - **Comando esplicito:** presenter inline

  - **Fare doppio clic sull'indicatore di ambiente:** Finestra popup di CodeLens

- **Ignorare** sempre il contenuto dei dettagli ogni volta che l'utente preme esc.

- **Considerare** sempre il contesto dell'interfaccia utente sull'oggetto. Per i relatori di contenuto che consentono l'interazione all'interno del contenitore, valutare attentamente se visualizzare informazioni aggiuntive al passaggio del mouse, che potrebbero essere dannose per il flusso di lavoro dell'utente.

- **Non visualizzare** mai contenuto al passaggio del mouse che sembra modificabile o invita l'interazione dell'utente. Questo comportamento può frustrare gli utenti se tentano di spostare il cursore sul contenuto dei dettagli, in quanto il comportamento standard per una descrizione comando è chiudere immediatamente quando il cursore non è più sul contenuto master che lo ha generato.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modelli di selezione

### <a name="overview"></a>Panoramica
 Un modello di selezione è il meccanismo usato per indicare e confermare le operazioni su uno o più oggetti di interesse all'interno dell'interfaccia utente. Questo argomento illustra i modelli di interazione di selezione Visual Studio editor di documenti: editor di testo, superfici di progettazione e superfici di modellazione.

 Gli utenti devono avere un modo per indicare Visual Studio cosa stanno lavorando e Visual Studio deve rispondere in modo prevedibile con commenti e suggerimenti agli utenti su cosa sta operando. Le differenze o una comunicazione errata tra l'utente e l'interfaccia utente possono causare la mancata notazione di un'azione, che può avere conseguenze impreviste. Spesso l'errore passa inosservato fino a quando l'utente non vede che qualcosa manca o è cambiato. I modelli di selezione sono quindi una delle parti più importanti della progettazione dell'interfaccia utente. Anche se i modelli di Visual Studio sono coerenti con Windows, esistono lievi variazioni.

 In Visual Studio, come in Windows, i modelli di selezione variano a seconda del contesto in cui si verifica l'interazione. Le selezioni possono essere eseguite in quattro tipi di oggetti:

- Testo

- Oggetti grafici

- Elenchi e alberi

- Griglie

  All'interno di questi oggetti sono disponibili tre tipi di selezioni:

- Contigui

- Disgiunto

- Region

#### <a name="scope"></a>Ambito
 Il componente più importante della selezione è assicurarsi che l'utente sappia in quale finestra sta lavorando (attivazione) e dove si trova lo stato attivo (selezione). Visual Studio estende la funzionalità di gestione delle finestre in Windows, ma lo schema di attivazione è lo stesso: l'interazione con una finestra porta lo stato attivo alla finestra. Visual Studio due indicatori per l'attivazione: uno per le finestre dei documenti e uno per le finestre degli strumenti.

 Per le finestre del documento, la finestra attiva è indicata da una scheda della finestra del documento che viene visualizzata in primo piano e ne modifica il colore di sfondo:

 ![Selezione della scheda attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Selezione della scheda attiva**

 Per le finestre degli strumenti, la finestra attiva è indicata da una modifica del colore dell'area della barra del titolo della finestra degli strumenti:

 ![Selezione della finestra degli strumenti attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Finestra degli strumenti attiva che mostra la selezione primaria di un nodo**

 ![Selezione della finestra degli strumenti inattiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Finestra degli strumenti inattiva, che mostra la selezione latente del nodo**

 Quando una finestra è attiva, lo stato attivo viene indicato in base ai modelli di selezione descritti in questa sezione delle linee guida.

#### <a name="context"></a>Contesto
 Visual Studio è stato progettato per mantenere un concetto solido di contesto, tenendo traccia del lavoro dell'utente. È attiva una sola finestra, sia che si tratta di uno strumento o di una finestra del documento. Tuttavia, la finestra del documento più in alto mantiene sempre una selezione latente. Anche se lo stato attivo potrebbe essere in una finestra degli strumenti, l'ultima finestra del documento attiva visualizza una selezione, anche in uno stato inattivo. Questa operazione viene eseguita per mantenere il contesto dell'utente nel documento che sta modificando, dimostrando che Visual Studio ha mantenuto il proprio stato in modo che possa tornare e passare facilmente tra le finestre degli strumenti e le finestre del documento.

### <a name="text-selection"></a>Selezione testo
 Visual Studio editor rigorosamente testuali, ad esempio l'editor di testo predefinito, usano lo stesso modello di selezione del testo e lo stesso aspetto descritti nella pagina [Mouse](/windows/desktop/uxguide/inter-mouse) e puntatori delle linee guida per l'interazione dell'esperienza utente di Windows in MSDN. Lo stato attivo per l'input nell'editor di testo è indicato da una barra verticale denominata punto di inserimento. Il punto di inserimento è spesso un singolo pixel e colorato come l'inverso di qualsiasi elemento visualizzato dietro di esso. Lampeggia in base alla frequenza impostata dall'impostazione **Frequenza di lampeggiamento** cursore nella scheda Velocità dell'applet Tastiera in Pannello di controllo.  

#### <a name="contiguous-and-disjoint-selection"></a>Selezione contigua e non contigua
 La selezione all'interno dell'editor di testo è solo contigua. Le selezioni di testo non contigue non sono consentite, ma devono essere indirizzate negli editor di oggetti grafici. Quando il puntatore del mouse dell'utente si trova su un'area di testo, il cursore assume la forma di un raggio a I. Un singolo clic posiziona il punto di inserimento nell'editor di testo nella posizione del clic. Tenendo premuto il pulsante del mouse, viene avviata un'evidenziazione della selezione e il rilascio del pulsante del mouse termina l'evidenziazione della selezione.

#### <a name="region-selection-box-selection"></a>Selezione dell'area (selezione della casella)
 Visual Studio supporta le selezioni di area nell'editor di testo e questa operazione è denominata selezione di caselle. La selezione della casella consente all'utente di selezionare un'area di testo che non segue il normale flusso di testo. Come per la selezione di testo standard, la selezione deve essere contigua. La selezione della casella viene avviata tenendo premuto ALT mentre si trascina con il mouse. La selezione della casella può essere avviata anche tenendo premuto ALT e MAIUSC mentre si usano i tasti di direzione per indicare l'area di selezione. La selezione della casella usa l'evidenziazione di selezione normale e mostra il cursore del punto di inserimento lampeggiante alla fine dell'area di selezione.

 ![Casella &#40;di&#41; in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Selezione dell'area (casella) in Visual Studio**

#### <a name="text-selection-appearance"></a>Aspetto della selezione del testo
 I colori usati per la selezione attiva e inattiva nell'editor possono essere personalizzati. Per personalizzare l'aspetto visivo dell'editor, un utente può passare a Strumenti **> Opzioni** e quindi cercare in Ambiente > Tipi di carattere e colori > Editor **di testo**.

### <a name="graphical-selection"></a>Selezione grafica

#### <a name="interaction"></a>Interazione
 La selezione di oggetti grafici può essere complessa e dipende da diversi fattori:

- **Modello di selezione principale dell'editor.** Gli editor che contengono oggetti grafici possono essere usati anche per modificare testo o griglie. Ad esempio, l'editor potrebbe essere un editor basato su testo che supporta anche la posizione di oggetti grafici, ad esempio la finestra di Visual Studio xaml. Il supporto di più tipi di oggetto può influire sul modo in cui l'utente seleziona gruppi formati da diversi tipi di oggetti.

- **Supporto per gli stati di selezione primaria e secondaria.** Un editor può fornire stati di selezione primaria e secondaria in modo che gli oggetti possano essere modificati all'unisono, allineati tra loro, ridimensionati insieme e così via.

- **Supporto della modifica sul posto.** Gli editor possono anche consentire la modifica del contenuto degli oggetti grafici. Ad esempio, una forma rettangolare potrebbe contenere anche testo all'interno che può essere modificato dall'utente. Inoltre, il testo potrebbe essere centrato o giustificato. La modifica sul posto comporta un livello più dettagliato di interazione dell'utente e pertanto richiede un set appropriato di segnali visivi per la presentazione delle informazioni sullo stato all'utente.

#### <a name="mouse-interaction"></a>Interazione con il mouse

|Input|Result|
|-----------|------------|
|Fare clic su un oggetto non selezionato|Seleziona l'oggetto e visualizza una linea tratteggiata e i punti di manipolazione di selezione, se l'oggetto è ridimensionabile.|
|Fare clic su un oggetto selezionato|Attiva la modifica sul posto se l'oggetto la supporta. Facendo clic all'esterno dell'oggetto viene disattivata la modalità di modifica sul posto.|
|Fare doppio clic su un oggetto|Apre il code-behind dell'oggetto per la modifica e potrebbe inserire un gestore eventi predefinito, se appropriato.|
|Puntare a un oggetto|Modifica il puntatore al cursore di spostamento. L'aspetto dell'oggetto, ad esempio la luminosità o il colore, potrebbe cambiare.|
|Puntare a un punto di manipolazione di selezione|Modifica il puntatore al cursore di ridimensionamento. Per gli oggetti che supportano la rotazione, alcuni punti di manipolazione di selezione potrebbero cambiare il puntatore in un cursore di rotazione perché il puntatore è posizionato in modo diverso (ad esempio, spostato più lontano) rispetto al punto di manipolazione di selezione.|
|Trascinamento|Anche se l'oggetto non è stato selezionato in precedenza, cambia il puntatore al cursore di spostamento e sposta l'oggetto.|
|L'editor perde lo stato attivo|Disattiva la modalità di modifica sul posto, anche se l'oggetto mantiene il contenuto e l'aspetto che aveva durante l'ultima operazione/stato di selezione.|
|Selezione di oggetti|Indicato da un bordo, una linea punteggiata o un altro trattamento visivamente distinto per evidenziare il limite dell'oggetto.|
|Ridimensionare un oggetto selezionato|Indicato dai punti di manipolazione di selezione.<br /><br /> Un oggetto ridimensionabile ha otto handle, che rappresentano ogni direzione in cui può essere ridimensionato. È possibile usare meno handle se l'oggetto può essere ridimensionato solo in determinate direzioni. Quando l'utente ridimensiona un oggetto fino a quando otto handle non sono interattivi, è possibile usare quattro handle. Le dimensioni degli handle devono essere associate alle metriche del bordo della finestra e del bordo con la funzione dell'API **GetSystemMetrics** in modo che le dimensioni siano proporzionali alla risoluzione dello schermo.<br /><br /> ![Quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Ruotare un oggetto selezionato|![Punti di manipolazione di rotazione](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interazione tramite tastiera

|Input|Result|
|-----------|------------|
|Scheda|Sposta l'indicatore dello stato attivo nell'ordine logico degli oggetti nell'editor. Può essere da sinistra a destra o dall'alto verso il basso a seconda del valore della proprietà **TabIndex** (o equivalente), dell'ordine di creazione dell'oggetto e dello scopo complessivo dell'editor. MAIUSC+TAB inverte la direzione dell'indicatore dello stato attivo.|
|BARRA SPAZIATRICE|Attiva la modalità di panoramica mentre viene mantenuta la pressione del tasto. L'input del mouse aggiuntivo è necessario per eseguire una panoramica della posizione del viewport.|
|CTRL+BARRA SPAZIATRICE|Attiva la modalità zoom mentre viene mantenuta la pressione dei tasti. L'input del mouse aggiuntivo è necessario per aumentare e ridurre il fattore di zoom.|
|CTRL+ALT+segno meno|Riduce il fattore di zoom di un livello.|
|CTRL+ALT+segno più|Aumenta il fattore di zoom di un livello.|
|MAIUSC O CTRL|Aggiunge l'oggetto al gruppo di selezione. CTRL consente anche di rimuovere gli oggetti singolarmente dal gruppo di selezione.|
|Immettere|Esegue il comando predefinito per l'oggetto (in genere Open o Edit).|
|F2|Attiva la modifica sul posto per l'oggetto .|
|Tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto di direzione premuto, in piccoli incrementi (ad esempio, 1 pixel alla volta)|
|CTRL+tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto di direzione premuto, con incrementi maggiori (ad esempio, 10 pixel alla volta)|
|MAIUSC+tasti di direzione|Ridimensiona gli oggetti selezionati nella rispettiva direzione, in piccoli incrementi (ad esempio, 1 pixel alla volta)|
|CTRL+MAIUSC+tasti di direzione|Ridimensiona gli oggetti selezionati nella rispettiva direzione, con incrementi maggiori (ad esempio, 10 pixel alla volta)|

 Quando gli utenti modificano i controlli sul posto, può essere utile ridimensionare automaticamente gli oggetti con l'input dell'utente. Ad esempio, se l'utente modifica un controllo etichetta, l'etichetta dovrebbe crescere per visualizzare il testo appena digitato dall'utente. In caso contrario, l'utente deve ridimensionare manualmente il controllo dopo aver modificato il testo. Se l'utente dispone di molti controlli, questa diventa un'attività marcia e non produttiva.

#### <a name="graphical-containers"></a>Contenitori grafici
 In alcuni casi, gli editor grafici forniscono contenitori per altri oggetti grafici, ad esempio il controllo Windows Forms Panel o il controllo Grid Layout nella finestra di progettazione HTML. Se l'editor fornisce contenitori per altri oggetti grafici, è necessario usare il modello di selezione seguente solo per il contenitore (gli oggetti all'interno del contenitore seguono il modello standard come descritto in precedenza):

|Input|Result|
|-----------|------------|
|Fare clic sul contenitore con un solo clic|Seleziona l'oggetto contenitore senza selezionare direttamente nessuno degli oggetti contenuti. Il contenitore può essere spostato e/o ridimensionato con l'input standard del mouse e della tastiera (come descritto in precedenza). Gli oggetti contenuti vengono spostati in relazione al contenitore, ma gli oggetti contenuti non vengono ridimensionati a meno che non siano selezionati direttamente.|
|Passare il puntatore del mouse sull'area limite del contenitore|Trasforma il mouse nel cursore di spostamento, a indicare che il contenitore può essere spostato.|
|Trascinare l'area limite del contenitore|Passa il mouse al cursore di spostamento e sposta il contenitore (e gli oggetti contenuti all'interno). Il contenitore non può essere spostato senza essere prima selezionato con un solo clic.|
|Fare clic su un oggetto all'interno del contenitore|Deseleziona il contenitore (se selezionato) e seleziona solo l'oggetto selezionato.|
|MAIUSC+clic OPPURE CTRL+clic su un oggetto contenuto e/o un contenitore|Aggiunge l'oggetto selezionato a una selezione o a un gruppo di selezione esistente. Se l'oggetto selezionato è già membro del gruppo di selezione, viene rimosso dal gruppo di selezione.|

 Gli oggetti contenuti devono essere conformi al modello di selezione di base, come descritto nella sezione precedente. Dal test di usabilità della finestra di progettazione Windows Forms, gli utenti si aspettaranno un accesso trasparente agli oggetti contenuti senza passaggi successivi (imposti dall'oggetto di contenimento).

#### <a name="disjoint-and-region-selections"></a>Selezioni di aree e non contigue
 Gli editor di oggetti grafici devono supportare selezioni non contigue. Si noti che questo grafico non mostra l'aspetto del controllo per Visual Studio. Per [specifiche visive dettagliate, vedere](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) Aspetto della selezione di oggetti grafici.

 ![Selettori di elementi non contigui e di aree](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Selezione non contigua**

 Gli editor grafici devono anche fornire selezioni di aree con un indicatore di selezione del tipo di selezione con selezione del tipo di selezione. Se l'editor grafico supporta altri tipi di oggetto (ad esempio testo), le selezioni di aree potrebbero non essere possibili a seconda dei vincoli di tali altri tipi di oggetto.

 ![Selezione di testo scorrevole](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Selezione di testo scorrevole**

#### <a name="primary-and-secondary-selections"></a>Selezioni primarie e secondarie
 Alcuni editor di oggetti grafici consentono all'utente di modificare o allineare gli oggetti nei gruppi. In questo caso, è necessario introdurre il concetto di selezioni primarie e secondarie. La selezione principale è l'oggetto a cui tutti gli altri oggetti rispondono per le operazioni di gruppo. L'oggetto selezionato per primo dall'utente diventa il controllo principale e le selezioni successive diventano le selezioni secondarie. La selezione primaria ha un trattamento visivo distinto dalle selezioni secondarie per indicare quale oggetto è primario:

 ![Selezione primaria e secondaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Selezione primaria con due selezioni secondarie**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Aspetto della selezione di oggetti grafici
 I quadratini di selezione sono quadrati disegnati in un motivo rettangolare intorno al rettangolo di selezione dell'oggetto. Il grafico seguente mostra esempi dei vari stati che un oggetto grafico può avere con handle, ridimensionamento e aspetto di modifica sul posto. Le dimensioni degli handle devono essere collegate alle metriche dei bordi e dei bordi della finestra usando l'API **GetSystemMetrics.**

| Stato | Aspetto | Dettagli dell'oggetto visivo |
|-------------------------|---------------| - |
| **Deselezionato** | Predefinito | ![Stato del pulsante predefinito](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Selezione primaria** | Ridimensionabile | ![Selezione primaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Selezione primaria** | Non ridimensionabile | ![Selezione primaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Selezione primaria** | Bloccato | ![Selezione primaria bloccata](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Selezione secondaria** | Ridimensionabile | ![Selezione secondaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Selezione secondaria** | Non ridimensionabile | ![Selezione secondaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Selezione secondaria** | Bloccato | ![Selezione secondaria bloccata](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Interfaccia utente attiva** | Predefinito | ![Stato attivo dell'interfaccia utente](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Visualizzare i modelli di selezione

#### <a name="tree-view"></a>Visualizzazione struttura
 La selezione in una visualizzazione albero viene visualizzata con una semplice evidenziazione. Se l'utente fa clic sul nome di un nodo o su un'icona di nodo, il nodo viene selezionato. I glifi triangolari a sinistra del nodo espandono o contraeno il controllo struttura ad albero, ma non influiscono sulla selezione dell'utente, con una sola eccezione: al momento della compressione di un nodo padre quando la selezione si trova su un elemento figlio di tale nodo, la selezione viene spostata sul nodo padre.

 ![Visualizzazione albero tipica in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Visualizzazione albero tipica in Visual Studio**

 Le visualizzazioni albero possono supportare selezioni contigue e non contigue, anche in più livelli dell'albero. Nei nodi della struttura ad albero visibili devono essere effettuate selezioni multiple contigue o non contigue. Se un nodo è compresso, la selezione non contigua viene persa e il nodo compresso ottiene la selezione. In questo modo, l'utente può visualizzare i nodi interessati da un'operazione. Quando i nodi vengono compressi, non è chiaro quali nodi potrebbero essere interessati.

 Quando si seleziona un nodo padre, l'operazione deve essere applicata al nodo padre, anche se in alcuni casi può essere opportuno applicare un'operazione all'elemento padre e a tutti i relativi elementi figlio. In questo caso, fornire un'interfaccia utente aggiuntiva durante l'operazione, ad esempio una casella di controllo o una finestra di dialogo di conferma per rendere esplicita l'opzione "Applica a tutti gli elementi figlio" all'utente.

##### <a name="renaming"></a>Ridenominazione
 Se i nodi nell'albero supportano la ridenominazione, la ridenominazione deve essere eseguita sul posto. L'operazione sul posto deve essere lo standard in tutti i controlli albero in Visual Studio. Fornire un comando di ridenominazione che attivi immediatamente la modalità di modifica sul posto, con la selezione del testo che copre l'intero nome del nodo, pronta ad accettare l'input dell'utente. Se il nodo rappresenta un file, il nome file deve contenere l'estensione . L'evidenziazione della selezione deve includere solo il corpo del nome file e non l'estensione.

|Input|Result|
|-----------|------------|
|INVIO (tasto)|Esegue il commit dell'operazione di ridenominazione|
|Tasto ESC|Annulla l'operazione di ridenominazione|
|Facendo clic all'esterno dell'area di modifica sul posto|Esegue il commit dell'operazione di ridenominazione|
|Annulla|Fornire un'operazione di annullamento semplice per annullare l'operazione di ridenominazione|

#### <a name="selection-within-lists-and-grid-controls"></a>Selezione all'interno di elenchi e controlli griglia
 Il concetto chiave nella selezione dell'elenco è che è basato su righe, vale a dire che quando viene effettuata una selezione l'intera riga viene selezionata come unità. Al contrario, le griglie possono consentire la selezione di celle specifiche senza influire su altri aspetti della riga. Le griglie possono contenere anche una gerarchia di righe annidate,ad esempio in un controllo TreeGrid, che consente di selezionare e deselezionare interi rami della gerarchia intera tramite l'interazione con le righe padre. La selezione negli elenchi viene visualizzata da un semplice colore di evidenziazione sull'intera riga di dati. Lo stato attivo viene visualizzato da un bordo punteggiato a pixel singolo intorno alla riga o alla cella modificabile corrente (riga se tutte le celle sono di sola lettura).

> [!NOTE]
> **Lo stato** attivo **e la** selezione sono concetti diversi. *Lo* stato attivo è un'indicazione dell'elemento dell'interfaccia utente  destinato a ricevere input non indirizzato in modo esplicito a un altro oggetto, mentre la selezione fa riferimento allo stato di inclusione di un oggetto in un set di oggetti in cui possono essere eseguite operazioni successive.

 Le selezioni negli elenchi possono essere contigue, disgiunte o di area. Quando sono consentite più selezioni, la selezione contigua e non contigua deve essere sempre supportata, mentre il supporto per le selezioni di area (casella) è facoltativo. Le selezioni di area vengono avviate trascinando lo spazio vuoto del corpo dell'elenco.

| Oggetto | Selezione |
|--------|------------|
| Elenco | Contigui |
| Elenco | Disgiunto |
| Elenco | Region |

 Facendo clic una sola volta su un elenco, viene selezionata la riga in cui si è verificato il clic. Se l'utente fa clic in una cella dell'elenco che supporta la modifica sul posto, la cella viene attivata immediatamente anche per la modifica sul posto. In caso contrario, l'intera riga viene selezionata immediatamente e mostra un'evidenziazione.

 Il trascinamento nel corpo dell'elenco esegue una delle tre operazioni seguenti:

- Avvia la selezione di un'area se l'elenco la supporta e il puntatore del mouse è nello spazio vuoto

- Avvia un'operazione di trascinamento della selezione se la cella o la riga dell'elenco supporta l'origine di trascinamento

- Seleziona la riga corrente

##### <a name="in-place-editing"></a>Modifica sul posto
 Quando è consentita la modifica sul posto, sono disponibili due modelli di base: controllo di modifica semplice e selezione proprietà. Con un controllo di modifica semplice, il contenuto viene evidenziato e pronto per l'input dell'utente non appena viene attivata la modifica sul posto. Quando viene implementato un selettore di proprietà, il pulsante che richiama il selettore di proprietà viene visualizzato una volta attivata la modalità di modifica sul posto e la selezione corrente non è evidenziata. Il pulsante di selezione deve essere giustificato a destra nella cella. Per esempi di modifica sul posto, vedere finestra **Proprietà** **e** Elenco attività in Visual Studio.

##### <a name="keyboard-support"></a>Supporto per la tastiera
 Il supporto della tastiera per la selezione in elenchi e griglie segue le convenzioni standard di Windows:

- I tasti di direzione si spostano nell'elenco, selezionando ogni riga/cella quando viene spostato lo stato attivo.

- MAIUSC+freccia esegue una selezione contigua nella direzione dei tasti di direzione.

- CTRL+ freccia seguita da BARRA SPAZIATRICE consente di alternare l'aggiunta e la rimozione di elementi dell'elenco dalla selezione, creando una selezione non contigua.

- Per le griglie che contengono gerarchie annidate, il tasto freccia DESTRA espande una riga padre e la freccia SINISTRA ne comprime una.

- Il tasto TAB sposta lo stato attivo tra le celle della riga corrente se le celle sono modificabili.

- Il tasto INVIO esegue il comando predefinito sull'elemento nell'elenco (spesso **Apri**).

- Il tasto F2 attiva la modifica sul posto per la cella attualmente selezionata.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistenza e salvataggio delle impostazioni

### <a name="overview"></a>Panoramica
 Anche se ogni componente software in Visual Studio è in genere responsabile del proprio stato e della persistenza, Visual Studio salva automaticamente le impostazioni in alcuni casi, ad esempio con le dimensioni e le posizioni delle finestre. La tabella seguente è una combinazione di impostazioni salvate automaticamente e impostazioni che richiedono un utente esplicito o un'azione programmata da eseguire.

|Oggetto|Elementi da salvare|Quando salvare|Posizione in cui salvare|
|------------|------------------|------------------|-------------------|
|Oggetto selezionabile (ad esempio, una riga di codice)|Un punto di interruzione in una riga di codice<br /><br /> Collegamento utente associato alla riga di codice|Quando il progetto viene salvato|File **delle opzioni utente (con** estensione suo) per il progetto|
|Finestra di dialogo|Posizione della finestra di dialogo, se è stata spostata<br /><br /> Visualizzazione usata per l'ultima volta dall'utente nella finestra di dialogo|Alla chiusura della finestra di dialogo<br /><br /> Al termine Visual Studio sessione|In memoria<br /><br /> Registro di sistema **in HKEY_Current_User**|
|Finestra|Dimensioni e posizione della finestra|Alla chiusura della finestra<br /><br /> Quando la modalità Visual Studio cambia<br /><br /> Al termine Visual Studio sessione|File **delle opzioni utente (con** estensione suo) per il progetto<br /><br /> File di opzioni personalizzate per le impostazioni della finestra|
|Documento|Selezione corrente nel documento<br /><br /> Visualizzazione del documento<br /><br /> Ultimi punti visitati dall'utente|Quando il documento viene salvato|File **delle opzioni utente (con** estensione suo) per il progetto|
|Project|Riferimenti ai file<br /><br /> Riferimenti alle directory su disco<br /><br /> Riferimenti ad altri software<br /><br /> Componenti<br /><br /> Informazioni sullo stato del progetto stesso|Quando il progetto viene salvato|File di progetto|
|Soluzione|Riferimenti ai progetti<br /><br /> Riferimenti ai file|Quando il progetto o la soluzione viene salvata|File **di soluzione (sln)**|
|Impostazioni in **Strumenti > opzioni**|Personalizzazioni della tastiera<br /><br /> Personalizzazioni della barra degli strumenti<br /><br /> Combinazioni di colori|Alla chiusura **della finestra di > strumenti**<br /><br /> Al termine Visual Studio sessione|Registro di sistema **in HKEY_Current_User**|

 Ciò che l'utente sta eseguendo e quando lo sta eseguendo determina se un'impostazione viene salvata in memoria (durante la sessione), salvata su disco (tra sessioni come impostazione del Registro di sistema), come parte del file di progetto o di soluzione stesso, come parte del file delle opzioni della soluzione (con estensione **suo)** o come file di impostazioni personalizzate che solo il componente software conosce. La tabella precedente mostra diversi eventi in cui è possibile salvare le impostazioni. Esistono tuttavia altre volte in cui può essere necessario salvare lo stato:

- Quando l'utente cambia posizione all'interno di una finestra o di una finestra

- Quando l'utente trasferisce lo stato attivo a un'altra finestra

- Quando l'utente passa dalla modalità progettazione alla modalità di debug

- Quando l'utente si disconnette dall'account

- Quando il computer entra in ibernazione o si arresta

- Quando il computer o il disco rigido sta per essere riformattato e configurato di nuovo

### <a name="window-configurations"></a>Configurazioni delle finestre
 Una configurazione della finestra è la presentazione di base dell'ambiente di sviluppo, ovvero uno schema costituito dall'elenco di finestre degli strumenti presenti e dal modo in cui vengono disposte. Per le finestre gestite dall'IDE (finestre IDE), le informazioni sul layout vengono rese persistenti per ogni utente, quindi quando un utente avvia l'IDE, il layout della finestra viene visualizzato come l'ultima volta che sono stati Visual Studio. Lo stato e la posizione delle finestre IDE vengono mantenuti in un file di opzioni personalizzato in formato XML. Le finestre degli strumenti create dai pacchetti caricati nell'IDE conservano le informazioni sullo stato nel Registro di sistema e possono essere o meno per utente.

#### <a name="profile-specific-layouts"></a>Layout specifici del profilo
 Ogni profilo include layout di finestre degli strumenti, organizzati in modo familiare a specifici utenti dello sviluppatore (gli sviluppatori Visual C++ prevedono di visualizzare il **Esplora soluzioni** sul lato sinistro dell'IDE, mentre gli sviluppatori C# prevedono di vedere **il Esplora soluzioni a** destra). I layout di finestra specifici del profilo vengono caricati dopo che l'utente ha scelto un profilo all'avvio. L'autore di un pacchetto deve determinare il layout della finestra più adatto all'esperienza del cliente, sapendo che le modifiche apportate dall'utente alla configurazione della finestra verranno rese persistenti.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Input tocco
 Gli utenti usano sempre più prodotti di sviluppo Microsoft nei dispositivi touch. Esistono tuttavia barriere che rendono difficile l'uso degli strumenti di sviluppo nei dispositivi touch. Gli utenti si aspettano che i prodotti forniranno un'esperienza di tocco affidabile e precisa. Lo scopo di queste linee guida è quello di informare le decisioni sulle funzionalità di tocco da incorporare e di favorire un'esperienza di tocco coerente Visual Studio prodotti correlati.

### <a name="levels-of-experience"></a>Livelli di esperienza
 I livelli di esperienza seguenti sono concepiti come guida per aiutare i team a decidere quali funzionalità di tocco offrire in base al livello desiderato di interesse per gli investimenti.

- **L'esperienza di** base è per i team che vogliono fornire funzionalità di tocco in modo che non ci siano dead end per tutto il lavoro.

- **L'esperienza ottimizzata** è per i team che vogliono offrire le funzionalità di tocco più comuni, ad esempio quelle in genere disponibili nelle applicazioni browser Internet.

- **L'esperienza con privilegi** elevati è per i team che vogliono aggiungere funzionalità come movimenti o altre funzionalità facoltative che possono rendere l'applicazione più semplice da toccare.

||Esperienza di base|Esperienza ottimizzata|Esperienza con privilegi elevati|
|-|----------------------|--------------------------|-------------------------|
|**Consente agli utenti di ...**|Correggere il codice e la lettura a livello di soluzione/progetto senza dead end|Eseguire attività di manutenzione, refactoring e navigazione|Operare in un'esperienza coerente, intuitiva e fluida con sicurezza|
|**Editor**|Panoramica e selezione con tocco<br /><br /> Tocco della barra di scorrimento per passare e premere +trascinamento|Zoom avvicinamento delle dita<br /><br /> Scorrimento rapido<br /><br /> Selezione<br /><br /> Uso semplice del menu di scelta rapida||
|**Finestre degli strumenti principali**|Panoramica dell'elenco<br /><br /> Selezione degli elementi<br /><br /> Tocco della barra di scorrimento per passare e premere +trascinamento|Scorrimento e selezione di elementi semplici||
|**Windowing**||Ridimensionare la finestra<br /><br /> Barra di accesso rapido||
|**Documentare bene**||Navigazione semplice tra i file aperti||
|**Movimenti**||Assicurarsi che i movimenti comuni funzionino nell'IDE|Azioni basate su movimenti<br /><br /> Supporto del trascinamento della selezione e delle finestre di progettazione|
|**Altre considerazioni**|||Tastiera su schermo personalizzata|

#### <a name="gestures"></a>Movimenti
 I movimenti forniscono agli utenti un collegamento ai comandi che altrimenti potrebbero richiedere un'interazione più complessa. Fare riferimento alle linee guida di Windows sui movimenti tocco comuni per le applicazioni [desktop](/windows/desktop/wintouch/windows-touch-gestures-overview)e seguire queste indicazioni per la maggior parte dei movimenti, inclusi i movimenti semplici, ad esempio la panoramica e lo zoom.
