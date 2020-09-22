---
title: Notifiche e stato
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f17b875f0637883222a633cb1082ad24788d4c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840083"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notifiche e avanzamento per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Sistemi di notifica

### <a name="overview"></a>Panoramica
 Esistono diversi modi per informare l'utente che cosa accade in Visual Studio in relazione alle attività di sviluppo del software.

 Quando si implementa qualsiasi tipo di notifica:

- **Mantieni il numero di notifiche al numero minimo** effettivo. I messaggi di notifica devono essere applicati alla maggior parte degli utenti di Visual Studio o agli utenti di una funzionalità/area funzionale specifica. Un utilizzo eccessivo delle notifiche potrebbe sidetrack l'utente o ridurre la facilità di utilizzo del sistema.

- **Assicurarsi di presentare messaggi chiari** e utilizzabili che l'utente può utilizzare per richiamare il contesto appropriato per effettuare scelte più complesse e intraprendere ulteriori azioni.

- **Presentare messaggi sincroni e asincroni in modo appropriato.** Le notifiche sincrone indicano che un elemento richiede attenzione immediata, ad esempio quando si verifica un arresto anomalo di un servizio Web o viene generata un'eccezione di codice. L'utente deve essere informato immediatamente di queste situazioni in modo che ne richieda l'input, ad esempio in una finestra di dialogo modale. Le notifiche asincrone sono quelle che l'utente deve conoscere, ma non deve necessariamente agire immediatamente, ad esempio quando un'operazione di compilazione viene completata o la distribuzione di un sito Web termina. Questi messaggi devono essere più ambientali e non interrompere il flusso attività dell'utente.

- **Usare le finestre di dialogo modali solo quando necessario per impedire all'utente di eseguire ulteriori azioni** prima di riconoscere il messaggio o di prendere una decisione nella finestra di dialogo.

- **Rimuovere le notifiche di ambiente quando non sono più valide.** Non richiedere all'utente di ignorare una notifica se è già stata eseguita un'azione per risolvere il problema a cui è stata inviata una notifica.

- **Tenere presente che le notifiche possono causare false correlazioni.** Gli utenti potrebbero ritenere che una o più azioni abbiano attivato una notifica quando in realtà non era presente alcuna relazione causale. È possibile deselezionare il messaggio di notifica sul contesto, il trigger e l'origine della notifica.

### <a name="choosing-the-right-method"></a>Scelta del metodo corretto
 Usare questa tabella per facilitare la scelta del metodo appropriato per notificare all'utente il messaggio.

|Metodo|Uso|Non utilizzare|
|------------|---------|----------------|
|[Finestre di dialogo di messaggio di errore modale](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Usare quando è richiesta una risposta utente prima di procedere.|Non usare quando non è necessario bloccare l'utente e interrompere il flusso. Evitare di usare finestre di dialogo modali se è possibile visualizzare il messaggio in un altro modo meno intrusivo.|
|[Barra di stato IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Utilizzare quando sono presenti informazioni testuali di ambiente relative allo stato di un processo.|Non usare autonomamente. Usato in combinazione con un altro meccanismo di feedback.|
|[Barra informazioni incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|In una finestra degli strumenti o in una finestra del documento, utilizzare per notificare lo stato di avanzamento, lo stato di errore, i risultati e/o le informazioni di utilità pratica.|Non usare se le informazioni non sono rilevanti per la posizione in cui viene inserita la barra informazioni.<br /><br /> Non usare al di fuori di una finestra del documento o degli strumenti.|
|[Modifiche del cursore del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Può essere usato per notificare che un processo è in corso. Utilizzato anche per notificare che è presente una modifica dello stato del mouse, ad esempio quando è in corso il trascinamento della selezione o se il cursore del mouse si trova in una determinata modalità, ad esempio la modalità di disegno.|Non utilizzare per le modifiche di stato breve o se è probabile che lo svolazzare del cursore (ad esempio, quando è associato a parti di un processo a esecuzione più lungo anziché all'intero processo).|
|[Indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Usare quando è necessario segnalare lo stato di avanzamento (determinato o indeterminato). Sono disponibili diversi tipi di indicatori di stato e un utilizzo specifico per ciascuno di essi. Vedere [indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Finestra delle notifiche di Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La finestra notifiche non è estendibile pubblicamente. Viene tuttavia usato per comunicare un intervallo di messaggi relativi a Visual Studio, inclusi i problemi critici relativi alla licenza e le notifiche informative degli aggiornamenti a Visual Studio o ai pacchetti.|Non usare per altri tipi di notifiche.|
|[Elenco errori](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando il problema si riferisce direttamente alla soluzione attualmente aperta dell'utente con un problema (errore/avviso/informazioni), potrebbe essere necessario intervenire sul codice.<br /><br /> Questo include, ad esempio:<br /><br /> -Messaggi del compilatore (errore, avviso/informazioni)<br /><br /> -Analizzatore del codice/messaggi di diagnostica sul codice<br /><br /> -Messaggi di compilazione<br /><br /> Potrebbe essere appropriato per i problemi relativi al progetto o ai file di soluzione, ma considerare prima un'indicazione Esplora soluzioni.|Non usare per gli elementi che non hanno alcuna relazione con il codice della soluzione aperta dell'utente.|
|Notifiche dell'Editor: lampadina|Usare quando è disponibile una correzione per risolvere un problema esistente nel file aperto.<br /><br /> Si noti che la lampadina deve essere usata anche per ospitare azioni rapide eseguite sul codice dell'utente su richiesta, ad esempio il refactoring, ma in questo caso non verrà visualizzato "stile notifica".|Non usare per gli elementi che non hanno alcuna relazione con il file aperto.|
|Notifiche dell'Editor: controllo ortografia durante|Usare per avvisare l'utente di un problema con un particolare intervallo del codice aperto (ad esempio, una zigzag rossa per gli errori).|Non usare per gli elementi che non si riferiscono a un particolare intervallo del codice aperto.|
|[Barre di stato incorporate](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilizzare per fornire lo stato correlato al contenuto o al processo nel contesto di una finestra degli strumenti, di una finestra del documento o di una finestra di dialogo specifica.|Non usare per le notifiche generali del prodotto, i processi o gli elementi che non hanno alcuna relazione con il contenuto all'interno della finestra specifica.|
|[Notifiche della barra delle applicazioni di Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Usare per esporre le notifiche per i processi out-of-process o per le applicazioni complementari.|Non usare per le notifiche relative all'IDE.|
|[Bolle di notifica](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Utilizzare per notificare un processo remoto o modificare **all'esterno** dell'IDE.|Non usare come mezzo per notificare all'utente i processi **nell'** IDE.|

### <a name="notification-methods"></a>Metodi di notifica

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Finestre di dialogo di messaggio di errore modale
 Una finestra di dialogo di messaggio di errore modale viene utilizzata per visualizzare un messaggio di errore che richiede la conferma o l'azione dell'utente.

 ![Messaggio di errore modale](../../extensibility/ux-guidelines/media/0901-01-modalerrormessage.png "0901-01_ModalErrorMessage")

 **Finestra di dialogo di messaggio di errore modale che avvisa l'utente di una stringa di connessione non valida a un database**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Barra di stato IDE
 La probabilità che gli utenti notino che il testo della barra di stato è correlato all'esperienza del computer all-around ed esperienza specifica con la piattaforma Windows. La base dei clienti di Visual Studio tende a essere vissuta in entrambe le aree, anche se gli utenti di Windows competenti potrebbero non subire modifiche nella barra di stato. Pertanto, la barra di stato è più adatta a scopo informativo o come spunto ridondante per le informazioni presentate altrove. Qualsiasi tipo di informazione critica che l'utente deve risolvere immediatamente deve essere specificato in una finestra di dialogo o nella finestra degli strumenti di notifica.

 La barra di stato di Visual Studio è progettata per consentire la visualizzazione di diversi tipi di informazioni. È divisa in aree per commenti, progettazione, indicatore di stato, animazione e client.

 L'area feedback e l'area della finestra di progettazione sono sempre visibili. L'indicatore di stato e le aree di animazione sono sempre dinamici e basati sul contesto utente. L'area della finestra di progettazione ha una larghezza statica determinata dalla lunghezza della stringa di cui viene eseguito il pull da una risorsa associata per il messaggio di testo. In questo modo, la localizzazione consente di ridimensionare la larghezza senza richiedere una modifica del codice. Per la lingua inglese, la larghezza di questa stringa è approssimativamente di 220 pixel. L'area della finestra di progettazione si comporterà normalmente e l'area feedback assorbirà lo spazio rimanente.

 Viene anche visualizzata la barra di stato per aggiungere interesse visivo e valore funzionale comunicando varie modifiche allo stato dell'IDE, ad esempio quando l'IDE è in modalità di debug.

 ![Modifiche ai colori della barra di stato dell'IDE](../../extensibility/ux-guidelines/media/0901-02-idestatusbar.png "0901-02_IDEStatusBar")

 **Colori della barra di stato IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Barra informazioni incorporata
 È possibile utilizzare una barra informazioni nella parte superiore della finestra di un documento o di una finestra degli strumenti per informare l'utente di uno stato o di una condizione. Può inoltre offrire comandi in modo che l'utente possa eseguire facilmente un'azione. La barra informazioni è un controllo shell standard. Evitare di creare il proprio, che agirà e sembrerà incoerente con altri utenti nell'IDE. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) per i dettagli di implementazione e le linee guida sull'utilizzo.

 ![Barra informazioni incorporata](../../extensibility/ux-guidelines/media/0901-03-embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Barra informazioni incorporata in una finestra del documento, che avvisa l'utente che l'IDE è in modalità di debug cronologico e che l'editor non risponde nello stesso modo in cui si trova in modalità di debug standard.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Modifiche del cursore del mouse
 Quando si modifica il cursore del mouse, utilizzare i colori collegati al servizio VSColor e sono già associati al cursore. È possibile utilizzare le modifiche del cursore per indicare un'operazione in corso, nonché per individuare le zone in cui l'utente posiziona il puntatore del mouse su una destinazione che può essere trascinata, rilasciata o utilizzata per selezionare un oggetto.

 Utilizzare il cursore del mouse occupato/attendi solo quando tutto il tempo della CPU disponibile deve essere riservato per un'operazione, impedendo all'utente di esprimere altri input. Nella maggior parte dei casi con applicazioni ben scritte che usano il multithreading, i tempi in cui gli utenti non possono eseguire altre operazioni dovrebbero essere rari.

 Tenere presente che le modifiche del cursore sono utili come spunto ridondante per le informazioni presentate altrove. Non fare affidamento su una modifica del cursore come unico modo per comunicare con l'utente, in particolare quando si tenta di trasmettere elementi cruciali che l'utente deve soddisfare.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indicatori di stato
 Gli indicatori di stato sono importanti per fornire il feedback dell'utente durante i processi che importano più di alcuni secondi per il completamento. Gli indicatori di stato possono essere visualizzati sul posto (in prossimità del punto di avvio dell'azione in corso), in una barra di stato incorporata, in una finestra di dialogo modale o nella barra di stato di Visual Studio. Per informazioni sull'uso e sull'implementazione, seguire le istruzioni disponibili in [indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) .

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Finestra notifiche di Visual Studio
 La finestra notifiche di Visual Studio informa gli sviluppatori delle licenze, dell'ambiente (Visual Studio), delle estensioni e degli aggiornamenti. Gli utenti possono ignorare le singole notifiche o scegliere di ignorare determinati tipi di notifiche. L'elenco delle notifiche ignorate viene gestito in una pagina di **opzioni > di strumenti** .

 La finestra notifiche non è attualmente estendibile.

 ![Finestra delle notifiche di Visual Studio](../../extensibility/ux-guidelines/media/0901-06-vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Finestra degli strumenti notifiche di Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Elenco errori
 Una notifica all'interno dell'elenco errori indica gli errori e gli avvisi che si sono verificati durante la compilazione e il processo di compilazione e consente all'utente di spostarsi nel codice con tale errore di codice specifico.

 ![Elenco errori](../../extensibility/ux-guidelines/media/0901-08-errorlist.png "0901-08_ErrorList")

 **Elenco errori in Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Barre di stato incorporate
 Poiché la barra di stato IDE è dinamica, con il contesto dell'area client impostato sulla finestra del documento attiva e l'aggiornamento delle informazioni sul contesto dell'utente e/o sulle risposte di sistema, è difficile mantenere una visualizzazione continua delle informazioni o fornire lo stato dei processi asincroni a lungo termine. La barra di stato IDE, ad esempio, non è appropriata per le notifiche relative ai risultati dell'esecuzione dei test per più esecuzioni e/o per le selezioni di elementi immediatamente attivabili. È importante mantenere tali informazioni sullo stato nel contesto del documento o della finestra degli strumenti in cui l'utente effettua una selezione o avvia un processo.

 ![Barra di stato incorporata](../../extensibility/ux-guidelines/media/0901-09-embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barra di stato incorporata in Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Notifiche della barra delle applicazioni di Windows
 L'area di notifica di Windows è accanto al clock di sistema sulla barra delle applicazioni di Windows. Molte utilità e componenti software forniscono icone in quest'area, in modo che l'utente possa ottenere un menu di scelta rapida per le attività a livello di sistema, ad esempio la modifica della risoluzione dello schermo o il recupero degli aggiornamenti software.

 Le notifiche a livello di ambiente devono essere rilevate nell'hub notifiche di Visual Studio, non nell'area di notifica di Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bolle di notifica
 Le bolle di notifica possono apparire come informazioni all'interno di un editor o di una finestra di progettazione o come parte dell'area di notifica di Windows. L'utente percepisce tali bolle come problemi che possono essere risolti in un secondo momento, un vantaggio per le notifiche non critiche. Le bolle non sono appropriate per le informazioni critiche che l'utente deve risolvere immediatamente. Se si usano le bolle di notifica in Visual Studio, seguire le [indicazioni sul desktop di Windows per le bolle di notifica](https://msdn.microsoft.com/library/windows/desktop/dn742472\(v=vs.85\).aspx).

 ![Fumetto della notifica](../../extensibility/ux-guidelines/media/0901-07-notificationbubbles.png "0901-07_NotificationBubbles")

 **Bolla di notifica nell'area di notifica di Windows usata per Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indicatori di stato

### <a name="overview"></a>Panoramica
 Gli indicatori di stato sono una parte importante di un sistema di notifica per fornire commenti e suggerimenti degli utenti. Indicano all'utente quando verranno completati i processi e le operazioni. I tipi di indicatori noti includono indicatori di stato, cursori rotanti e icone animate. Il tipo e il posizionamento di un indicatore di stato dipendono dal contesto, inclusi quelli segnalati e il tempo necessario per il completamento del processo o dell'operazione.

#### <a name="factors"></a>Fattori
 Per determinare il tipo di indicatore appropriato, è necessario determinare i fattori seguenti.

1. **Temporizzazione:** periodo di tempo durante il quale l'operazione verrà eseguita

2. **Modalità:** se l'operazione è modale per l'ambiente (blocca l'interfaccia utente fino al completamento del processo)

3. **Permanenti/temporanei:** indica se il risultato finale dello stato di avanzamento deve essere segnalato e/o visualizzabile in un secondo momento

4. **Determinato/indeterminato:** indica se è possibile calcolare l'ora di fine e l'avanzamento dell'operazione

5. **Posizione grafica/testuale:** indica se l'avanzamento o il processo viene acquisito inline, nel corpo di un messaggio o in un controllo specifico, ad esempio il controllo albero

6. **Prossimità:** indica se lo stato di avanzamento deve essere in prossimità dell'interfaccia utente a cui è correlato. Ad esempio, è possibile che si trovi nella barra di stato, che potrebbe essere lontano o che deve essere vicino al pulsante che ha avviato il processo?

#### <a name="determinate-progress"></a>Stato determinato

|Tipo di stato|Quando e come usare|Note|
|-------------------|-------------------------|-----------|
|Indicatore di stato (determinato)|Durata prevista di >5 secondi.<br /><br /> Può includere la descrizione testuale dei dettagli del processo.|**Non** incorporare il testo nell'animazione.|
|Barra informazioni|Messaggistica associata all'interfaccia utente contestuale. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Può includere la descrizione testuale dei dettagli del processo.|**Non** usare più barre informazioni quando è necessario indicare più processi. Usare invece le barre di stato in pila.|
|Finestra di output|Notifica temporanea: processo a livello di app che l'utente vuole **rivedere** i dettagli di dopo il completamento.|**Non** usare se l'utente dovrà fare riferimento ai dati in un secondo momento.|
|File di registro|Associato a una notifica intemporanea nei casi in cui è importante **salvare** i dettagli dopo il completamento.||
|Status bar|Notifica temporanea: processo a livello di app per cui l'utente **non** dovrà ottenere dettagli dopo il completamento.<br /><br /> Include un indicatore di stato incorporato.<br /><br /> Può includere la descrizione testuale dei dettagli del processo.||

#### <a name="indeterminate-progress"></a>Stato di avanzamento indeterminato

|Tipo di stato|Quando e come usare|Note|
|-------------------|-------------------------|-----------|
|Indicatore di stato (indeterminato)|Durata prevista di >5 secondi.<br /><br /> Può includere la descrizione testuale dei dettagli del processo.|**Non** incorporare il testo nell'animazione.|
|Formiche (punti orizzontali animati)|Round trip al server.<br /><br /> Posizionata vicino al punto di contesto all'interno del contenitore padre.|**Non** usare se non è associato a un intero contenitore.|
|Casella di selezione (anello di stato)|Processo associato all'interfaccia utente contestuale o dove lo spazio è una considerazione.<br /><br /> Può includere la descrizione testuale dei dettagli del processo.||
|Barra informazioni|Messaggistica associata all'interfaccia utente contestuale. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Non** usare più barre informazioni quando è necessario indicare più processi. Usare invece le barre di stato in pila.|
|Finestra di output|Notifica temporanea: processo a livello di app a cui l'utente vorrà **esaminare** i dettagli dopo il completamento.|**Non** usare per le informazioni che devono essere mantenute tra le sessioni.|
|File di registro|Associato a una notifica intemporanea nei casi in cui è importante **salvare** i dettagli dopo il completamento.||
|Status bar|Notifica temporanea: processo a livello di app per cui l'utente **non** dovrà ottenere dettagli dopo il completamento.<br /><br /> Include l'indicatore di stato incorporato.<br /><br /> Può includere la descrizione testuale dei dettagli del processo.||

### <a name="progress-indicator-types"></a>Tipi indicatore di stato

#### <a name="progress-bars"></a>Indicatori di stato

##### <a name="indeterminate"></a>Indeterminato
 ![Indicatore di stato indeterminato](../../extensibility/ux-guidelines/media/0901-04-indeterminate.png "0901-04_Indeterminate")

 **Indicatore di stato indeterminato**

 "Indeterminate" significa che non è possibile determinare lo stato di avanzamento generale di un'operazione o di un processo. Utilizzare gli indicatori di stato indeterminati per le operazioni che richiedono un periodo di tempo illimitato o che accedono a un numero sconosciuto di oggetti. Usare una descrizione testuale per accompagnare ciò che accade. Usare i timeout per assegnare i limiti alle operazioni basate sul tempo. Gli indicatori di stato indeterminati utilizzano le animazioni per mostrare che lo stato di avanzamento viene effettuato, ma non forniscono altre informazioni. Non scegliere un indicatore di stato indeterminato in base solo alla possibile mancanza di precisione.

##### <a name="determinate"></a>Determinato
 ![Indicatore di stato determinato](../../extensibility/ux-guidelines/media/0901-05-determinate.png "0901-05_Determinate")

 **Indicatore di stato determinato**

 "Determinato" significa che un'operazione o un processo richiede un periodo di tempo limitato, anche se non è possibile prevedere accuratamente tale periodo di tempo. Indica chiaramente il completamento. Non lasciare che un indicatore di stato vada al 100%, a meno che l'operazione non sia stata completata. L'animazione dell'indicatore di stato determinata viene spostata da sinistra a destra da 0 a 100%.

 Non spostare mai l'indicatore di stato indietro durante un'operazione. La barra dovrebbe andare avanti costantemente all'inizio dell'operazione e raggiungere il 100% alla fine. Il punto dell'indicatore di stato è fornire all'utente un'idea del tempo necessario per l'intera operazione, indipendentemente dal numero di passaggi necessari.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Creazione di report simultanei (barre di stato in pila)
 Se un'operazione richiede molto tempo, ad esempio alcuni minuti, è possibile usare due barre di stato, una che mostra lo stato di avanzamento generale di un'operazione e un'altra per l'avanzamento del passaggio corrente. Se, ad esempio, un programma di installazione copia molti file, è possibile usare una barra di stato per indicare la durata dell'intero processo, mentre un secondo può indicare la percentuale di copia del file o della directory corrente. Non segnalare più di cinque operazioni simultanee o processi utilizzando barre di stato in pila. Se si dispone di più di cinque operazioni o processi simultanei da segnalare, utilizzare una finestra di dialogo modale con un pulsante Annulla e segnalare i dettagli sullo stato di avanzamento al Finestra di output.

##### <a name="textual-descriptions"></a>Descrizioni testuali
 Usare una descrizione testuale per accompagnare ciò che accade e il tempo stimato per il completamento. Se non è possibile determinare il tempo necessario per un'operazione, la scelta migliore per fornire commenti e suggerimenti potrebbe essere un'icona animata anziché un indicatore di stato.

 Visual Studio fornisce un indicatore di stato standard nella barra di stato che può essere usato da qualsiasi prodotto integrato in Visual Studio. Per le descrizioni testuali di ciò che accade quando l'indicatore di stato è animato, è possibile aggiornare il testo della barra di stato.

#### <a name="other-progress-indicators"></a>Altri indicatori di stato

##### <a name="ants-animated-horizontal-dots"></a>Formiche (punti orizzontali animati)
 ![Ant dello stato](../../extensibility/ux-guidelines/media/0903-01-ants.png "0903-01_Ants")

 "Ants", i puntini orizzontali animati forniscono un riferimento visivo per un processo del server di round trip indeterminato.

##### <a name="spinner-progress-ring"></a>Casella di selezione (anello di stato)
 ![Casella di selezione dello stato](../../extensibility/ux-guidelines/media/0903-02-spinner.png "0903-02_Spinner")

 La casella di selezione, nota anche come "anello di avanzamento", è un indicatore di stato indeterminato usato principalmente in relazione all'interfaccia utente contestuale. Consente di visualizzare una casella di selezione in prossimità del contenuto correlato, ad esempio un'intestazione di categoria testuale, un messaggio di posta elettronica o un controllo.

##### <a name="cursor-feedback"></a>Feedback del cursore
 Per le operazioni che accettano tra 2-7 secondi, fornire feedback del cursore. In genere, ciò significa usare il cursore di attesa fornito dal sistema operativo. Per informazioni aggiuntive, vedere la [Proprietà cursori. Wait](https://msdn.microsoft.com/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)dell'articolo MSDN.

#### <a name="progress-indicator-locations"></a>Percorsi indicatore di stato

##### <a name="status-bar"></a>Status bar
 La barra di stato consente all'applicazione di visualizzare messaggi e informazioni utili all'utente senza interrompere il lavoro dell'utente. In genere visualizzato nella parte inferiore di una finestra, lo stato di avanzamento sarà un riquadro Descrizione comando che include un messaggio sulla misura dello stato di avanzamento in combinazione con un indicatore di avanzamento.

 ![Barra di stato con indicatore di stato](../../extensibility/ux-guidelines/media/0903-03-statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barra di stato con indicatore di stato**

 ![Barra di stato con messaggistica](../../extensibility/ux-guidelines/media/0903-04-statusbarmessage.png "0903-04_StatusBarMessage")

 **Barra di stato con descrizione testuale**

##### <a name="infobar"></a>Barra informazioni
 Analogamente alla barra di stato, la barra informazioni fornisce notifiche e messaggistica contestuali, che possono anche essere abbinate a indicatori di stato indeterminati, ad esempio l'indicatore di stato o la casella di selezione. La barra informazioni non deve fornire lo stato di avanzamento del livello granulare o un'indicazione di stato determinata. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barra informazioni con indicatore di stato e messaggistica](../../extensibility/ux-guidelines/media/0903-05-infobar.png "0903-05_InfoBar")

 **Barra informazioni con indicatore di stato e descrizione testuale**

 ![Barra informazioni in una finestra](../../extensibility/ux-guidelines/media/0903-06-infobarinwindow.png "0903-06_InfoBarInWindow")

 **Barra informazioni nella finestra analisi codice**

##### <a name="inline"></a>Inline
 L'indicazione dello stato di avanzamento in linea può essere rappresentata da qualsiasi tipo di caricatore di stato. In genere, l'indicatore di stato è associato alla messaggistica, ma questo non è un requisito.

 ![Casella di selezione dello stato inline](../../extensibility/ux-guidelines/media/0903-07-inlinespinner.png "0903-07_InlineSpinner")

 **Casella di selezione combinata con descrizione testuale**

 ![Indicatori di stato in pila inline](../../extensibility/ux-guidelines/media/0903-08-inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Indicatori di stato in pila determinati**

 ![Messaggistica sullo stato inline](../../extensibility/ux-guidelines/media/0903-09-inlinetext.png "0903-09_InlineText")

 **Esplora server testo inline: aggiornamento in corso...**

##### <a name="tool-windows"></a>Finestre degli strumenti
 L'indicazione di stato globale è rappresentata da un indicatore di stato indeterminato posizionato direttamente sotto la barra degli strumenti.

 ![Indicatore di stato indeterminato globale](../../extensibility/ux-guidelines/media/0903-23-globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer indicatore di stato indeterminato globale**

##### <a name="dialogs"></a>Finestre di dialogo
 I dialoghi possono contenere qualsiasi tipo di caricatore di stato. Gli indicatori di stato possono essere abbinati alla messaggistica e combinati con più livelli di indicazione dello stato di avanzamento per rappresentare i processi granulari e i processi secondari.

 ![Finestra di dialogo con più tipi di indicatori di stato](../../extensibility/ux-guidelines/media/0903-11-dialog.png "0903-11_Dialog")

 **Finestra di dialogo di Visual Studio con processi simultanei e più tipi di indicatori di stato**

 ![Finestra di dialogo con caricatore dello stato e messaggistica](../../extensibility/ux-guidelines/media/0903-12-dialog2.png "0903-12_Dialog2")

 **Finestra di dialogo di Visual Studio con caricatore di stato e comandi inline di messaggistica**

##### <a name="document-well"></a>Documento
 L'area documento consente di visualizzare più tipi di caricatore di stato in combinazione con i controlli.

 ![Messaggistica sullo stato nella finestra del documento](../../extensibility/ux-guidelines/media/0903-13-documentwell.png "0903-13_DocumentWell")

 **Indicatore di stato indeterminato sotto la barra degli strumenti**

##### <a name="output-window"></a>Finestra di output
 La finestra di output è appropriata per la gestione della progressione dei processi e dello stato di avanzamento in corso tramite messaggistica testuale inline. È consigliabile utilizzare la barra di stato insieme a qualsiasi report di stato della finestra di output.

 ![Messaggistica sullo stato nella finestra di output](../../extensibility/ux-guidelines/media/0903-14-outputwindow.png "0903-14_OutputWindow")

 **Finestra di output con lo stato del processo in corso e la messaggistica di attesa**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Barre informazioni

### <a name="overview"></a>Panoramica
 Barre informazioni forniscono all'utente un indicatore vicino al punto di attenzione e l'utilizzo del controllo della barra informazioni condivisa garantisce la coerenza nell'aspetto e nell'interazione visive.

 ![Barra informazioni](../../extensibility/ux-guidelines/media/0904-01-infobar.png "0904-01_Infobar")

 **Barre informazioni in Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Usi appropriati per una barra informazioni

- Per fornire all'utente un messaggio non di blocco, ma importante, pertinente al contesto corrente

- Per indicare che l'interfaccia utente è in uno stato o una condizione che comporta alcune implicazioni dell'interazione, ad esempio il debug cronologico

- Per notificare all'utente che il sistema ha rilevato problemi, ad esempio quando un'estensione causa problemi di prestazioni

- Per fornire all'utente un modo per eseguire facilmente un'azione, ad esempio quando l'Editor rileva che un file contiene schede e spazi misti

##### <a name="do"></a>Cosa fare

- Mantieni il testo del messaggio della barra informazioni breve e fino al punto.

- Mantieni il testo nei collegamenti e nei pulsanti concisi.

- Verificare che le opzioni di "azione" fornite agli utenti siano minime, mostrando solo le azioni necessarie.

##### <a name="dont"></a>Non:

- Utilizzare una barra informazioni per offrire comandi standard che devono essere posizionati in una barra degli strumenti.

- Utilizzare una barra informazioni al posto di una finestra di dialogo modale.

- Creare un messaggio mobile all'esterno di una finestra.

- Usare più barre informazioni in diverse posizioni all'interno della stessa finestra.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>È possibile visualizzare più barre informazioni contemporaneamente?
 Sì, più barre informazioni possono essere visualizzati contemporaneamente. Verranno visualizzati in un ordine prima di tutto, primo servito con la prima barra informazioni visualizzata nella parte superiore e barre informazioni aggiuntivi visualizzati di seguito.

 L'utente visualizzerà un massimo di tre barre informazioni alla volta, dopodiché, se sono disponibili più barre informazioni, l'area della barra informazioni diventerà scorrevole.

### <a name="creating-an-infobar"></a>Creazione di una barra informazioni
 La barra informazioni è costituita da quattro sezioni, da sinistra a destra:

- **Icona:** Qui è possibile aggiungere qualsiasi icona che si vuole visualizzare per la barra informazioni, ad esempio un'icona di avviso.

- **Testo:** È possibile aggiungere testo per descrivere lo scenario/situazione in cui si trova l'utente, insieme ai collegamenti all'interno del testo, se necessario. Ricordarsi di tenere il testo conciso.

- **Azioni:** Questa sezione deve contenere collegamenti e pulsanti per le azioni che l'utente può eseguire nella barra informazioni.

- **Pulsante Chiudi:** L'ultima sezione a destra può avere un pulsante Chiudi.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creazione di una barra informazioni standard nel codice gestito
 La classe InfoBarModel può essere utilizzata per creare un'origine dati per una barra informazioni. Usare uno di questi quattro costruttori:

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

 Di seguito è riportato un esempio in cui viene creato un InfoBarModel con testo con un collegamento ipertestuale, un pulsante di azione e un'icona.

 ![Barra informazioni con collegamento ipertestuale](../../extensibility/ux-guidelines/media/0904-02-infobarhyperlink.png "0904-02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Creazione di una barra informazioni standard nel codice nativo
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
 L'implementazione di InfoBarModel o IVsInfoBar è costituita da modelli di dati che devono essere trasformati in un UIElement per poter essere visualizzati nell'interfaccia utente. Un oggetto UIElement può essere recuperato con il servizio SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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
 Barre informazioni può essere visualizzato in una o più delle seguenti posizioni:

- Finestre degli strumenti

- All'interno di una scheda del documento

> [!IMPORTANT]
> È possibile posizionare una barra informazioni per fornire un messaggio sul contesto globale. Questo aspetto viene visualizzato tra le barre degli strumenti e l'area documento. Questa operazione non è consigliata perché causa problemi con "Jump and jerk" dell'IDE e deve essere evitata, a meno che non sia assolutamente necessario e appropriato.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Inserimento di una barra informazioni in un ToolWindowPane
 Il Metodo ToolWindowPane. AddInfoBar (IVsInfoBar) può essere usato per aggiungere una barra informazioni a una finestra degli strumenti. Questa API può aggiungere un IVsInfoBar (di cui InfoBarModel è un'implementazione predefinita) o un IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Inserimento di una barra informazioni in un documento o non in ToolWindowPane
 Per inserire una barra informazioni in qualsiasi IVsWindowFrame, utilizzare la proprietà VSFPROPID_InfoBarHost per ottenere IVsInfoBarHost per il frame, quindi aggiungere la barra informazioni UIElement.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Immissione di una barra informazioni nella finestra principale
 Per inserire una barra informazioni nella finestra principale, usare il VSSPROPID_MainWindowInfoBarHost del servizio IVsShell per ottenere il IVsInfoBarHost della finestra principale e quindi aggiungervi l'oggetto UIElement della barra informazioni.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Si saprà quando l'utente esegue un'azione nella barra informazioni?
 Sì, ogni azione evento viene restituita all'autore della barra delle informazioni. Fino all'autore della barra informazioni è quindi necessario intervenire nell'IDE in base alla selezione dell'utente nella barra informazioni. Barre informazioni verrà rimosso automaticamente dall'host di cui è stato fatto clic sul pulsante Chiudi, ma è necessario lavoro aggiuntivo se è necessario rimuovere altre barre informazioni dopo la chiusura. I dati di telemetria dovranno anche essere registrati in modo indipendente da ogni barra informazioni.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Ricezione di eventi della barra informazioni in un ToolWindowPane
 ToolWindowPane ha due eventi per barre informazioni. L'evento InfoBarClosed viene generato quando una barra informazioni in ToolWindowPane viene chiusa. L'evento InfoBarActionItemClicked viene generato quando si fa clic su un collegamento ipertestuale o un pulsante all'interno della barra informazioni.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Ricezione di eventi della barra informazioni direttamente da UIElement
 IVsInfoBarUIElement. Advise può essere utilizzato per sottoscrivere gli eventi direttamente da UIElement di una barra informazioni. L'implementazione di IVsInfoBarUIEvents consente all'autore di ricevere eventi di chiusura e clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Convalida degli errori
 Quando un utente immette informazioni non accettabili, ad esempio quando un campo obbligatorio viene ignorato o quando i dati vengono immessi in un formato non corretto, è preferibile usare la convalida del controllo o il feedback vicino al controllo anziché usare una finestra di dialogo di errore popup di blocco.

### <a name="field-validation"></a>Convalida campi
 Il modulo e la convalida dei campi sono costituiti da tre componenti: un controllo, un'icona e una descrizione comando. Sebbene vari tipi di controlli possano utilizzare questa funzione, come esempio viene utilizzata una casella di testo.

 ![Convalida campo &#40;&#41;vuota ](../../extensibility/ux-guidelines/media/0905-01-fieldvalidation.png "0905-01_FieldValidation")

 Se il campo è obbligatorio, deve essere presente il testo della filigrana **\<Required>** e lo sfondo del campo deve essere giallo chiaro (VSColor: `Environment.ControlEditRequiredBackground` ) e il primo piano deve essere grigio (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Convalida campo con etichetta "Obbligatorio"](../../extensibility/ux-guidelines/media/0905-02-fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Il programma può determinare che il controllo si trova in uno stato di *contenuto non valido immesso* quando lo stato attivo viene spostato in un altro controllo o quando l'utente fa clic su un pulsante [OK] commit o quando l'utente salva il documento o il modulo.

 Quando viene determinato lo stato del contenuto non valido, viene visualizzata un'icona all'interno del controllo o accanto a essa. Una descrizione comando che descrive l'errore dovrebbe essere visualizzata al passaggio del mouse sull'icona o sul controllo. Inoltre, viene visualizzato un bordo di 1 pixel intorno al controllo che sta creando lo stato non valido.

 ![Specifiche del layout della convalida campo](../../extensibility/ux-guidelines/media/0905-03-layoutspecs.png "0905-03_LayoutSpecs")

 **Specifiche di layout per la convalida dei campi**

#### <a name="acceptable-variations-for-icon-location"></a>Variazioni accettabili per la posizione dell'icona
 Esistono innumerevoli casi univoci in cui gli utenti devono essere informati sugli errori di convalida. Considerando il tipo di controllo e la configurazione dell'interfaccia utente, scegliere la posizione dell'icona appropriata per la situazione specifica.

 ![Posizioni accettabili per le icone](../../extensibility/ux-guidelines/media/0905-04-iconlocation.png "0905-04_IconLocation")

 **Variazioni accettabili per le posizioni delle icone di convalida dei campi**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Convalida che richiede un round trip a un server o a una connessione di rete
 In alcuni casi, è necessario un round trip al server per verificare il contenuto ed è importante mostrare gli Stati di avanzamento, verifica e errore dell'utente. Nella figura seguente viene illustrato un esempio di questo caso e l'interfaccia utente consigliata.

 ![Convalida che prevede un round trip a un server](../../extensibility/ux-guidelines/media/0905-05-roundtrip.png "0905-05_RoundTrip")

 **Convalida che prevede un round trip a un server**

 Si noti che è necessario fornire uno spazio disponibile sufficiente a destra del controllo per poter contenere la "verifica..." e il testo "Retry".

#### <a name="in-place-warning-text"></a>Testo di avviso sul posto
 Quando è disponibile spazio per inserire il messaggio di errore vicino al controllo in uno stato di errore, è preferibile usare solo la descrizione comando.

 ![Avviso&#45;posto](../../extensibility/ux-guidelines/media/0905-06-inplacewarning.png "0905-06_InPlaceWarning")

 **Testo di avviso sul posto**

#### <a name="watermarks"></a>Filigrane
 A volte un intero controllo o finestra si trova in uno stato di errore. In questa situazione, utilizzare una filigrana per indicare l'errore.

 ![Filigrana](../../extensibility/ux-guidelines/media/0905-07-watermark.png "0905-07_Watermark")

 **Convalida campo filigrana**
