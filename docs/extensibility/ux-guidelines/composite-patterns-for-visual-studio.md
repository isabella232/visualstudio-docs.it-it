---
title: Modelli compositi per Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698624"
---
# <a name="composite-patterns-for-visual-studio"></a>Modelli compositi per Visual Studio
I modelli compositi combinano l'interazione e gli elementi di progettazione in configurazioni distinte. Alcuni dei modelli compositi più importanti in Visual Studio per quanto riguarda la coerenza includono:Some of the most important composite patterns in Visual Studio with regard to consistency include:

- [Visualizzazione dei dati](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfaccia utente per gli oggetti e visualizzazione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistenza e salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Ingresso tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Visualizzazione dei dati

### <a name="overview"></a>Panoramica
 I grafici sono un modo visivo per aggregare e visualizzare i dati al fine di migliorare il processo decisionale. Possono aiutare gli utenti di fronte a un sacco di dati, ma poco significato vedere ciò che merita attenzione e ciò che potrebbe essere necessario un'azione.

 L'utente beneficerà di un grafico se una delle seguenti condizioni è vera:

- Il grafico aiuterà gli utenti a identificare le attività su cui possono agire?

- Il grafico consentirà agli utenti di prevedere le conseguenze di potenziali modifiche?

- Il grafico aiuterà gli utenti a individuare le tendenze e identificare i modelli?

- Il grafico consentirà agli utenti di prendere decisioni migliori?

- Il grafico consente di rispondere a una domanda specifica che gli utenti possono avere nel contesto specificato?

#### <a name="general-rules-for-charts"></a>Regole generali per i grafici

- Etichettare chiaramente i dati. Le illustrazioni senza spiegazione sono solo belle immagini.

- Iniziare gli assi a zero per evitare di inclinare le proporzioni. La lunghezza della linea e la dimensione della barra sono importanti indicazioni visive per comprendere le relazioni tra i punti dati.

- Creare grafici, non infografiche. Le infografiche sono rappresentazioni artistiche dei dati e il loro obiettivo principale è la narrazione visiva. I grafici possono (e dovrebbero) essere visivamente accattivanti, ma lasciare che i dati parlino da soli.

- Evita skeumorphism, grafici a barre pittoriche, hashmark di contrasto e altri tocchi infografici.

- Non utilizzare effetti 3D come elemento decorativo. Usali solo se sono realmente parte integrante della capacità dell'utente di comprendere le informazioni.

- Evitare di utilizzare più linee e riempimenti, poiché più di due colori possono rendere questo tipo di grafico difficile da leggere e interpretare correttamente.

- Non utilizzare un grafico (o qualsiasi illustrazione) come unico mezzo per comprendere un concetto o interagire con i dati. Ciò presenta difficoltà per gli utenti con disabilità visive.

- Non utilizzare i grafici come elementi gratuiti o decorativi in una pagina. In altre parole, se un grafico non aggiunge alcun valore o aiuta gli utenti a risolvere un problema, non utilizzarlo.

### <a name="chart-types"></a>Tipi di grafico
 Tipi di grafici utilizzati in Visual Studio includono grafici a barre, grafici a linee, un grafico a torta modificato noto come un grafico ad anello o "grafico ad anello", sequenze temporali, grafici a dispersione (denominati anche "grafici a cluster") e diagrammi di Gantt. Ogni tipo di grafico è utile per comunicare un tipo diverso di informazioni.

### <a name="other-charting-considerations"></a>Altre considerazioni sulla creazione di grafici

#### <a name="color"></a>Colore
 Esiste una tavolozza specifica di colori per la creazione di grafici definiti per l'utilizzo in Visual Studio.There is a specific palette of charting colors defined for use in Visual Studio. La tavolozza è accessibile per i principali tipi di daltonismo, ei colori possono essere differenziati anche se utilizzati come fette molto strette di colore. Puoi usare questi colori in qualsiasi combinazione per qualsiasi tipo di grafico o grafico nell'interfaccia utente. Non è necessario utilizzare tutti e sette i colori se non è necessario che molti colori distinti. Questi colori non sono stati progettati per essere utilizzati con elementi in primo piano, pertanto non posizionare il testo o i glifi sopra questi colori. Queste tonalità devono essere hardcoded ed esposte alla personalizzazione dell'utente in **Strumenti > Opzioni** (vedere [Esposizione di colori per gli utenti finali).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Swatch|Hex|RGB|
|------------|---------|---------|
|![Campione 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Campione BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Campione FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Campione 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Campione 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Campione 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Campione B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>Interfaccia utente per gli oggetti e visualizzazione
 Questa sezione fornisce il contesto per la visualizzazione, noto anche come visualizzazione di anteprima del codice, un tipo di interfaccia utente su oggetto univoco per Visual Studio.This section gives context to peeking, also known as code peek view, a type of on-object UI unique to Visual Studio.

### <a name="overview"></a>Panoramica

- L'interfaccia utente per gli oggetti deve fornire all'utente ulteriori informazioni o interattività senza compromettere l'attività principale.

- Il modello principale per l'interfaccia utente per gli oggetti in Visual Studio è noto come "informazioni al punto di attenzione".

- L'interfaccia utente per gli oggetti in Visual Studio è inline o mobile e durevole o temporanea.

  - La visualizzazione Anteprima codice, un tipo di interfaccia utente per gli oggetti in Visual Studio, è inline e durevole.

  - CodeLens, un tipo di interfaccia utente per gli oggetti in Visual Studio, è mobile e temporaneo

  Comprendere il funzionamento di una parte di codice o trovare dettagli su tale codice spesso richiede che uno sviluppatore cambi contesto e passi ad altro contenuto o a un'altra finestra. Questi cambiamenti di contesto possono essere dirompenti, perché gli utenti possono perdere lo stato attivo sull'attività originale se lasciano la finestra principale. Inoltre, ottenere che il contesto originale può essere difficile, soprattutto se il passaggio da una finestra all'altra ha causato il codice originale per essere oscurato da un'altra interfaccia utente.

  L'interfaccia utente per gli oggetti segue un modello denominato "informazioni al punto di attenzione". Questi messaggi, finestre popup e finestre di dialogo forniscono agli utenti informazioni aggiuntive e pertinenti che aggiungono chiarimenti o interattività senza perdere lo stato attivo sull'attività principale. Esempi di interfaccia utente per gli oggetti includono le finestre popup che vengono visualizzate quando un utente passa il puntatore del mouse su un'icona nell'area di notifica, la sottolineature ondulato rosse sotto una parola errata e la visualizzazione di anteprima introdotta in Visual Studio 2013.

### <a name="decision-points"></a>Punti di decisione
 All'interno di Visual Studio, esistono diversi modi per utilizzare questo modello di informazioni al punto di attenzione. Scegliere il meccanismo giusto e implementarlo in modo coerente e prevedibile è essenziale per l'esperienza complessiva. In caso contrario, agli utenti potrebbe essere presentata un'esperienza confusa o incoerente che riduce lo stato attivo dal contenuto stesso.

#### <a name="relationships-between-master-and-detail-content"></a>Relazioni tra il contenuto principale e il contenuto di dettaglio
 Le informazioni al punto di attenzione vengono utilizzate per visualizzare una relazione tra il contenuto su cui l'utente è focalizzato (il contenuto "master") e il contenuto correlato aggiuntivo (il contenuto "dettaglio"). In questo modello, il contenuto di dettaglio è chiaramente correlato al contenuto con cui l'utente sta lavorando e può essere visualizzato vicino al contenuto principale. Le informazioni aggiuntive o le informazioni che non possono essere riepilogate senza sovraccaricare il contenuto principale devono seguire un altro modello, ad esempio una finestra degli strumenti.

- **Visualizza sempre** il contenuto di dettaglio in prossimità del contenuto principale.

- **Assicurarsi sempre** che il contenuto di dettaglio consenta comunque all'utente di rimanere concentrato sul contenuto principale. Spesso, il modo migliore per ottenere questo risultato consiste nel rendere il contenuto di dettaglio il più vicino possibile al contenuto principale. Questa operazione può essere eseguita eseguendo il rendering del contenuto di dettaglio in una finestra popup accanto al contenuto principale o eseguendo il rendering del contenuto di dettaglio inline sotto il contenuto principale.

- **Non** utilizzare mai le informazioni al punto di attenzione che allontana l'utente dal contenuto principale. Se gli utenti devono visualizzare il contenuto di dettaglio separatamente, esporre un'azione esplicita che consente all'utente di eseguire questa operazione.

#### <a name="design-details"></a>Dettagli di progettazione
 Dopo aver determinato che l'interfaccia utente per gli oggetti è la scelta giusta, esistono quattro considerazioni di progettazione principali:Once you have determined that on-object UI is the right choice, there are four main design considerations:

1. **Persistenza:** si prevede che il contenuto sia durevole o temporaneo?
   Gli utenti vorranno mantenere visibili le informazioni a cui fare riferimento o con cui interagire? O gli utenti vorranno rapidamente dare un'occhiata alle informazioni e poi continuare con il loro compito principale?

2. **Tipo di contenuto:** il contenuto sarà informativo, utilizzabile o di navigazione?
   L'utente ha bisogno di ulteriori dettagli sul contenuto principale? L'utente deve completare un'attività che influisce sul contenuto principale? O l'utente deve essere indirizzato a un'altra risorsa?

3. **Tipo di indicatore:** un indicatore ambientale ha senso?
   Le informazioni possono essere riassunte in modo utile e visualizzate senza sovraccaricare il contenuto principale?

4. **Gesti:** quali gesti verranno utilizzati per richiamare e chiudere l'interfaccia utente?
   In che modo l'utente verrà aggiornato il contenuto dettagliato e lo invierà? È un valore nell'aggiunta di un gesto, ad esempio il blocco per passare tra gli stati transitori e durevoli?

   Ognuno di questi quattro punti decisionali avrà un impatto sui componenti principali dell'interfaccia utente per gli oggetti.

### <a name="on-object-ui-components"></a>Componenti dell'interfaccia utente per gli oggettiOn-object UI components

1. Tipo di contenitore (presentatore di contenuto)

    - Virgola mobile

    - Inline

2. Tipo di contenuto

    - Informativo: dati che potrebbero essere statici o dinamici

    - Azioni: comandi che modificano il contenuto principale

    - Navigazione: collegamenti che portano l'utente a un'altra finestra o applicazione, ad esempio MSDN

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

5. Indicatori ambientali (opzionale)

    - Sottolineatura ondulata

    - Icona smart tag

    - Altri indicatori ambientali

#### <a name="container-content-presenter-type"></a>Tipo di contenitore (presentatore di contenuto)
 Ci sono due opzioni principali disponibili per presentare il contenuto al punto di attenzione:

1. **Inline:** un presentatore inline, ad esempio la visualizzazione di anteprima che è stata introdotta nell'editor di codice di Visual Studio 2013, rende spazio per il nuovo contenuto spostando il contenuto esistente.

    - **Preferisci** i relatori in linea se prevedi che gli utenti dedicano una quantità significativa di tempo a fare riferimento o interagire con il contenuto che presenti.

    - **Evitare** i relatori in linea se si prevede che gli utenti vorranno dare un'occhiata alle informazioni presentate, quindi continuare con l'attività principale con un'interruzione minima.

2. **Floating:** un relatore mobile è posizionato il più vicino possibile al contenuto selezionato, ma non altera il layout del contenuto esistente. È possibile utilizzare varie strategie, ad esempio la visualizzazione di un pannello di contenuto mobile sopra lo spazio vuoto disponibile più vicino al simbolo selezionato.

    - **Preferisci** i relatori mobili se prevedi che gli utenti vorranno dare un'occhiata alle informazioni che presenti, quindi continuare con il loro compito principale con un'interruzione minima.

    - **Evita** i relatori mobili se prevedi che gli utenti dedicano una quantità significativa di tempo a fare riferimento o interagire con il contenuto che presenti.

#### <a name="content-type"></a>Tipo di contenuto
 Esistono tre tipi principali di contenuto che possono essere visualizzati all'interno di qualsiasi contenitore dell'interfaccia utente per gli oggetti. È possibile visualizzare qualsiasi combinazione di questi tipi di informazioni. I tre tipi sono:

1. **Informativo:** la maggior parte dei contenitori dell'interfaccia utente per gli oggetti visualizzerà un tipo di contenuto informativo. Il contenuto può rappresentare informazioni sullo stato attuale dell'ambiente o può rappresentare informazioni su un potenziale stato futuro dell'ambiente. Ad esempio, può essere utilizzato per mostrare l'effetto di un comando specifico, ad esempio un refactoring, sul codice esistente.

    - **Utilizzare sempre** la rappresentazione canonica delle informazioni visualizzate. Ad esempio, il codice dovrebbe essere simile al codice, completo di evidenziazione della sintassi e deve rispettare qualsiasi tipo di carattere e altre impostazioni di ambiente che l'utente ha impostato.

    - **Valutare sempre** la possibilità di supportare qualsiasi azione sul contenuto informativo che sarebbe possibile se le stesse informazioni vengono presentate come contenuto principale. Ad esempio, se si presenta codice esistente all'interno di un contenitore dell'interfaccia utente per gli oggetti, è consigliabile supportare la possibilità di esplorare e modificare tale codice.

    - **Considerare sempre** l'utilizzo di un colore di sfondo diverso se si presenta contenuto informativo che rappresenta un potenziale stato futuro.

2. Azionebile: alcuni contenitori dell'interfaccia utente per gli oggetti offrono la possibilità di eseguire un'azione sul contenuto master, ad esempio un'operazione di refactoring.

    - **Posizionare sempre** i comandi utilizzabili separatamente dal contenuto informativo.

    - **Abilitare** e disabilitare sempre le azioni quando appropriato.

    - **Fare sempre** riferimento alle linee guida standard per la rappresentazione dei comandi all'interno delle finestre di dialogo.

    - **Mantenere sempre** il numero di azioni esposte in un contenitore dell'interfaccia utente per gli oggetti al minimo assoluto. L'interazione con l'interfaccia utente per gli oggetti deve essere un'esperienza leggera e veloce. L'utente non deve spendere energia per la gestione del contenitore dell'interfaccia utente dell'oggetto stesso.

    - **Considerare sempre** come e quando un contenitore dell'interfaccia utente per gli oggetti verrà chiuso o chiuso. Come procedura consigliata, qualsiasi azione che conclude la finestra di dialogo tra il contenuto master e il contenuto di dettaglio deve chiudere anche il contenitore dell'interfaccia utente per gli oggetti quando viene richiamata tale azione.

3. **Navigazione:** alcuni contenitori dell'interfaccia utente per gli oggetti includono collegamenti che portano l'utente a un'altra finestra o applicazione, ad esempio l'apertura di un articolo MSDN nel browser Web dell'utente.

    - **Anteporre sempre** "Apri" a qualsiasi collegamento di navigazione in modo che gli utenti non siano sorpresi di passare a qualche altro contenuto.

    - **Separare sempre** i collegamenti di navigazione dai collegamenti utilizzabili.

#### <a name="ambient-indicators-optional"></a>Indicatori ambientali (opzionale)
 Gli indicatori di ambiente possono essere sottili, incluso il testo presentato in un colore contrastante dal resto del codice, o ovvio, inclusi i simboli del tickler come sottolineature ondulatoriche e icone smart tag. Gli indicatori ambientali comunicano la disponibilità di ulteriori informazioni pertinenti. Idealmente, forniscono informazioni utili anche senza richiedere all'utente di interagire con loro.

- **Posizionare sempre** un indicatore di ambiente in modo che non distragga o travolge l'utente. Se è impossibile posizionare un indicatore ambientale in questo modo, prendere in considerazione un'altra soluzione.

- **Posizionare sempre** l'indicatore di ambiente il più vicino possibile al contenuto a cui è correlato.

- **Provare sempre** a creare un indicatore che riassuma le informazioni che rende disponibili. È consigliabile fornire un conteggio del numero di elementi di dati disponibili (ad esempio, "3 riferimenti" anziché semplicemente "Riferimenti") o pensare a un altro modo per riepilogare i dati.

  - Nei casi in cui i dati per un indicatore non possono sempre essere calcolati e visualizzati, è immediatamente consigliabile fornire un feedback progressivo durante il calcolo dei valori. Ad esempio, prendi in considerazione l'animazione di modifiche che riflettono gli aggiornamenti ai dati disponibili, in modo simile al modo in cui il riquadro animato della posta elettronica in Windows Phone viene aggiornato con l'aumentare del numero di messaggi di posta elettronica non letti.

- **Non** aggiungere mai più indicatori di quelli che un utente può ragionevolmente accettare per un determinato contenuto. Gli indicatori ambientali dovrebbero essere utili senza richiedere alcuna interazione da parte dell'utente. Gli indicatori perdono l'atmosfera se richiedono overflow e altri controlli di gestione per visualizzarli.

#### <a name="gestures"></a>Movimenti
 Un aspetto chiave per consentire all'utente di mantenere lo stato attivo sul contenuto principale è supportando i movimenti corretti per aprire e chiudere il contenuto di dettaglio aggiuntivo.

- **Richiedere sempre** all'utente di eseguire un gesto esplicito per aprire il contenuto aggiuntivo. I gesti aperti comuni includono:

  - **Passaggio del mouse:** descrizioni comandi o contenuto informativo non interattivo

  - **Comando esplicito:** presentatore inlineExplicit command: inline presenter

  - **Fare doppio clic sull'indicatore di ambiente:** Finestra popup CodeLens

- **Ignorare sempre** il contenuto di dettaglio ogni volta che l'utente preme il tasto Esc.

- **Considerare sempre** il contesto dell'interfaccia utente dell'oggetto. Per i presentatori di contenuto che consentono l'interazione all'interno del contenitore, valutare attentamente se visualizzare informazioni aggiuntive al passaggio del mouse, il che potrebbe essere dannoso per il flusso di lavoro dell'utente.

- **Non** visualizzare mai al passaggio del mouse contenuti che sembrano modificabili o che invitano l'interazione dell'utente. Questo comportamento può frustrare gli utenti se tentano di spostare il cursore sul contenuto di dettaglio, poiché il comportamento standard per una descrizione comando consiste nel chiudere immediatamente quando il cursore non si trova più sul contenuto principale che lo ha prodotto.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Modelli di selezione

### <a name="overview"></a>Panoramica
 Un modello di selezione è il meccanismo utilizzato per indicare e confermare le operazioni su uno o più oggetti di interesse all'interno dell'interfaccia utente. In questo argomento vengono illustrati i modelli di interazione di selezione all'interno degli editor di documenti di Visual Studio: editor di testo, aree di progettazione e superfici di modellazione.

 Gli utenti devono disporre di un modo per indicare a Visual Studio su cosa stanno lavorando e Visual Studio deve rispondere in modo prevedibile con commenti e suggerimenti agli utenti su ciò che sta operando. Differenze o una comunicazione errata tra l'utente e l'interfaccia utente può causare all'utente di non notare un'azione, che può avere conseguenze indesiderate. Spesso, l'errore passa inosservato fino a quando l'utente vede che qualcosa manca o è cambiato. I modelli di selezione sono quindi una delle parti più critiche della progettazione dell'interfaccia utente. Anche se i modelli di selezione in Visual Studio sono coerenti con Windows, esistono lievi variazioni.

 In Visual Studio, come in Windows, i modelli di selezione variano a seconda del contesto in cui si verifica l'interazione. Le selezioni possono essere eseguite in quattro tipi di oggetti:

- Testo

- Oggetti grafici

- Elenchi e alberi

- Griglie

  All'interno di questi oggetti, ci sono tre tipi di selezioni:

- Contigui

- Disgiunto

- Region

#### <a name="scope"></a>Scope
 Il componente più importante della selezione è garantire che l'utente sappia in quale finestra sta lavorando (attivazione) e dove si trova lo stato attivo (selezione). Visual Studio estende la funzionalità di gestione delle finestre in Windows, ma lo schema di attivazione è lo stesso: l'interazione con una finestra porta lo stato attivo alla finestra. Visual Studio dispone di due indicatori per l'attivazione: uno per le finestre di documento e uno per le finestre degli strumenti.

 Per le finestre di documento, la finestra attiva è indicata da una scheda della finestra del documento che viene visualizzata in primo piano e ne modifica il colore di sfondo:

 ![Selezione della scheda attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Selezione scheda attiva**

 Per le finestre degli strumenti, la finestra attiva è indicata da una modifica del colore dell'area della barra del titolo della finestra degli strumenti:

 ![Selezione della finestra degli strumenti attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Finestra degli strumenti attiva che mostra la selezione primaria di un nodo**

 ![Selezione della finestra degli strumenti inattiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Finestra degli strumenti inattiva, che mostra la selezione latente del nodo**

 Una volta attiva una finestra, lo stato attivo viene indicato in base ai modelli di selezione descritti in questa sezione delle linee guida.

#### <a name="context"></a>Context
 Visual Studio è stato progettato per mantenere un concetto forte di contesto, tenendo traccia di dove l'utente sta lavorando. È attiva una sola finestra, sia che si tratti di uno strumento o di una finestra del documento. Tuttavia, la finestra del documento in primo piano mantiene sempre una selezione latente. Anche se lo stato attivo potrebbe essere in una finestra degli strumenti, la finestra del documento che è stata l'ultima attiva visualizza una selezione, anche in uno stato inattivo. Questo viene fatto per mantenere il contesto dell'utente nel documento che stavano modificando, mostrando loro che Visual Studio ha mantenuto il loro stato in modo che possano tornare e spostarsi senza soluzione di continuità tra le finestre degli strumenti e finestre del documento.

### <a name="text-selection"></a>Selezione testo
 Gli editor di Visual Studio rigorosamente testuali, ad esempio l'editor di testo incorporato, usano lo stesso modello di selezione del testo e lo stesso aspetto descritti nella pagina [Mouse e puntatori](/windows/desktop/uxguide/inter-mouse) delle Linee guida per l'interazione con l'esperienza utente di Windows su MSDN. Lo stato attivo per l'input nell'editor di testo è indicato da una barra verticale denominata punto di inserimento. Il punto di inserimento è spesso un singolo pixel e colorato come l'inverso di tutto ciò che appare dietro di esso. Lampeggia in base alla frequenza impostata dall'impostazione **Frequenza di lampeggiare** del cursore nella scheda **Velocità** dell'applet **Tastiera** nel Pannello di controllo.

#### <a name="contiguous-and-disjoint-selection"></a>Selezione contigua e disgiunta
 La selezione all'interno dell'editor di testo è solo contigua. Le selezioni di testo disgiunte non sono consentite, ma devono essere affrontate negli editor di oggetti grafici. Quando il puntatore del mouse dell'utente si trova su un'area di testo, il cursore assume la forma di una trave a I. Un singolo clic posiziona il punto di inserimento nell'editor di testo in corrispondenza della posizione del clic. Tenendo premuto il pulsante del mouse inizia un'evidenziazione di selezione e rilasciando il pulsante del mouse termina l'evidenziazione di selezione.

#### <a name="region-selection-box-selection"></a>Selezione area (selezione casella)
 Visual Studio supporta le selezioni di area nell'editor di testo e questa operazione è denominata selezione della casella. La selezione della casella consente all'utente di selezionare un'area di testo che non segue il normale flusso di testo. Come per la selezione di testo standard, la selezione deve essere contigua. La selezione della casella viene avviata tenendo premuto il tasto Alt durante il trascinamento con il mouse. La selezione della casella può essere avviata anche tenendo premuti i tasti Alt e Maiusc mentre si utilizzano i tasti freccia per indicare l'area di selezione. La selezione della casella utilizza l'evidenziazione di selezione normale e mostra il cursore del punto di inserimento lampeggiante alla fine dell'area di selezione.

 ![Casella&#41; di &#40;selezione in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Selezione dell'area (casella) in Visual StudioRegion (box) selection in Visual Studio**

#### <a name="text-selection-appearance"></a>Aspetto della selezione del testo
 I colori utilizzati per la selezione attiva e inattiva nell'editor possono essere personalizzati. Per personalizzare l'aspetto visivo dell'editor, un utente può passare a **Strumenti > Opzioni**e quindi cercare in Ambiente > tipi di **carattere e colori >Editor di testo**.

### <a name="graphical-selection"></a>Selezione grafica

#### <a name="interaction"></a>Interazione
 La selezione degli oggetti grafici può essere complessa e dipende da una serie di fattori:

- **Modello di selezione principale dell'editor.** Gli editor che contengono oggetti grafici possono essere utilizzati anche per modificare il testo o le griglie. Ad esempio, l'editor potrebbe essere un editor basato su testo che supporta anche il posizionamento di oggetti grafici, ad esempio la finestra di progettazione XAML di Visual Studio.For example, the editor might be a text-based editor that also supports the placement of graphical objects, such as the Visual Studio XAML designer. Il supporto di più tipi di oggetto può influire sul modo in cui l'utente seleziona i gruppi costituiti da diversi tipi di oggetti.

- **Supporto per gli stati di selezione primario e secondario.** Un editor può fornire stati di selezione primari e secondari in modo che gli oggetti possano essere modificati all'unisono, allineati tra loro, ridimensionati insieme e così via.

- **Supporto per la modifica sul posto.** Gli editor possono anche consentire la modifica del contenuto dei relativi oggetti grafici. Ad esempio, una forma rettangolare potrebbe contenere anche testo all'interno che può essere modificato dall'utente. Inoltre, tale testo potrebbe essere centrato o giustificato. La modifica sul posto comporta un livello più dettagliato di interazione dell'utente e pertanto richiede un set appropriato di segnali visivi per la presentazione di informazioni sullo stato all'utente.

#### <a name="mouse-interaction"></a>Interazione con il mouse

|Input|Risultato|
|-----------|------------|
|Fare clic su un oggetto non selezionato|Seleziona l'oggetto e visualizza una linea tratteggiata e le maniglie di selezione, se l'oggetto è ridimensionabile.|
|Fare clic su un oggetto selezionato|Attiva la modifica sul posto se l'oggetto la supporta. Facendo clic all'esterno dell'oggetto si disattiva la modalità di modifica sul posto.|
|Fare doppio clic su un oggetto|Apre il code-behind dell'oggetto per la modifica e potrebbe inserire un gestore eventi predefinito, se appropriato.|
|Posizionare il puntatore del tutto su un oggetto|Cambia il puntatore nel cursore di spostamento. L'aspetto dell'oggetto, ad esempio la luminosità o il colore, potrebbe cambiare.|
|Posizionare il puntatore del moledi di selezione|Trasforma il puntatore nel cursore di ridimensionamento. Per gli oggetti che supportano la rotazione, alcune maniglie di selezione potrebbero modificare il puntatore in un cursore di rotazione quando il puntatore è posizionato in modo diverso (ad esempio, spostato più lontano) rispetto al punto di manipolazione di selezione.|
|Trascinamento|Anche se l'oggetto non è selezionato in precedenza, sposta il puntatore sul cursore di spostamento e sposta l'oggetto.|
|L'editor perde lo stato attivo|Disattiva la modalità di modifica sul posto, anche se l'oggetto mantiene il contenuto e l'aspetto che aveva durante l'ultima operazione/stato di selezione.|
|Selezione degli oggetti|Indicato da un bordo, una linea tratteggiata o un altro trattamento visivamente distinto per evidenziare il contorno dell'oggetto.|
|Ridimensionare un oggetto selezionato|Indicato dalle maniglie di selezione.<br /><br /> Un oggetto ridimensionabile ha otto maniglie, che rappresentano ogni direzione in cui può essere ridimensionato. È possibile utilizzare meno maniglie se l'oggetto può essere ridimensionato solo in determinate direzioni. Quando l'utente ridimensiona un oggetto fino al punto in cui otto handle non sarebbero interattivi, è possibile utilizzare quattro handle. Le dimensioni degli handle devono essere associate alle metriche del bordo e del bordo della finestra con la funzione API **GetSystemMetrics** per ridimensionarle in proporzione alla risoluzione dello schermo.<br /><br /> ![Quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Ruotare un oggetto selezionato|![Punti di manipolazione di rotazione](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interazione con la tastiera

|Input|Risultato|
|-----------|------------|
|Scheda|Sposta l'indicatore di stato attivo tra l'ordine logico degli oggetti nell'editor. Questo può essere da sinistra a destra o dall'alto verso il basso a seconda **TabIndex** (o equivalente) valore della proprietà, ordine di creazione dell'oggetto e lo scopo generale dell'editor. Maiusc-Tab inverte la direzione dell'indicatore di messa a fuoco.|
|BARRA SPAZIATRICE|Attiva la modalità di panoramica mentre la pressione dei tasti viene mantenuta. Per eseguire la panoramica della posizione della finestra è necessario un ulteriore input del mouse.|
|CTRL+BARRA SPAZIATRICE|Attiva la modalità zoom quando la sequenza di tasti viene mantenuta. Per aumentare e ridurre il fattore di zoom è necessario un ulteriore input del mouse.|
|Ctrl-Alt-Segno meno|Riduce il fattore di zoom di un livello.|
|Ctrl-Alt-Segno più|Aumenta di un livello il fattore di zoom.|
|Maiusc Or Ctrl|Aggiunge l'oggetto al gruppo di selezione. Ctrl consente inoltre di rimuovere gli oggetti singolarmente dal gruppo di selezione.|
|Immettere|Esegue il comando predefinito per l'oggetto (in genere Apri o Modifica).|
|F2|Attiva la modifica sul posto per l'oggetto.|
|Tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto freccia premuto, con piccoli incrementi (ad esempio, 1 pixel alla volta)|
|CTRL: tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto freccia premuto, con incrementi maggiori (ad esempio, 10 pixel alla volta)|
|Maiusc-tasti di direzione|Ridimensiona gli oggetti selezionati nella rispettiva direzione, in piccoli incrementi (ad esempio, 1 pixel alla volta)|
|Ctrl-Maiusc-tasti di direzione|Ridimensiona gli oggetti selezionati nella rispettiva direzione, con incrementi maggiori (ad esempio, 10 pixel alla volta)|

 Quando gli utenti modificano i controlli sul posto, potrebbe essere opportuno che gli oggetti vengano ridimensionati automaticamente con l'input dell'utente. Ad esempio, se l'utente modifica un controllo etichetta, l'etichetta deve aumentare per visualizzare il testo appena digitato dall'utente. In caso contrario, l'utente deve ridimensionare manualmente il controllo dopo la modifica del testo. Se l'utente ha molti controlli, questo diventa un compito rote e improduttivo.

#### <a name="graphical-containers"></a>Contenitori grafici
 In alcuni casi, gli editor grafici forniscono contenitori per altri oggetti grafici, ad esempio il controllo Panel di Windows Form o il controllo Grid Layout nella finestra di progettazione HTML. Se l'editor fornisce contenitori per altri oggetti grafici, è necessario usare il modello di selezione seguente solo per il contenitore (gli oggetti all'interno del contenitore seguono il modello standard come descritto in precedenza):If your editor provides containers for other graphical objects, then the following selection model should be used for the container only (objects within the container follow the standard model as described above):

|Input|Risultato|
|-----------|------------|
|Fare clic sul contenitore|Seleziona l'oggetto contenitore senza selezionare direttamente nessuno degli oggetti contenuti. Il contenitore può essere spostato e/o ridimensionato con l'input standard del mouse e della tastiera (come descritto in precedenza). Gli oggetti contenuti vengono spostati in relazione al contenitore, ma gli oggetti contenuti non vengono ridimensionati a meno che non siano anche selezionati direttamente.|
|Posizionare il puntatore del mouse sull'area di delimitazione del contenitore|Trasforma il mouse nel cursore di spostamento, che indica che il contenitore può essere spostato.|
|Trascinare l'area di delimitazione del contenitore|Cambia il mouse sul cursore di spostamento e sposta il contenitore (e gli oggetti contenuti all'interno). Il contenitore non può essere spostato senza prima essere selezionato con un solo clic.|
|Fare clic su un oggetto all'interno del contenitore|Deseleziona il contenitore (se selezionato) e seleziona solo l'oggetto selezionato.|
|Maiusc-clic OPPURE Ctrl-clic su un oggetto contenuto e/o un contenitore|Aggiunge l'oggetto selezionato a una selezione o a un gruppo di selezione esistente. Se l'oggetto selezionato è già un membro del gruppo di selezione, viene rimosso dal gruppo di selezione.|

 Gli oggetti contenuti devono aderire al modello di selezione di base come descritto nella sezione precedente. Dai test di usabilità della finestra di progettazione Di Windows Form, gli utenti prevedevano un accesso trasparente agli oggetti contenuti senza intervenire sui passaggi (imposti dall'oggetto di contenimento).

#### <a name="disjoint-and-region-selections"></a>Selezioni disgiunte e di regione
 Gli editor di oggetti grafici devono supportare selezioni non contigui. Si noti che questo grafico non mostra l'aspetto del controllo per Visual Studio. Vedere [Aspetto della selezione di oggetti grafici](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) per informazioni dettagliate sulle specifiche visive.

 ![Selettori di elementi non contigui e di aree](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Selezione disgiunta**

 Gli editor grafici devono inoltre fornire le selezioni di area con un indicatore di selezione di tipo perimetro di selezione. Se l'editor grafico supporta altri tipi di oggetto (ad esempio testo), le selezioni di area potrebbero non essere possibili a seconda dei vincoli di tali altri tipi di oggetto.

 ![Selezione di testo scorrevole](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Selezione di testo scorrevole**

#### <a name="primary-and-secondary-selections"></a>Selezioni primarie e secondarie
 Alcuni editor di oggetti grafici consentono all'utente di modificare o allineare gli oggetti in gruppi. In questo caso, è necessario introdurre il concetto di selezioni primarie e secondarie. La selezione primaria è l'oggetto a cui tutti gli altri oggetti rispondono per le operazioni di gruppo. L'oggetto che l'utente seleziona per primo diventa il controllo primario e le selezioni successive diventano le selezioni secondarie. La selezione primaria ha un trattamento visivo distinto dalle selezioni secondarie per indicare quale oggetto è primario:

 ![Selezione primaria e secondaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Selezione primaria con due selezioni secondarie**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Aspetto per la selezione di oggetti grafici
 Le maniglie di selezione sono quadrati disegnati in un motivo rettangolare intorno al rettangolo di selezione dell'oggetto. Il grafico seguente mostra esempi dei vari stati che un oggetto grafico può avere con handle, ridimensionamento e aspetto di modifica sul posto. Le dimensioni degli handle devono essere legate alle metriche del bordo e del bordo della finestra usando l'API **GetSystemMetrics.The** size of the handles should be tied to window border and edge metrics using the GetSystemMetrics API.

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

### <a name="view-selection-models"></a>Visualizzare i modelli di selezione

#### <a name="tree-view"></a>Visualizzazione albero
 La selezione in una vista ad albero viene mostrata con una semplice evidenziazione. Se l'utente fa clic sul nome di un nodo o sull'icona di un nodo, il nodo viene selezionato. I glifi triangolari a sinistra del nodo espandono o contraggono il controllo struttura ad albero ma non influiscono sulla selezione dell'utente, con un'eccezione: quando si comprime un nodo padre quando la selezione si trova su un elemento figlio di tale nodo, la selezione si sposta sull'elemento padre.

 ![Visualizzazione albero tipica in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Visualizzazione albero tipica in Visual Studio**

 Le visualizzazioni albero possono supportare selezioni contigue e disgiunte, anche su più livelli dell'albero. È necessario effettuare selezioni multiple contigue o disgiunte sui nodi della struttura ad albero visibili. Se un nodo è compresso, la selezione disgiunta viene persa e il nodo che è stato compresso ottiene la selezione. In questo modo, l'utente può visualizzare i nodi che saranno interessati da un'operazione. Quando i nodi vengono compressi, non è chiaro quali nodi potrebbero essere interessati.

 Quando viene selezionato un nodo padre, l'operazione deve essere applicata all'elemento padre, anche se in alcuni casi può essere opportuno che un'operazione venga applicata all'elemento padre e a tutti i relativi elementi figlio. In questo caso, fornire un'interfaccia utente aggiuntiva durante l'operazione, ad esempio una casella di controllo o una finestra di dialogo di conferma per rendere esplicita all'utente l'opzione "Applica a tutti gli elementi figlio".

##### <a name="renaming"></a>Ridenominazione
 Se i nodi nell'albero supportano la ridenominazione, la ridenominazione deve essere eseguita sul posto. The in-place operation should be the standard across all tree controls in Visual Studio. Fornire un comando di ridenominazione che attiva immediatamente la modalità di modifica sul posto, con la selezione di testo che copre l'intero nome del nodo, pronto ad accettare l'input dell'utente. Se il nodo rappresenta un file, il nome del file deve contenere l'estensione. L'evidenziazione della selezione deve includere solo il corpo del nome del file e non l'estensione.

|Input|Risultato|
|-----------|------------|
|INVIO (tasto)|Esegue il commit dell'operazione di ridenominazione|
|Tasto Esc|Annulla l'operazione di ridenominazione|
|Fare clic all'esterno dell'area di modifica sul posto|Esegue il commit dell'operazione di ridenominazione|
|Annullamento|Fornire un'annullamento semplice per annullare l'operazione di ridenominazione|

#### <a name="selection-within-lists-and-grid-controls"></a>Selezione all'interno di elenchi e controlli griglia
 Il concetto chiave nella selezione dell'elenco è che è basato su righe, vale a dire che quando viene effettuata una selezione l'intera riga viene selezionata come unità. Al contrario, le griglie possono consentire la selezione di celle specifiche senza influire su altri aspetti della riga. Le griglie possono anche contenere una gerarchia di righe annidate (ad esempio in un TreeGrid) che consentono di selezionare e deselezionare interi rami della gerarchia interagendo con le righe padre. La selezione negli elenchi è indicata da un semplice colore di evidenziazione sull'intera riga di dati. Lo stato attivo viene visualizzato da un bordo punteggiato a pixel singolo intorno alla riga o alla cella modificabile corrente (riga se tutte le celle sono di sola lettura).

> [!NOTE]
> **Focus** e **selezione** sono concetti diversi. *Lo stato attivo* è un'indicazione di quale elemento dell'interfaccia utente è destinato a ricevere l'input non indirizzato in modo esplicito a un altro oggetto, mentre la *selezione* fa riferimento allo stato di inclusione di un oggetto in un set di oggetti in cui possono essere eseguite operazioni successive.

 Le selezioni negli elenchi possono essere contigue, disgiunte o regioni. Quando sono consentite selezioni multiple, la selezione contigua e disgiunta deve essere sempre supportata, mentre il supporto per le selezioni di area (casella) è facoltativo. Le selezioni dell'area vengono avviate trascinando nello spazio vuoto del corpo dell'elenco.

| Oggetto | Selezione |
|--------|------------|
| Elenco | Contigui |
| Elenco | Disgiunto |
| Elenco | Region |

 Facendo clic una volta su un elenco, viene selezionata la riga in cui si è verificato il clic. Se l'utente fa clic in una cella di elenco che supporta la modifica sul posto, la cella viene attivata immediatamente anche per la modifica sul posto. In caso contrario, l'intera riga viene immediatamente selezionata e mostra un'evidenziazione.

 Il trascinamento nel corpo dell'elenco comporta una delle tre operazioni seguenti:

- Avvia una selezione di area se l'elenco la supporta e il mouse verso il basso è nello spazio vuoto

- Avvia un'operazione di trascinamento della selezione se la cella o la riga dell'elenco supporta l'origine del trascinamento

- Seleziona la riga corrente

##### <a name="in-place-editing"></a>Modifica sul posto
 Quando è consentita la modifica sul posto, sono disponibili due modelli di base: controllo di modifica semplice e selezione proprietà. Con un semplice controllo di modifica, il contenuto viene evidenziato e pronto per l'input dell'utente non appena viene attivata la modifica sul posto. Quando viene implementato un selettore di proprietà, il pulsante che richiama il selettore di proprietà viene visualizzato una volta attivata la modalità di modifica sul posto e la selezione corrente non viene evidenziata. Il pulsante di selezione deve essere giustificato a destra nella cella. Per esempi di modifica sul posto, vedere la finestra Proprietà e **l'Elenco attività** in Visual Studio.For in-place editing examples, see the **Properties Window** and Task List in Visual Studio.

##### <a name="keyboard-support"></a>Supporto per la tastiera
 Il supporto della tastiera per la selezione in elenchi e griglie segue le convenzioni standard di Windows:

- I tasti freccia consentono di spostarsi nell'elenco, selezionando ogni riga/cella quando lo stato attivo viene spostato.

- Maiusc e freccia esegue una selezione contigua nella direzione dei tasti freccia.

- La combinazione di tasti CTRL e freccia seguita dalla barra spaziatrice consente di alternare l'aggiunta e la rimozione di voci di elenco dalla selezione, creando una selezione non contigua.

- Per le griglie che contengono gerarchie nidificate, il tasto freccia destra espande una riga padre e il tasto freccia sinistra ne comprime una.

- Il tasto Tab sposta lo stato attivo tra le celle nella riga corrente se le celle sono modificabili.

- Il tasto Invio esegue il comando predefinito sull'elemento nell'elenco (spesso **Apri).**

- Il tasto F2 attiva la modifica sul posto per la cella attualmente selezionata.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Persistenza e salvataggio delle impostazioni

### <a name="overview"></a>Panoramica
 Anche se ogni componente software in Visual Studio è in genere responsabile del proprio stato e persistenza, Visual Studio salva automaticamente le impostazioni in alcuni casi, ad esempio con le dimensioni e le posizioni delle finestre. La tabella seguente è una combinazione di impostazioni salvate automaticamente e impostazioni che richiedono l'intervento esplicito dell'utente o programmato.

|Oggetto|Cosa salvare|Quando salvare|Dove salvare|
|------------|------------------|------------------|-------------------|
|Oggetto selezionabile (ad esempio, una riga di codice)Selectable object (for example, a line of code)|Un punto di interruzione in una riga di codice<br /><br /> Un collegamento utente associato alla riga di codice|Quando il progetto viene salvato|Il file **delle opzioni utente (.suo)** per il progetto|
|Finestra di dialogo|La posizione della finestra di dialogo, se è stata spostata<br /><br /> Visualizzazione utilizzata per l'ultima volta dall'utente nella finestra di dialogo|Quando la finestra di dialogo si chiude<br /><br /> Al termine della sessione di Visual Studio|In memoria<br /><br /> Registro di sistema nel **HKEY_Current_User**|
|Finestra|Le dimensioni e la posizione della finestra|Quando la finestra si chiude<br /><br /> Quando cambia la modalità di Visual Studio<br /><br /> Al termine della sessione di Visual Studio|Il file **delle opzioni utente (.suo)** per il progetto<br /><br /> File di opzioni personalizzate per le impostazioni della finestra|
|Document|La selezione corrente nel documento<br /><br /> La visualizzazione del documento<br /><br /> Gli ultimi luoghi visitati dall'utente|Quando il documento viene salvato|Il file **delle opzioni utente (.suo)** per il progetto|
|Project|Riferimenti ai file<br /><br /> Riferimenti alle directory su disco<br /><br /> Riferimenti ad altri software<br /><br /> Componenti<br /><br /> Informazioni sullo stato del progetto stesso|Quando il progetto viene salvato|File di progetto|
|Soluzione|Riferimenti a progetti<br /><br /> Riferimenti ai file|Quando il progetto o la soluzione viene salvata|File di **soluzione (sln)**|
|Impostazioni in **Strumenti > Opzioni**|Personalizzazioni della tastiera<br /><br /> Personalizzazioni della barra degli strumenti<br /><br /> Combinazioni di colori|Quando si chiude la finestra di dialogo **Strumenti > Opzioni**<br /><br /> Al termine della sessione di Visual Studio|Registro di sistema nel **HKEY_Current_User**|

 Le operazioni eseguite dall'utente e quando lo fanno determinano se un'impostazione viene salvata in memoria (durante la sessione), salvata su disco (tra le sessioni come impostazione del Registro di sistema), come parte del file di progetto o di soluzione stesso, come parte del file delle opzioni della **soluzione (con** estensione suo) o come file di impostazioni personalizzate che solo il componente software conosce. La tabella precedente mostra diversi eventi in cui è possibile salvare le impostazioni. Tuttavia, ci sono altre volte in cui si potrebbe desiderare di salvare lo stato:

- Quando l'utente cambia posizione all'interno di una finestra di dialogo o di una finestra

- Quando l'utente trasferisce lo stato attivo a un'altra finestra

- Quando l'utente passa dalla modalità progettazione alla modalità di debugWhen the user switches from design to debug mode

- Quando l'utente si disconnette dal proprio account

- Quando il computer entra in ibernazione o si spegne

- Quando il computer/disco rigido sta per essere riformattato e configurato di nuovo

### <a name="window-configurations"></a>Configurazioni delle finestre
 Una configurazione di finestra è la presentazione di base dell'ambiente di sviluppo - è uno schema costituito dall'elenco delle finestre degli strumenti presenti e dal modo in cui sono disposte. Per le finestre gestite dall'IDE (finestre dell'IDE), le informazioni sul layout vengono mantenute per ogni utente, pertanto quando un utente avvia l'IDE, il layout della finestra viene visualizzato lo stesso come quando hanno chiuso Visual Studio. Lo stato e la posizione delle finestre dell'IDE vengono mantenuti in un file di opzioni personalizzate in formato XML. Finestre degli strumenti che vengono create dai pacchetti caricati nell'IDE mantenere le informazioni sullo stato nel Registro di sistema e possono o non possono essere per utente.

#### <a name="profile-specific-layouts"></a>Layout specifici del profilo
 Ogni profilo include layout di finestre degli strumenti, organizzati in modo familiare agli utenti specifici degli utenti di sviluppo (gli sviluppatori di Visual C, si aspettano di vedere il **Esplora soluzioni** sul lato sinistro dell'IDE, mentre gli sviluppatori di C, si aspettano di vedere il **Esplora soluzioni** a destra). I layout di finestra specifici del profilo vengono caricati dopo che l'utente sceglie un profilo all'avvio. L'autore di un pacchetto deve determinare il layout della finestra più adatto per l'esperienza del cliente, sapendo che le modifiche apportate dall'utente alla configurazione della finestra verranno quindi rese persistenti.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Ingresso tocco
 Gli utenti utilizzano sempre più spesso i prodotti di sviluppo Microsoft sui dispositivi touch. Tuttavia, esistono barriere che rendono difficile l'utilizzo degli strumenti di sviluppo sui dispositivi touch. Gli utenti si aspettano che i nostri prodotti forniscano un'esperienza touch affidabile e precisa. Lo scopo di queste linee guida è informare le decisioni sulle funzionalità di tocco da incorporare e incoraggiare un'esperienza di tocco coerente in Visual Studio e nei prodotti correlati.

### <a name="levels-of-experience"></a>Livelli di esperienza
 I seguenti livelli di esperienza sono destinati a servire come guida per aiutare i team a decidere quali funzionalità di tocco offrire in base al livello desiderato di interesse per gli investimenti nel tocco.

- **L'esperienza di base** è per i team che vogliono fornire funzionalità di tocco in modo che non ci siano vicoli ciechi in tutto il loro lavoro.

- **L'esperienza ottimizzata** è destinata ai team che desiderano fornire le funzionalità di tocco più comuni (ad esempio, quelle in genere disponibili nelle applicazioni browser Internet).

- **L'esperienza elevata** è destinata ai team che desiderano aggiungere funzionalità, ad esempio gesti o altre funzionalità facoltative, che possono rendere l'applicazione compatibile con il tocco.

||Esperienza di base|Esperienza ottimizzata|Esperienza elevata|
|-|----------------------|--------------------------|-------------------------|
|Consente agli utenti di ...|Correggere il codice e la lettura a livello di soluzione/progetto senza vicoli ciechiFix code and solution/project-level reading without dead ends|Eseguire attività di manutenzione, refactoring e navigazione|Operare in un'esperienza coerente, intuitiva e fluida in tutta sicurezza|
|Editor|Panoramica e selezione tramite tocco<br /><br /> Tocco della barra di scorrimento per saltare e premere|Ingrandimento con avvicinamento delle dita<br /><br /> Scorrimento rapido<br /><br /> Selezione<br /><br /> Facile utilizzo del menu contestuale||
|Finestre degli strumenti superiori|Panoramica dell'elenco<br /><br /> Selezione degli elementi<br /><br /> Tocco della barra di scorrimento per saltare e premere|Facile scorrimento e selezione degli elementi||
|Windowing||Ridimensiona finestra<br /><br /> Barra di accesso rapido||
|Documento bene||Facile navigazione tra i file aperti||
|Movimenti||Assicurarsi che i movimenti comuni funzionino nell'IDEEnsure common gestures work across the IDE|Azioni basate sui gesti<br /><br /> Supporta il trascinamento della selezione e le finestre di progettazioneSupport drag-and-drop and designers|
|Altre considerazioni|||Tastiera su schermo personalizzata|

#### <a name="gestures"></a>Movimenti
 I gesti forniscono agli utenti un collegamento ai comandi che potrebbero altrimenti richiedere un'interazione più complessa. Fare riferimento alle linee guida di Windows sui [movimenti tocco comuni per le applicazioni desktop](/windows/desktop/wintouch/windows-touch-gestures-overview)e seguire queste indicazioni per la maggior parte dei movimenti, inclusi semplici gesti, ad esempio panoramica e zoom.
