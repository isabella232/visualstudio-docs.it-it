---
title: Animations
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd51e99f59f22eb31252be2a41c3b3fb5e89f846
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077251"
---
# <a name="animations-for-visual-studio"></a>Animazioni per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Nozioni fondamentali di animazione

### <a name="animation-best-practices-in-visual-studio"></a>Procedure consigliate di animazione in Visual Studio
 Seguire queste regole per assicurare stili di animazione coerente e facile da usare in Visual Studio IDE.

- **In modo selettivo.** Limitare le animazioni a quelle che svolgono funzioni specifiche.

- **Velocità e tempi sono importanti** per garantire che le transizioni sono naturale e veloce:

    - Completare le transizioni animate entro mezzo secondo (500 millisecondi).

    - Le animazioni che si verificano spesso devono essere sufficientemente rapido che non interrompono del flusso di lavoro dell'utente.

    - Le animazioni non devono essere così rapida o jarring che è difficile da comprendere, ma non tanto lenta che rende uno impazienti per la transizione alla fine.

    - Usare la variabile temporizzazione per enfatizzare l'importanza. Ad esempio, quando si passa attraverso una sequenza di elementi in un diagramma classi, più veloci tramite le transizioni tra gli elementi quindi rallentare per concentrarsi sugli elementi importanti.

- **Usare l'interpolazione lineare graduale** da uno stato a altro, fornendo un senso di movimento tranquilla e naturale

- Quando possibile, **usare un'animazione con meno evidente al passaggio del mouse** per indicare elementi interattivi sotto il mouse.

- Se si basano sulle animazioni in funzionalità quindi **fornire un mezzo per disattivarli** in locale (per tutte le feature) come opzione nel **strumenti > Opzioni** finestra di dialogo.

- **Solo un'animazione deve essere eseguita in un momento** e lo trasmette solo una parte delle informazioni.

- **Accorgimento è importante.** Nella maggior parte dei casi animazione non ha l'attenzione utente richiesta per soddisfare lo scopo. Piccole modifiche nella temporizzazione, sequenza e il comportamento potrebbero influire in modo significativo sulla percezione e possono fare la differenza tra un'animazione efficace e inefficace.

- Quando si usa l'animazione per attirare l'attenzione su un valore, **assicurarsi che vale la pena di interrompere l'utente**di concentrazione.

- **Quando viene visualizzato lo stato di avanzamento o lo stato** tramite animazione:

    - Arrestare che mostra lo spostamento di stato di avanzamento durante il processo sottostante non viene raggiunto.

    - Distinguere i processi indeterminati da determinato per processi.

    - Assicurarsi che un'animazione abbia personali stati di completamento e non riuscite.

    - Riduci l'uso di animazioni di effetto che mostrano lo stato e assicurarsi che abbiano un valore reale, fornendo informazioni aggiuntive dell'utilizzo effettivo. Sono esempi le emergenze e modifiche allo stato temporaneo

#### <a name="do-not"></a>Non:

- Utilizzano i movimenti di piccole dimensioni (spostamento in un footprint ridotto), preferendo si dissolve e modifica tramite lo spostamento di oggetti.

- Usare le animazioni che si verificano su una vasta area della superficie sullo schermo. Indipendentemente dalle dimensioni, questo stile di animazione è fuorviante per l'utente.

- Usare le animazioni che non riguardano l'oggetto che utente è attualmente incentrato sulle o l'interazione con.

- Usare le animazioni che richiedono l'interazione dell'utente per reimpostare lo stato, ad esempio obbligando l'utente di rispondere a una notifica per renderlo di arrestare lampeggiare lampeggiante. L'interazione con essi in alcun modo dovrebbe essere sufficiente per non prenderli in considerazione.

  Per altre informazioni sulle applicazioni per le procedure consigliate, vedere [modelli di animazione](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Criteri di misurazione di animazione

- Il sistema deve reagire in modo visibile ai movimenti utente inferiore ai 10 millisecondi.

- Non richiede più di 500 millisecondi per completare le transizioni animate.

- È un modo per compensare le transizioni che richiedono tempi più lunghi per separarlo in due parti; la prima parte di un'animazione, ad esempio, potrebbe essere il contenitore di contenuto vuoto (fino a 500 millisecondi) seguito dal contenuto che si dissolve nel contenitore (fino a 500 millisecondi).

- Per tempi di caricamento che possono essere calcolate, è preferibile un indicatore di stato determinante (indicatore di stato percentuale-fine).

- Per tempi di caricamento che non possono essere calcolati, un indicatore di occupato, ad esempio un cursore o un'animazione di rotazione incorporato (durante il caricamento o all'indicatore di utilizzo) è appropriato.

### <a name="animation-as-communicator"></a>Animazione come communicator
 Nell'interfaccia utente di Visual Studio, animazione funge solo da uno strumento di comunicazione.  Viene usato per comunicare un'ampia gamma di informazioni, ad esempio modifiche strutturali nell'interfaccia utente; ad esempio, quando un menu si apre o chiude. Animazione può consentire di visualizzare il comportamento dipendente dal tempo di sistemi complessi, ad esempio visualizzazione stato di avanzamento installazione oppure essere utilizzata per attirare l'attenzione con avvisi e notifiche.

 Le animazioni dell'interfaccia utente in genere funzionano in quattro modi: visualizzare, attirare l'attenzione, simulare e indicare risposta volte/stato di avanzamento.

#### <a name="visualize"></a>Visualizzare
 Animazione può evidenziare la natura tridimensionale di oggetti e rendono più semplice per gli utenti visualizzare la relativa struttura spaziale. A tale scopo, l'animazione potrebbe necessario per ruotare l'oggetto in un cerchio completo, lenta disattivarla e viceversa, o portare l'oggetto più vicino e leggermente aumentarne le dimensioni per evidenziare il rollover o lo stato attivo.

 Anche se gli oggetti tridimensionali possono essere spostati con il controllo utente, la finestra di progettazione debba determinare in anticipo (a livello di codice o manualmente) come per il miglior animare uno spostamento che vengono fornite informazioni sugli ottimale dell'oggetto. Ciò programmato animazione può quindi essere attivato dall'utente posizionando il cursore sull'oggetto, mentre gli spostamenti controllata dall'utente richiedano all'utente di capire come modificare l'oggetto. Limitare lo spostamento a un singolo asse o un orientamento alla volta. la scalabilità, ruotare, o tradurre, ma non eseguire più di una contemporaneamente.

 La categoria Visualize include gli aspetti dei dati, relazioni, stato, struttura, sequenza e ora.

##### <a name="data"></a>Dati
 Vengono illustrate informazioni sulla variabile e complesse:

- Spostarsi all'interno di visualizzazioni di informazioni, ad esempio grafici e diagrammi

- L'esecuzione di istruzioni tramite una sequenza, tour guidato e paging

- Chiamare i dettagli, sta puntando e l'evidenziazione informazioni specifiche

- Sovrapporre i dettagli e informazioni aggiuntive su un elemento con lo stato attivo

- Morphing di una rappresentazione struttura o dell'organizzazione a altra

- Che rappresenta le modifiche nel tempo tramite dispositivi di scorrimento, i file Wheel scatto e shuttle e controlli di trasporto (play, stop e pause).

##### <a name="relationships"></a>Relazioni

- Viene illustrato come gli elementi sono correlati tra loro o gli elementi che si riferiscono a un determinato elemento.

- Mostrare le relazioni di gerarchie e padre-figlio o pari livello

- Un elemento genera un'altra

- Riduce al minimo un elemento a un altro elemento

- Un elemento con tethering a un altro

##### <a name="state"></a>Stato

- Aggiornamenti del contenuto.

- Selezione e lo stato attivo utente

- Stato

- Errori

##### <a name="structure"></a>Struttura

- La trasformazione tramite pivot in un nodo della struttura

- Il riorientamento

- Ridurre e ingrandire, o espandere e comprimere

##### <a name="sequence"></a>Sequence

- Sequenza di presentazione

- Capovolgimento tramite le immagini

##### <a name="time"></a>Ora

- Mostra modifiche nel tempo, intervallo di tempo e screencast

- Spostare da spostare nel Cestino, annullare e ripetere

- Ripristinare lo stato cronologico

#### <a name="attract-attention"></a>Attirare l'attenzione
 Se l'obiettivo è per attirare l'attenzione dell'utente a un singolo elemento all'esterno di diversi o per avvisare l'utente per informazioni aggiornate, quindi un'animazione può essere opportuno. Pagina di avvio delle applicazioni, ad esempio, potrebbe impiegare un pulsante di Guida introduttiva con scorrimento nella posizione corretta dopo il caricamento della pagina.

 Come regola, l'ultimo elemento di spostamento nella schermata attrae l'attenzione dell'utente.  In una serie di elementi animati, l'attenzione dell'utente seguirà l'ultimo oggetto mobile.

##### <a name="alert"></a>Avviso

- Avvisare l'utente, attenzione, indicano lo stato di avanzamento

- Mostra che un elemento viene eseguito correttamente o non correttamente o Mostra lo stato di avanzamento o modifiche di stato di avanzamento

- Richiedere agli utenti durante un'attività, ad esempio ricerca di ulteriori informazioni online o per ottenere informazioni sull'attività corrente

##### <a name="notifications"></a>Notifiche

- Avvisare l'utente su una condizione di errore

- Interrompono l'utente per vedere se desiderano allontanarsi

- Delicatamente informare l'utente che è stata completata o modificato, ad esempio quando un download viene completato un processo.

#### <a name="simulate"></a>Simulare
 In questa categoria sono physicality e dimensionalità.

- Illustrare da dove provengono gli oggetti o in cui accedono al

- Espandere e comprimere o aprire e chiudere

- La panoramica, lo scorrimento e pagina attiva

- Sovrapposizione e ordinamento z

- Sequenza video e accordion

- Capovolgimento e rotazione dell'interfaccia utente

#### <a name="response-and-progress-indicators"></a>Indicatori di risposta e lo stato di avanzamento
 Gli indicatori di stato sono due importanti vantaggi:

- Entrambi gli indicatori di stato indeterminato e determinato per rassicurare l'utente che il sistema non è arrestato e sta lavorando per il problema.

- Gli indicatori determinato per concedere all'utente che un senso di avanzamento dell'azione è in corso, nonché un sentimento di avvicinandosi alla data di fine.

## <a name="BKMK_AnimationPatterns"></a> Modelli di animazione

### <a name="overview"></a>Panoramica
 Le animazioni in Visual Studio sono concepite per fornire una funzione specifica e non ostacolare la produttività degli utenti. Caratteristiche di animazione generale da rispettare per includere:

- Piccola e non intrusivo

- Naturali e realistico

- Sottili e avvolta

- Veloci ed efficienti

- Tipo "relaxed", non accelera l'esecuzione

  La figura seguente mostra gli stili di animazione consigliati per l'uso in Visual Studio. Nessuna animazione e animazioni lievi, ad esempio la dissolvenza in entrata / dissolvenza sono utilizzati più di frequente. Applicazione limitata dello spostamento delle animazioni come espandere e comprimere, X e Y posizione modifica e la rotazione.

  ![Gli stili di animazione consigliati per Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 a_VSAnimStyles")

  **Stili di animazione consigliati per Visual Studio**

#### <a name="appear-and-disappear"></a>Vengono visualizzati e nascosti
 Con questo modello, un elemento passa da visibile a out-di-visualizzazione e viceversa senza un'animazione di transizione:

 ![Vengono visualizzati&#47;non vengono più visualizzati animazione in Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 b_AppearAndDisappear")

##### <a name="correct-usage"></a>Utilizzo corretto
 Elementi dell'interfaccia utente aggiornati che necessario immediatamente comparire o scomparire in modo che l'utente non è né abbagliato né dall'inquadratura. Inoltre, le animazioni di movimento lenta potrebbero essere percepite come un trascinamento delle prestazioni, che non viene eseguita con lo stile vengono visualizzati e scompaiono.

##### <a name="incorrect-usage"></a>Utilizzo non corretto
 Casi in cui dell'interfaccia utente viene visualizzato immediatamente che l'utente non avrà idea di cosa è successo e aggiunta di un'animazione potrebbe facilitare la comprensione del contesto.

##### <a name="animation-properties"></a>Proprietà di animazione
 L'intervallo di tempo è in genere zero secondi.

##### <a name="examples"></a>Esempi

- Finestre degli strumenti Nascondi automaticamente

- Attivato da tastiera editor dell'interfaccia utente, ad esempio IntelliSense e Guida per i parametri

- Aree di codice di espansione e compressione

#### <a name="fade-in-and-fade-out"></a>Dissolvenza in entrata e dissolvenza
 Con questo modello, la transizione di un elemento dell'interfaccia utente da (% 0 opacity) non è visibile a visibile (100% di opacità) o viceversa:

 ![Dissolvenza in entrata&#45;in&#47;dissolvenza in entrata&#45;out animazione in Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 c_FadeInFadeOut")

##### <a name="correct-usage"></a>Utilizzo corretto
 Animazione dell'interfaccia utente più comune è consigliato. È un effetto meno evidente che aggiunge interesse senza interrompere il flusso. In alcuni casi, l'utente potrebbe non anche tenere presente che è un'animazione e semplicemente percepisce un sistema di interfaccia utente fluida e propagazione.

##### <a name="animation-properties"></a>Proprietà di animazione

- Opacità di partenza: 0% per la dissolvenza, 100% di dissolvenza

- Opacità di fine: 100% per la dissolvenza, 0% per la dissolvenza

- Durata: versione autonoma di 200 millisecondi, quando usato come parte di una sequenza di animazione di combinazione di 100 millisecondi

- Stile di interpolazione: Seno InOut

##### <a name="examples"></a>Esempi

- Finestre degli strumenti Nascondi automaticamente

- Menu di aperto e chiusura

- Transizioni di scheda di sfondo e primo piano

#### <a name="color-blend-from-a-to-b"></a>Sfumatura di colore da A B
 Con questo modello, un elemento dell'interfaccia utente di modificare da colore A b:

 ![In Visual Studio animazione di miscele di colore](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 d_ColorBlend")

##### <a name="correct-usage"></a>Utilizzo corretto
 Una transizione animato quando un elemento dell'interfaccia utente cambia colore da un contesto o stato a altro.

##### <a name="animation-properties"></a>Proprietà di animazione

- Colore iniziale: Interfaccia utente specifico

- Colore finale: Interfaccia utente specifico

- Durata: versione autonoma di 200 millisecondi, quando usato come parte di una sequenza di animazione di combinazione di 100 millisecondi

- Stile di interpolazione: Seno InOut

##### <a name="examples"></a>Esempi

- Documentare le transizioni di stato di finestra (attivo, ultimo attive e inattive)

- Strumento transizioni di stato di finestra (con lo stato attivo e con stato non attivo)

#### <a name="expand-and-contract"></a>Espandere e comprimere
 Con questo modello, un elemento dell'interfaccia utente si espande in X, Y o entrambe le direzioni:

 ![Espandere&#47;contratto di animazione in Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 e_ExpandContract")

##### <a name="correct-usage"></a>Utilizzo corretto
 Una transizione animato quando un elemento dell'interfaccia utente cambia le dimensioni da un contesto a altro.

##### <a name="animation-properties"></a>Proprietà di animazione

- Scala x: % o una dimensione specifica, in pixel,

- Y scala: % o una dimensione specifica, in pixel,

- Posizione di ancoraggio: In genere superiore sinistro (per le lingue da sinistra a destra) o alto a destra (per le lingue da destra a sinistra)

- Durata: versione autonoma di 200 millisecondi, quando usato come parte di una sequenza di animazione di combinazione di 100 millisecondi

##### <a name="examples"></a>Esempi

- Pannello Esplora architettura espandere e comprimere

- Inizio pagina articoli espandere e comprimere

#### <a name="x-y-position-change"></a>Modifica di posizione X-Y
 Con questo modello, un elemento dell'interfaccia utente cambia la posizione X o Y o entrambi:

 ![X&#47;animazione in Visual Studio di modifica della posizione Y](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 f_XYPositionChange")

##### <a name="correct-usage"></a>Utilizzo corretto
 Una transizione animato quando un elemento dell'interfaccia utente cambia posizione da un contesto a altro.

##### <a name="animation-properties"></a>Proprietà di animazione

- Posizione di inizio X e Y: Interfaccia utente specifico

- Alla fine X e Y posizione: Interfaccia utente specifico

- Tracciato di movimento: nessuno

- Durata: versione autonoma di 200 millisecondi, quando usato come parte di una sequenza di animazione di combinazione di 100 millisecondi

- Stile di interpolazione: Seno InOut

##### <a name="example"></a>Esempio
 Il riordinamento della scheda

#### <a name="rotate"></a>Ruota
 Con questo modello consente di ruotare l'elemento dell'interfaccia utente:

 ![Animazione di rotazione in Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 g_Rotate")

##### <a name="correct-usage"></a>Utilizzo corretto
 Solo per l'indicatore di stato rotante indeterminato.

##### <a name="animation-properties"></a>Proprietà di animazione

- Gradi di rotazione: 360

- Centro di rotazione: Parte centrale dell'oggetto

- Durata: Continui

##### <a name="example"></a>Esempio
 Indicatore di stato indeterminato (rotazione)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Azioni dell'interfaccia utente della shell comuni e consigliate le animazioni

#### <a name="tab-open"></a>Scheda aperta

- Style: Vengono visualizzati

- Durata: Zero secondi

  ![Scheda animazione di apertura in Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 h_TabOpen")

#### <a name="tab-close"></a>Chiudi scheda

- Style: Modifica posizione X

- Durata: 200 millisecondi

  ![Scheda animazione di chiusura in Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 i_TabClose")

#### <a name="tab-reorder"></a>Riordinamento della scheda

- Style: Modifica posizione X

- Durata: 200 millisecondi

  ![Scheda animazione di riordinamento in Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 j_TabReorder")

#### <a name="close-floating-document"></a>Chiuso documento mobile

- Style: Vengono visualizzati

- Durata: 200 millisecondi

  ![Chiudi mobile animazione documenti in Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Transizione di stato finestra

- Style: Per coerenza con altre finestre, lasciare il sistema operativo corrente definiscono l'animazione di chiusura del documento.

- Durata: 200 millisecondi

  ![Animazione di transizione di stato di finestra in Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 l_WindowStateTransition")

#### <a name="menu-open"></a>Menu di scelta

- Style: Fade-in

- Durata: 200 millisecondi

  ![Animazione di apertura di menu in Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 m_MenuOpen")

#### <a name="menu-close"></a>Chiudi menu di scelta

- Style: Dissolvenza

- Durata: 200 millisecondi

  ![Animazione di chiusura dal menu in Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Nascondi automaticamente rivelare finestra degli strumenti

- Style: Vengono visualizzati

- Durata: Zero secondi

  ![Automatico&#45;Nascondi l'animazione della finestra degli strumenti in Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")
