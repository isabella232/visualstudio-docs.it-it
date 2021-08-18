---
title: Notifiche e stato di avanzamento per Visual Studio | Microsoft Docs
description: Informazioni su diversi modi per informare gli utenti di ciò che accade in Visual Studio sulle attività di sviluppo del software.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e4c42692a4540febbcce4355f0324355a92e362b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144470"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notifiche e avanzamento per Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Sistemi di notifica

### <a name="overview"></a>Panoramica
 Esistono diversi modi per informare l'utente di ciò che accade in Visual Studio relative alle attività di sviluppo del software.

 Quando si implementa qualsiasi tipo di notifica:

- **Mantenere il numero di notifiche al numero effettivo** minimo. I messaggi di notifica devono essere applicati alla maggior parte Visual Studio utenti o a utenti di un'area di funzionalità o funzionalità specifica. Un uso eccessivo delle notifiche può eseguire il sidetracking dell'utente o diminuire la facilità d'uso percepita del sistema.

- **Assicurarsi di presentare messaggi chiari** e utilizzabili che l'utente può usare per richiamare il contesto appropriato per effettuare scelte più complesse ed eseguire ulteriori azioni.

- **Presentare messaggi sincroni e asincroni in modo appropriato.** Le notifiche sincrone indicano che qualcosa richiede attenzione immediata, ad esempio quando un servizio Web si arresta in modo anomalo o viene generata un'eccezione di codice. L'utente deve essere informato immediatamente di tali situazioni in modo da richiederne l'input, ad esempio in una finestra di dialogo modale. Le notifiche asincrone sono quelle che l'utente deve conoscere, ma su cui non è necessario intervenire immediatamente, ad esempio quando un'operazione di compilazione viene completata o una distribuzione del sito Web. Questi messaggi devono essere più ambientali e non interrompere il flusso di attività dell'utente.

- **Usare le finestre di dialogo modali** solo quando necessario per impedire all'utente di eseguire altre azioni prima di riconoscere il messaggio o prendere una decisione presentata nel dialogo.

- **Rimuovere le notifiche di ambiente quando non sono più valide.** Non richiedere all'utente di ignorare una notifica se ha già intrapreso un'azione per risolvere il problema per cui ha avuto notifica.

- **Tenere presente che le notifiche possono causare correlazioni false.** Gli utenti potrebbero pensare che una o più azioni hanno attivato una notifica quando in realtà non esiste alcuna relazione causale. Essere chiari nel messaggio di notifica sul contesto, il trigger e l'origine della notifica.

### <a name="choosing-the-right-method"></a>Scelta del metodo appropriato
 Usare questa tabella per facilitare la scelta del metodo appropriato per notificare il messaggio all'utente.

|Metodo|Uso|Non utilizzare|
|------------|---------|----------------|
|[Finestre di dialogo di messaggi di errore modali](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Usare quando è necessaria una risposta dell'utente prima di procedere.|Non usare quando non è necessario bloccare l'utente e interrompere il flusso. Evitare di usare finestre di dialogo modali se è possibile visualizzare il messaggio in un altro modo, meno intrusivo.|
|[Barra di stato dell'IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Usare quando sono presenti informazioni testuali di ambiente relative allo stato di un processo.|Non usare da solo. Ideale in combinazione con un altro meccanismo di feedback.|
|[Barra informazioni incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|In una finestra degli strumenti o in una finestra del documento usare per notificare lo stato di avanzamento, lo stato di errore, i risultati e/o le informazioni utilizzabili.|Non usare se le informazioni non sono rilevanti per la posizione in cui è posizionata la barra informazioni.<br /><br /> Non usare all'esterno di una finestra documento/strumento.|
|[Modifiche apportate al cursore del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Può essere usato per notificare che è in corso un processo. Utilizzato anche per notificare la modifica dello stato del mouse, ad esempio quando è in corso il trascinamento della selezione o che il cursore del mouse è in una determinata modalità, ad esempio la modalità di disegno.|Non usare per le brevi modifiche dello stato di avanzamento o se è probabile che il cursore svolazza ( ad esempio, quando è associato a parti di un processo più lungo anziché all'intero processo).|
|[Indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Usare quando è necessario segnalare lo stato di avanzamento (determinato o indeterminato). Sono disponibili diversi tipi di indicatori di stato e un utilizzo specifico per ognuno di essi. Vedere [Indicatori di stato.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)||
|[Finestra delle notifiche di Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La finestra Notifiche non è estensibile pubblicamente. Tuttavia, viene usato per comunicare una gamma di messaggi su Visual Studio, inclusi i problemi critici relativi alla licenza e le notifiche informativi degli aggiornamenti Visual Studio o ai pacchetti.|Non usare per altri tipi di notifiche.|
|[Elenco errori](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando il problema riguarda direttamente la soluzione attualmente aperta dell'utente che ha un problema (errore,avviso/informazioni), potrebbe essere necessario intervenire sul codice.<br /><br /> Ciò include, ad esempio:<br /><br /> - Messaggi del compilatore (errore/avviso/informazioni)<br /><br /> - Messaggi di diagnostica/analizzatore del codice relativi al codice<br /><br /> - Messaggi di compilazione<br /><br /> Può essere appropriato per i problemi relativi ai file di progetto o di soluzione, ma si consideri prima Esplora soluzioni'indicazione.|Non usare per gli elementi che non hanno alcuna relazione con il codice della soluzione aperta dell'utente.|
|Notifiche dell'editor: Lampadina|Usare quando è disponibile una correzione per risolvere un problema esistente nel file aperto.<br /><br /> Si noti che la lampadina deve essere usata anche per l'hosting di azioni rapide eseguite sul codice dell'utente su richiesta, ad esempio i refactoring, ma in questo caso non verrà visualizzato "stile di notifica".|Non utilizzare per gli elementi che non hanno alcuna relazione con il file aperto.|
|Notifiche dell'editor: controllo a ondza|Usare questa opzione per avvisare l'utente di un problema relativo a un intervallo specifico del codice aperto, ad esempio una linea onnivaia rossa per gli errori.|Non usare per gli elementi che non sono correlati a un intervallo specifico del codice aperto.|
|[Barre di stato incorporate](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Usare per fornire lo stato correlato al contenuto o al processo all'interno del contesto di una finestra degli strumenti, di una finestra del documento o di una finestra di dialogo specifica.|Non usare per notifiche generali sui prodotti, processi o elementi che non hanno alcuna relazione con il contenuto all'interno della finestra specifica.|
|[Windows sulla barra delle applicazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Usare per visualizzare le notifiche per i processi out-of-process o le applicazioni complementari.|Non usare per le notifiche rilevanti per l'IDE.|
|[Bolle di notifica](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Usare per notificare un processo remoto o una modifica **all'esterno** dell'IDE.|Non usare come mezzo per notificare all'utente i processi **all'interno dell'IDE.**|

### <a name="notification-methods"></a>Metodi di notifica

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Finestre di dialogo di messaggi di errore modali
 Una finestra di dialogo di messaggio di errore modale viene usata per visualizzare un messaggio di errore che richiede la conferma o l'azione dell'utente.

 ![Messaggio di errore modale](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Finestra di dialogo di messaggio di errore modale che avvisa l'utente di una stringa di connessione non valida a un database**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Barra di stato dell'IDE
 La probabilità che gli utenti notino il testo della barra di stato è correlata all'esperienza completa del computer e all'esperienza specifica con Windows piattaforma. La Visual Studio clienti tende a essere esperta in entrambe le aree, anche se anche Windows utenti potrebbero perdere le modifiche nella barra di stato. Pertanto, la barra di stato è più adatta per scopi in forma informativo o come segnale ridondante per le informazioni presentate altrove. Qualsiasi tipo di informazioni critiche che l'utente deve risolvere immediatamente deve essere fornito in una finestra di dialogo o nella finestra degli strumenti Notifiche.

 La Visual Studio di stato è progettata per consentire la visualizzazione di diversi tipi di informazioni. È suddiviso in aree per il feedback, la finestra di progettazione, l'indicatore di stato, l'animazione e il client.

 L'area di feedback e l'area della finestra di progettazione sono sempre visibili. L'indicatore di stato e le aree di animazione sono sempre dinamici e basati sul contesto utente. L'area della finestra di progettazione ha una larghezza statica determinata dalla lunghezza della stringa estratta da una risorsa di supporto per il messaggio di testo. In questo modo la localizzazione può ridimensionare la larghezza senza richiedere una modifica al codice. Per l'inglese, la larghezza di questa stringa è di circa 220 pixel. L'area di progettazione si comporterà normalmente e l'area di feedback asserirà lo spazio rimanente.

 La barra di stato viene colorata anche per aggiungere interesse visivo e valore funzionale comunicando varie modifiche dello stato dell'IDE, ad esempio quando l'IDE è in modalità di debug.

 ![Modifiche ai colori della barra di stato dell'IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Colori della barra di stato dell'IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Barra informazioni incorporata
 È possibile usare una barra informazioni nella parte superiore di una finestra del documento o di una finestra degli strumenti per informare l'utente di uno stato o di una condizione. Può anche offrire comandi in modo che l'utente possa intervenire facilmente. La barra informazioni è un controllo della shell standard. Evitare di creare codice personalizzato, che agirà e apparirà incoerente con altri utenti nell'IDE. Per [informazioni dettagliate sull'implementazione](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) e indicazioni sull'utilizzo, vedere Barre informazioni.

 ![Barra informazioni incorporata](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Barra informazioni incorporata in una finestra del documento, che avvisa l'utente che l'IDE è in modalità di debug cronologico e che l'editor non risponde come nella modalità di debug standard.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Modifiche apportate al cursore del mouse
 Quando si modifica il cursore del mouse, usare i colori associati al servizio VSColor e già associati al cursore. Le modifiche del cursore possono essere usate per indicare un'operazione in corso, nonché per selezionare le zone in cui l'utente passa il mouse su una destinazione che può essere trascinata, rilasciata o usata per selezionare un oggetto.

 Usare il cursore del mouse occupato/in attesa solo quando tutto il tempo cpu disponibile deve essere riservato per un'operazione, impedendo all'utente di esprimere altri input. Nella maggior parte dei casi con applicazioni ben scritte che usano il multithreading, i casi in cui agli utenti viene impedito di eseguire altre operazioni dovrebbero essere rari.

 Tenere presente che le modifiche del cursore sono utili come segnale ridondante per le informazioni presentate altrove. Non basarsi su una modifica del cursore come unico modo di comunicare con l'utente, soprattutto quando si tenta di comunicare un elemento critico che l'utente deve affrontare.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indicatori di stato
 Gli indicatori di stato sono importanti per fornire all'utente commenti e suggerimenti durante i processi il cui completamento può richiedere più di pochi secondi. Gli indicatori di stato possono essere visualizzati sul posto (vicino al punto di avvio dell'azione in corso), in una barra di stato incorporata, in una finestra di dialogo modale o nella barra Visual Studio stato. Seguire le indicazioni riportate in [Indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) relativi all'uso e all'implementazione.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio Finestra Notifiche
 La Visual Studio Notifiche notifiche notifica agli sviluppatori informazioni su licenze, ambiente (Visual Studio), estensioni e aggiornamenti. Gli utenti possono ignorare le singole notifiche o scegliere di ignorare determinati tipi di notifiche. L'elenco delle notifiche ignorate viene gestito in una **pagina Strumenti > opzioni.**

 La finestra Notifiche non è attualmente estendibile.

 ![Finestra delle notifiche di Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio Finestra degli strumenti Notifiche**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Elenco errori
 Una notifica all'interno dell'elenco errori indica gli errori e gli avvisi che si sono verificati durante la compilazione e o il processo di compilazione e consente all'utente di passare all'errore di codice specifico nel codice.

 ![Elenco errori](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Elenco errori in Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Barre di stato incorporate
 Poiché la barra di stato dell'IDE è dinamica, con il contesto dell'area client impostato sulla finestra del documento attivo e l'aggiornamento delle informazioni sul contesto dell'utente e/o sulle risposte di sistema, è difficile mantenere una visualizzazione continua delle informazioni o fornire lo stato nei processi asincroni a lungo termine. Ad esempio, la barra di stato dell'IDE non è appropriata per le notifiche dei risultati dell'esecuzione dei test per più esecuzioni e/o per le selezioni di elementi immediatamente utilizzabili. È importante conservare tali informazioni sullo stato nel contesto del documento o della finestra degli strumenti in cui l'utente effettua una selezione o avvia un processo.

 ![Barra di stato incorporata](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barra di stato incorporata in Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Windows sulla barra delle applicazioni
 L Windows di notifica si trova accanto all'orologio di sistema sulla barra Windows barra delle applicazioni. Molte utilità e componenti software forniscono icone in quest'area in modo che l'utente possa ottenere un menu di scelta rapida per le attività a livello di sistema, ad esempio la modifica della risoluzione dello schermo o l'acquisizione di aggiornamenti software.

 Le notifiche a livello di ambiente devono essere evase nell'hub notifiche Visual Studio, non nell'area Windows notifica.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bolle di notifica
 Le bolle di notifica possono essere visualizzate come informazioni all'interno di un editor/finestra di progettazione o come parte dell'area Windows notifica. L'utente considera queste bolle come problemi che possono essere risolti in un secondo momento, un vantaggio per le notifiche non critiche. Le bolle non sono appropriati per le informazioni critiche che l'utente deve risolvere immediatamente. Se si usano bolle di notifica in Visual Studio, seguire le linee [guida Windows Desktop per le bolle di notifica](/windows/desktop/uxguide/mess-notif).

 ![Fumetto della notifica](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bolla di notifica nell'area Windows notifica usata per Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indicatori di stato

### <a name="overview"></a>Panoramica
 Gli indicatori di stato sono una parte importante di un sistema di notifica per fornire all'utente commenti e suggerimenti. L'utente viene a sapere quando verranno completati i processi e le operazioni. I tipi di indicatore familiari includono barre di stato, cursori rotanti e icone animate. Il tipo e la posizione di un indicatore di stato dipendono dal contesto, inclusi gli elementi segnalati e il tempo necessario per il completamento del processo o dell'operazione.

#### <a name="factors"></a>Fattori
 Per determinare il tipo di indicatore appropriato, è necessario determinare i fattori seguenti.

1. **Intervallo:** periodo di tempo necessario per l'operazione

2. **Modalità: indica se l'operazione** è modale per l'ambiente (blocca l'interfaccia utente fino al completamento del processo)

3. **Persistente/temporaneo:** indica se il risultato finale dello stato di avanzamento deve essere segnalato e/o visualizzabile in un secondo momento

4. **Determinato/Indeterminato: indica** se l'ora di fine e lo stato di avanzamento dell'operazione possono essere calcolati

5. **Posizione grafica/testuale:** se lo stato di avanzamento o il processo viene acquisito inline, nel corpo di un messaggio o in un controllo specifico, ad esempio il controllo Tree

6. **Prossimità: indica** se lo stato di avanzamento deve essere vicino all'interfaccia utente a cui è correlato. Ad esempio, può essere nella barra di stato, che potrebbe essere lontano o deve essere vicino al pulsante che ha avviato il processo?

#### <a name="determinate-progress"></a>Stato determinato

|Tipo di stato|Quando e come usare|Note|
|-------------------|-------------------------|-----------|
|Indicatore di stato (determinato)|Durata prevista di >5 secondi.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.|**NON incorporare testo nell'animazione.**|
|Barra informazioni|Messaggistica associata all'interfaccia utente contestuale. Vedere [Barre informazioni.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)<br /><br /> Può includere una descrizione testuale dei dettagli del processo.|**NON usare** più barre informazioni quando è necessario indicare più processi. In alternativa, usare gli barre di stato in pila.|
|Finestra di output|Notifica temporanea: processo a livello di app di cui l'utente **vuole esaminare i** dettagli dopo il completamento.|**NON usare se l'utente** dovrà fare riferimento ai dati in un secondo momento.|
|File di registro|Abbinata alla notifica intransiente nei casi in cui è importante salvare **i dettagli** dopo il completamento.||
|Status bar|Notifica temporanea: processo a livello di app di cui **l'utente non avrà bisogno di** dettagli dopo il completamento.<br /><br /> Include un indicatore di stato incorporato.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.||

#### <a name="indeterminate-progress"></a>Stato di avanzamento indeterminato

|Tipo di stato|Quando e come usare|Note|
|-------------------|-------------------------|-----------|
|Indicatore di stato (indeterminato)|Durata prevista di >5 secondi.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.|**NON incorporare testo nell'animazione.**|
|Formiche (punti orizzontali animati)|Round trip al server.<br /><br /> Posizionato vicino al punto di contesto nella parte superiore del contenitore padre.|NON usare se non è padre **dell'intero** contenitore.|
|Spinner (anello di stato)|Processo associato all'interfaccia utente contestuale o in cui lo spazio è una considerazione.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.||
|Barra informazioni|Messaggistica associata all'interfaccia utente contestuale. Vedere [Barre informazioni.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)|**NON usare** più barre informazioni quando è necessario indicare più processi. In alternativa, usare gli barre di stato in pila.|
|Finestra di output|Notifica temporanea: processo a livello di app di cui l'utente vuole esaminare **i** dettagli dopo il completamento.|**NON usare per** le informazioni che devono essere mantenute tra le sessioni.|
|File di registro|Abbinata alla notifica intransiente nei casi in cui è importante salvare **i dettagli** dopo il completamento.||
|Status bar|Notifica temporanea: processo a livello di app di cui **l'utente non avrà bisogno di** dettagli dopo il completamento.<br /><br /> Include l'indicatore di stato incorporato.<br /><br /> Può includere una descrizione testuale dei dettagli del processo.||

### <a name="progress-indicator-types"></a>Tipi di indicatori di stato

#### <a name="progress-bars"></a>Barre di stato

##### <a name="indeterminate"></a>Indeterminato
 ![Indicatore di stato indeterminato](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Indicatore di stato indeterminato**

 "Indeterminato" indica che non è possibile determinare lo stato complessivo di un'operazione o di un processo. Usare gli indicatore di stato indeterminati per le operazioni che richiedono un periodo di tempo illimitato o che accedono a un numero sconosciuto di oggetti. Usare una descrizione testuale per accompagnare ciò che accade. Usare i timeout per assegnare limiti alle operazioni basate sul tempo. Gli indicatore di stato indeterminati usano animazioni per mostrare lo stato di avanzamento, ma non forniscono altre informazioni. Non scegliere un indicatore di stato indeterminato basato solo sulla possibile mancanza di accuratezza.

##### <a name="determinate"></a>Determinato
 ![Indicatore di stato determinato](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Indicatore di stato determinato**

 "Determinate" significa che un'operazione o un processo richiede una quantità di tempo delimitata, anche se tale quantità di tempo non può essere stimata in modo accurato. Indicare chiaramente il completamento. Non lasciare che un indicatore di stato passi al 100% a meno che l'operazione non sia stata completata. L'animazione dell'indicatore di stato determinato viene spostata da sinistra a destra da 0 a 100%.

 Non spostare mai l'indicatore di stato indietro durante un'operazione. La barra deve procedere costantemente all'inizio dell'operazione e raggiungere il 100% al termine. Il punto dell'indicatore di stato è dare all'utente un'idea del tempo necessario per l'intera operazione, indipendentemente dal numero di passaggi coinvolti.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Creazione di report simultanei (barre di stato in pila)
 Se un'operazione può richiedere molto tempo, ad esempio alcuni minuti, è possibile usare due barre di stato, una che mostra lo stato di avanzamento complessivo di un'operazione e un'altra per l'avanzamento del passaggio corrente. Ad esempio, se un programma di installazione copia molti file, è possibile usare un indicatore di stato per indicare il tempo necessario per l'intero processo, mentre un secondo può indicare la percentuale del file o della directory corrente da copiare. Non segnalare più di cinque operazioni o processi simultanei usando gli barre di stato in pila. Se si dispone di più di cinque operazioni o processi simultanei da segnalare, usare una finestra di dialogo modale con un pulsante Annulla e segnalare i dettagli di stato al Finestra di output.

##### <a name="textual-descriptions"></a>Descrizioni testuali
 Usare una descrizione testuale per accompagnare ciò che accade e il tempo stimato per il completamento. Se non è possibile determinare il tempo necessario per un'operazione, una scelta migliore per fornire commenti e suggerimenti potrebbe essere un'icona animata anziché un indicatore di stato.

 Visual Studio un indicatore di stato standard nella barra di stato che può essere usato da qualsiasi prodotto integrato in Visual Studio. Per descrizioni testuali di ciò che accade mentre l'indicatore di stato è animato, è possibile aggiornare il testo della barra di stato.

#### <a name="other-progress-indicators"></a>Altri indicatori di stato

##### <a name="ants-animated-horizontal-dots"></a>Formiche (punti orizzontali animati)
 ![Ant dello stato](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 Le "formiche", punti orizzontali animati, forniscono un riferimento visivo per un processo server round trip indeterminato.

##### <a name="spinner-progress-ring"></a>Spinner (anello di stato)
 ![Casella di selezione dello stato](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 La casella di selezione (nota anche come "anello di avanzamento") è un indicatore di stato indeterminato usato principalmente in relazione all'interfaccia utente contestuale. Visualizzare una casella di selezione in prossimità del contenuto correlato, ad esempio un'intestazione di categoria testuale, un messaggio o un controllo.

##### <a name="cursor-feedback"></a>Feedback del cursore
 Per le operazioni che possono richiedere da 2 a 7 secondi, fornire il feedback del cursore. In genere, ciò significa usare il cursore di attesa fornito dal sistema operativo. Per indicazioni, vedere l'articolo di MSDN [Cursors.Wait Property ( Proprietà Cursors.Wait](/dotnet/api/system.windows.input.cursors.wait)).

#### <a name="progress-indicator-locations"></a>Posizioni degli indicatori di stato

##### <a name="status-bar"></a>Status bar
 La barra di stato consente all'applicazione di visualizzare messaggi e informazioni utili senza interrompere il lavoro dell'utente. In genere visualizzato nella parte inferiore di una finestra, lo stato di avanzamento sarà un riquadro descrizione comando che include un messaggio sulla misura dello stato in combinazione con un indicatore dell'indicatore di stato.

 ![Barra di stato con indicatore di stato](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barra di stato con indicatore di stato**

 ![Barra di stato con messaggistica](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barra di stato con descrizione testuale**

##### <a name="infobar"></a>Barra informazioni
 Analogamente alla barra di stato, la barra informazioni fornisce notifiche contestuali e messaggistica, che possono anche essere abbinate a indicatori di stato indeterminati, ad esempio l'indicatore di stato o la casella di selezione. La barra informazioni non deve fornire un livello granulare di avanzamento o un'indicazione specifica dello stato di avanzamento. Vedere [Barre informazioni.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)

 ![Barra informazioni con indicatore di stato e messaggistica](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barra informazioni con indicatore di stato e descrizione testuale**

 ![Barra informazioni in una finestra](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Inline
 L'indicazione dello stato di avanzamento inline può essere rappresentata da uno qualsiasi dei tipi di caricatore di stato. In genere l'indicatore di stato è associato alla messaggistica, ma questo non è un requisito.

 ![Casella di selezione dello stato inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Casella di selezione combinata con descrizione testuale**

 ![Indicatori di stato in pila inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Determinate barre di stato in pila**

 ![Messaggistica sullo stato inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Esplora server testo inline: Aggiornamento in corso...**

##### <a name="tool-windows"></a>Finestre degli strumenti
 L'indicazione dello stato globale è rappresentata da un indicatore di stato indeterminato posizionato direttamente sotto la barra degli strumenti.

 ![Indicatore di stato indeterminato globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer stato indeterminato globale**

##### <a name="dialogs"></a>Finestre di dialogo
 I dialoghe possono contenere qualsiasi tipo di caricatore di stato. Gli indicatori di stato possono essere associati alla messaggistica e combinati con più livelli di indicazione dello stato per rappresentare processi granulari e secondari.

 ![Finestra di dialogo con più tipi di indicatori di stato](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Visual Studio dialogo con processi simultanei e più tipi di indicatori di stato**

 ![Finestra di dialogo con caricatore dello stato e messaggistica](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Visual Studio dialogo con il caricatore di stato e l'esecuzione di comandi inline di messaggistica**

##### <a name="document-well"></a>Documentare l'oggetto
 L'elemento del documento può visualizzare più tipi di caricatore di stato in combinazione con i controlli .

 ![Messaggistica sullo stato nella finestra del documento](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Indicatore di stato indeterminato sotto la barra degli strumenti**

##### <a name="output-window"></a>Finestra di output
 La finestra Output è appropriata per la gestione dell'avanzamento del processo e dello stato di avanzamento continuo tramite la messaggistica testuale inline. È consigliabile usare la barra di stato insieme a qualsiasi report sullo stato della finestra di output.

 ![Messaggistica sullo stato nella finestra di output](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Finestra di output con stato del processo in corso e messaggi di attesa**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Barre informazioni

### <a name="overview"></a>Panoramica
 Le barre informazioni forniscono all'utente un indicatore vicino al proprio punto di attenzione e l'uso del controllo barra informazioni condiviso garantisce coerenza nell'aspetto visivo e nell'interazione.

 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Barre informazioni in Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Usi appropriati per una barra informazioni

- Per fornire all'utente un messaggio non bloccante ma importante pertinente per il contesto corrente

- Per indicare che l'interfaccia utente si trova in un determinato stato o condizione che comporta alcune implicazioni di interazione, ad esempio il debug cronologico

- Per notificare all'utente che il sistema ha rilevato problemi, ad esempio quando un'estensione causa problemi di prestazioni

- Fornire all'utente un modo per eseguire facilmente un'azione, ad esempio quando l'editor rileva che un file contiene tabulazioni e spazi misti

##### <a name="do"></a>Cosa fare

- Mantenere il testo del messaggio della barra informazioni breve e fino al punto.

- Mantenere il testo su collegamenti e pulsanti concisi.

- Assicurarsi che le opzioni di "azione" fornite agli utenti siano minime, visualizzando solo le azioni necessarie.

##### <a name="dont"></a>Non:

- Usare una barra informazioni per offrire comandi standard da inserire in una barra degli strumenti.

- Usare una barra informazioni al posto di una finestra di dialogo modale.

- Creare un messaggio mobile all'esterno di una finestra.

- Usare più barre informazioni in diverse posizioni all'interno della stessa finestra.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>È possibile visualizzare più barre informazioni contemporaneamente?
 Sì, è possibile visualizzare più barre informazioni contemporaneamente. Verranno visualizzati in ordine first-come-first-served con la prima barra informazioni visualizzata nella parte superiore e le barre informazioni aggiuntive visualizzate di seguito.

 L'utente visualizza un massimo di tre barre informazioni alla volta, dopo di che, se sono disponibili altre barre informazioni, l'area della barra informazioni diventa scorrevole.

### <a name="creating-an-infobar"></a>Creazione di una barra informazioni
 La barra informazioni include quattro sezioni, da sinistra a destra:

- **Icona:** Qui è possibile aggiungere qualsiasi icona da visualizzare per la barra informazioni, ad esempio un'icona di avviso.

- **Testo:** È possibile aggiungere testo per descrivere lo scenario o la situazione in cui si trova l'utente, insieme ai collegamenti all'interno del testo, se necessario. Ricordarsi di mantenere il testo conciso.

- **Azioni:** Questa sezione deve contenere collegamenti e pulsanti per le azioni che l'utente può eseguire nella barra informazioni.

- **Pulsante Chiudi:** L'ultima sezione a destra può avere un pulsante chiudi.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creazione di una barra informazioni standard nel codice gestito
 La classe InfoBarModel può essere usata per creare un'origine dati per una barra informazioni. Usare uno di questi quattro costruttori:

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Creazione di una barra informazioni standard in codice nativo
 Implementare l'interfaccia IVsInfoBar per fornire una barra informazioni dal codice nativo.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Recupero di un oggetto UIElement della barra informazioni da una barra informazioni
 L'implementazione di InfoBarModel o IVsInfoBar è un modello di dati che deve essere trasformato in UIElement per essere visualizzato nell'interfaccia utente. È possibile recuperare un oggetto UIElement con il servizio SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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

### <a name="placement"></a>Selezione host
 Le barre informazioni possono essere visualizzate in una o più delle posizioni seguenti:

- Finestre degli strumenti

- All'interno di una scheda del documento

> [!IMPORTANT]
> È possibile posizionare una barra informazioni per fornire un messaggio sul contesto globale. Verrà visualizzato tra le barre degli strumenti e l'oggetto del documento. Questa operazione non è consigliata perché causa problemi con "jump and jump" dell'IDE e deve essere evitata a meno che non sia assolutamente necessario e appropriato.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Posizionamento di una barra informazioni in un oggetto ToolWindowPane
 Il metodo ToolWindowPane.AddInfoBar(IVsInfoBar) può essere usato per aggiungere una barra informazioni a una finestra degli strumenti. Questa API può aggiungere un oggetto IVsInfoBar (di cui InfoBarModel è un'implementazione predefinita) o un oggetto IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Inserimento di una barra informazioni in un documento o in un oggetto non ToolWindowPane
 Per inserire una barra informazioni in qualsiasi IVsWindowFrame, usa la proprietà VSFPROPID_InfoBarHost per ottenere IVsInfoBarHost per il frame e quindi aggiungi l'elemento UIElement della barra informazioni.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Inserimento di una barra informazioni nella finestra principale
 Per inserire una barra informazioni nella finestra principale, usare il VSSPROPID_MainWindowInfoBarHost del servizio IVsShell per ottenere l'oggetto IVsInfoBarHost della finestra principale e quindi aggiungere l'elemento UIElement della barra informazioni.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Saprò quando l'utente esegue un'azione nella barra informazioni?
 Sì, ogni azione dell'evento verrà restituita all'autore della barra informazioni. È quindi l'autore della barra informazioni a eseguire un'azione nell'IDE in base alla selezione dell'utente nella barra informazioni. Le barre informazioni verranno rimosse automaticamente dall'host su cui è stato fatto clic sul pulsante Chiudi, ma sono necessarie operazioni aggiuntive se è necessario rimuovere altre barre informazioni dopo la chiusura. I dati di telemetria dovranno anche essere registrati in modo indipendente da ogni barra informazioni.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Ricezione di eventi della barra informazioni in toolWindowPane
 ToolWindowPane include due eventi per le barre informazioni. L'evento InfoBarClosed viene generato quando viene chiusa una barra informazioni in ToolWindowPane. L'evento InfoBarActionItemClicked viene generato quando si fa clic su un collegamento ipertestuale o un pulsante all'interno della barra informazioni.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Ricezione di eventi della barra informazioni direttamente da UIElement
 IVsInfoBarUIElement.Advise può essere usato per sottoscrivere eventi direttamente da UIElement di una barra informazioni. L'implementazione di IVsInfoBarUIEvents consentirà all'autore di ricevere eventi di chiusura e clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Convalida degli errori
 Quando un utente immette informazioni non accettabili, ad esempio quando un campo obbligatorio viene ignorato o quando i dati vengono immessi in un formato non corretto, è meglio usare la convalida del controllo o il feedback accanto al controllo invece di usare una finestra di dialogo di errore popup di blocco.

### <a name="field-validation"></a>Convalida campi
 La convalida di moduli e campi è costituita da tre componenti: un controllo , un'icona e una descrizione comando. Anche se diversi tipi di controlli possono usare questa funzionalità, verrà usata una casella di testo come esempio.

 ![Convalida dei campi &#40;campi&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Se il campo è obbligatorio, deve essere presente il testo della filigrana e lo sfondo del campo deve essere giallo chiaro (VSColor: ) e il primo piano deve essere grigio **\<Required>** `Environment.ControlEditRequiredBackground` (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Convalida campo con etichetta "Obbligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Il programma può determinare che il  controllo è in uno stato di contenuto non valido immesso quando lo stato attivo viene spostato su un altro controllo o quando l'utente fa clic su un pulsante di commit [OK] o quando l'utente salva il documento o il modulo.

 Quando viene determinato lo stato di contenuto non valido, viene visualizzata un'icona all'interno del controllo o accanto. Al passaggio del mouse dovrebbe essere visualizzata una descrizione comando che descrive l'errore dell'icona o del controllo. Inoltre, dovrebbe essere visualizzato un bordo di 1 pixel intorno al controllo che crea lo stato non valido.

 ![Specifiche del layout della convalida campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Specifiche di layout per la convalida dei campi**

#### <a name="acceptable-variations-for-icon-location"></a>Variazioni accettabili per la posizione dell'icona
 Esistono moltissimi casi univoci in cui gli utenti devono essere informati sugli errori di convalida. Considerando il tipo di controllo e la configurazione dell'interfaccia utente, scegliere il posizionamento dell'icona appropriato per la situazione specifica.

 ![Posizioni accettabili per le icone](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variazioni accettabili per le posizioni delle icone di convalida dei campi**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Convalida che richiede un round trip a un server o a una connessione di rete
 In alcuni casi, è necessario round trip al server per verificare il contenuto e sarebbe importante visualizzare lo stato di avanzamento, la verifica e gli stati di errore dell'utente. La figura seguente mostra un esempio di questo caso e l'interfaccia utente consigliata.

 ![Convalida che prevede un round trip a un server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Convalida che prevede un round trip a un server**

 Si noti che è necessario fornire uno spazio disponibile adeguato a destra del controllo per consentire l'esecuzione del controllo "Verifying..." e il testo "Riprova".

#### <a name="in-place-warning-text"></a>Testo dell'avviso sul posto
 Quando è disponibile spazio per inserire il messaggio di errore vicino al controllo in uno stato di errore, è preferibile usare solo la descrizione comando.

 ![Nella&#45;avviso](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Testo dell'avviso sul posto**

#### <a name="watermarks"></a>Filigrane
 A volte un intero controllo o finestra si trova in uno stato di errore. In questo caso, usare una filigrana per indicare l'errore.

 ![Filigrana](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Convalida del campo limite**
