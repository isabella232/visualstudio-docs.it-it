---
title: Animazioni
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825362"
---
# <a name="animations-for-visual-studio"></a>Animazioni per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Nozioni fondamentali sull'animazione

### <a name="animation-best-practices-in-visual-studio"></a>Procedure consigliate per l'animazione in Visual Studio
 Seguire queste regole per garantire stili di animazione coerenti e intuitivi nell'IDE di Visual Studio.

- **Essere selettivi.** Limitare le animazioni a quelle che svolgono scopi specifici.

- La **tempistica e la velocità sono importanti** per garantire che le transizioni abbiano un aspetto rapido e naturale:

  - Completa le transizioni animate entro un mezzo secondo (500 millisecondi).

  - Le animazioni che si verificano spesso devono essere sufficientemente veloci da non interrompere il flusso di lavoro dell'utente.

  - Le animazioni non devono essere così veloci o stonate perché è difficile da comprendere, ma non così lente che la transizione venga completata.

  - Usare la temporizzazione variabile per enfatizzare l'importanza. Ad esempio, quando si passa a una sequenza di elementi in un diagramma classi, la velocità tra le transizioni tra gli elementi viene rallentata per concentrarsi sugli elementi importanti.

- **Usare l'interpolazione graduale non lineare** da uno stato a un altro, garantendo un movimento calmo e naturale

- Quando possibile, **usare un'animazione sottile al passaggio** del mouse per indicare gli elementi interattivi sotto il mouse.

- Se si usano in modo significativo le animazioni nelle funzionalità, è possibile **disattivarle localmente (** per tutte le funzionalità) come opzione nella finestra di dialogo **strumenti > opzioni** .

- **Deve verificarsi una sola animazione alla volta** e fornire solo una informazione.

- **La sottigliezza è importante.** Nella maggior parte dei casi, non è necessario che l'animazione richieda l'attenzione dell'utente per svolgere lo scopo. Modifiche minime nell'intervallo di tempo, sequenziazione e comportamento possono influire in modo significativo sulla percezione e possono fare la differenza tra un'animazione efficace e inefficace.

- Quando si usa l'animazione per attirare l'attenzione su un elemento, **assicurarsi che valga la pena interrompere il**training dell'utente.

- **Quando si visualizza lo stato di avanzamento o lo stato** tramite l'animazione:

  - Arrestare la visualizzazione dello spostamento dello stato di avanzamento quando il processo sottostante non avanza.

  - Distinguere i processi indeterminati dai processi determinati.

  - Verificare che in un'animazione siano presenti stati di completamento e di errore identificabili.

  - Ridurre l'uso delle animazioni degli effetti che mostrano lo stato e assicurarsi che abbiano un valore reale fornendo informazioni aggiuntive sull'uso effettivo. Gli esempi includono modifiche e emergenze di stato temporanee

#### <a name="do-not"></a>Non:

- Utilizzare piccoli movimenti (spostamento in un footprint ridotto), preferendo dissolvenze e modifiche allo spostamento degli oggetti.

- Usare le animazioni che si verificano in un'area di grandi dimensioni dello schermo. Indipendentemente dalle dimensioni, questo stile di animazione distrae l'utente.

- Utilizzare animazioni che non si riferiscono all'oggetto a cui l'utente è attualmente concentrato o che interagisce.

- Usare le animazioni che richiedono l'interazione dell'utente per reimpostare lo stato, ad esempio forzando l'utente a rispondere a una notifica lampeggiante per evitare il lampeggio. L'interazione con essi in qualsiasi modo dovrebbe essere sufficiente per ignorarli.

  Per altre informazioni sulle applicazioni per queste procedure consigliate, vedere [modelli di animazione](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metriche di animazione

- Il sistema deve rispondere in modo invisibile ai movimenti utente in meno di 10 millisecondi.

- Le transizioni animate non devono richiedere più di 500 millisecondi per il completamento.

- Un modo per compensare le transizioni che richiedono tempi più lunghi consiste nel separarlo in due parti; ad esempio, la prima parte di un'animazione potrebbe essere il contenitore di contenuto vuoto (fino a 500 millisecondi) seguito dal contenuto che si dissolve nel contenitore (fino a 500 millisecondi).

- Per i tempi di caricamento che possono essere calcolati, è preferibile un indicatore di stato determinante (indicatore di avanzamento percentuale).

- Per i tempi di caricamento che non possono essere calcolati, è opportuno un indicatore occupato, ad esempio un cursore o un'animazione rotante incorporata (caricamento o indicatore di funzionamento).

### <a name="animation-as-communicator"></a>Animazione come Communicator
 Nell'interfaccia utente di Visual Studio, l'animazione funziona solo come strumento di comunicazione.  Viene usato per comunicare una serie di informazioni, ad esempio modifiche strutturali nell'interfaccia utente. ad esempio, quando un menu viene aperto o chiuso. L'animazione consente di visualizzare il comportamento dipendente dal tempo di sistemi complessi, ad esempio la visualizzazione dello stato di avanzamento dell'installazione o l'utilizzo per attirare l'attenzione su avvisi e notifiche.

 Le animazioni dell'interfaccia utente in genere funzionano in quattro modi: visualizzare, attirare l'attenzione, simulare e indicare i tempi di risposta e lo stato di avanzamento.

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

- Rappresentazione delle modifiche nel tempo mediante i cursori temporali, le ruote jog-and-Shuttle e i controlli di trasporto (riproduzione, arresto e sospensione).

##### <a name="relationships"></a>Relazioni

- Illustra il modo in cui gli elementi sono correlati tra loro o quali elementi sono correlati a un determinato elemento.

- Mostra gerarchie e relazioni padre-figlio o di pari livello

- Un elemento genera un altro elemento

- Un elemento viene ridotto a un altro elemento

- Un elemento legato a un altro

##### <a name="state"></a>State

- Content updates (Aggiornamenti del contenuto) .

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
 Se l'obiettivo è quello di attirare l'attenzione dell'utente su un singolo elemento o di avvisare l'utente di aggiornare le informazioni, un'animazione può essere appropriata. Ad esempio, è possibile che la pagina iniziale dell'applicazione usi un pulsante Introduzione che scorre in posizione dopo il caricamento della pagina.

 Come regola, l'ultimo elemento spostato sullo schermo attira l'attenzione dell'utente.  In una serie di elementi animati, l'attenzione dell'utente seguirà l'ultimo oggetto in cui viene spostato.

##### <a name="alert"></a>Avviso

- Avvisa l'utente, fai attenzione, Mostra lo stato di avanzamento

- Indica che un elemento viene eseguito correttamente o in modo errato oppure Mostra le modifiche dello stato o dello stato di avanzamento

- Richiedi agli utenti durante un'attività, ad esempio la ricerca di altre informazioni online o l'apprendimento dell'attività corrente

##### <a name="notifications"></a>Notifiche

- Avvisare l'utente di una condizione di errore

- Interrompi l'utente per vedere se desiderano partecipare ad altri elementi

- Informare delicatamente l'utente che un processo è stato completato o modificato, ad esempio quando un download è stato completato.

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
 Le animazioni in Visual Studio servono una funzione specifica e non ostacolano la produttività degli utenti. Le caratteristiche di animazione generali da rispettare includono:

- Piccolo e non intrusivo

- Naturale e realistico

- Sottile e sommesso

- Veloce ed efficiente

- Rilassato, non frettoloso

  La figura seguente Mostra gli stili di animazione consigliati per l'uso in Visual Studio. Non viene usata più di frequente alcuna animazione e animazioni impercettibili come dissolvenza in entrata/dissolvenza. È disponibile un'applicazione limitata di animazioni di movimento, ad esempio espansione e contratto, modifica della posizione X e Y e rotazione.

  ![Stili di animazione consigliati per Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")

  **Stili di animazione consigliati per Visual Studio**

#### <a name="appear-and-disappear"></a>Visualizzazione e scomparsa
 Con questo modello, un elemento passa da visibile a out-of-View e viceversa senza un'animazione di transizione:

 ![Visualizza&#47;animazione scompare in Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")

##### <a name="correct-usage"></a>Corretto utilizzo
 Nuovi elementi dell'interfaccia utente che devono apparire o scomparire immediatamente, in modo che l'utente non sia distratto né ostruito. Inoltre, le animazioni a movimenti lenti possono essere percepite come un trascinamento delle prestazioni, che non si verificherà con lo stile di visualizzazione e di scomparsa.

##### <a name="incorrect-usage"></a>Utilizzo non corretto
 I casi in cui l'interfaccia utente viene visualizzata in modo improvviso, l'utente non ha idea di cosa è successo e l'aggiunta di un'animazione contribuirebbe alla comprensione contestuale.

##### <a name="animation-properties"></a>Proprietà animazione
 Il ritardo di tempo è in genere pari a zero secondi.

##### <a name="examples"></a>Esempi

- Finestre degli strumenti Nascondi automaticamente

- Interfaccia utente dell'editor attivata da tastiera, ad esempio IntelliSense e la guida per i parametri

- Espandere e comprimere le aree di codice

#### <a name="fade-in-and-fade-out"></a>Dissolvenza e dissolvenza
 Con questo modello, un elemento dell'interfaccia utente esegue la transizione da non visibile (0% opacità) a visibile (100% di opacità) o viceversa:

 ![Dissolvenza&#45;nell'animazione&#47;dissolvenza&#45;out in Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")

##### <a name="correct-usage"></a>Corretto utilizzo
 Si tratta dell'animazione dell'interfaccia utente più comunemente consigliata. Si tratta di un effetto sottile che aggiunge interesse senza interrompere il flusso. In alcuni casi, è possibile che l'utente non renda conto che è presente un'animazione e che percepisce semplicemente un sistema di interfaccia utente scorrevole e fluido.

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
 Con questo modello, un elemento dell'interfaccia utente cambia dal colore A al colore B:

 ![Animazione di miscele di colore in Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")

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
 Con questo modello, un elemento dell'interfaccia utente si espande in X, Y o in entrambe le direzioni:

 ![Espandi&#47;animazione del contratto in Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")

##### <a name="correct-usage"></a>Corretto utilizzo
 Come transizione animata quando un elemento dell'interfaccia utente cambia dimensione da un contesto a un altro.

##### <a name="animation-properties"></a>Proprietà animazione

- Scala X:% o dimensione specifica (in pixel)

- Scala Y:% o dimensione specifica (in pixel)

- Posizione di ancoraggio: generalmente superiore sinistro (per le lingue da sinistra a destra) o superiore destro (per le lingue da destra a sinistra)

- Durata: 200 millisecondi autonomi, 100 millisecondi se usati come parte di una sequenza di animazione combinata

##### <a name="examples"></a>Esempi

- Espandere e comprimere il pannello Esplora architettura

- Espandi e Comprimi elemento della pagina iniziale

#### <a name="x-y-position-change"></a>Modifica della posizione X-Y
 Con questo modello, un elemento dell'interfaccia utente modifica la posizione X o Y o entrambi:

 ![Animazione X&#47;Y modifica posizione in Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")

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
 Con questo modello, l'elemento dell'interfaccia utente ruota:

 ![Animazione di rotazione in Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")

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

- Stile: visualizzato

- Durata: zero secondi

  ![Animazione di apertura della scheda in Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")

#### <a name="tab-close"></a>Chiusura tabulazione

- Stile: modifica della posizione X

- Durata: 200 millisecondi

  ![Animazione di chiusura della scheda in Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")

#### <a name="tab-reorder"></a>Riordino tabulazione

- Stile: modifica della posizione X

- Durata: 200 millisecondi

  ![Animazione di riordinamento della scheda in Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")

#### <a name="close-floating-document"></a>Chiudi documento mobile

- Stile: visualizzato

- Durata: 200 millisecondi

  ![Animazione di chiusura documento mobile in Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Transizione dello stato della finestra

- Stile: per essere coerente con altre finestre, consentire al sistema operativo corrente di definire l'animazione di chiusura del documento.

- Durata: 200 millisecondi

  ![Animazione di transizione stato della finestra in Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")

#### <a name="menu-open"></a>Menu aperto

- Stile: dissolvenza in entrata

- Durata: 200 millisecondi

  ![Animazione di apertura del menu in Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")

#### <a name="menu-close"></a>Chiudi menu

- Stile: dissolvenza in uscita

- Durata: 200 millisecondi

  ![Animazione di chiusura del menu in Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Nascondi automaticamente la finestra degli strumenti

- Stile: visualizzato

- Durata: zero secondi

  ![Animazione della finestra degli strumenti Nascondi automaticamente&#45;in Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")
