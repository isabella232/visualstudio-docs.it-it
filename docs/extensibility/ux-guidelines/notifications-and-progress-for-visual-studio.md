---
title: Notifiche e stato per Visual Studio . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699878"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notifiche e avanzamento per Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Sistemi di notifica

### <a name="overview"></a>Panoramica
 Esistono diversi modi per informare l'utente su ciò che accade in Visual Studio per quanto riguarda le attività di sviluppo software.

 Quando si implementa qualsiasi tipo di notifica:

- **Mantenere il numero di notifiche al** numero effettivo minimo. I messaggi di notifica devono essere applicati alla maggior parte degli utenti di Visual Studio o agli utenti di un'area di funzionalità o funzionalità specifica. L'uso eccessivo delle notifiche può evitare l'utente o diminuire la facilità d'uso percepita del sistema.

- **Assicurarsi di presentare messaggi chiari** e utilizzabili che l'utente può utilizzare per richiamare il contesto appropriato per effettuare scelte più complesse e intraprendere ulteriori azioni.

- **Presentare messaggi sincroni e asincroni in modo appropriato.** Le notifiche sincrone indicano che è necessaria un'attenzione immediata, ad esempio quando un servizio Web si arresta in modo anomalo o viene generata un'eccezione di codice. L'utente deve essere informato di tali situazioni immediatamente in un modo che richiede l'input, ad esempio in una finestra di dialogo modale. Le notifiche asincrone sono quelle che l'utente deve conoscere ma su cui non deve essere richiesto di agire immediatamente, ad esempio quando viene completata un'operazione di compilazione o la distribuzione di un sito Web. Tali messaggi devono essere più di ambiente e non interrompere il flusso di attività dell'utente.

- Utilizzare le finestre di **dialogo modali solo quando necessario per impedire all'utente** di eseguire ulteriori azioni prima di riconoscere il messaggio o prendere una decisione presentata nella finestra di dialogo.

- **Rimuovere le notifiche di ambiente quando non sono più valide.** Non richiedere all'utente di ignorare una notifica se ha già intrapreso un'azione per risolvere il problema per cui è stata notificata.

- **Tenere presente che le notifiche possono portare a false correlazioni.** Gli utenti potrebbero ritenere che una o più delle loro azioni abbia attivato una notifica quando in realtà non esisteva alcuna relazione causale. Essere chiari nel messaggio di notifica sul contesto, il trigger e l'origine della notifica.

### <a name="choosing-the-right-method"></a>Scegliere il metodo giusto
 Utilizzare questa tabella per facilitare la scelta del metodo corretto per notificare all'utente il messaggio.

|Metodo|Uso|Non utilizzare|
|------------|---------|----------------|
|[Finestre di dialogo dei messaggi di errore modaliModal error message dialogs](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Utilizzare quando è necessaria una risposta dell'utente prima di procedere.|Non utilizzare quando non è necessario bloccare l'utente e interromperne il flusso. Evitare di utilizzare finestre di dialogo modali se è possibile visualizzare il messaggio in un altro modo meno intrusivo.|
|[Barra di stato IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Utilizzare quando sono presenti informazioni testuali di ambiente relative allo stato di un processo.|Non usare da solo. Ideale in combinazione con un altro meccanismo di feedback.|
|[Barra informazioni incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|In una finestra degli strumenti o in una finestra del documento, utilizzare per notificare lo stato di avanzamento, lo stato di errore, i risultati e/o le informazioni utilizzabili.|Non utilizzare se le informazioni non sono rilevanti per la posizione in cui è posizionata la barra informazioni.<br /><br /> Non utilizzare all'esterno di una finestra documento/strumento.|
|[Modifiche del cursore del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Può essere utilizzato per notificare che un processo è in corso. Utilizzato anche per notificare che è presente una modifica dello stato del mouse, ad esempio quando è in corso il trascinamento della selezione o che il cursore del mouse è in una determinata modalità, ad esempio la modalità di disegno.|Non usare per brevi modifiche di stato o se è probabile che il cursore svolazzasse (ad esempio, quando è legato a parti di un processo a esecuzione prolungata anziché all'intero processo).|
|[Indicatori di avanzamento](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Utilizzare quando è necessario segnalare lo stato di avanzamento (determinato o indeterminato). Ci sono una varietà di tipi di indicatore di stato e l'utilizzo specifico per ciascuno. Vedere [Indicatori di avanzamento](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Finestra delle notifiche di Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La finestra Notifiche non è pubblicamente estensibile. Tuttavia, viene utilizzato per comunicare una serie di messaggi su Visual Studio, inclusi problemi critici con la licenza e notifiche informative degli aggiornamenti a Visual Studio o pacchetti.|Non utilizzare per altri tipi di notifiche.|
|[Elenco errori](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando il problema si riferisce direttamente alla soluzione attualmente aperta dell'utente che ha un problema (errore/avviso/info), potrebbe essere necessario intervenire sul codice.<br /><br /> Ciò includerebbe, ad esempio:<br /><br /> - Messaggi del compilatore (errore/avviso/info)<br /><br /> - Analizzatore di codice/Messaggi di diagnostica sul codice- Code Analyzer/Diagnostic messages about the code<br /><br /> - Costruire messaggi<br /><br /> Può essere appropriato per i problemi relativi ai file di progetto o di soluzione, ma considerare prima un'indicazione di Esplora soluzioni.|Non utilizzare per gli elementi che non hanno alcuna relazione con il codice della soluzione aperta dell'utente.|
|Notifiche dell'editor: Lampadina|Utilizzare questa opzione quando è disponibile una correzione per risolvere un problema presente nel file aperto.<br /><br /> Si noti che Light Bulb deve essere utilizzato anche per l'hosting di azioni rapide eseguite sul codice dell'utente su richiesta, ad esempio il refactoring, ma in questo caso non verrà visualizzato "stile di notifica".|Non utilizzare per gli elementi che non hanno alcuna relazione con il file aperto.|
|Notifiche dell'editor: squiggles|Utilizzare per avvisare l'utente di un problema con un determinato intervallo di codice aperto (ad esempio, una ondulata rossa per gli errori).|Non utilizzare per gli articoli che non si riferiscono a un determinato intervallo del codice aperto.|
|[Barre di stato incorporate](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilizzare per fornire lo stato relativo al contenuto o al processo nel contesto di una finestra degli strumenti, una finestra del documento o una finestra di dialogo specifica.|Non utilizzare per le notifiche generali dei prodotti, i processi o gli articoli che non hanno alcuna relazione con il contenuto all'interno della finestra specifica.|
|[Notifiche della barra delle applicazioni di Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Utilizzare per visualizzare le notifiche per processi out-of-process o applicazioni complementari.|Non utilizzare per le notifiche rilevanti per l'IDE.|
|[Bolle di notifica](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Utilizzare per notificare un processo remoto o una modifica **all'esterno** dell'IDE.|Non utilizzare come mezzo per notificare all'utente dei processi **all'interno** dell'IDE.|

### <a name="notification-methods"></a>Metodi di notifica

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Finestre di dialogo dei messaggi di errore modaliModal error message dialogs
 Una finestra di dialogo di messaggio di errore modale viene utilizzata per visualizzare un messaggio di errore che richiede la conferma o l'azione dell'utente.

 ![Messaggio di errore modale](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Una finestra di dialogo di messaggio di errore modale che avvisa l'utente di una stringa di connessione non valida a un database**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Barra di stato IDE
 La probabilità che gli utenti notino il testo della barra di stato è correlata alla loro esperienza all-around del computer e all'esperienza specifica con la piattaforma Windows. La base di clienti di Visual Studio tende ad essere sperimentata in entrambe le aree, anche se anche gli utenti di Windows esperti potrebbero perdere le modifiche nella barra di stato. Pertanto, la barra di stato è meglio utilizzata per scopi informativi o come un segnale ridondante per le informazioni presentate altrove. Qualsiasi tipo di informazioni critiche che l'utente deve risolvere immediatamente deve essere fornito in una finestra di dialogo o nella finestra degli strumenti di notifiche.

 La barra di stato di Visual Studio è progettata per consentire la visualizzazione di diversi tipi di informazioni. È suddiviso in aree per feedback, finestra di progettazione, barra di stato, animazione e client.

 L'area commenti e suggerimenti e l'area della finestra di progettazione sono sempre visibili. L'indicatore di stato e le aree di animazione sono sempre dinamici e basati sul contesto utente. L'area della finestra di progettazione ha una larghezza statica determinata dalla lunghezza della stringa che viene estratta da una risorsa associata per il messaggio di testo. Ciò consente alla localizzazione di ridimensionare la larghezza senza richiedere una modifica del codice. Per l'inglese, la larghezza di questa stringa è di circa 220 pixel. L'area di progettazione si comporterà normalmente e l'area di feedback assorbirà lo spazio rimanente.

 La barra di stato è anche colorata per aggiungere interesse visivo e valore funzionale comunicando varie modifiche di stato IDE, ad esempio quando l'IDE è in modalità di debug.

 ![Modifiche ai colori della barra di stato dell'IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Colori della barra di stato dell'IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Barra informazioni incorporata
 Una barra informazioni può essere utilizzata nella parte superiore di una finestra del documento o della finestra degli strumenti per informare l'utente di uno stato o di una condizione. Può anche offrire comandi in modo che l'utente possa avere un modo per agire facilmente. La barra informazioni è un controllo shell standard. Evitare di creare il proprio, che agirà e apparirà incoerente con gli altri nell'IDE. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) per i dettagli di implementazione e le indicazioni sull'utilizzo.

 ![Barra informazioni incorporata](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Una barra informazioni incorporata in una finestra del documento, avvisando l'utente che l'IDE è in modalità di debug cronologico e l'editor non risponderà nello stesso modo come avviene in modalità di debug standard.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Modifiche del cursore del mouse
 Quando si modifica il cursore del mouse, utilizzare i colori associati al servizio VSColor e già associati al cursore. Le modifiche del cursore possono essere utilizzate per indicare un'operazione in corso, nonché le zone di hit in cui l'utente passa il mouse su una destinazione che può essere trascinata, rilasciata o utilizzata per selezionare un oggetto.

 Utilizzare il cursore del mouse occupato/attesa solo quando tutto il tempo CPU disponibile deve essere riservato per un'operazione, impedendo all'utente di esprimere qualsiasi ulteriore input. Nella maggior parte dei casi con applicazioni ben scritte che utilizzano il multithreading, i momenti in cui agli utenti viene impedito di eseguire altre operazioni dovrebbero essere rari.

 Tenere presente che le modifiche del cursore sono utili come segnale ridondante per le informazioni presentate altrove. Non fare affidamento su un cambiamento di cursore come unico modo di comunicare con l'utente, soprattutto quando si cerca di trasmettere qualcosa che è fondamentale che l'utente deve affrontare.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Indicatori di avanzamento
 Gli indicatori di avanzamento sono importanti per fornire feedback all'utente durante i processi che richiedono più di pochi secondi per essere completati. Gli indicatori di stato possono essere visualizzati sul posto (vicino al punto di avvio dell'azione in corso), in una barra di stato incorporata, in una finestra di dialogo modale o nella barra di stato di Visual Studio.Progress indicators can be shown in-place (near the launching point of the action in progress), in an embedded status bar, in a modal dialog, or in the Visual Studio status bar. Seguire le indicazioni riportate negli indicatori di [avanzamento](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) relativi al loro utilizzo e implementazione.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Finestra Notifiche di Visual Studio
 La finestra Notifiche di Visual Studio notifica agli sviluppatori le licenze, l'ambiente (Visual Studio), le estensioni e gli aggiornamenti. Gli utenti possono ignorare singole notifiche o scegliere di ignorare determinati tipi di notifiche. L'elenco delle notifiche ignorate viene gestito in una pagina **Strumenti > Opzioni.**

 La finestra Notifiche non è attualmente estensibile.

 ![Finestra delle notifiche di Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Finestra degli strumenti Notifiche di Visual StudioVisual Studio Notifications tool window**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Elenco errori
 Una notifica all'interno dell'elenco di errori indica errori e avvisi che si sono verificati durante la compilazione e/o il processo di compilazione e consente all'utente di passare nel codice all'errore di codice specifico.

 ![Elenco errori](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Elenco errori in Visual StudioError list in Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Barre di stato incorporate
 Poiché la barra di stato dell'IDE è dinamica, con il contesto dell'area client impostato sulla finestra del documento attivo e l'aggiornamento delle informazioni sul contesto dell'utente e/o le risposte di sistema, è difficile mantenere una visualizzazione continua delle informazioni o fornire lo stato sui processi asincroni a lungo termine. Ad esempio, la barra di stato dell'IDE non è appropriata per le notifiche dei risultati delle esecuzioni dei test per più esecuzioni e/o selezioni di elementi immediatamente utilizzabili. È importante mantenere tali informazioni sullo stato nel contesto del documento o della finestra degli strumenti in cui l'utente effettua una selezione o avvia un processo.

 ![Barra di stato incorporata](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barra di stato incorporata in Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Notifiche della barra delle applicazioni di Windows
 L'area di notifica di Windows è accanto all'orologio di sistema sulla barra delle applicazioni di Windows. Molte utilità e componenti software forniscono icone in quest'area in modo che l'utente possa ottenere un menu di scelta rapida per le attività a livello di sistema, ad esempio la modifica della risoluzione dello schermo o l'ottenimento di aggiornamenti software.

 Le notifiche a livello di ambiente devono essere esunte nell'hub Notifiche di Visual Studio, non nell'area di notifica di Windows.Environment-level notifications should be surfaced in the Visual Studio Notifications hub, not the Windows notification area.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bolle di notifica
 I fumetti di notifica possono essere visualizzati come informazioni all'interno di un editor/progettazione o come parte dell'area di notifica di Windows.Notification bubbles can appear as informational within an editor/designer or as part of the Windows Notification area. L'utente percepisce queste bolle come problemi che possono risolvere in seguito, il che è un vantaggio per le notifiche non critiche. Le bolle sono inadeguate per le informazioni critiche che l'utente deve risolvere immediatamente. Se si utilizzano bolle di notifica in Visual Studio, seguire le indicazioni di [Windows Desktop per i fumetti](/windows/desktop/uxguide/mess-notif)di notifica .

 ![Fumetto della notifica](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Notification bubble in the Windows Notification area used for Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Indicatori di avanzamento

### <a name="overview"></a>Panoramica
 Gli indicatori di avanzamento sono una parte importante di un sistema di notifica per fornire feedback all'utente. Indicano all'utente quando verranno completati i processi e le operazioni. Tipi di indicatori familiari includono barre di avanzamento, cursori rotanti e icone animate. Il tipo e la posizione di un indicatore di stato dipendono dal contesto, inclusi ciò che viene segnalato e il tempo necessario per completare il processo o l'operazione.

#### <a name="factors"></a>Fattori
 Per determinare il tipo di indicatore appropriato, è necessario determinare i seguenti fattori.

1. **Tempo:** durata dell'operazione

2. **Modalità:** se l'operazione è modale per l'ambiente (blocca l'interfaccia utente fino al completamento del processo)

3. **Persistente/transitorio:** se il risultato finale dell'avanzamento deve essere segnalato e/o visualizzabile in un secondo momento

4. **Determinato/Indeterminato:** indica se è possibile calcolare l'ora di fine e lo stato di avanzamento dell'operazione

5. **Posizione grafica/testuale:** se l'avanzamento o il processo viene acquisito inline, nel corpo di un messaggio o in un controllo specifico, ad esempio il controllo Tree

6. **Prossimità:** indica se lo stato di avanzamento deve essere in prossimità dell'interfaccia utente a cui è correlato. (Ad esempio, può essere nella barra di stato, che potrebbe essere lontano, o deve essere vicino al pulsante che ha avviato il processo?)

#### <a name="determinate-progress"></a>Stato di avanzamento determinato

|Tipo di avanzamento|Quando e come usare|Note|
|-------------------|-------------------------|-----------|
|Barra di avanzamento (determinata)|Durata prevista di >5 secondi.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.|**NON** incorporare il testo nell'animazione.|
|Barra informazioni|Messaggi associati all'interfaccia utente contestuale. Consultate [Barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Può includere una descrizione testuale dei dettagli del processo.|**NON** utilizzare più barre informazioni quando è necessario indicare più processi. Utilizzare invece le barre di stato in pila.|
|Finestra di output|Notifica temporanea: processo a livello di app di cui l'utente desidera **esaminare** i dettagli dopo il completamento.|**NON** utilizzare se l'utente dovrà fare riferimento ai dati in un secondo momento.|
|File di registro|Abbinato a notifica intransigente nei casi in cui è importante **salvare** i dettagli dopo il completamento.||
|Barra di stato|Notifica temporanea: processo a livello di app di cui l'utente **non avrà bisogno** di dettagli dopo il completamento.<br /><br /> Include una barra di avanzamento incorporata.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.||

#### <a name="indeterminate-progress"></a>Avanzamento indeterminato

|Tipo di avanzamento|Quando e come usare|Note|
|-------------------|-------------------------|-----------|
|Barra di avanzamento (indeterminata)|Durata prevista di >5 secondi.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.|**NON** incorporare il testo nell'animazione.|
|Formiche (punti orizzontali animati)|Viaggio di andata e ritorno al server.<br /><br /> Posizionato vicino al punto di contesto nella parte superiore del contenitore padre.|**NON** utilizzare se non è associato a un intero contenitore.|
|Filatore (anello di avanzamento)|Processo associato all'interfaccia utente contestuale o in cui lo spazio è una considerazione.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.||
|Barra informazioni|Messaggi associati all'interfaccia utente contestuale. Consultate [Barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**NON** utilizzare più barre informazioni quando è necessario indicare più processi. Utilizzare invece le barre di stato in pila.|
|Finestra di output|Notifica temporanea: processo a livello di app di cui l'utente vorrà **esaminare** i dettagli dopo il completamento.|**NON** utilizzare per le informazioni che devono essere mantenute tra le sessioni.|
|File di registro|Abbinato a notifica intransigente nei casi in cui è importante **salvare** i dettagli dopo il completamento.||
|Barra di stato|Notifica temporanea: processo a livello di app di cui l'utente **non avrà bisogno** di dettagli dopo il completamento.<br /><br /> Include la barra di avanzamento incorporata.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.||

### <a name="progress-indicator-types"></a>Tipi di indicatori di stato

#### <a name="progress-bars"></a>Barre di avanzamento

##### <a name="indeterminate"></a>Indeterminato
 ![Indicatore di stato indeterminato](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Indicatore di stato indeterminato**

 "Indeterminato" indica che non è possibile determinare l'avanzamento complessivo di un'operazione o di un processo. Usare barre di stato indeterminato per le operazioni che richiedono una quantità illimitata di tempo o che accedono a un numero sconosciuto di oggetti. Utilizzare una descrizione testuale per accompagnare ciò che sta accadendo. Utilizzare i timeout per assegnare limiti alle operazioni basate sul tempo. Le barre di stato indeterminato usano le animazioni per mostrare che lo stato di avanzamento è in corso, ma non forniscono altre informazioni. Non scegliere una barra di avanzamento indeterminata basata solo sulla possibile mancanza di precisione.

##### <a name="determinate"></a>Determinato
 ![Indicatore di stato determinato](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Indicatore di stato determinato**

 "Determinate" significa che un'operazione o un processo richiede una quantità limitata di tempo, anche se tale quantità di tempo non può essere prevista con precisione. Indicare chiaramente il completamento. Non lasciare che una barra di avanzamento vada al 100% a meno che l'operazione non sia stata completata. L'animazione dell'indicatore di stato determina le aree da sinistra a destra si sposta da 0 a 100%.

 Non spostare mai indietro l'indicatore di stato durante un'operazione. La barra deve muoversi in avanti costantemente all'inizio dell'operazione e raggiungere il 100% quando termina. Il punto della barra di avanzamento consiste nel dare all'utente un'idea della durata dell'intera operazione, indipendentemente dal numero di passaggi coinvolti.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Report simultanei (barre di stato in pila)
 Se un'operazione richiederà molto tempo, ad esempio diversi minuti, è possibile utilizzare due barre di avanzamento, una che mostra lo stato di avanzamento complessivo di un'operazione e un'altra per la progressione del passaggio corrente. Ad esempio, se un programma di installazione sta copiando molti file, è possibile utilizzare una barra di avanzamento per indicare la durata dell'intero processo, mentre un secondo può indicare la percentuale del file o della directory corrente da copiare. Non segnalare più di cinque operazioni o processi simultanei utilizzando barre di stato in pila. Se si dispone di più di cinque operazioni o processi simultanei da segnalare, utilizzare una finestra di dialogo modale con un pulsante Annulla e riportare i dettagli dello stato di avanzamento nella finestra di output.

##### <a name="textual-descriptions"></a>Descrizioni testuali
 Utilizzare una descrizione testuale per accompagnare ciò che sta accadendo e il tempo stimato per il completamento. Se è impossibile determinare la durata di un'operazione, una scelta migliore per fornire un feedback potrebbe essere un'icona animata anziché una barra di avanzamento.

 Visual Studio provides a standard progress bar in the status bar that can be used by any product integrated into Visual Studio. Per le descrizioni testuali di ciò che accade mentre la barra di avanzamento è animata, il testo della barra di stato può essere aggiornato.

#### <a name="other-progress-indicators"></a>Altri indicatori di avanzamento

##### <a name="ants-animated-horizontal-dots"></a>Formiche (punti orizzontali animati)
 ![Ant dello stato](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Formiche", punti orizzontali animati, forniscono un riferimento visivo per un processo di server di andata e ritorno indeterminato.

##### <a name="spinner-progress-ring"></a>Filatore (anello di avanzamento)
 ![Casella di selezione dello stato](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 La casella di selezione (nota anche come "anello di stato") è un indicatore di stato indeterminato utilizzato principalmente in relazione all'interfaccia utente contestuale. Visualizzare una casella di selezione in prossimità del contenuto correlato, ad esempio un'intestazione di categoria testuale, un messaggio o un controllo.

##### <a name="cursor-feedback"></a>Feedback del cursore
 Per le operazioni che richiedono da 2 a 7 secondi, fornire un feedback del cursore. In genere, ciò significa utilizzare il cursore di attesa fornito dal sistema operativo. Per istruzioni, vedere l'articolo msdn [Msdn Cursors.Wait Property](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Posizioni dell'indicatore di stato

##### <a name="status-bar"></a>Barra di stato
 La barra di stato offre all'applicazione una posizione in cui visualizzare messaggi e informazioni utili all'utente senza interrompere il lavoro dell'utente. In genere visualizzato nella parte inferiore di una finestra, lo stato per lo stato sarà un riquadro della descrizione comandi che include un messaggio sulla misura dello stato di avanzamento in combinazione con un indicatore di stato.

 ![Barra di stato con indicatore di stato](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barra di stato con indicatore di stato**

 ![Barra di stato con messaggistica](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barra di stato con descrizione testuale**

##### <a name="infobar"></a>Barra informazioni
 Analogamente alla barra di stato, la barra informazioni fornisce la notifica contestuale e la messaggistica, che possono anche essere abbinate a indicatori di stato indeterminati, ad esempio la barra di stato o la casella di selezione. La barra informazioni non deve fornire un avanzamento del livello granulare o un'indicazione di avanzamento determinato. Consultate [Barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barra informazioni con indicatore di stato e messaggistica](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barra informazioni con barra di avanzamento e descrizione testuale**

 ![Barra informazioni in una finestra](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Inline
 L'indicazione sullo stato inline può essere rappresentata da uno qualsiasi dei tipi di caricatore di stato. In genere l'indicatore di stato è associato alla messaggistica, ma questo non è un requisito.

 ![Casella di selezione dello stato inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner combinato con descrizione testuale**

 ![Indicatori di stato in pila inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Determinate barre di avanzamento in pila**

 ![Messaggistica sullo stato inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Testo in linea di Esplora server: Aggiornamento in corso...**

##### <a name="tool-windows"></a>Finestre degli strumenti
 L'indicazione di avanzamento globale è rappresentata da una barra di avanzamento indeterminata posizionata direttamente sotto la barra degli strumenti.

 ![Indicatore di stato indeterminato globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Indicatore di stato indeterminato globale di Team Explorer**

##### <a name="dialogs"></a>Finestre di dialogo
 Le finestre di dialogo possono contenere qualsiasi tipo di caricatore di stato. Gli indicatori di avanzamento possono essere abbinati alla messaggistica e combinati con più livelli di indicazione dello stato di avanzamento per rappresentare processi granulari e secondari.

 ![Finestra di dialogo con più tipi di indicatori di stato](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Finestra di dialogo di Visual Studio con processi simultanei e più tipi di indicatore di statoVisual Studio dialog with concurrent processes and multiple progress indicator types**

 ![Finestra di dialogo con caricatore dello stato e messaggistica](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Finestra di dialogo di Visual Studio con il caricatore di stato e l'esecuzione di comandi inline di messaggistica**

##### <a name="document-well"></a>Documento bene
 Il documento può visualizzare anche più tipi di caricatore di stato in combinazione con i controlli.

 ![Messaggistica sullo stato nella finestra del documento](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barra di avanzamento indeterminato sotto la barra degli strumenti**

##### <a name="output-window"></a>Finestra di output
 La finestra Output è appropriata per la gestione dell'avanzamento del processo e dello stato di avanzamento in corso tramite messaggi di testo in linea. È necessario utilizzare la barra di stato insieme a qualsiasi report sullo stato di avanzamento della finestra di output.

 ![Messaggistica sullo stato nella finestra di output](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Finestra di output con stato del processo in corso e messaggistica di attesa**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Barre informazioni

### <a name="overview"></a>Panoramica
 Le barre informazioni forniscono all'utente un indicatore vicino al proprio punto di attenzione e l'utilizzo del controllo della barra informazioni condivisa garantisce coerenza nell'aspetto visivo e nell'interazione.

 ![Barra informazioni](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Barre informazioni in Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Usi appropriati per una barra informazioni

- Per dare all'utente un messaggio non bloccante ma importante rilevante per il contesto corrente

- Per indicare che l'interfaccia utente si trova in un determinato stato o condizione che comporta alcune implicazioni di interazione, ad esempio il debug cronologicoTo indicate that the UI is in a certain state or condition that carries some interaction implications, such as historical debugging

- Per notificare all'utente che il sistema ha rilevato problemi, ad esempio quando un'estensione causa problemi di prestazioni

- Per fornire all'utente un modo per eseguire facilmente un'azione, ad esempio quando l'editor rileva che un file contiene tabulazioni e spazi misti

##### <a name="do"></a>Eseguire queste operazioni:

- Mantenere il testo del messaggio della barra informazioni breve e al punto.

- Mantenere il testo su collegamenti e pulsanti concisi.

- Assicurarsi che le opzioni di "azione" fornite agli utenti siano minime, mostrando solo le azioni necessarie.

##### <a name="dont"></a>Non:

- Utilizzare una barra informazioni per offrire comandi standard che devono essere inseriti in una barra degli strumenti.

- Utilizzare una barra informazioni al posto di una finestra di dialogo modale.

- Creare un messaggio mobile all'esterno di una finestra.

- Usa più barre informazioni in diverse posizioni all'interno della stessa finestra.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>È possibile visualizzare più barre informazioni contemporaneamente?
 Sì, è possibile visualizzare più barre informazioni contemporaneamente. Essi saranno visualizzati in ordine primo arrivato, primo servito con la prima barra informazioni che mostra in alto e barre informazioni aggiuntive mostrate di seguito.

 L'utente vedrà un massimo di tre barre informazioni alla volta, dopo di che, se sono disponibili più barre informazioni, l'area della barra informazioni diventerà scorrevole.

### <a name="creating-an-infobar"></a>Creazione di una barra informazioni
 La barra informazioni è di quattro sezioni, da sinistra a destra:

- **Icona:** Qui devi aggiungere qualsiasi icona che desideri visualizzare per la barra informazioni, ad esempio un'icona di avviso.

- **Testo:** È possibile aggiungere testo per descrivere lo scenario/situazione in cui si trova l'utente, insieme ai collegamenti all'interno del testo, se necessario. Ricordarsi di mantenere il testo conciso.

- **Azioni:** Questa sezione dovrebbe contenere collegamenti e pulsanti per le azioni che l'utente può eseguire nella barra informazioni.

- **Pulsante Chiudi:** L'ultima sezione a destra può avere un pulsante di chiusura.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creazione di una barra informazioni standard nel codice gestitoCreating a standard infobar in managed code
 Il InfoBarModel classe può essere utilizzata per creare un'origine dati per una barra informazioni. Utilizzare uno di questi quattro costruttori:Use one of these four constructors:

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 Ecco un esempio che crea un InfoBarModel con testo con un collegamento ipertestuale, un pulsante di azione e un'icona.

 ![Barra informazioni con collegamento ipertestuale](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>Creazione di una barra informazioni standard nel codice nativoCreating a standard infobar in native code
 Implementare il IVsInfoBar interfaccia per fornire una barra informazioni dal codice nativo.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Ottenere una barra informazioni UIElement da una barra informazioniGetting an infobar UIElement from an infobar
 Il InfoBarModel o IVsInfoBar implementazione sono modelli di dati che devono essere trasformati in un UIElement per essere visualizzati nell'interfaccia utente. Oggetto UIElement può essere recuperato con il SVsInfoBarUIFactory/IVsInfoBarUIFactory servizio.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>Posizione
 Le barre informazioni possono essere visualizzate in una o più delle seguenti posizioni:

- Finestre degli strumenti

- All'interno di una scheda del documento

> [!IMPORTANT]
> È possibile posizionare una barra informazioni per dare un messaggio sul contesto globale. Questo apparirebbe tra le barre degli strumenti e il documento bene. Questa operazione non è consigliata perché causa problemi con "salto e scatto" dell'IDE e deve essere evitato a meno che non sia assolutamente necessario e appropriato.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Inserimento di una barra informazioni in un ToolWindowPane
 Il ToolWindowPane.AddInfoBar(IVsInfoBar) metodo può essere utilizzato per aggiungere una barra informazioni a una finestra degli strumenti. Questa API può aggiungere un IVsInfoBar (di cui InfoBarModel è un'implementazione predefinita) o un IVsUIElement.This API can either add an IVsInfoBar (of which InfoBarModel is a default implementation), or an IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Inserimento di una barra informazioni in un documento o non in un toolWindowPane
 To place an infobar into any IVsWindowFrame, use the VSFPROPID_InfoBarHost property to get the IVsInfoBarHost for the frame, and then add the infobar UIElement.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>Posizionamento di una barra informazioni nella finestra principale
 Per inserire una barra informazioni nella finestra principale, usare il VSSPROPID_MainWindowInfoBarHost del servizio IVsShell per ottenere IVsInfoBarHost della finestra principale e quindi aggiungere la barra informazioni UIElement.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Saprò quando l'utente esegue un'azione nella barra informazioni?
 Sì, restituiremo ogni azione evento all'autore della barra informazioni. Spetta quindi all'autore della barra informazioni eseguire un'azione nell'IDE in base alla selezione dell'utente nella barra informazioni. Le barre informazioni verranno rimosse automaticamente dall'host su cui è stato fatto clic sul pulsante Chiudi, ma sono necessarie ulteriori operazioni se è necessario rimuovere altre barre informazioni dopo la chiusura. Anche la telemetria dovrà essere registrata in modo indipendente da ogni barra informazioni.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Ricezione di eventi della barra informazioni in un ToolWindowPaneReceiving infobar events in a ToolWindowPane
 ToolWindowPane dispone di due eventi per le barre informazioni. Il InfoBarClosed evento viene generato quando una barra informazioni nel ToolWindowPane viene chiuso. Il InfoBarActionItemClicked evento viene generato quando si fa clic su un collegamento ipertestuale o un pulsante all'interno della barra informazioni.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Ricezione di eventi della barra informazioni direttamente da UIElementReceiving infobar events directly from the UIElement
 IVsInfoBarUIElement.Advise può essere utilizzato per sottoscrivere gli eventi direttamente da UIElement di una barra informazioni. Implementazione IVsInfoBarUIEvents consentirà all'autore di ricevere gli eventi di chiusura e clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Convalida degli errori
 Quando un utente immette informazioni non accettabili, ad esempio quando un campo obbligatorio viene ignorato o quando i dati vengono immessi nel formato non corretto, è preferibile utilizzare la convalida del controllo o il feedback vicino al controllo anziché utilizzare una finestra di dialogo di errore popup di blocco.

### <a name="field-validation"></a>Convalida campi
 La convalida di form e campi è costituita da tre componenti: un controllo, un'icona e una descrizione comando. Mentre diversi tipi di controlli possono utilizzare questo, una casella di testo verrà utilizzata come esempio.

 ![Convalida del campo &#40;&#41;vuoto](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Se il campo è obbligatorio, deve ** \<** essere presente il testo della filigrana che `Environment.ControlEditRequiredBackground`indica Obbligatorio>e lo sfondo del campo deve essere giallo chiaro (VSColor: ) e il primo piano deve essere grigio (VSColor: `Environment.ControlEditRequiredHintText`):

 ![Convalida campo con etichetta "Obbligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Il programma può determinare che il controllo è in uno stato di *contenuto non valido immesso* quando lo stato attivo viene spostato su un altro controllo o quando l'utente fa clic su un pulsante di commit [OK] o quando l'utente salva il documento o il form.

 Quando viene determinato lo stato del contenuto non valido, viene visualizzata un'icona all'interno del controllo o accanto a esso. Una descrizione comando che descrive l'errore dovrebbe essere visualizzata al passaggio del mouse dell'icona o del controllo. Inoltre, un bordo di 1 pixel dovrebbe essere visualizzato intorno al controllo che sta creando lo stato non valido.

 ![Specifiche del layout della convalida campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Specifiche di layout per la convalida dei campi**

#### <a name="acceptable-variations-for-icon-location"></a>Variazioni accettabili per la posizione dell'icona
 Ci sono innumerevoli casi unici in cui gli utenti devono essere informati sugli errori di convalida. Considerando il tipo di controllo e la configurazione dell'interfaccia utente, scegliere il posizionamento dell'icona appropriato alla situazione.

 ![Posizioni accettabili per le icone](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variazioni accettabili per le posizioni delle icone di convalida dei campiAcceptable variations for field validation icon locations**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Convalida che richiede un round trip a un server o a una connessione di rete
 In alcuni casi, è necessario un round trip al server per verificare il contenuto e sarebbe importante mostrare gli stati di avanzamento, verifica e errore dell'utente. La figura seguente mostra un esempio di questo caso e l'interfaccia utente consigliata.

 ![Convalida che prevede un round trip a un server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Convalida che prevede un round trip a un server**

 Si noti che è necessario fornire un adeguato spazio disponibile a destra del controllo per poter contenere il comando "Verifica in corso..." e il testo "Riprova".

#### <a name="in-place-warning-text"></a>Testo di avviso sul posto
 Quando è disponibile spazio per inserire il messaggio di errore vicino al controllo in uno stato di errore, è preferibile utilizzare la sola descrizione comando.

 ![In&#45;luogo di avviso](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Testo di avviso sul posto**

#### <a name="watermarks"></a>Filigrane
 A volte un intero controllo o finestra è in uno stato di errore. In questo caso, utilizzare una filigrana per indicare l'errore.

 ![Filigrana](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Convalida del campo Filigrana**
