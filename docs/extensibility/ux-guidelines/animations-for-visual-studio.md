---
title: 'Animazioni per Visual Studio : Documenti Microsoft'
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698612"
---
# <a name="animations-for-visual-studio"></a>Animazioni per Visual Studio
## <a name="animation-fundamentals"></a>Fondamenti dell'animazione

### <a name="animation-best-practices-in-visual-studio"></a>Procedure consigliate per l'animazione in Visual StudioAnimation best practices in Visual Studio
Seguire queste regole per garantire stili di animazione coerenti e di facile utilizzo nell'IDE di Visual Studio.Follow these rules to ensure consistent and user-friendly animation styles across the Visual Studio IDE.

- **Siate selettivi.** Limita le animazioni a quelle che servono a scopi specifici.

- **Tempismo e velocità sono importanti** per garantire che le transizioni si sentano rapide e naturali:

  - Completa le transizioni animate entro mezzo secondo (500 millisecondi).

  - Le animazioni che si verificano frequentemente devono essere sufficientemente rapide da non interrompere il flusso di lavoro dell'utente. Guarda l'animazione in un ciclo e regola la temporizzazione fino a quando non ti sembra giusto.

  - Le animazioni non dovrebbero essere così veloci o stridenti che è difficile da capire, ma non così lento che rende impaziente per la transizione alla fine.

  - Utilizzare la temporizzazione variabile per enfatizzare l'importanza. Ad esempio, quando ci si sposta in una sequenza di elementi in un diagramma classi, velocizzare le transizioni tra gli elementi, quindi rallentare per concentrarsi su elementi importanti.

- **Utilizzare graduale non lineare allentamento** da uno stato all'altro, dando un senso di movimento calmo e naturale.

- Quando possibile, **utilizzare un'animazione sottile al passaggio del mouse** per indicare gli elementi interattivi sotto il mouse.

- Se si fa molto affidamento sulle animazioni nelle feature, **fornire un mezzo per disattivarle** localmente (per tutte le feature) come opzione nella finestra di dialogo Strumenti > **Opzioni.**

- **Deve verificarsi una sola animazione alla volta** e trasmettere solo un'informazione. Più di un oggetto in movimento o il tentativo di trasmettere più cose può essere fonte di confusione.

- **La sottigliezza è importante.** Nella maggior parte dei casi, l'animazione non deve richiedere l'attenzione dell'utente per soddisfare il suo scopo. Piccoli cambiamenti nella temporizzazione, nella sequenza e nel comportamento potrebbero avere un impatto significativo sulla percezione e possono fare la differenza tra un'animazione efficace e inefficace.

- Quando si utilizza l'animazione per attirare l'attenzione su qualcosa, **assicurarsi che vale la pena interrompere il**treno di pensiero dell'utente.

- **Quando si mostra lo stato o lo stato** tramite animazione:

  - Interrompere la visualizzazione dello stato di avanzamento quando il processo sottostante non avanza.

  - Distinguere i processi indeterminati dai processi determinati.

  - Assicurarsi che un'animazione abbia stati di completamento e di errore identificabili.

  - Riduci al minimo l'uso delle animazioni degli effetti che mostrano lo stato e assicurati che abbiano un valore reale fornendo informazioni aggiuntive sull'uso effettivo. Esempi includono cambiamenti transitori dello stato e le emergenze

#### <a name="animation-donts"></a>Animazione non:

- Non utilizzare piccoli movimenti (movimento con un ingombro ridotto). Preferisci le dissolvenze e le modifiche rispetto agli oggetti in movimento.

- Non usare animazioni che si svolgono su un'ampia area dello schermo. Indipendentemente dalle dimensioni, questo stile di animazione è fonte di distrazione per l'utente.

- Non usare animazioni non correlate all'oggetto su cui l'utente è attualmente attivo o con cui interagisce.

- Non usare animazioni che richiedono l'interazione dell'utente per reimpostare lo stato, ad esempio forzare l'utente a rispondere a una notifica lampeggiante per farlo lampeggiare. Interagire con loro in qualsiasi modo dovrebbe essere sufficiente per respingerli.

Per ulteriori informazioni sulle applicazioni per queste procedure consigliate, consultate Modelli di [animazione.](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)

### <a name="animation-metrics"></a>Metriche di animazione

- Il sistema deve reagire visibilmente ai movimenti dell'utente in meno di 10 millisecondi.

- Il completamento delle transizioni animate non dovrebbe richiedere più di 500 millisecondi.

- Un modo per compensare le transizioni che richiedono tempi più lunghi consiste nel separarle in due parti. Ad esempio, la prima parte di un'animazione potrebbe essere il contenitore di contenuto vuoto (fino a 500 millisecondi), seguito dalla dissolvenza del contenuto nel contenitore (fino a 500 millisecondi).

- Per i tempi di caricamento che possono essere calcolati, è preferibile un indicatore di stato determinante (indicatore di stato con percentuale completata).

- Per i tempi di caricamento che non possono essere calcolati, è appropriato un indicatore di occupato come un cursore o un'animazione di rotazione incorporata (indicatore di caricamento o di lavoro).

### <a name="animation-as-communicator"></a>Animazione come comunicatore
Nell'interfaccia utente di Visual Studio l'animazione funziona solo come strumento di comunicazione.  Viene usato per comunicare una varietà di informazioni, ad esempio modifiche strutturali nell'interfaccia utente (ad esempio, quando un menu si apre o si chiude). L'animazione consente di visualizzare il comportamento dipendente dal tempo di sistemi complessi, ad esempio la visualizzazione dello stato di avanzamento dell'installazione. Le animazioni possono anche essere usate per attirare l'attenzione con avvisi e notifiche.

 Le animazioni dell'interfaccia utente in genere funzionano in quattro modi: visualizzare, attirare l'attenzione, simulare e gli indicatori di tempo/avanzamento di risposta.

#### <a name="visualize"></a>Visualizzazione
L'animazione può enfatizzare la natura tridimensionale degli oggetti e semplificare la visualizzazione della struttura spaziale da parte degli utenti. A tale scopo, l'animazione potrebbe essere necessario ruotare l'oggetto in un cerchio completo, ruotarlo lentamente avanti e indietro o avvicinare l'oggetto e aumentarne leggermente le dimensioni per enfatizzare il rollover o lo stato attivo.

Anche se gli oggetti tridimensionali possono essere spostati con il controllo utente, la finestra di progettazione deve determinare in anticipo (a livello di codice o manualmente) come animare al meglio un movimento che fornisce una comprensione ottimale dell'oggetto. Questa animazione programmata può quindi essere attivata dall'utente posizionando il cursore sull'oggetto, mentre i movimenti controllati dall'utente richiedono all'utente di capire come manipolare l'oggetto. Limitare il movimento a un singolo asse o orientamento alla volta; scalare, ruotare o traslare, ma non eseguire più di una operazione contemporaneamente.

La categoria Visualizza include gli aspetti di dati, relazioni, stato, struttura, sequenza e ora.

##### <a name="data"></a>Data
Illustrare informazioni complesse e variabili:

- Spostamento tra visualizzazioni di informazioni come grafici e grafici

- Esecuzione di una sequenza, una visita guidata e il paging

- Richiamare i dettagli, puntare ed evidenziare informazioni specifiche

- Sovrapposizione di dettagli e informazioni aggiuntive su un elemento attivo

- Morphing da una rappresentazione strutturale o organizzativa a un'altra

- Rappresentare le modifiche nel tempo utilizzando i cursori del tempo, le ruote jog-and-shuttle e i controlli di trasporto (riproduzione, arresto e pausa)

##### <a name="relationships"></a>Relazioni

- Illustrare il modo in cui gli elementi sono correlati tra loro o quali elementi sono correlati a un determinato elemento

- Mostrare gerarchie e relazioni padre-figlio o di pari livello

- Un elemento genera un altro

- Un elemento viene ridotto a un altro elemento

- Un elemento legato ad un altro

##### <a name="state"></a>State

- Aggiornamenti dei contenuti

- Messa a fuoco e selezione dell'utente

- Progress

- Errors

##### <a name="structure"></a>Struttura

- Pivoting della struttura su un nodo

- Riorientato

- Ridurre a icona e ingrandire oppure espandere e comprimere

##### <a name="sequence"></a>Sequenza

- Sequenza di diapositive

- Scorrimento tra le immagini

##### <a name="time"></a>Tempo

- Mostra il cambiamento nel tempo, il time lapse e lo screencast

- Passare al cestino, annullare e rifare

- Ripristinare lo stato cronologico

#### <a name="attract-attention"></a>Attirare l'attenzione
Se l'obiettivo è attirare l'attenzione dell'utente su un singolo elemento su più elementi o per avvisare l'utente di informazioni aggiornate, un'animazione potrebbe essere appropriata. Ad esempio, la pagina iniziale dell'applicazione potrebbe utilizzare un pulsante Guida introduttiva che scorre in posizione dopo il caricamento della pagina.

Di norma, l'ultimo elemento in movimento sullo schermo attira l'attenzione dell'utente.  In una serie di elementi animati, l'attenzione dell'utente seguirà l'ultimo oggetto in movimento.

##### <a name="alert"></a>Avviso

- Avvisare l'utente, ottenere attenzione, mostrare i progressi

- Mostrare che qualcosa viene fatto correttamente o in modo errato o mostrare lo stato di avanzamento o le modifiche di stato

- Richiedere agli utenti durante un'attività, ad esempio trovare ulteriori informazioni online o conoscere l'attività corrente

##### <a name="notifications"></a>Notifiche

- Avvisare l'utente di una condizione di errore

- Interrompere l'utente per vedere se desidera partecipare a qualcos'altro

- Informare delicatamente l'utente che un processo è stato completato o modificato, ad esempio quando un download è completo.

#### <a name="simulate"></a>Simulate
Questa categoria comprende la fisicità e la dimensionalità.

- Illustrare la provenivienie o la posizione degli oggetti

- Espandere e comprimere o aprire e chiudere

- Panoramica, scorrimento e giri di pagina

- Impilamento e ordinamento z

- Carosello e fisarmonica

- Capovolgimento e rotazione dell'interfaccia utente

#### <a name="response-and-progress-indicators"></a>Indicatori di risposta e di avanzamento
Gli indicatori di avanzamento presentano un paio di vantaggi notevoli:

- Entrambi gli indicatori di stato determinati e indeterminati rassicurano l'utente che il sistema non si è arrestato in modo anomalo e sta lavorando al problema.

- Indicatori determinati danno all'utente un senso di quanto lungo l'azione sta progredendo, così come una sensazione di avvicinarsi al traguardo.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Modelli di animazione

### <a name="overview"></a>Panoramica
Le animazioni in Visual Studio hanno lo scopo di servire una funzione specifica senza ostacolare la produttività dell'utente. In genere, le animazioni in Visual Studio devono essere:Generally, animations in Visual Studio should be:

- Piccolo e discreto

- Naturale e realistico

- Sottile e sommesso

- Veloce ed efficiente

- Rilassato, non frettoloso

Questa illustrazione mostra gli stili di animazione consigliati per Visual Studio.This illustration shows the animation styles we recommend for Visual Studio. Nessuna animazione o animazioni sottili come dissolvenza in entrata/dissolvenza sono i più utilizzati. C'è un'applicazione limitata di animazioni di movimento come espandere e contrarre, cambio di posizione X e Y e rotazione.

![Stili di animazione consigliati per Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Stili di animazione consigliati per Visual Studio

#### <a name="appear-and-disappear"></a>Appaiono e scompaiono
Con questo modello, un elemento passa da visibile a out-of-view e viceversa senza un'animazione di transizione.

![Appaiono e scompaiono l'animazione](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Appaiono e scompaiono l'animazione

##### <a name="correct-usage"></a>Utilizzo corretto
Nuovi elementi dell'interfaccia utente che devono apparire o scomparire istantaneamente in modo che l'utente non sia né distratto né ostacolato. Inoltre, le animazioni con movimento lento potrebbero essere percepite come un trascinamento delle prestazioni, che non si verificherà con lo stile di visualizzazione e scomparsa.

##### <a name="incorrect-usage"></a>Utilizzo non corretto
Casi in cui l'interfaccia utente viene visualizzata così bruscamente l'utente non ha idea di cosa sia successo e l'aggiunta di un'animazione potrebbe aiutare con la comprensione contestuale.

##### <a name="animation-properties"></a>Proprietà animazione
Il ritardo è generalmente pari a zero secondi.

##### <a name="examples"></a>Esempi
- Nascondi automaticamente le finestre degli strumenti

- Interfaccia utente dell'editor attivata da tastiera, ad esempio IntelliSense e Guida ai parametri

- Espandere e comprimere aree di codice

#### <a name="fade-in-and-fade-out"></a>Dissolvenza in entrata e in uscita
Con questo modello, un elemento dell'interfaccia utente passa da non visibile (0% di opacità) a visibile (100% opacità) o viceversa.

![Animazione con dissolvenza in entrata e in uscita](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animazione con dissolvenza in entrata e in uscita

##### <a name="correct-usage"></a>Utilizzo corretto
Questa è l'animazione dell'interfaccia utente più comunemente consigliata. È un effetto sottile che aggiunge interesse senza interrompere il flusso. In alcuni casi, l'utente potrebbe anche non rendersi conto che c'è un'animazione, percepire un sistema dell'interfaccia utente fluido e scorrevole.

##### <a name="animation-properties"></a>Proprietà animazione

- Opacità iniziale: 0% per fade-in, 100% per fade-out

- Opacità finale: 100% per fade-in, 0% per fade-out

- Durata: 200 millisecondi autonomi, 100 millisecondi se utilizzati come parte di una sequenza di animazione combinata

- Stile di andamento: Sine InOut

##### <a name="examples"></a>Esempi

- Nascondi automaticamente le finestre degli strumenti

- Apertura e chiusura del menu

- Transizioni di tabulazione in primo sfondo e in primo piano

#### <a name="color-blend-from-a-to-b"></a>Miscela di colore da A a B
Con questo modello, un elemento dell'interfaccia utente cambia dal colore A al colore B.With this pattern, a UI element changes from color A to color B.

![Animazione di fusione colore](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animazione di fusione colore

##### <a name="correct-usage"></a>Utilizzo corretto
Come transizione animata quando un elemento dell'interfaccia utente cambia colore da un contesto o uno stato a un altro.

##### <a name="animation-properties"></a>Proprietà animazione

- Colore iniziale: specifico dell'interfaccia utenteStarting color: UI-specific

- Colore finale: specifico dell'interfaccia utente

- Durata: 200 millisecondi autonomi, 100 millisecondi se utilizzati come parte di una sequenza di animazione combinata

- Stile di andamento: Sine InOut

##### <a name="examples"></a>Esempi

- Transizioni dello stato della finestra del documento (attivo, ultimo attivo e inattivo)

- Transizioni di stato della finestra degli strumenti (messa a fuoco e non messa a fuoco)Tool window state transitions (focused and unfocused)

#### <a name="expand-and-contract"></a>Espandi e contratto
Con questo modello, un elemento dell'interfaccia utente si espande nelle direzioni X, Y o entrambe.

![Espandi e contrae animazione](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Espandi e contrae animazione

##### <a name="correct-usage"></a>Utilizzo corretto
Come transizione animata quando un elemento dell'interfaccia utente cambia dimensione da un contesto a un altro.

##### <a name="animation-properties"></a>Proprietà animazione

- Scala X: % o dimensione specifica (in pixel)

- Scala Y: % o dimensione specifica (in pixel)

- Posizione di ancoraggio: generalmente in alto a sinistra (per le lingue da sinistra a destra) o in alto a destra (per le lingue da destra a sinistra)

- Durata: 200 millisecondi autonomi, 100 millisecondi se utilizzati come parte di una sequenza di animazione combinata

##### <a name="examples"></a>Esempi

- Espansione e compressione del pannello Esplora architettura

- Espansione e compressione dell'elemento della pagina iniziale di Visual Studio 2017

#### <a name="x-y-position-change"></a>Cambio di posizione X-Y
Con questo modello, un elemento dell'interfaccia utente modifica la posizione X o Y o entrambi.

![Animazione di modifica della posizione X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animazione di modifica della posizione X-Y

##### <a name="correct-usage"></a>Utilizzo corretto
Come transizione animata quando un elemento dell'interfaccia utente cambia posizione da un contesto a un altro.

##### <a name="animation-properties"></a>Proprietà animazione

- Posizione X e Y iniziale: specifica dell'interfaccia utenteStarting X and Y position: UI-specific

- Fine della posizione X e Y: specifica dell'interfaccia utente

- Percorso di movimento: nessuno

- Durata: 200 millisecondi autonomi, 100 millisecondi se utilizzati come parte di una sequenza di animazione combinata

- Stile di andamento: Sine InOut

##### <a name="example"></a>Esempio
Riordinamento delle schede

#### <a name="rotate"></a>Ruota
Con questo modello, l'elemento dell'interfaccia utente ruota.

![Animazione di rotazione dell'elemento dell'interfaccia utenteUI element rotation](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animazione di rotazione dell'elemento dell'interfaccia utenteUI element rotation

##### <a name="correct-usage"></a>Utilizzo corretto
Solo per l'indicatore di stato di rotazione indeterminato.

##### <a name="animation-properties"></a>Proprietà animazione

- Grado di rotazione: 360

- Centro di rotazione: al centro dell'oggetto

- Durata: continua

##### <a name="example"></a>Esempio
Indicatore di stato indeterminato (spinning)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Azioni comuni dell'interfaccia utente della shell e animazioni consigliateCommon shell UI actions and recommended animations

#### <a name="tab-open"></a>Scheda aperta
![Animazione a schede aperte](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animazione a schede aperte

- Stile: appare

- Durata: zero secondi

#### <a name="tab-close"></a>Scheda chiusa
![Animazione di chiusura delle schede](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animazione di chiusura delle schede

- Stile: cambio di posizione X

- Durata: 200 millisecondi

#### <a name="tab-reorder"></a>Riordinamento delle tabulazioni
![Animazione di riordinamento della scheda in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animazione di riordino delle tabulazioni

- Stile: cambio di posizione X

- Durata: 200 millisecondi

#### <a name="close-floating-document"></a>Chiudere il documento mobile
![Chiudere l'animazione dei documenti mobili](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Chiudere l'animazione dei documenti mobili

- Stile: appare

- Durata: 200 millisecondi

#### <a name="window-state-transition"></a>Transizione dello stato della finestra
![Animazione della transizione dello stato della finestra](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animazione della transizione dello stato della finestra

- Stile: per essere coerente con altre finestre, lasciare che il sistema operativo corrente definisca l'animazione di chiusura del documento.

- Durata: 200 millisecondi

#### <a name="menu-open"></a>Menu aperto
![Animazione aperta dal menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animazione aperta dal menu

- Stile: dissolvenza in entrata

- Durata: 200 millisecondi

#### <a name="menu-close"></a>Menu vicino
![Animazione di chiusura del menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animazione di chiusura del menu

- Stile: fade-out

- Durata: 200 millisecondi

#### <a name="auto-hide-tool-window-reveal"></a>Nascondi automaticamente finestra degli strumenti rivelare
![Nascondi automaticamente la finestra degli strumenti rivela l'animazione](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Nascondi automaticamente la finestra degli strumenti rivela l'animazione

- Stile: appare

- Durata: zero secondi
