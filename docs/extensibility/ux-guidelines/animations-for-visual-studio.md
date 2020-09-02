---
title: Animazioni per Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698612"
---
# <a name="animations-for-visual-studio"></a>Animazioni per Visual Studio
## <a name="animation-fundamentals"></a>Nozioni fondamentali sull'animazione

### <a name="animation-best-practices-in-visual-studio"></a>Procedure consigliate per l'animazione in Visual Studio
Seguire queste regole per garantire stili di animazione coerenti e intuitivi nell'IDE di Visual Studio.

- **Essere selettivi.** Limitare le animazioni a quelle che svolgono scopi specifici.

- La **tempistica e la velocità sono importanti** per garantire che le transizioni abbiano un aspetto rapido e naturale:

  - Completa le transizioni animate entro un mezzo secondo (500 millisecondi).

  - Le animazioni che si verificano spesso devono essere sufficientemente veloci da non interrompere il flusso di lavoro dell'utente. Controllare l'animazione in un ciclo e regolare l'intervallo fino a quando non si ritiene appropriato.

  - Le animazioni non devono essere così veloci o stonate perché è difficile da comprendere, ma non così lente che la transizione venga completata.

  - Usare la temporizzazione variabile per enfatizzare l'importanza. Ad esempio, quando si passa a una sequenza di elementi in un diagramma classi, la velocità tra le transizioni tra gli elementi viene rallentata per concentrarsi sugli elementi importanti.

- **Usare l'interpolazione graduale non lineare** da uno stato a un altro, garantendo un movimento calmo e naturale.

- Quando possibile, **usare un'animazione sottile al passaggio** del mouse per indicare gli elementi interattivi sotto il mouse.

- Se si fa affidamento sulle animazioni nelle funzionalità, **fornire un mezzo per** disattivarle localmente (per tutte le funzionalità) come opzione nella finestra di dialogo **strumenti > opzioni** .

- **Deve verificarsi una sola animazione alla volta** e fornire solo una informazione. Più di un oggetto che si sta muovendo o provando a comportare più elementi può creare confusione.

- **La sottigliezza è importante.** Nella maggior parte dei casi, non è necessario che l'animazione richieda l'attenzione dell'utente per soddisfare i propri scopi. Modifiche minime nell'intervallo di tempo, sequenziazione e comportamento possono influire in modo significativo sulla percezione e possono fare la differenza tra un'animazione efficace e inefficace.

- Quando si usa l'animazione per attirare l'attenzione su un elemento, **assicurarsi che valga la pena interrompere il**training dell'utente.

- **Quando si visualizza lo stato di avanzamento o lo stato** tramite l'animazione:

  - Arrestare la visualizzazione dello spostamento dello stato di avanzamento quando il processo sottostante non avanza.

  - Distinguere i processi indeterminati dai processi determinati.

  - Verificare che in un'animazione siano presenti stati di completamento e di errore identificabili.

  - Ridurre l'uso delle animazioni degli effetti che mostrano lo stato e assicurarsi che abbiano un valore reale fornendo informazioni aggiuntive sull'uso effettivo. Gli esempi includono modifiche e emergenze di stato temporanee

#### <a name="animation-donts"></a>Animazione non:

- Non usare piccoli movimenti (spostamento in un footprint ridotto). Preferisce dissolvenze e modifiche allo stato di avanzamento degli oggetti.

- Non usare animazioni che si svolgono in un'area di grandi dimensioni dello schermo. Indipendentemente dalle dimensioni, questo stile di animazione distrae l'utente.

- Non usare animazioni non correlate all'oggetto a cui l'utente è attualmente concentrato o che interagisce.

- Non usare animazioni che richiedono l'interazione dell'utente per reimpostare lo stato, ad esempio forzando l'utente a rispondere a una notifica lampeggiante per evitare il lampeggio. L'interazione con essi in qualsiasi modo dovrebbe essere sufficiente per ignorarli.

Per altre informazioni sulle applicazioni per queste procedure consigliate, vedere [modelli di animazione](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metriche di animazione

- Il sistema deve rispondere in modo invisibile ai movimenti utente in meno di 10 millisecondi.

- Per completare le transizioni animate non è necessario più di 500 millisecondi.

- Un modo per compensare le transizioni che richiedono tempi più lunghi consiste nel separarlo in due parti. Ad esempio, la prima parte di un'animazione potrebbe essere il contenitore di contenuto vuoto (fino a 500 millisecondi), seguito dal contenuto che si dissolve nel contenitore (fino a 500 millisecondi).

- Per i tempi di caricamento che possono essere calcolati, è preferibile un indicatore di stato determinante (indicatore di avanzamento percentuale).

- Per i tempi di caricamento che non possono essere calcolati, è opportuno un indicatore occupato come un cursore o un'animazione di rotazione incorporata (indicatore di caricamento o di lavoro).

### <a name="animation-as-communicator"></a>Animazione come Communicator
Nell'interfaccia utente di Visual Studio, l'animazione funziona solo come strumento di comunicazione.  Viene usato per comunicare una serie di informazioni, ad esempio modifiche strutturali nell'interfaccia utente, ad esempio quando un menu viene aperto o chiuso. L'animazione consente di visualizzare il comportamento dipendente dal tempo di sistemi complessi, ad esempio la visualizzazione dello stato di avanzamento dell'installazione. Le animazioni possono anche essere usate per attirare l'attenzione su avvisi e notifiche.

 Le animazioni dell'interfaccia utente in genere funzionano in quattro modi: visualizzare, attirare l'attenzione, simulare e tempi di risposta/indicatori di stato.

#### <a name="visualize"></a>Visualizzare
L'animazione può evidenziare la natura tridimensionale degli oggetti e semplificare la visualizzazione della struttura spaziale da parte degli utenti. Per ottenere questo risultato, è possibile che l'animazione debba ruotare l'oggetto in un cerchio completo, spostarlo lentamente avanti e indietro o avvicinare l'oggetto e aumentare leggermente le dimensioni per evidenziare il rollover o lo stato attivo.

Anche se gli oggetti tridimensionali possono essere spostati con il controllo utente, la finestra di progettazione deve determinare in anticipo (a livello di codice o manualmente) come applicare un'animazione migliore a un movimento che fornisce una comprensione ottimale dell'oggetto. Questa animazione programmata può quindi essere attivata dall'utente posizionando il cursore sull'oggetto, mentre per i movimenti controllati dall'utente è necessario che l'utente possa comprendere come modificare l'oggetto. Limitare lo spostamento a un singolo asse o orientamento alla volta; ridimensionare, ruotare o tradurre, ma non eseguire più di una simultaneamente.

La categoria Visualizza include gli aspetti di dati, relazioni, stato, struttura, sequenza e tempo.

##### <a name="data"></a>Dati
Illustrare le informazioni complesse e variabili:

- Spostarsi tra visualizzazioni di informazioni come grafici e grafici

- Esecuzione di una sequenza, presentazione guidata e paging

- Richiamo di dettagli, puntamento ed evidenziazione di informazioni specifiche

- Sovrapposizione di dettagli e informazioni aggiuntive sulla parte superiore di un elemento con stato attivo

- Morphing da una rappresentazione strutturale o organizzativa a un'altra

- Rappresentazione delle modifiche nel tempo mediante i dispositivi di scorrimento del tempo, le ruote jog-and-Shuttle e i controlli di trasporto (riproduzione, arresto e sospensione)

##### <a name="relationships"></a>Relazioni

- Illustrare il modo in cui gli elementi sono correlati tra loro o quali elementi sono correlati a un determinato elemento

- Mostra gerarchie e relazioni padre-figlio o di pari livello

- Un elemento genera un altro elemento

- Un elemento viene ridotto a un altro elemento

- Un elemento legato a un altro

##### <a name="state"></a>State

- Aggiornamenti del contenuto

- Stato attivo e selezione utente

- Avanzamento

- Errors

##### <a name="structure"></a>Struttura

- Pivot della struttura in un nodo

- Riorientare

- Riduci a icona e Ingrandisci, Espandi e Comprimi

##### <a name="sequence"></a>Sequenza

- Sequenza di slideshow

- Capovolgimento di immagini

##### <a name="time"></a>Ora

- Mostra modifica nel tempo, intervallo di tempo e screencast

- Passa a cestino, Annulla e Ripeti

- Ripristina stato cronologico

#### <a name="attract-attention"></a>Attirare l'attenzione
Se l'obiettivo è quello di attirare l'attenzione dell'utente su un singolo elemento da più o di avvisare l'utente di aggiornare le informazioni, un'animazione potrebbe essere appropriata. La pagina iniziale dell'applicazione, ad esempio, potrebbe usare un pulsante Introduzione che scorre in posizione dopo il caricamento della pagina.

Come regola, l'ultimo elemento spostato sullo schermo attira l'attenzione dell'utente.  In una serie di elementi animati, l'attenzione dell'utente seguirà l'ultimo oggetto in cui viene spostato.

##### <a name="alert"></a>Avviso

- Avvisa l'utente, fai attenzione, Mostra lo stato di avanzamento

- Indica che un elemento viene eseguito correttamente o in modo errato oppure Mostra le modifiche dello stato o dello stato di avanzamento

- Richiedi agli utenti durante un'attività, ad esempio la ricerca di altre informazioni online o l'apprendimento dell'attività corrente

##### <a name="notifications"></a>Notifiche

- Avvisare l'utente di una condizione di errore

- Interrompi l'utente per vedere se desiderano partecipare ad altri elementi

- Informare l'utente che il processo è stato completato o modificato, ad esempio al termine di un download.

#### <a name="simulate"></a>Simulate
Questa categoria copre la fisicità e la dimensionalità.

- Illustrare la provenienza degli oggetti o il percorso in cui passano

- Espandi e Comprimi o Apri e Chiudi

- Panoramica, scorrimento e curva di pagina

- Ordinamento in pila e z

- Carosello e Accordion

- Capovolgimento e rotazione dell'interfaccia utente

#### <a name="response-and-progress-indicators"></a>Indicatori di stato e risposta
Gli indicatori di stato presentano un paio di vantaggi significativi:

- Gli indicatori di stato sia determinati che indeterminati rassicurano l'utente che il sistema non si è arrestato in modo anomalo e sta lavorando al problema.

- Gli indicatori determinati consentono all'utente di comprendere il livello di avanzamento dell'azione, oltre a una sensazione di avvicinarsi alla fine.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Modelli di animazione

### <a name="overview"></a>Panoramica
Le animazioni in Visual Studio sono destinate a svolgere una funzione specifica senza ostacolare la produttività degli utenti. In genere, le animazioni in Visual Studio devono essere:

- Piccolo e non intrusivo

- Naturale e realistico

- Sottile e sommesso

- Veloce ed efficiente

- Rilassato, non frettoloso

Questa illustrazione Mostra gli stili di animazione consigliati per Visual Studio. Non viene usata più di frequente alcuna animazione o animazioni impercettibili come dissolvenza in entrata/dissolvenza in uscita. È disponibile un'applicazione limitata di animazioni di spostamento come Expand e contract, la modifica della posizione X e Y e la rotazione.

![Stili di animazione consigliati per Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Stili di animazione consigliati per Visual Studio

#### <a name="appear-and-disappear"></a>Visualizzazione e scomparsa
Con questo modello, un elemento passa da visibile a out-of-View e viceversa senza un'animazione di transizione.

![Visualizza e scompare animazione](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Visualizza e scompare animazione

##### <a name="correct-usage"></a>Corretto utilizzo
Nuovi elementi dell'interfaccia utente che devono apparire o scomparire immediatamente, in modo che l'utente non sia distratto né ostruito. Inoltre, le animazioni a spostamenti rallentati potrebbero essere percepite come un trascinamento delle prestazioni, che non si verificherà con lo stile visualizzato e scomparire.

##### <a name="incorrect-usage"></a>Utilizzo non corretto
I casi in cui l'interfaccia utente viene visualizzata in modo improvviso, l'utente non ha idea di cosa è successo e l'aggiunta di un'animazione contribuirebbe alla comprensione contestuale.

##### <a name="animation-properties"></a>Proprietà animazione
Il ritardo di tempo è in genere pari a zero secondi.

##### <a name="examples"></a>Esempi
- Finestre degli strumenti Nascondi automaticamente

- Interfaccia utente dell'editor attivata da tastiera, ad esempio IntelliSense e guida ai parametri

- Espandere e comprimere le aree di codice

#### <a name="fade-in-and-fade-out"></a>Dissolvenza e dissolvenza
Con questo modello, un elemento dell'interfaccia utente esegue la transizione da non visibile (0% opacità) a visibile (100% di opacità) o viceversa.

![Animazione di dissolvenza e dissolvenza](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animazione di dissolvenza e dissolvenza

##### <a name="correct-usage"></a>Corretto utilizzo
Si tratta dell'animazione dell'interfaccia utente più comunemente consigliata. Si tratta di un effetto sottile che aggiunge interesse senza interrompere il flusso. In alcuni casi, l'utente potrebbe non rendersi conto che è presente un'animazione, percependo un sistema di interfaccia utente uniforme e propagante.

##### <a name="animation-properties"></a>Proprietà animazione

- Opacità iniziale: 0% per la dissolvenza, 100% per la dissolvenza in uscita

- Opacità finale: 100% per la dissolvenza, 0% per la dissolvenza in uscita

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

- Stile di interpolazione: seno InOut

##### <a name="examples"></a>Esempi

- Finestre degli strumenti Nascondi automaticamente

- Menu di apertura e chiusura

- Transizioni di tabulazioni in background e in primo piano

#### <a name="color-blend-from-a-to-b"></a>Blend dei colori da a a B
Con questo modello, un elemento dell'interfaccia utente cambia dal colore A al colore B.

![Animazione di Blend di colori](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animazione di Blend di colori

##### <a name="correct-usage"></a>Corretto utilizzo
Come transizione animata quando un elemento dell'interfaccia utente cambia colore da un contesto o uno stato a un altro.

##### <a name="animation-properties"></a>Proprietà animazione

- Colore iniziale: specifico dell'interfaccia utente

- Colore finale: specifico dell'interfaccia utente

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

- Stile di interpolazione: seno InOut

##### <a name="examples"></a>Esempi

- Transizioni di stato della finestra del documento (attivo, ultimo attivo e inattivo)

- Transizioni di stato della finestra degli strumenti (con stato attivo e non attivo)

#### <a name="expand-and-contract"></a>Espandi e contra
Con questo modello, un elemento dell'interfaccia utente si espande in X, Y o in entrambe le direzioni.

![Espandi e Comprimi animazione](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Espandi e Comprimi animazione

##### <a name="correct-usage"></a>Corretto utilizzo
Come transizione animata quando un elemento dell'interfaccia utente cambia dimensione da un contesto a un altro.

##### <a name="animation-properties"></a>Proprietà animazione

- Scala X:% o dimensione specifica (in pixel)

- Scala Y:% o dimensione specifica (in pixel)

- Posizione di ancoraggio: generalmente superiore sinistro (per le lingue da sinistra a destra) o superiore destro (per le lingue da destra a sinistra)

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

##### <a name="examples"></a>Esempi

- Espandere e comprimere il pannello Esplora architettura

- Espansione e compressione dell'elemento della pagina iniziale di Visual Studio 2017

#### <a name="x-y-position-change"></a>Modifica della posizione X-Y
Con questo modello, un elemento dell'interfaccia utente modifica la posizione X o Y o entrambi.

![Animazione di modifica della posizione X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animazione di modifica della posizione X-Y

##### <a name="correct-usage"></a>Corretto utilizzo
Come transizione animata quando un elemento dell'interfaccia utente cambia posizione da un contesto a un altro.

##### <a name="animation-properties"></a>Proprietà animazione

- Posizione X e Y iniziale: specifica dell'interfaccia utente

- Posizione X e Y finale: specifica dell'interfaccia utente

- Percorso movimento: nessuno

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

- Stile di interpolazione: seno InOut

##### <a name="example"></a>Esempio
Riordino tabulazione

#### <a name="rotate"></a>Ruota
Con questo modello, l'elemento dell'interfaccia utente ruota.

![Animazione rotazione elementi dell'interfaccia utente](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animazione rotazione elementi dell'interfaccia utente

##### <a name="correct-usage"></a>Corretto utilizzo
Solo per l'indicatore di avanzamento della rotazione indeterminato.

##### <a name="animation-properties"></a>Proprietà animazione

- Grado di rotazione: 360

- Centro rotazione: al centro dell'oggetto

- Durata: continua

##### <a name="example"></a>Esempio
Indicatore di stato indeterminato (rotazione)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Azioni comuni dell'interfaccia utente della shell e animazioni consigliate

#### <a name="tab-open"></a>Scheda aperta
![Animazione di apertura scheda](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animazione di apertura scheda

- Stile: visualizzato

- Durata: zero secondi

#### <a name="tab-close"></a>Chiusura tabulazione
![Animazione di chiusura scheda](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animazione di chiusura scheda

- Stile: modifica della posizione X

- Durata: 200 millisecondi

#### <a name="tab-reorder"></a>Riordino tabulazione
![Animazione di riordinamento della scheda in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animazione riordino tabulazione

- Stile: modifica della posizione X

- Durata: 200 millisecondi

#### <a name="close-floating-document"></a>Chiudi documento mobile
![Animazione di chiusura del documento mobile](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Animazione di chiusura del documento mobile

- Stile: visualizzato

- Durata: 200 millisecondi

#### <a name="window-state-transition"></a>Transizione dello stato della finestra
![Animazione della transizione dello stato della finestra](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animazione della transizione dello stato della finestra

- Stile: per essere coerente con altre finestre, consentire al sistema operativo corrente di definire l'animazione di chiusura del documento.

- Durata: 200 millisecondi

#### <a name="menu-open"></a>Menu aperto
![Animazione di apertura menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animazione di apertura menu

- Stile: dissolvenza in entrata

- Durata: 200 millisecondi

#### <a name="menu-close"></a>Chiudi menu
![Animazione di chiusura menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animazione di chiusura menu

- Stile: dissolvenza in uscita

- Durata: 200 millisecondi

#### <a name="auto-hide-tool-window-reveal"></a>Nascondi automaticamente la finestra degli strumenti
![Animazione per la finestra degli strumenti Nascondi automaticamente](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Animazione per la finestra degli strumenti Nascondi automaticamente

- Stile: visualizzato

- Durata: zero secondi
