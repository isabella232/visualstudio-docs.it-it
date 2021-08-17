---
title: Animazioni per Visual Studio | Microsoft Docs
description: Informazioni sulle regole che consentono di garantire stili di animazione coerenti e descrittivi nell Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 933856cffcf7a012be7d9774b3d703aa92e335fb5d7939d804ef49043875f1a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388396"
---
# <a name="animations-for-visual-studio"></a>Animazioni per Visual Studio
## <a name="animation-fundamentals"></a>Nozioni fondamentali sulle animazioni

### <a name="animation-best-practices-in-visual-studio"></a>Procedure consigliate per l'animazione in Visual Studio
Seguire queste regole per garantire stili di animazione coerenti e descrittivi nell Visual Studio IDE.

- **Essere selettivi.** Limitare le animazioni a quelle che servono a scopi specifici.

- **La tempistica e la velocità sono** importanti per garantire che le transizioni siano rapide e naturali:

  - Completare le transizioni animate entro mezzo secondo (500 millisecondi).

  - Le animazioni che si verificano di frequente devono essere sufficientemente rapide da non interrompere il flusso di lavoro dell'utente. Osservare l'animazione in un ciclo e regolare l'intervallo fino a quando non sembra a destra.

  - Le animazioni non devono essere così veloci o insoddisfacenti da risultare difficili da comprendere, ma non così lente da rendere l'utente insoddisfacente per il completamento della transizione.

  - Usare la temporizzazione variabile per evidenziare l'importanza. Ad esempio, quando si esplora una sequenza di elementi in un diagramma classi, velocizzare le transizioni tra gli elementi e quindi rallentare per concentrarsi sugli elementi importanti.

- **Usare l'interpolazione graduale non lineare** da uno stato a un altro, dando un senso di movimento naturale e originale.

- Quando possibile, **usare un'animazione sottile al passaggio del** mouse per indicare elementi interattivi sotto il mouse.

- Se si fa affidamento sulle animazioni  nelle funzionalità, specificare un modo per disattivarle in locale (per tutte le funzionalità) come opzione nella finestra di dialogo Strumenti **> opzioni.**

- **Deve verificarsi una sola animazione alla volta** e comunicare solo un'informazione. Più di un oggetto che si sposta o tenta di comunicare più elementi può generare confusione.

- **La sottigliezza è importante.** Nella maggior parte dei casi, l'animazione non deve richiedere l'attenzione dell'utente per svolgere il proprio scopo. Le piccole modifiche di temporizzazione, sequenziazione e comportamento possono influire in modo significativo sulla percezione e possono fare la differenza tra un'animazione efficace e inefficace.

- Quando si usa l'animazione per attirare **l'attenzione** su un elemento, assicurarsi che valga la pena interrompere il modo di pensare dell'utente.

- **Quando si visualizza lo stato o lo stato tramite** l'animazione:

  - Interrompere la visualizzazione dello spostamento dello stato quando il processo sottostante non avanza.

  - Distinguere i processi indeterminati dai processi determinati.

  - Assicurarsi che un'animazione abbia stati di completamento e di errore identificabili.

  - Ridurre al minimo l'uso delle animazioni degli effetti che mostrano lo stato e assicurarsi che siano di valore reale fornendo informazioni aggiuntive sull'uso effettivo. Alcuni esempi includono le modifiche dello stato temporaneo e le emergenze

#### <a name="animation-donts"></a>L'animazione non ha effetto:

- Non usare movimenti di piccole dimensioni (movimento in un footprint ridotto). Preferisce dissolvenze e modifiche rispetto agli oggetti in movimento.

- Non usare animazioni che si svolgono su un'ampia area di spazio sullo schermo. Indipendentemente dalle dimensioni, questo stile di animazione distrae l'utente.

- Non usare animazioni non correlate all'oggetto su cui l'utente è attualmente attivo o con cui interagisce.

- Non usare animazioni che richiedono l'interazione dell'utente per reimpostare lo stato, ad esempio forzando l'utente a rispondere a una notifica flash per arrestare il lampeggiamento. Interagire con essi in qualsiasi modo dovrebbe essere sufficiente per ignorarli.

Per altre informazioni sulle applicazioni per queste procedure consigliate, vedere Modelli [di animazione.](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)

### <a name="animation-metrics"></a>Metriche di animazione

- Il sistema deve reagire in modo visibile ai movimenti dell'utente in meno di 10 millisecondi.

- Il completamento delle transizioni animate non deve richiedere più di 500 millisecondi.

- Un modo per compensare le transizioni che richiedono tempi più lunghi è separarlo in due parti. Ad esempio, la prima parte di un'animazione potrebbe essere il contenitore di contenuto vuoto (fino a 500 millisecondi), seguito dal contenuto che si dissolve nel contenitore (fino a 500 millisecondi).

- Per i tempi di caricamento che possono essere calcolati, è preferibile un indicatore di stato determinante (indicatore di avanzamento percentuale completata).

- Per i tempi di caricamento che non possono essere calcolati, è appropriato un indicatore occupato come un cursore o un'animazione di rotazione incorporata (caricamento o indicatore di lavoro).

### <a name="animation-as-communicator"></a>Animazione come icona
Nell Visual Studio interfaccia utente, l'animazione funziona solo come strumento di comunicazione.  Viene usato per comunicare un'ampia gamma di informazioni, ad esempio modifiche strutturali nell'interfaccia utente, ad esempio quando un menu si apre o si chiude. L'animazione consente di visualizzare il comportamento dipendente dal tempo di sistemi complessi, ad esempio la visualizzazione dello stato di avanzamento dell'installazione. Le animazioni possono essere usate anche per attirare l'attenzione con avvisi e notifiche.

 Le animazioni dell'interfaccia utente in genere funzionano in quattro modi: visualizzare, attirare l'attenzione, simulare e rispondere a indicatori di stato/tempi di risposta.

#### <a name="visualize"></a>Visualizzare
L'animazione può evidenziare la natura tridimensionale degli oggetti e semplificare la visualizzazione della struttura spaziale da parte degli utenti. A tale scopo, l'animazione potrebbe dover ruotare l'oggetto in un cerchio completo, ruotarlo lentamente avanti e indietro o avvicinare l'oggetto e aumentarne leggermente le dimensioni per evidenziare il rollover o lo stato attivo.

Anche se gli oggetti tridimensionali possono essere spostati con il controllo utente, la finestra di progettazione deve determinare in anticipo (a livello di codice o manualmente) come animare al meglio un movimento che fornisce una comprensione ottimale dell'oggetto. Questa animazione programmata può quindi essere attivata dall'utente posizionando il cursore sull'oggetto, mentre i movimenti controllati dall'utente richiedono all'utente di comprendere come modificare l'oggetto. Limitare lo spostamento a un singolo asse o orientamento alla volta; ridimensionare, ruotare o traslare, ma non eseguire più di una operazione simultaneamente.

La categoria Visualizza include gli aspetti dei dati, delle relazioni, dello stato, della struttura, della sequenza e del tempo.

##### <a name="data"></a>Dati
Illustrare informazioni complesse e variabili:

- Spostamento tra visualizzazioni di informazioni come grafici e grafici

- Esecuzione di una sequenza, presentazione guidata e suddivisione in pagine

- Visualizzazione di dettagli, puntamento ed evidenziazione di informazioni specifiche

- Sovrapposizione di dettagli e informazioni aggiuntive sopra un elemento con stato attivo

- Morphing da una rappresentazione strutturale o organizzativa a un'altra

- Rappresentazione delle modifiche nel tempo tramite dispositivi di scorrimento del tempo, rotelle di scorrimento e rotelle e controlli di trasporto (riproduzione, arresto e pausa)

##### <a name="relationships"></a>Relazioni

- Illustrare in che modo gli elementi sono correlati tra loro o quali elementi sono correlati a un determinato elemento

- Mostra gerarchie e relazioni padre-figlio o di pari livello

- Un elemento genera un altro elemento

- Un elemento viene ridotto a icona a un altro elemento

- Un elemento con tethering a un altro

##### <a name="state"></a>State

- Aggiornamenti del contenuto

- Stato attivo e selezione dell'utente

- Avanzamento

- Errors

##### <a name="structure"></a>Struttura

- Pivot della struttura in un nodo

- Riorientamento

- Ridurre a icona e ingrandire o espandere e comprimere

##### <a name="sequence"></a>Sequenza

- Sequenza presentazione

- Scorrimento delle immagini

##### <a name="time"></a>Ora

- Mostra variazione nel tempo, intervallo di tempo e screencast

- Sposta nel Cestino, annulla e ripeti

- Ripristinare lo stato cronologico

#### <a name="attract-attention"></a>Attirare l'attenzione
Se l'obiettivo è quello di attirare l'attenzione dell'utente su un singolo elemento da diversi elementi o di avvisare l'utente di informazioni aggiornate, potrebbe essere appropriata un'animazione. Ad esempio, la pagina iniziale dell'applicazione potrebbe usare un pulsante Attività iniziali che scorre sul posto dopo il caricamento della pagina.

Di norma, l'ultimo elemento in movimento sullo schermo attrae l'attenzione dell'utente.  In una serie di elementi animati, l'attenzione dell'utente seguirà l'ultimo oggetto in movimento.

##### <a name="alert"></a>Avviso

- Avvisare l'utente, ottenere attenzione, mostrare lo stato di avanzamento

- Mostrare che un'operazione viene eseguita correttamente o in modo errato oppure mostrare lo stato di avanzamento o le modifiche dello stato

- Richiedere agli utenti durante un'attività, ad esempio trovare altre informazioni online o imparare a conoscere l'attività corrente

##### <a name="notifications"></a>Notifiche

- Avvisare l'utente di una condizione di errore

- Interrompi l'utente per verificare se vuole partecipare a un'altra attività

- Gli utenti che hanno eseguito un processo sono stati completati o modificati, ad esempio al termine di un download.

#### <a name="simulate"></a>Simulate
Questa categoria copre la fisicità e la dimensionalità.

- Illustrare da dove provengono gli oggetti o da dove vengono visitati

- Espandere e comprimere o aprire e chiudere

- Panoramica, scorrimento e turni di pagina

- Impilamento e ordinamento z

- Carousel e accordion

- Capovolgimento e rotazione dell'interfaccia utente

#### <a name="response-and-progress-indicators"></a>Indicatori di risposta e di stato
Gli indicatori di stato presentano due vantaggi importanti:

- Sia gli indicatori di stato determinati che indeterminati assicurano all'utente che il sistema non si è arrestato in modo anomalo e sta lavorando al problema.

- Gli indicatori determinati offrono all'utente un'idea dell'avanzamento dell'azione, nonché la impressione di avvicinarsi al completamento.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Modelli di animazione

### <a name="overview"></a>Panoramica
Le animazioni in Visual Studio servono a una funzione specifica senza ostacolare la produttività degli utenti. In genere, le animazioni in Visual Studio devono essere:

- Piccole e discrete

- Naturale e realistico

- Sottile e sottodominio

- Veloce ed efficiente

- Relaxed, not hurried

Questa illustrazione mostra gli stili di animazione consigliati per Visual Studio. Nessuna animazione o animazioni sottiglie, ad esempio dissolvenza in entrata/uscita, sono le più usate. È disponibile un'applicazione limitata di animazioni di spostamento, ad esempio espansione e contratto, modifica della posizione X e Y e rotazione.

![Stili di animazione consigliati per Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Stili di animazione consigliati per Visual Studio

#### <a name="appear-and-disappear"></a>Apparire e scomparire
Con questo modello, un elemento passa da visibile a non visibile e indietro senza un'animazione di transizione.

![Animazione di visualizzazione e sparire](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animazione di visualizzazione e sparire

##### <a name="correct-usage"></a>Uso corretto
Nuovi elementi dell'interfaccia utente che devono apparire o scomparire immediatamente in modo che l'utente non sia distratto né ostruito. Inoltre, le animazioni lente potrebbero essere percepite come un trascinamento delle prestazioni, che non si verifica con lo stile di visualizzazione e di scomparsa.

##### <a name="incorrect-usage"></a>Utilizzo non corretto
Nei casi in cui l'interfaccia utente viene visualizzata così improvvisamente, l'utente non ha idea di cosa sia successo e l'aggiunta di un'animazione può essere utile per comprendere il contesto.

##### <a name="animation-properties"></a>Proprietà dell'animazione
Il ritardo è in genere pari a zero secondi.

##### <a name="examples"></a>Esempio
- Nascondi automaticamente le finestre degli strumenti

- Interfaccia utente dell'editor attivata tramite tastiera, ad esempio IntelliSense e guida per i parametri

- Espandere e comprimere aree di codice

#### <a name="fade-in-and-fade-out"></a>Dissolvenza in entrata e in uscita
Con questo modello, un elemento dell'interfaccia utente passa da non visibile (opacità 0%) a visibile (opacità del 100%) o viceversa.

![Animazione con dissolvenza in entrata e in uscita](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animazione con dissolvenza in entrata e in uscita

##### <a name="correct-usage"></a>Uso corretto
Questa è l'animazione dell'interfaccia utente più comunemente consigliata. Si tratta di un effetto sottile che aggiunge interesse senza interrompere il flusso. In alcuni casi, l'utente potrebbe non rendersi nemmeno conto che è presente un'animazione, percependo un sistema di interfaccia utente uniforme e scorrevole.

##### <a name="animation-properties"></a>Proprietà dell'animazione

- Opacità iniziale: 0% per la dissolvenza in entrata, 100% per la dissolvenza in uscita

- Opacità finale: 100% per la dissolvenza in entrata, 0% per la dissolvenza in uscita

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

- Stile di semplificazione: Sine InOut

##### <a name="examples"></a>Esempio

- Nascondi automaticamente le finestre degli strumenti

- Menu aperto e chiuso

- Transizioni di schede in primo piano e di sfondo

#### <a name="color-blend-from-a-to-b"></a>Combinazione di colori da A a B
Con questo modello, un elemento dell'interfaccia utente cambia dal colore A al colore B.

![Animazione della combinazione di colori](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animazione della combinazione di colori

##### <a name="correct-usage"></a>Uso corretto
Come transizione animata quando un elemento dell'interfaccia utente cambia colore da un contesto o uno stato a un altro.

##### <a name="animation-properties"></a>Proprietà dell'animazione

- Colore iniziale: specifico dell'interfaccia utente

- Colore finale: specifico dell'interfaccia utente

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

- Stile di semplificazione: Sine InOut

##### <a name="examples"></a>Esempio

- Transizioni di stato della finestra del documento (attive, ultime attive e inattive)

- Transizioni di stato della finestra degli strumenti (con stato attivo e con stato non attivo)

#### <a name="expand-and-contract"></a>Espandere e contrarsi
Con questo modello, un elemento dell'interfaccia utente si espande in X, Y o in entrambe le direzioni.

![Espandere e comprimere l'animazione](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Espandere e comprimere l'animazione

##### <a name="correct-usage"></a>Uso corretto
Come transizione animata quando le dimensioni di un elemento dell'interfaccia utente cambiano da un contesto a un altro.

##### <a name="animation-properties"></a>Proprietà dell'animazione

- Scala X: % o dimensione specifica (in pixel)

- Scala Y: % o dimensione specifica (in pixel)

- Posizione di ancoraggio: in genere in alto a sinistra (per le lingue da sinistra a destra) o in alto a destra (per le lingue da destra a sinistra)

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

##### <a name="examples"></a>Esempio

- Espandere e comprimere il pannello Esplora architetture

- Visual Studio pagina iniziale di 2017 espandere e comprimere

#### <a name="x-y-position-change"></a>Modifica della posizione X-Y
Con questo modello, un elemento dell'interfaccia utente modifica la posizione X o Y o entrambi.

![Animazione di modifica della posizione X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animazione di modifica della posizione X-Y

##### <a name="correct-usage"></a>Uso corretto
Come transizione animata quando un elemento dell'interfaccia utente cambia posizione da un contesto a un altro.

##### <a name="animation-properties"></a>Proprietà dell'animazione

- Posizione X e Y iniziale: specifica dell'interfaccia utente

- Posizione X e Y finali: specifica dell'interfaccia utente

- Percorso di movimento: nessuno

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

- Stile di semplificazione: Sine InOut

##### <a name="example"></a>Esempio
Riordinamento delle schede

#### <a name="rotate"></a>Ruota
Con questo modello, l'elemento dell'interfaccia utente ruota.

![Animazione di rotazione degli elementi dell'interfaccia utente](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animazione di rotazione degli elementi dell'interfaccia utente

##### <a name="correct-usage"></a>Uso corretto
Solo per l'indicatore di stato di rotazione indeterminato.

##### <a name="animation-properties"></a>Proprietà dell'animazione

- Grado di rotazione: 360

- Centro di rotazione: al centro dell'oggetto

- Durata: continuo

##### <a name="example"></a>Esempio
Indicatore di stato indeterminato (rotazione)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Azioni comuni dell'interfaccia utente della shell e animazioni consigliate

#### <a name="tab-open"></a>Scheda aperta
![Animazione per l'apertura di schede](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animazione per l'apertura di schede

- Stile: vengono visualizzati

- Durata: zero secondi

#### <a name="tab-close"></a>Chiusura della scheda
![Animazione di chiusura della scheda](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animazione di chiusura della scheda

- Stile: modifica della posizione X

- Durata: 200 millisecondi

#### <a name="tab-reorder"></a>Riordino delle schede
![Animazione di riordinamento della scheda in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animazione di riordinamento delle schede

- Stile: modifica della posizione X

- Durata: 200 millisecondi

#### <a name="close-floating-document"></a>Chiudere il documento mobile
![Animazione chiudi documento mobile](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Animazione chiudi documento mobile

- Stile: vengono visualizzati

- Durata: 200 millisecondi

#### <a name="window-state-transition"></a>Transizione dello stato della finestra
![Animazione della transizione dello stato della finestra](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animazione della transizione dello stato della finestra

- Stile: per coerenza con altre finestre, consentire al sistema operativo corrente di definire l'animazione di chiusura del documento.

- Durata: 200 millisecondi

#### <a name="menu-open"></a>Menu aperto
![Animazione di apertura menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animazione di apertura menu

- Stile: dissolvenza in entrata

- Durata: 200 millisecondi

#### <a name="menu-close"></a>Chiusura del menu
![Animazione di chiusura menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animazione di chiusura menu

- Stile: dissolvenza in uscita

- Durata: 200 millisecondi

#### <a name="auto-hide-tool-window-reveal"></a>Visualizzazione della finestra degli strumenti nascondi automaticamente
![Animazione di visualizzazione della finestra degli strumenti Nascondi automaticamente](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Animazione di visualizzazione della finestra degli strumenti Nascondi automaticamente

- Stile: vengono visualizzati

- Durata: zero secondi
