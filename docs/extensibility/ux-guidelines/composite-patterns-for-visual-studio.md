---
title: Modelli compositi per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b80f12ead3811c7e0776fa403446c3d8b536d141
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513494"
---
# <a name="composite-patterns-for-visual-studio"></a>Modelli compositi per Visual Studio
Pattern compositi combinano gli elementi di interazione e progettazione di configurazioni distinte. Alcuni dei modelli compositi più importanti in Visual Studio per quanto riguarda la coerenza includono:  
  
-   [Visualizzazione dei dati](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Per gli oggetti dell'interfaccia utente e la lettura](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistenza e il salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="BKMK_DataVisualization"></a> Visualizzazione dei dati  
  
### <a name="overview"></a>Panoramica  
 I grafici sono una modalità visiva per aggregare e visualizzare i dati allo scopo di migliorare il processo decisionale. Consentono agli utenti di fronte a una grande quantità di dati, ma vale a dire little vedere ciò che merita attenzione e ciò che potrebbe essere necessario un'azione.  
  
 L'utente trarranno vantaggio da un grafico se viene soddisfatta una delle condizioni seguenti:  
  
-   Consente il grafico agli utenti di identificare le attività che potervi intervenire?  
  
-   Il grafico consentirà agli utenti prevedere le conseguenze di potenziali modifiche?  
  
-   Il grafico consentirà agli utenti di individuare tendenze e identificare i modelli?  
  
-   Il grafico consentirà agli utenti di prendere decisioni migliori?  
  
-   Il grafico aiuterà rispondere a domande specifiche che gli utenti possono avere nel contesto specificato?  
  
#### <a name="general-rules-for-charts"></a>Regole generali per i grafici  
  
-   Chiaramente dati etichetta. Nelle illustrazioni senza spiegazioni sono semplicemente belle immagini.  
  
-   Avviare assi da zero per evitare le proporzioni di inclinazione. Le dimensioni di lunghezza e indicatore di riga sono importanti indicatori visivi per comprendere le relazioni tra i punti dati.  
  
-   Creare grafici, non infografiche. Infografiche sono artistiche rappresentazioni dei dati e l'obiettivo principale è storytelling visual. I grafici possono (e dovrebbero) essere visivamente accattivante, ma lasciare che i dati parlino da soli.  
  
-   Evitare skeumorphism, grafici grafici a barre, hashmark a contrasto elevato e altri tocchi infografica.  
  
-   Non utilizzare effetti 3D come elemento decorativo. Utilizzarle solo se è effettivamente parte integrante di capacità dell'utente di comprendere le informazioni.  
  
-   Evitare di utilizzare più linee e riempimenti, più di due colori possono rendere difficili da leggere e interpretare correttamente questo tipo di grafico.  
  
-   Non utilizzare un grafico (o qualsiasi illustrazione) come unico mezzo di comprendere un concetto o l'interazione con i dati. Questo presenta difficoltà per gli utenti con problemi visivi.  
  
-   Non usare i grafici come elementi decorativi o gratuiti in una pagina. In altre parole, se non aggiunta un grafico che qualsiasi valore o la Guida utenti risolvere un problema, non utilizzarlo.  
  
### <a name="chart-types"></a>Tipi di grafico  
 Tipi di grafico utilizzato in Visual Studio includono i grafici a barre, grafici a linee, un grafico a torta modificato nota come grafico ad anello o "grafico ad anello," sequenze temporali, a dispersione tracciati (detti anche "grafici a del cluster") e i diagrammi di Gantt. Ogni tipo di grafico è utile per la comunicazione di un tipo di informazioni diverso.  
  
### <a name="other-charting-considerations"></a>Altre considerazioni sulla creazione di grafici  
  
#### <a name="color"></a>Colore  
 È presente una specifica tavolozza della creazione di grafici di colori definiti per l'uso in Visual Studio. È accessibile per i tipi principali di distinguere la tavolozza e i colori possono essere differenziati anche quando si usa come sezioni molto ridotta del colore. È possibile usare questi colori in qualsiasi combinazione per qualsiasi tipo di grafico o diagramma nell'interfaccia utente. Non devi usare tutti i colori di sette, se non è necessario che molti colori distinti. Questi colori non sono stati progettati per essere utilizzato con tutti gli elementi in primo piano, in modo che non si inserisce testo o glifi sopra questi colori. Queste sfumature diverse devono essere impostate come hardcoded ed esposte alla personalizzazione dell'utente in **strumenti > Opzioni** (vedere [esponendo i colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Campione|HEX|RGB|  
|------------|---------|---------|  
|![Campione 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|& 71B252|113,178,82|  
|![Campione BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|& BF3F00|191,63,0|  
|![Campione FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|& FCB714|252,183,20|  
|![Campione 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|& 903F8B|144,63,139|  
|![Campione 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|& 117AD1|17,122,209|  
|![Campione 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|& 79D7F2|121,215,242|  
|![Campione B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|& B5B5B5|181,181,181|  
  
##  <a name="BKMK_OnObjectUI"></a> Per gli oggetti dell'interfaccia utente e la lettura  
 In questa sezione fornisce il contesto di visualizzazione, noto anche come visualizzazione rapida codice, un tipo di interfaccia utente per gli oggetti univoci a Visual Studio.  
  
### <a name="overview"></a>Panoramica  
  
-   Per gli oggetti dell'interfaccia utente dovrebbe concedere all'utente ulteriori informazioni o interattività senza pregiudicare le loro attività principale.  
  
-   Il motivo principale per l'interfaccia utente per gli oggetti in Visual Studio è noto come "informazioni al momento della attenzione".  
  
-   Interfaccia utente per gli oggetti in Visual Studio è sia inline o a virgola mobile e durevole o temporaneo.  
  
    -   Visualizzazione rapida di codice, un tipo di interfaccia utente per gli oggetti in Visual Studio è in linea e durevole.  
  
    -   CodeLens, un tipo di interfaccia utente per gli oggetti in Visual Studio, è temporaneo e a virgola mobile  
  
 Comprendere il funzionamento di un frammento di codice o trovare dettagli su tale codice, spesso richiede uno sviluppatore cambiare contesto e passare a altro contenuto o un'altra finestra. Questi cambiamenti di contesto possono essere problematica, perché gli utenti possono perdere concentrarsi sulle loro attività originale se gli utenti lasciano le finestra principale. Inoltre, recupero che back contesto originale può essere difficile, soprattutto se cambio windows ha causato il codice originale venga nascosto da altra interfaccia utente.  
  
 Per gli oggetti dell'interfaccia utente segue uno schema denominato "informazioni al momento della attenzione". Questi messaggi, le finestre popup e finestre di dialogo contengono agli utenti informazioni aggiuntive, rilevanti che aggiunge chiarimenti o interattività senza distrarti dal loro attività principale. Esempi dell'interfaccia utente per gli oggetti includono le finestre popup visualizzate quando un utente si posiziona il puntatore del mouse su un'icona nell'area di notifica, la sottolineatura a zigzag rossa sotto una parola errata e la visualizzazione rapida introdotta in Visual Studio 2013.  
  
### <a name="decision-points"></a>Punti di decisione  
 All'interno di Visual Studio, esistono diversi modi per usare questo modello di informazioni al momento di attenzione. Scelta del meccanismo a destra e implementarla in modo coerente e stimabile è essenziale per l'esperienza complessiva. In caso contrario, potrebbe essere visualizzati agli utenti un'esperienza poco chiara o incoerente che comporta un peggioramento rivoluzionare il contenuto stesso.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relazioni tra schema e i dettagli del contenuto  
 Le informazioni al momento della particolare attenzione viene usate per visualizzare una relazione tra il contenuto che l'utente è concentrato sul (il contenuto di "master") e altre correlate contenuto (il contenuto "detail"). In questo modello, il contenuto di dettaglio è chiaramente correlato al contenuto, l'utente sta collaborando e può essere visualizzata vicino al contenuto principale. Informazioni aggiuntive o informazioni che non possono essere riassunto senza sovraccaricare il contenuto master devono seguire un altro modello, ad esempio una finestra degli strumenti.  
  
-   **Sempre** visualizzare il contenuto di dettaglio in stretta vicinanza al contenuto principale.  
  
-   **Sempre** assicurarsi che il contenuto di dettaglio consente comunque all'utente di rimanere concentrati sul contenuto master. Spesso, il modo migliore per ottenere questo risultato è per il rendering del contenuto di dettaglio come vicino il contenuto master come possibili. Questa operazione può essere eseguita per il rendering del contenuto di dettagli in una finestra popup accanto al contenuto principale o eseguendo il rendering dell'inline del contenuto dettaglio sotto il contenuto di master.  
  
-   **Mai** usare informazioni al momento della attenzione che indirizza l'utente dal contenuto principale. Se gli utenti devono visualizzare il contenuto del dettaglio separatamente, esporre un'azione esplicita che consente all'utente di eseguire questa operazione.  
  
#### <a name="design-details"></a>Dettagli di progettazione  
 Dopo aver determinato che per gli oggetti dell'interfaccia utente è la scelta giusta, sono disponibili quattro considerazioni di progettazione principale:  
  
1.  **Persistenza:** il contenuto deve essere permanente o temporaneo?   
    Gli utenti dovranno mantenere visibili per fare riferimento o interagire con le informazioni? O gli utenti di effettuare rapidamente visualizzare rapidamente le informazioni e quindi continuare con l'attività principale?  
  
2.  **Tipo di contenuto:** il contenuto sarà informativi, interattivi o per la navigazione?   
    L'utente necessita di ulteriori dettagli sul contenuto master? È necessario completare un'attività che interessa il contenuto principale dell'utente? Oppure è necessario che l'utente essere reindirizzati a un'altra risorsa?  
  
3.  **Tipo di indicatore:** ha un indicatore ambiente senso?   
    Possano le informazioni da riepilogati in modo utile e visualizzare senza sovraccaricare il contenuto master?  
  
4.  **Movimenti:** movimenti ciò che verrà utilizzato per richiamare e ignorare l'interfaccia utente?   
    Come verrà visualizziamo il contenuto di dettaglio e inviarlo da subito l'utente? È possibile valore per l'aggiunta di un movimento, ad esempio l'aggiunta per passare tra gli stati temporanei e permanenti?  
  
 Ognuno di questi aspetti tenuti in quattro considerazione avrà un impatto sui componenti principali dell'interfaccia utente per gli oggetti.  
  
### <a name="on-object-ui-components"></a>Componenti dell'interfaccia utente per gli oggetti  
  
1.  Tipo di contenitore (Visualizzatore di contenuto)  
  
    -   Virgola mobile  
  
    -   Inline  
  
2.  Tipo di contenuto  
  
    -   Messaggio informativo: i dati che potrebbero essere statico o dinamico  
  
    -   Eseguibili: i comandi modificare il contenuto principale  
  
    -   Per la navigazione: collegamenti che visualizzano l'utente a un'altra finestra o applicazione, ad esempio MSDN  
  
3.  Movimenti  
  
    -   Chiamata  
  
    -   Licenziamento  
  
    -   L'aggiunta  
  
    -   Altre interazioni  
  
4.  Modello di persistenza ed eseguire il commit  
  
    -   Temporaneo  
  
    -   Durevole  
  
    -   Automatico  
  
    -   On demand  
  
5.  Indicatori di ambiente (facoltativi)  
  
    -   Sottolineatura a zigzag  
  
    -   Icona smart tag  
  
    -   Altri indicatori di ambiente  
  
#### <a name="container-content-presenter-type"></a>Tipo di contenitore (Visualizzatore di contenuto)  
 Esistono due principali opzioni disponibili per presentare il contenuto nel punto di attenzione:  
  
1.  **Inline:** un presentatore inline, ad esempio la visualizzazione rapida che è stato introdotto nell'Editor di Visual Studio 2013 codice rende lo spazio per nuovi contenuti spostando il contenuto esistente.  
  
    -   **Preferisce** Presenter inline se si prevede che gli utenti desiderano dedicare una quantità significativa di tempo che fa riferimento a o l'interazione con il contenuto presente.  
  
    -   **Evitare** Presenter inline se si prevede che gli utenti sarà possibile visualizzare rapidamente le informazioni è presente, quindi continuare con le principali attività con un'interruzione minima.  
  
2.  **Numeri reali:** un presentatore a virgola mobile è posizionato il più vicino al contenuto selezionato possibile ma non modifica il layout del contenuto esistente. Varie strategie possono essere impiegate, ad esempio visualizzando un pannello del contenuto mobile tramite il più vicino di spazio disponibile per il simbolo selezionato.  
  
    -   **Preferisce** mobile Presenter se si prevede che gli utenti sarà possibile visualizzare rapidamente le informazioni è presente, quindi continuare con le principali attività con un'interruzione minima.  
  
    -   **Evitare** mobile Presenter se si prevede che gli utenti dovranno dedicare una quantità significativa di tempo che fa riferimento a o l'interazione con il contenuto è presente.  
  
#### <a name="content-type"></a>Tipo di contenuto  
 Esistono tre tipi principali di contenuto che possono essere visualizzati all'interno di qualsiasi contenitore dell'interfaccia utente per gli oggetti. È possibile visualizzare qualsiasi combinazione di questi tipi di informazioni. I tre tipi sono:  
  
1.  **Messaggio informativo:** la maggior parte per gli oggetti contenitori dell'interfaccia utente visualizzerà un tipo di contenuto informativo. Il contenuto può rappresentare informazioni sullo stato attuale dell'ambiente o può rappresentare informazioni su uno stato potenziale futura dell'ambiente. Ad esempio, può essere usato per mostrare l'effetto di un comando specifico, ad esempio un'operazione di refactoring, sul codice esistente.  
  
    -   **Sempre** usare la rappresentazione canonica di informazioni da visualizzare. Ad esempio, codice dovrebbe essere simile a code, completa con l'evidenziazione della sintassi e deve rispettare qualsiasi tipo di carattere e altre impostazioni di ambiente impostate dall'utente.  
  
    -   **Sempre** considerare il supporto di tutte le azioni sul contenuto informativo che sarebbe possibile se le stesse informazioni viene presentate come contenuto master. Ad esempio, se il codice esistente all'interno di un contenitore dell'interfaccia utente per gli oggetti di presentazione, consigliabile prendere in considerazione che supportano la possibilità di esplorare e modificare tale codice.  
  
    -   **Sempre** è consigliabile usare un colore di sfondo diverso se la presentazione di contenuto informativo che rappresenta uno stato futuro potenziale.  
  
2.  Eseguibili: alcuni contenitori dell'interfaccia utente per gli oggetti verranno offrono la possibilità di eseguire alcune azioni sul contenuto master, ad esempio eseguire un'operazione di refactoring.  
  
    -   **Sempre** posizionare i comandi utilizzabili separatamente dal contenuto informativo.  
  
    -   **Sempre** abilitare e disabilitare le azioni quando appropriato.  
  
    -   **Sempre** fare riferimento alle linee guida standard per rappresentare comandi all'interno delle finestre di dialogo.  
  
    -   **Sempre** mantenere il numero di azioni esposte in un contenitore dell'interfaccia utente per gli oggetti di inattività minimo. L'interazione con l'interfaccia utente per gli oggetti deve essere un'esperienza semplice e veloce. L'utente non necessario impiegare energia sulla gestione di contenitore per gli oggetti dell'interfaccia utente stesso.  
  
    -   **Sempre** prendere in considerazione come e quando un contenitore dell'interfaccia utente per gli oggetti verrà chiuse o chiusa. Come procedura consigliata, qualsiasi azione che si conclude la finestra di dialogo tra il master e di dettaglio del contenuto deve chiudere anche il contenitore dell'interfaccia utente per gli oggetti quando viene richiamata l'azione.  
  
3.  **Spostamento:** alcuni per gli oggetti contenitori dell'interfaccia utente includono collegamenti che visualizzano l'utente a un'altra finestra o applicazione, ad esempio l'apertura di un articolo MSDN in web browser dell'utente.  
  
    -   **Sempre** anteporre un collegamento per la navigazione con "Apri" in modo che gli utenti non saranno sorpresi da cui si accede ad alcuni altri contenuti.  
  
    -   **Sempre** separare i collegamenti di navigazione tra i collegamenti di utilità pratici.  
  
#### <a name="ambient-indicators-optional"></a>Indicatori di ambiente (facoltativi)  
 Gli indicatori di ambiente possono essere meno evidenti, incluso il testo visualizzato in un colore a contrasto rispetto al resto del codice, o ovvio, compresi i simboli tickler come sottolineature a zigzag e icone di smart tag. Gli indicatori di ambiente di comunicare la disponibilità di informazioni aggiuntive e pertinenti. In teoria, forniscono informazioni utili anche senza richiedere all'utente di interagire con essi.  
  
-   **Sempre** posizionare un indicatore di ambiente in modo che non si distaccherà o sovraccaricare l'utente. Se non è possibile posizionare un indicatore di ambiente in modo tale, prendere in considerazione un'altra soluzione.  
  
-   **Sempre** posizionare più vicino possibile al contenuto che è correlato l'indicatore di ambiente.  
  
-   **Sempre** tenta di creare un indicatore che riepiloga le informazioni che vengono resi disponibili. Si consiglia di fornire un conteggio del numero di elementi di dati disponibili (ad esempio, "3 riferimenti" anziché semplicemente "Riferimenti") o pensare a un altro modo per riepilogare i dati.  
  
    -   In casi in cui i dati per un indicatore non possono sempre essere calcolati e visualizzati immediatamente si consiglia di fornire commenti e suggerimenti progressivo come vengono calcolati i valori. Si consideri ad esempio di animazione delle modifiche che riflettono gli aggiornamenti ai dati disponibili, simili al modo in cui che viene aggiornato nel live tile di posta elettronica in Windows Phone come il numero di messaggi di posta elettronica non letta aumenta.  
  
-   **Mai** aggiungere ulteriori indicatori rispetto a un utente può richiedere ragionevolmente per una determinata parte del contenuto. Gli indicatori di ambiente devono essere utili senza richiedere alcuna interazione da parte dell'utente. Gli indicatori di perdono loro ambiente se richiedono overflow e altri controlli di gestione per spostarle nella visualizzazione.  
  
#### <a name="gestures"></a>Movimenti  
 Un aspetto fondamentale che consente all'utente di concentrare l'attenzione sul contenuto del master è da che supportano i movimenti destro per aprire e chiudere il contenuto di dettagli aggiuntivi.  
  
-   **Sempre** richiedono all'utente di eseguire alcuni movimenti esplicito per aprire il contenuto aggiuntivo. I movimenti open comuni includono:  
  
    -   **Al passaggio del mouse:** le descrizioni comandi o contenuto informativo interattivo  
  
    -   **Comando esplicita:** presenter inline  
  
    -   **Fare doppio clic sull'indicatore di ambiente:** finestra popup CodeLens  
  
-   **Sempre** ignorare il contenuto di dettaglio ogni volta che l'utente preme il tasto Esc.  
  
-   **Sempre** prendere in considerazione il contesto dell'interfaccia utente per gli oggetti. Per contenuto Presenter che consentono l'interazione all'interno del contenitore, valutare attentamente se si desidera visualizzare informazioni aggiuntive sul passaggio del mouse, che è probabile che sia problematica per flusso di lavoro dell'utente.  
  
-   **Mai** visualizzare il contenuto al passaggio del mouse che sembra essere modificabile o invita l'interazione dell'utente. Questo comportamento può causare frustrazione utenti se tentano di spostare il cursore sul contenuto del dettaglio, come il comportamento standard per una descrizione comando consiste nel chiudere immediatamente quando il cursore non è più posizionato master contenuto che l'ha prodotta.  
  
##  <a name="BKMK_SelectionModels"></a> Modelli di selezione  
  
### <a name="overview"></a>Panoramica  
 Un modello di selezione è il meccanismo utilizzato per indicare e confermare le operazioni su uno o più oggetti di interesse all'interno dell'interfaccia utente. Questo argomento vengono illustrati i modelli di interazione di selezione all'interno degli editor di documento di Visual Studio: gli editor di testo, aree di progettazione e le superfici di modellazione.  
  
 Gli utenti devono avere un modo di indicare a Visual Studio quali stanno lavorando e Visual Studio deve rispondere in modo prevedibile con commenti e suggerimenti per gli utenti sui quali opera su. Le differenze o una comunicazione tra l'utente e l'interfaccia utente può comportare l'utente non si rendevano conto un'azione che può avere conseguenze impreviste. Spesso, l'errore va inosservata fino a quando l'utente vede che qualcosa è mancano o è stato modificato. I modelli di selezione sono pertanto una delle parti più importanti della progettazione dell'interfaccia utente. Anche se i modelli di selezione in Visual Studio siano coerenti con Windows, esistono piccole differenze.  
  
 In Visual Studio, come in Windows, i modelli di selezione sono diversi a seconda del contesto in cui si verifica l'interazione. Selezioni possono verificarsi in quattro tipi di oggetti:  
  
-   Testo  
  
-   Oggetti grafici  
  
-   Elenchi e strutture  
  
-   Griglie  
  
 All'interno di questi oggetti, esistono tre tipi di selezioni:  
  
-   Contigui  
  
-   Non contigue  
  
-   Region  
  
#### <a name="scope"></a>Ambito  
 Il componente più importante della selezione consiste nel garantire che l'utente sappia quale finestra funzionano (attivazione) e in cui lo stato attivo è disponibile (selezione). Visual Studio estende la funzionalità di gestione di finestra in Windows, ma lo schema di attivazione è lo stesso: l'interazione con una finestra Visualizza lo stato attivo alla finestra. Visual Studio include due indicatori per l'attivazione: uno per le finestre dei documenti e uno per finestre degli strumenti.  
  
 Per le finestre di documento, la finestra attiva è indicata da una scheda della finestra documento presto in primo piano e modificandone il colore di sfondo:  
  
 ![Selezione della scheda attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 01_ActiveTab")  
  
 **Selezione della scheda attiva**  
  
 Per le finestre, finestra attiva è indicata da una modifica il colore dell'area della barra del titolo della finestra degli strumenti:  
  
 ![Selezione della finestra degli strumenti attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 02_ActiveToolWindow")  
  
 **Finestra degli strumenti attiva che Mostra selezione primaria di un nodo**  
  
 ![Selezione della finestra degli strumenti inattiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 03_InactiveToolWindow")  
  
 **Finestra degli strumenti inattivo, che mostra la selezione non attivo del nodo**  
  
 Quando una finestra è attiva, in base ai modelli di selezione descritti in questa sezione delle linee guida è indicato lo stato attivo.  
  
#### <a name="context"></a>Contesto  
 Visual Studio è stato progettato per mantenere un complesso concetto di contesto, tenendo traccia in cui l'utente sta utilizzando. Una sola finestra è attiva, sia che si tratti di una finestra del documento o degli strumenti. Tuttavia, la finestra del documento in primo piano mantiene sempre una selezione non attivo. Anche se lo stato attivo potrebbe essere in una finestra degli strumenti, la finestra del documento che è stato ultima attività Visualizza una selezione, anche in uno stato inattivo. Questa operazione viene eseguita per mantenere il contesto dell'utente nel documento che stava modificando, mostrarli che Visual Studio mantiene il proprio stato in modo che possano restituire e spostare con facilità tra finestre dei documenti e finestre degli strumenti.  
  
### <a name="text-selection"></a>Selezione di testo  
 Editor di Visual Studio che sono rigorosamente testuali, ad esempio l'editor di testo incorporato, utilizzare lo stesso modello di selezione di testo e aspetto descritte nel [Mouse e i puntatori](/windows/desktop/uxguide/inter-mouse) pagina di Windows User Experience interazione Guidelines su MSDN. Lo stato attivo nell'editor di testo è indicato da una barra verticale, chiamata punto di inserimento. Il punto di inserimento è un singolo pixel thick e colorato come l'inverso di tutti gli elementi presenti dietro di essa. Fa lampeggiare secondo la frequenza impostata dal **intermittenza cursore** impostazione nel **velocità** scheda della finestra di **tastiera** applet del Pannello di controllo.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Selezione contigua e non contiguo  
 Solo selezione all'interno dell'editor di testo è contiguo. Testo selezioni non sono consentite, ma devono essere indirizzate in Editor oggetti grafici non contigui. Quando il puntatore del mouse è su un'area di testo, il cursore cambia in un cursore. Un solo clic inserisce il punto di inserimento nell'editor di testo in corrispondenza della posizione di clic. Tenendo premuto il pulsante del mouse viene avviata un'evidenziazione di selezione e rilasciare il pulsante del mouse termina la selezione evidenziata.  
  
#### <a name="region-selection-box-selection"></a>Selezione dell'area (selezione della casella)  
 Visual Studio supporta le selezioni di area nell'editor di testo e si tratta di selezione della casella. Selezione della casella consente all'utente di selezionare un'area di testo che non segue il flusso di testo normale. Come con la selezione di testo standard, la selezione deve essere contigua. Selezione della casella viene avviata, tenere premuto il tasto Alt mentre si trascina il mouse. Selezione della casella può anche essere avviata, tenere premuti i tasti Alt e MAIUSC mentre si utilizzano i tasti di direzione per indicare l'area di selezione. Selezione della casella viene utilizzato l'evidenziazione di selezione normale e Mostra il cursore di punto di inserimento lampeggiare alla fine dell'area di selezione.  
  
 ![A livello di area &#40;finestra&#41; selezione in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 04_BoxSelection")  
  
 **Selezione area (casella) in Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Aspetto del testo selezione  
 È possibile personalizzare i colori utilizzati per la selezione attiva e inattiva nell'editor. Per personalizzare l'aspetto visivo dell'editor, un utente può passare a **strumenti > Opzioni**, quindi vedere in **ambiente > tipi di carattere e colori > Editor di testo**.  
  
### <a name="graphical-selection"></a>Selezione con interfaccia grafica  
  
#### <a name="interaction"></a>Interazione  
 Selezione degli oggetti grafici può essere complessi e dipende da numerosi fattori:  
  
-   **Modello di selezione principale dell'editor.** Gli editor che contengono gli oggetti grafici sono anche utilizzabile per modificare il testo o griglie. L'editor, ad esempio, potrebbe essere un editor di testo che supporta anche la posizione di oggetti grafici, ad esempio la finestra di progettazione XAML di Visual Studio. Supporto di più tipi di oggetto può influire sul modo in cui l'utente seleziona i gruppi costituiti da diversi tipi di oggetti.  
  
-   **Supporto per gli stati di selezione primaria e secondaria.** Un editor può fornire selezione primaria e secondaria degli Stati, in modo che gli oggetti possono essere modificati all'unisono, allineati tra loro, ridimensionati insieme, e così via.  
  
-   **Supporto di modifica sul posto.** Editor è anche possono consentire il contenuto dei rispettivi oggetti di grafici da modificare. Ad esempio, una forma di rettangolo potrebbe anche contenere testo all'interno che può essere modificato dall'utente. Inoltre, che il testo potrebbe essere centrato o giustificato. La modifica sul posto implica un livello più dettagliato dell'interazione dell'utente e pertanto richiede un set appropriato di segnali visivi per presentare le informazioni sullo stato all'utente.  
  
#### <a name="mouse-interaction"></a>Interazione del mouse  
  
|Input|Risultato|  
|-----------|------------|  
|Fare clic su un oggetto non selezionato|Seleziona l'oggetto e visualizza una linea tratteggiata e quadratini di ridimensionamento, se l'oggetto è ridimensionabile.|  
|Fare clic su un oggetto selezionato|Attiva se l'oggetto supporta la modifica in diretta. Facendo clic all'esterno dell'oggetto disattiva la modalità di modifica sul posto.|  
|Fare doppio clic su un oggetto|Apre il code-behind l'oggetto per la modifica e potrebbe inserire un gestore eventi predefinito, se appropriato.|  
|Puntare a un oggetto|Il puntatore per il cursore di spostamento. L'aspetto dell'oggetto, ad esempio la luminosità o il colore, potrebbe cambiare.|  
|Scegliere un handle di selezione|Il puntatore per il cursore di ridimensionamento. Per gli oggetti che supportano la rotazione, alcune quadratini di ridimensionamento potrebbero modificare il puntatore a un cursore Ruota come il puntatore è posizionato in modo diverso (ad esempio, spostata più lontani) rispetto al quadratino di ridimensionamento.|  
|Trascinamento|Anche se l'oggetto non è selezionata in precedenza, il puntatore viene modificato il cursore di spostamento e sposta l'oggetto.|  
|Editor perde lo stato attivo|Disattiva modalità di modifica sul posto, anche se l'oggetto conserva il contenuto e l'aspetto che aveva durante il suo ultimo stato di selezione operazione /.|  
|Selezione oggetti|Indicato da un bordo, linea punteggiata o altri trattamento visivamente distinto per evidenziare i limiti dell'oggetto.|  
|Ridimensionare un oggetto selezionato|Indicato da handle di selezione.<br /><br /> Un oggetto ridimensionabile ha otto handle, che rappresenta ciascuna direzione in cui può essere ridimensionata. Un minor numero di handle possono essere utilizzati se l'oggetto può essere ridimensionata solo in determinate le direzioni. Quando si ridimensiona un oggetto fino a dove otto handle non è interattivi, quattro handle possono essere usati. Handle di dimensioni devono essere collegate alle metriche di bordo e il bordo di finestra con il **GetSystemMetrics** funzione API alla dimensione proporzionalmente la risoluzione dello schermo.<br /><br /> ![Quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 05_ResizeHandles")|  
|Ruotare un oggetto selezionato|![Ruota gli handle](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Interazione della tastiera  
  
|Input|Risultato|  
|-----------|------------|  
|Scheda|Consente di spostare l'indicatore di stato attivo tra l'ordine logico degli oggetti nell'editor. È possibile da sinistra a destra o alto verso il basso in base **TabIndex** (o equivalenti) il valore di proprietà dell'ordine di creazione degli oggetti e lo scopo complessivo dell'editor. Maiusc + Tab consente di invertire la direzione dell'indicatore di stato attivo.|  
|BARRA SPAZIATRICE|Attiva la modalità Panoramica mentre viene mantenuto pressione di tasto. Input da mouse aggiuntivi è necessario per eseguire la traslazione alla posizione del riquadro di visualizzazione.|  
|CTRL+BARRA SPAZIATRICE|Attiva modalità di zoom mentre viene mantenuto pressione di tasto. È necessario l'input del mouse aggiuntive per aumentare e diminuire il fattore di zoom.|  
|Ctrl + Alt + segno meno|Riduce il fattore di zoom di un livello.|  
|Ctrl + Alt + segno più|Aumenta il fattore di zoom di un livello.|  
|MAIUSC o Ctrl|Aggiunge l'oggetto al gruppo di selezione. CTRL consente inoltre di rimuovere gli oggetti singolarmente dal gruppo di selezione.|  
|INVIO|Esegue il comando predefinito per l'oggetto (in genere aprire o modificare).|  
|F2|Attiva la modifica sul posto per l'oggetto.|  
|Tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto premuto, incrementi minimi (ad esempio, 1 pixel in un momento)|  
|CTRL + tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto premuto, in incrementi di dimensioni maggiori (ad esempio, 10 pixel in un momento)|  
|MAIUSC + freccia chiavi|Ridimensiona gli oggetti selezionati nella direzione corrispondente, in incrementi di piccole dimensioni (ad esempio, 1 pixel in un momento)|  
|CTRL + MAIUSC + tasti di direzione|Ridimensiona gli oggetti selezionati nella direzione corrispondente, in incrementi di dimensioni maggiori (ad esempio, 10 pixel in un momento)|  
  
 Quando gli utenti modificano controlli attivati, si potrebbe avere senso per gli oggetti a ridimensionamento automatico con l'input utente. Ad esempio, se l'utente modifica un controllo etichetta, quindi l'etichetta di aumento delle dimensioni per visualizzare il testo appena digitato dall'utente. Se questa operazione non viene eseguita, l'utente deve ridimensionare il controllo manualmente dopo la modifica del testo. Se l'utente dispone di molti controlli, questo diventa un rote e attività compromessa.  
  
#### <a name="graphical-containers"></a>Contenitori di grafici  
 In alcuni casi, editor grafici forniscono i contenitori per altri oggetti di grafiche, ad esempio il controllo Panel di Windows Form o il controllo di Layout di griglia nella finestra di progettazione HTML. Se l'editor fornisce contenitori per altri oggetti di grafiche, il seguente modello di selezione deve essere usato per il contenitore solo (oggetti all'interno di seguire il contenitore di modelli standard come descritto in precedenza):  
  
|Input|Risultato|  
|-----------|------------|  
|Fare clic sul contenitore|Seleziona l'oggetto contenitore senza direttamente se si seleziona uno degli oggetti contenuti. Il contenitore può essere spostato e/o ridimensionato con input (come descritto in precedenza) da tastiera e mouse standard. Gli oggetti contenuti vengono spostati in relazione al contenitore, ma gli oggetti contenuti non vengono ridimensionati, a meno che siano selezionati anche direttamente.|  
|Passare il mouse sull'area di confine del contenitore|Assume il cursore di spostamento, che indica che il contenitore può essere spostato il mouse.|  
|Trascinare area limiti del contenitore|Modifica il puntatore del mouse per il cursore di spostamento e sposta il contenitore (e gli oggetti contenuti all'interno). Il contenitore non può essere spostato senza che sia necessario selezionato con un solo clic.|  
|Fare clic su un oggetto all'interno del contenitore|Consente di deselezionare il contenitore, se selezionata e consente di selezionare solo l'oggetto selezionato.|  
|MAIUSC + fare clic su o Ctrl + clic su un oggetto indipendente e/o il contenitore|Aggiunge l'oggetto selezionato alla selezione esistente o gruppo di selezione. Se l'oggetto selezionato è già un membro del gruppo di selezione, viene rimosso dal gruppo di selezione.|  
  
 Gli oggetti contenuti devono rispettare il modello di base di selezione come descritto nella sezione precedente. Da test di usabilità della finestra di progettazione Windows Form, gli utenti prevede l'accesso trasparente per gli oggetti contenuti senza effettuare dei passaggi coinvolti (sottopone l'oggetto di contenimento).  
  
#### <a name="disjoint-and-region-selections"></a>Non contiguo e le selezioni di area  
 Gli editor di oggetti grafici devono supportare selezioni non contigue. Si noti che questo grafico non mostra l'aspetto del controllo per Visual Studio. Visualizzare [aspetto selezione oggetti grafici](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) per specifiche dettagliate visual.  
  
 ![Non contigue e area selettori](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 07_DisjointRegionSelectors")  
  
 **Selezione non contiguo**  
  
 Editor grafici deve anche fornire le selezioni di area con un indicatore di selezione di testo scorrevole. Se l'editor grafico supporta altri tipi di oggetto (ad esempio, testo), quindi selezioni per l'area potrebbero non essere possibile in base ai vincoli di tali altri tipi di oggetto.  
  
 ![Selezione di testo scorrevole](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 08_MarqueeSelection")  
  
 **Selezione di testo scorrevole**  
  
#### <a name="primary-and-secondary-selections"></a>Selezioni primarie e secondarie  
 Alcuni editor oggetto grafica consente all'utente di modificare o allineare gli oggetti nei gruppi. In questo caso, il concetto di selezioni primarie e secondarie deve essere introdotto. La selezione primaria è l'oggetto a cui rispondono per operazioni del gruppo tutti gli altri oggetti. L'oggetto selezionato dall'utente prima di tutto diventa il controllo primario e selezioni successive diventano le selezioni secondarie. La selezione primaria ha un trattamento visual distinto dalle selezioni secondarie per indicare che l'oggetto è primaria:  
  
 ![Selezione primaria e secondaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 09_PrimarySecondary")  
  
 **Selezione primaria con due selezioni secondarie**  
  
####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Aspetto di selezione di oggetti grafici  
 Quadratini di ridimensionamento sono quadratini disegnate in un modello rettangolare intorno alla casella di delimitazione dell'oggetto. Il grafico seguente mostra esempi dei vari stati che può disporre di un oggetto grafico con handle di ridimensionamento e aspetto modifica sul posto. Le dimensioni dei punti di controllo devono essere collegate al bordo della finestra ed edge le metriche usando il **GetSystemMetrics** API.  
  
|Stato|Aspetto|Dettagli su Visual|  
|-----------|----------------|--------------------|  
|**Non selezionato**|Impostazione predefinita|![Predefinito dello stato del pulsante](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 10_DefaultState")||  
|**Selezione primaria**|Ridimensionabile|![Selezione primaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 11_PrimaryResize")|![Selezione primaria con quadratini di ridimensionamento &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713 12_PrimaryResizeZoom")|  
|**Selezione primaria**|Non ridimensionabile|![Selezione primaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 13_PrimaryNoResize")|![Selezione primaria senza quadratini di ridimensionamento &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713 14_PrimaryNoResizeZoom")|  
|**Selezione primaria**|Bloccato|![Selezione primaria bloccata](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 15_PrimaryLocked")|![Selezione primaria bloccata &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713 16_PrimaryLockedZoom")|  
|**Selezione secondaria**|Ridimensionabile|![Selezione secondaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 17_SecondaryResize")|![Selezione secondaria con quadratini di ridimensionamento &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713 18_SecondaryResizeZoom")|  
|**Selezione secondaria**|Non ridimensionabile|![Selezione secondaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 19_SecondaryNoResize")|![Selezione secondaria senza quadratini di ridimensionamento &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713 20_SecondaryNoResizeZoom")|  
|**Selezione secondaria**|Bloccato|![Selezione secondaria bloccata](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 21_SecondaryLocked")|![Selezione secondaria bloccata &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713 22_SecondaryLockedZoom")|  
|**Attiva nell'interfaccia utente**|Impostazione predefinita|![Lo stato attivo dell'interfaccia utente](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 23_UIActive")|![Lo stato attivo dell'interfaccia utente &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713 24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Visualizza selezione modelli  
  
#### <a name="tree-view"></a>Visualizzazione albero  
 Selezione di una visualizzazione albero viene visualizzato con un'evidenziazione semplice. Se l'utente fa clic sul nome di un nodo o un'icona di nodo, viene selezionato il nodo. I glifi forma di triangolo a sinistra del nodo di espandere o il controllo struttura ad albero di contratto ma non influenzano la selezione dell'utente, con una sola eccezione: dopo la compressione di un nodo padre quando la selezione si trova su un elemento figlio di tale nodo, la selezione si sposta all'elemento padre.  
  
 ![Visualizzazione albero tipica in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 25_TreeView")  
  
 **Visualizzazione albero tipica in Visual Studio**  
  
 Visualizzazioni dell'albero possono supportare le selezioni contigue e non contigui, persino tra più livelli nell'albero. Contigui o non contigui è necessario effettuare le selezioni multiple sui nodi dell'albero visibile. Se si comprime un nodo, la selezione non contiguo viene persa e il nodo che è stato compresso Ottiene la selezione. In questo modo, l'utente può visualizzare i nodi che verranno influenzati da un'operazione. Quando i nodi vengono compressi, diventa chiaro quali nodi interessati.  
  
 Quando si seleziona un nodo padre, applicare l'operazione per l'elemento padre, anche se potrebbero esserci casi in cui è opportuno per un'operazione da applicare per l'elemento padre e tutti i relativi figli. In questo caso, fornire un'interfaccia utente aggiuntiva durante l'operazione, ad esempio una casella di controllo o finestra di dialogo di conferma per rendere esplicito l'opzione "si applicano a tutti gli elementi figlio" all'utente.  
  
##### <a name="renaming"></a>Ridenominazione  
 Se i nodi dell'albero supportano la ridenominazione, la ridenominazione deve essere eseguita sul posto. L'operazione sul posto deve essere lo standard in tutti i controlli di struttura ad albero in Visual Studio. Specificare un comando rename che immediatamente viene attivata la modalità di modifica sul posto, con la selezione di testo che copre l'intero nome del nodo, pronto per accettare l'input dell'utente. Se il nodo rappresenta un file, il nome del file deve contenere l'estensione. L'evidenziazione di selezione deve includere solo il corpo del nome file e non dall'estensione.  
  
|Input|Risultato|  
|-----------|------------|  
|INVIO (tasto)|Esegue il commit dell'operazione di ridenominazione|  
|Tasto ESC|Annulla l'operazione di ridenominazione|  
|Facendo clic all'esterno dell'area di modifica sul posto|Esegue il commit dell'operazione di ridenominazione|  
|Annulla|Fornire una semplice operazione di annullamento per annullare l'operazione di ridenominazione|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Selezione all'interno di elenchi e i controlli griglia  
 Il concetto chiave nella selezione dell'elenco è che è basato su riga, il che significa che quando viene effettuata una selezione dell'intera riga è selezionato come unità. Al contrario, le griglie consentono celle specifiche da selezionare senza influire su qualsiasi altro aspetto della riga. Griglie potrebbero contenere anche una gerarchia di righe nidificate (ad esempio un TreeGrid) che consentono di intere diramazioni della gerarchia per essere selezionato e deselezionato interagendo con le righe padre. Selezione negli elenchi è indicata da un colore di evidenziazione semplice per l'intera riga di dati. Lo stato attivo è indicato da un singolo pixel punteggiato bordo riga modificabile corrente o la cella (riga se tutte le celle sono di sola lettura).  
  
> [!NOTE]
>  **Messa a fuoco** e **selezione** sono due concetti diversi. *Messa a fuoco* è un valore che indica quale dell'interfaccia utente di elemento è destinato per ricevere l'input non esplicitamente dirette a un altro oggetto, mentre *selezione* si riferisce allo stato dell'inclusione di un oggetto in un set di oggetti da cui successivi operazioni possono aver luogo.  
  
 Selezioni negli elenchi possono essere contigui, non contiguo, o area geografica. Quando selezioni multiple sono consentite, contigui e selezione indipendente deve sempre essere supportate, mentre il supporto per le selezioni di area (casella) è facoltativo. Selezioni per l'area possono essere avviate tramite trascinamento nello spazio vuoto del corpo dell'elenco.  
  
|Object|Selection|  
|------------|---------------|  
|List|Contigui|Sempre supportate (in caso di selezioni multiple sono consentite).|  
|List|Non contigue|Sempre supportate (in caso di selezioni multiple sono consentite).|  
|List|Region|Supporto facoltativo. Avviato mediante il trascinamento del mouse nello spazio vuoto del corpo dell'elenco.|  
  
 Fare clic su una sola volta in un elenco selezionare la riga in cui si è verificato il clic. Se l'utente di fare clic su una cella di elenco che supporta la modifica sul posto, la cella viene attivata anche immediatamente per la modifica sul posto. In caso contrario, l'intera riga immediatamente sia selezionata e Mostra un'evidenziazione.  
  
 Trascinare nel corpo elenco effettua una delle tre operazioni:  
  
-   Avvia una selezione per area, se l'elenco supporta l'elemento e la selezione tramite mouse si trova nello spazio vuoto  
  
-   Avvia un'operazione di trascinamento della selezione se la cella dell'elenco o la riga supporta da un'origine di trascinamento  
  
-   Seleziona la riga corrente  
  
##### <a name="in-place-editing"></a>La modifica sul posto  
 Quando è consentita la modifica sul posto, sono disponibili due modelli di base: selezione di controllo e la proprietà di modifica semplice. Con un controllo di modifica semplice, il contenuto è evidenziato e pronto per l'input non appena viene attivata la modifica sul posto dell'utente. In cui viene implementata una selezione di proprietà, il pulsante che richiama la selezione di proprietà viene visualizzato una volta che viene attivata la modalità di modifica sul posto e la selezione corrente non sia più evidenziata. Il pulsante di selezione deve essere allineato a destra della cella. Per esempi di modifica sul posto, vedere la **finestra delle proprietà** e **elenco attività** in Visual Studio.  
  
##### <a name="keyboard-support"></a>Supporto per la tastiera  
 Supporto per la tastiera per la selezione negli elenchi ed griglie segue le convenzioni standard di Windows:  
  
-   Tasti di direzione esplorare l'elenco, se si seleziona ogni riga/cella come lo stato attivo viene spostato.  
  
-   MAIUSC + freccia esegue una selezione contigua nella direzione dei tasti di direzione.  
  
-   CTRL + freccia seguita da attiva o disattiva la barra spaziatrice tra l'aggiunta e rimozione di elementi dell'elenco dalla selezione, la creazione di una selezione non contiguo.  
  
-   Per le griglie contenenti le gerarchie annidate, il tasto freccia destra consente di espandere una riga padre e il tasto freccia sinistra comprime uno.  
  
-   Il tasto Tab sposta lo stato attivo tra le celle nella riga corrente, se le celle possono essere modificate.  
  
-   Il tasto INVIO esegue il comando predefinito sull'elemento nell'elenco (spesso **aperto**).  
  
-   Il tasto F2 Attiva modifica sul posto per la cella attualmente selezionata.  
  
##  <a name="BKMK_PersistenceAndSavingSettings"></a> Persistenza e il salvataggio delle impostazioni  
  
### <a name="overview"></a>Panoramica  
 Anche se ogni componente software in Visual Studio è in genere responsabile per il proprio stato e la persistenza, Visual Studio Salva automaticamente le impostazioni in alcuni casi, ad esempio con posizioni e le dimensioni di finestra. Nella tabella seguente è una combinazione di impostazioni che richiedono un utente esplicito o programmato azione da intraprendere e le impostazioni salvate automaticamente.  
  
|Object|Gli elementi da salvare|Casi in cui salvare|Percorso in cui salvare|  
|------------|------------------|------------------|-------------------|  
|Oggetto selezionabile (ad esempio, una riga di codice)|Un punto di interruzione su una riga di codice<br /><br /> Un collegamento utente associato alla riga di codice|Quando viene salvato il progetto|Il **le opzioni utente (con estensione suo)** file per il progetto|  
|Finestra di dialogo|La posizione della finestra di dialogo, se è stato spostato<br /><br /> La vista che l'utente può essere utilizzato per ultimo nella finestra di dialogo|Quando si chiude la finestra di dialogo<br /><br /> Quando termina la sessione di Visual Studio|In memoria<br /><br /> Nel Registro di sistema **HKEY_Current_User**|  
|Window|Le dimensioni e la posizione della finestra|Quando si chiude la finestra<br /><br /> Quando cambia la modalità di Visual Studio<br /><br /> Quando termina la sessione di Visual Studio|Il **le opzioni utente (con estensione suo)** file per il progetto<br /><br /> File di opzioni personalizzate per le impostazioni della finestra|  
|Document|La selezione corrente nel documento<br /><br /> La visualizzazione del documento<br /><br /> L'ultimo diverse posizioni l'utente ha visitato|Quando il documento viene salvato|Il **le opzioni utente (con estensione suo)** file per il progetto|  
|Progetto|Riferimenti ai file<br /><br /> Riferimenti a directory su disco<br /><br /> Riferimenti ad altri software<br /><br /> Componenti<br /><br /> Informazioni sullo stato relative al progetto se stesso|Quando viene salvato il progetto|Il file di progetto|  
|Soluzione|Riferimenti a progetti<br /><br /> Riferimenti ai file|Quando viene salvata il progetto o soluzione|Il **soluzione (sln)** file|  
|Le impostazioni in **strumenti > Opzioni**|Personalizzazioni tastiera<br /><br /> Personalizzazioni barra degli strumenti<br /><br /> Combinazioni di colori|Quando la **strumenti > Opzioni** finestra di dialogo viene chiusa<br /><br /> Quando termina la sessione di Visual Studio|Nel Registro di sistema **HKEY_Current_User**|  
  
 Ciò che l'utente sta facendo e quando si esegue, determina se un'impostazione viene salvata in memoria (durante la sessione), salvata su disco (in più sessioni come un'impostazione del Registro di sistema), come parte del file di progetto o soluzione stesso, come parte di **soluzione Opzioni (con estensione suo)** file oppure come un impostazioni personalizzate del file che solo tale componente software è a conoscenza. La tabella precedente illustra diversi eventi in corrispondenza del quale è possano salvare le impostazioni. Tuttavia, esistono altri casi in cui si potrebbe voler salvare lo stato:  
  
-   Quando l'utente modifica posizione all'interno di una finestra o finestra di dialogo  
  
-   Quando l'utente trasferisce lo stato attivo a un'altra finestra  
  
-   Quando l'utente passa dalla progettazione alla modalità di debug  
  
-   Quando l'utente si disconnette il proprio account  
  
-   Quando il computer entra in ibernazione o arrestato  
  
-   Quando il disco rigido/computer sta per essere riformattato e configurare di nuovo  
  
### <a name="window-configurations"></a>Configurazioni di finestre  
 Una configurazione di finestre è la presentazione di base dell'ambiente di sviluppo: si tratta di un schema costituito l'elenco delle finestre degli strumenti presente e il modo in cui sono disposte. Per windows gestiti dall'IDE (windows IDE), le informazioni sul layout vengono resi persistenti per ogni utente, in modo che quando si avvia un utente dell'IDE, il layout di finestra viene visualizzato lo stesso come quando rimangono valide terminato Visual Studio. Lo stato e la posizione di windows dell'IDE viene mantenuto in un file di opzioni personalizzate in formato XML. Finestre degli strumenti che vengono create dai pacchetti caricati nell'IDE di rendere persistenti le informazioni sullo stato nel Registro di sistema e potrebbero o non sia per ogni utente.  
  
#### <a name="profile-specific-layouts"></a>Layout per il profilo  
 Ogni profilo includerà i layout delle finestre degli strumenti, organizzati in modo familiare agli utenti specifici degli sviluppatori (agli sviluppatori di Visual C++ prevedono di vedere le **Esplora soluzioni** sul lato sinistro dell'IDE, mentre gli sviluppatori c# prevedono di vedere la  **Esplora soluzioni** sulla destra). Layout delle finestre per il profilo vengono caricate dopo che l'utente sceglie un profilo di avvio. Un autore del pacchetto deve determinare il layout di finestra più adatto per l'esperienza dei clienti, sapendo che le modifiche apportate dall'utente per la configurazione della finestra quindi vengono rese persistenti.  
  
##  <a name="BKMK_TouchInput"></a> Input tocco  
 Gli utenti stanno utilizzando i prodotti di sviluppo Microsoft nei dispositivi di tocco. Tuttavia, esistono le barriere che rendono difficile usare gli strumenti di sviluppo nei dispositivi di tocco. Gli utenti si aspettano i prodotti per offrire un'esperienza touch affidabile e precisa. Lo scopo di queste linee guida è per guidare le decisioni sulle quali funzionalità di tocco di incorporare e per favorire un'esperienza touch coerente tra Visual Studio e i prodotti correlati.  
  
### <a name="levels-of-experience"></a>Livelli di esperienza  
 I seguenti livelli di esperienza sono utili per fungere da una Guida che consente ai team decide quali capacità del tocco per offrire in base al relativo livello desiderato di interesse di investimento in contatto.  
  
-   Il **esperienza di base** è per i team che vogliono fornire touch funzionalità in modo da non termina dei messaggi non recapitabili in tutto il proprio lavoro.  
  
-   Il **ottimizzato esperienza** è per i team che vogliono offrire più funzionalità di tocco comuni (ad esempio quelli disponibili in genere nelle applicazioni browser internet).  
  
-   Il **elevati esperienza** è per i team che vogliono aggiungere le funzionalità di questo tipo come movimenti o altre funzionalità facoltative che possono rendere le loro applicazioni touch-first descrittivo.  
  
||Esperienza di base|Esperienza ottimizzata|Esperienza con privilegi elevato|  
|-|----------------------|--------------------------|-------------------------|  
|Consente agli utenti di...|Correzione di codice e soluzione/progetto a livello di lettura senza strade|Eseguire attività di manutenzione, refactoring ed esplorazione|Operano in un'esperienza fluida, intuitiva e coerente in tutta sicurezza|  
|Editor|Panoramica tramite tocco e la selezione<br /><br /> Touch della barra di scorrimento a passare e premere e trascinare|Zoom con avvicinamento delle dita<br /><br /> Scorrimento rapido<br /><br /> Selection<br /><br /> Semplice utilizzo dei menu di scelta rapida||  
|Finestre degli strumenti superiore|La panoramica di elenco<br /><br /> Selezione di elementi<br /><br /> Touch della barra di scorrimento a passare e premere e trascinare|Selezione e lo scorrimento elemento semplice||  
|Windowing||Ridimensionare finestra<br /><br /> Barra di accesso rapido||  
|Documentare anche||Spostarti tra i file aperti||  
|Movimenti||I movimenti comuni il corretto funzionamento all'interno dell'IDE|Azioni in base al movimento<br /><br /> Supporto di trascinamento e rilascio e finestre di progettazione|  
|Altre considerazioni|||Tastiera su schermo personalizzata|  
  
#### <a name="gestures"></a>Movimenti  
 I movimenti di forniscono agli utenti un scelta rapida ai comandi che richiedono un'interazione più complicata. Vedere le linee guida di Windows nel [movimenti tocco comuni per le applicazioni Desktop](/windows/desktop/wintouch/windows-touch-gestures-overview)e seguire queste linee guida per la maggior parte dei movimenti, tra cui semplici movimenti, ad esempio mediante panoramica e zoom.