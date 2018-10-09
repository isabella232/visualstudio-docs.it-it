---
title: Le notifiche e avanzamento per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aee6e5656142d0597ff6101da5e2e5f690f8fcc5
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863952"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Le notifiche e avanzamento per Visual Studio
##  <a name="BKMK_NotificationSystems"></a> Sistemi di notifica  
  
### <a name="overview"></a>Panoramica  
 Esistono diversi modi per informare l'utente di ciò che accade in Visual Studio riguardanti le attività di sviluppo software.  
  
 Quando si implementa alcun tipo di notifica:  
  
-   **Mantenere il numero di notifiche al minimo** numero effettivo. I messaggi di notifica devono applicare alla maggior parte degli utenti di Visual Studio o agli utenti di un'area di funzionalità o la funzionalità specifiche. Un uso eccessivo di notifiche potrà sidetrack l'utente o confutano percepito la facilità di utilizzo del sistema.  
  
-   **Assicurarsi che si intende presentare chiare e utili messaggi** che l'utente può usare per richiamare il contesto appropriato per effettuare le scelte più complesse ed eseguire altre azioni.  
  
-   **Presentare in modo appropriato i messaggi sincroni e asincroni.** Le notifiche sincrone indicano che un elemento richiede attenzione immediata, ad esempio quando si blocca un servizio web o un codice di eccezione. L'utente dovrebbe essere informato di questi casi immediatamente in modo che richiede l'input, ad esempio in una finestra di dialogo modale. Notifiche asincrone sono quelle che l'utente dovrebbe conoscere, ma non verrà richiesto di intervenire immediatamente, ad esempio quando viene completata un'operazione di compilazione o una distribuzione di siti web viene completata. Tali messaggi devono essere più ambiente e non interrompere il flusso di attività dell'utente.  
  
-   **Usare le finestre di dialogo modale solo quando necessario, per impedire all'utente di eseguire altre azioni** prima di riconoscere il messaggio o prendere una decisione presentata nella finestra di dialogo.  
  
-   **Rimuovere notifiche ambiente quando non sono più validi.** Non richiedono all'utente di eliminare una notifica se già adottate azioni per risolvere il problema che sono stati informati.  
  
-   **Tenere presente che le notifiche possono causare false correlazioni.** Gli utenti potrebbero ritenere che uno o più delle loro azioni è attivata una notifica quando in realtà non esiste alcuna relazione causale con. Essere chiaro nel messaggio di notifica sul contesto, il trigger e l'origine della notifica.  
  
### <a name="choosing-the-right-method"></a>Scelta del metodo  
 Usare questa tabella per agevolare la scelta del metodo per notificare all'utente del messaggio.  
  
|Metodo|Usa|Non usare|  
|------------|---------|----------------|  
|[Finestre di dialogo di errore modale messaggio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Utilizzarlo quando è necessaria una risposta dell'utente prima di procedere.|Non usare quando non è necessario bloccare l'utente e interrompere il flusso. Evitare di usare le finestre di dialogo modale se è possibile visualizzare il messaggio in un altro metodo meno invasivo.|  
|[Barra di stato dell'IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Usare quando sono disponibili informazioni testuali ambiente relativi allo stato di un processo.|Non utilizzare da soli. Particolarmente utile in combinazione con un altro meccanismo di commenti e suggerimenti.|  
|[Barra informazioni incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|In una finestra degli strumenti o una finestra del documento, utilizzare per notificare lo stato di avanzamento, lo stato di errore, i risultati e/o informazioni di utilità pratica.|Non utilizzare se le informazioni non sono rilevanti per il percorso in cui si trova la barra informazioni.<br /><br /> Non usare all'esterno di una finestra del documento o strumento.|  
|[Modifiche del cursore del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Consente di inviare una notifica che un processo sta succedendo. Usato anche per inviare una notifica che si verifica un cambiamento di stato nel mouse, ad esempio quando l'opzione Trascina selezione è in corso o che il cursore del mouse è in una determinata modalità, ad esempio la modalità di disegno.|Non usare per le modifiche di stato di avanzamento breve o se gelatinoso del cursore è probabile (ad esempio, quando associato alle parti di un processo in esecuzione più lunga anziché per l'intero processo).|  
|[Indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Usare quando è necessario segnalare lo stato (indicatore o indeterminato). Esistono svariati tipi di indicatori di stato di avanzamento e l'utilizzo specifico per ognuna. Visualizzare [gli indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Finestra di Visual Studio notifiche](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La finestra delle notifiche non è estendibile pubblicamente. Tuttavia, utilizzato per comunicare un intervallo di messaggi relativi a Visual Studio, inclusi i problemi critici con la licenza e informative notifiche degli aggiornamenti per Visual Studio o ai pacchetti.|Non utilizzare per altri tipi di notifiche.|  
|[Elenco errori](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando il problema è correlato direttamente alla soluzione attualmente aperta dell'utente di problemi (errore/avviso/informazioni), si potrebbe essere necessario intervenire sul codice.<br /><br /> Ciò includerà, ad esempio:<br /><br /> -I messaggi del compilatore (errore/avviso/informazioni)<br /><br /> -I messaggi di Analizzatore/diagnostica codice sul codice<br /><br /> -I messaggi di compilazione<br /><br /> Può essere appropriata per i problemi relativi ai file di progetto o una soluzione, ma è consigliabile innanzitutto un'indicazione di Esplora soluzioni.|Non usare per gli elementi che non ha alcuna relazione con il codice dell'utente soluzione aperta.|  
|Le notifiche dell'editor: lampadina|Usare quando si ha una correzione disponibile per risolvere un problema che esiste nel file aperto.<br /><br /> Si noti che lampadina deve inoltre essere utilizzato per l'hosting delle azioni rapide eseguibili automaticamente vengono eseguite nel codice dell'utente su richiesta, ad esempio refactoring, ma in tal caso non verrà visualizzato "style notifica".|Non usare per gli elementi privi di qualsiasi relazione al file aperto.|  
|Le notifiche dell'editor: sottolineature ondulate|Utilizzare per avvisare l'utente a un problema con un intervallo specifico del codice aperto (ad esempio, una sottolineatura ondulata rossa per gli errori).|Non usare per gli elementi che non sono correlati a un intervallo specifico del codice aperto.|  
|[Barre di stato incorporato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilizzare per fornire lo stato relative al contenuto o un processo nel contesto di una finestra degli strumenti specifici, una finestra del documento o la finestra di dialogo.|Non usare per le notifiche generiche sul prodotto, processi o gli elementi che non hanno alcuna relazione con il contenuto all'interno della finestra specifica.|  
|[Notifiche sulla barra delle applicazioni di Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Utilizzare per le notifiche per i processi out-of-process della superficie di attacco o companion in applicazioni.|Non usare per le notifiche che riguardano l'IDE.|  
|[Fumetti notifica](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Consente di inviare una notifica di un processo remoto o cambiare **esterno** dell'IDE.|Non usare come mezzo per avvisare l'utente di processi **all'interno di** dell'IDE.|  
  
### <a name="notification-methods"></a>Metodi di notifica  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> Finestre di dialogo di errore modale messaggio  
 Una finestra di dialogo di errore modale messaggio utilizzato per visualizzare un messaggio di errore che richiede la conferma dell'utente o un'azione.  
  
 ![Messaggio di errore modale](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **Una finestra di messaggio di errore modale avvisa l'utente di una stringa di connessione non è valido in un database**  
  
####  <a name="BKMK_IDEStatusBar"></a> Barra di stato dell'IDE  
 La probabilità che gli utenti si noti che il testo della barra di stato è correlata ai propri computer versatile degli utenti e l'esperienza specifica con la piattaforma Windows. La base clienti di Visual Studio tende a essere esperti in entrambi i casi, anche se competente anche agli utenti di Windows potrebbero mancare alcune delle modifiche nella barra di stato. Pertanto, la barra di stato è più adatta per scopi informativi o come un segnale ridondante per le informazioni presentate in un' posizione. In una finestra di dialogo o nella finestra degli strumenti delle notifiche, è necessario specificare qualsiasi tipo di informazioni critiche che l'utente deve essere risolto immediatamente.  
  
 La barra di stato di Visual Studio è progettata per consentire diversi tipi di informazioni da visualizzare. È suddiviso in aree geografiche per commenti e suggerimenti, finestra di progettazione, indicatore di stato, animazione e client.  
  
 L'area commenti e suggerimenti e l'area della finestra di progettazione sono sempre visibili. L'indicatore di stato e l'animazione aree sono sempre dinamici e basati sul contesto utente. L'area di progettazione ha una larghezza statica determinata dalla lunghezza della stringa di cui viene eseguito il pull dalla risorsa associata per il messaggio di testo. In questo modo la localizzazione di ridimensionare la larghezza senza richiedere una modifica del codice. Per l'inglese, la larghezza di questa stringa è circa 220 pixel. L'area di progettazione si comporterà in genere e l'area commenti e suggerimenti verrà absorb lo spazio rimanente.  
  
 La barra di stato viene colorata anche per aggiungere l'interesse visivo e il valore funzionale comunicando vari cambiamenti di stato dell'IDE, ad esempio quando l'IDE è in modalità di debug.  
  
 ![Sulla barra di colore cambia stato IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **Colori della barra di stato dell'IDE**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> Barra informazioni incorporata  
 Una barra informazioni è utilizzabile nella parte superiore di una finestra del documento o una finestra degli strumenti per informare l'utente di uno stato o una condizione. Può anche offrire i comandi in modo che l'utente può avere un modo per effettuare con facilità un'azione. La barra informazioni è un controllo standard della shell. Evitare di creare il proprio, che verrà funzionare e non corrispondere a quelli di altri utenti nell'IDE. Visualizzare [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) per i dettagli di implementazione e linee guida sull'uso.  
  
 ![Barra informazioni incorporata](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **Una barra informazioni incorporata in una finestra del documento, avvisa l'utente che l'IDE è in modalità debug cronologico e l'editor non risponderà esattamente come avviene in modalità di debug standard.**  
  
####  <a name="BKMK_MouseCursorChanges"></a> Modifiche del cursore del mouse  
 Quando si modifica il cursore del mouse, utilizzare i colori che sono associati a VSColor service e sono già associate con il cursore. Cursore cambia può essere utilizzato per indicare un'operazione in corso, nonché premere zone in cui l'utente si posiziona su una destinazione che può essere trascinata, rilasciata in o utilizzata per selezionare un oggetto.  
  
 Usare il cursore del mouse occupato/attesa solo quando tutto il tempo della CPU disponibile deve essere riservato per un'operazione, impedendo all'utente di esprimere qualsiasi ulteriore input. Nella maggior parte dei casi con le applicazioni ben scritte tramite il multithreading, devono essere rare volte quando agli utenti viene impedito di eseguire altre operazioni.  
  
 Tenere presente che le modifiche cursore sono utili quando un segnale ridondante per le informazioni presentate in un' posizione. Non fare affidamento su una modifica di cursore come modalità esclusiva di comunicare con l'utente in particolare quando si desidera comunicare qualcosa che è fondamentale che l'utente deve soddisfare.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> Indicatori di stato  
 Gli indicatori di stato sono importanti per fornire il feedback utente durante processi che hanno più di pochi secondi per il completamento. È possibile visualizzare gli indicatori di stato sul posto (quasi il punto di avvio dell'azione in corso), in una barra di stato incorporato, nella finestra di dialogo modale o nella barra di stato di Visual Studio. Seguire le indicazioni fornite in [gli indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) relative all'uso e l'implementazione.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Finestra di Visual Studio notifiche  
 La finestra delle notifiche di Visual Studio notifica gli sviluppatori su licenze, ambiente (Visual Studio), estensioni e aggiornamenti. Gli utenti possono ignorare singole notifiche o possono scegliere di ignorare determinati tipi di notifiche. L'elenco delle notifiche ignorate viene gestito in una **strumenti > Opzioni** pagina.  
  
 La finestra delle notifiche non è attualmente estendibile.  
  
 ![Finestra di Visual Studio notifiche](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Finestra dello strumento di Visual Studio notifiche**  
  
####  <a name="BKMK_ErrorList"></a> Elenco errori  
 Una notifica all'interno dell'elenco di errore indicano errori e avvisi che si è verificato durante la compilazione e o processo di compilazione e consente all'utente di spostarsi nel codice per tale errore codice specifico.  
  
 ![Elenco errori](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Elenco di errori in Visual Studio**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> Barre di stato incorporato  
 Poiché la barra di stato dell'IDE è dinamica, con il contesto di area client impostato sulla finestra del documento attivo e informazioni di aggiornamento per il contesto dell'utente e/o le risposte di sistema, è difficile mantenere una visualizzazione continua delle informazioni o fornire lo stato su a lungo termine processi asincroni. Ad esempio, la barra di stato dell'IDE non è appropriata per le notifiche dei risultati di esecuzione dei test per più esecuzioni e/o le selezioni delle voci immediatamente a frutto. È importante mantenere tali informazioni sullo stato nel contesto della finestra di documento o lo strumento in cui l'utente effettua una selezione o avvia un processo.  
  
 ![Barra di stato incorporato](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Barra di stato incorporato in Visual Studio**  
  
####  <a name="BKMK_WindowsTray"></a> Notifiche sulla barra delle applicazioni di Windows  
 L'area di notifica si trova accanto al sistema di Windows dell'orologio della barra delle applicazioni di Windows. Molti componenti software e utilità forniscono le icone in quest'area, in modo che l'utente può disporre di un menu di scelta rapida per le attività a livello di sistema, ad esempio la modifica risoluzione dello schermo o come ottenere gli aggiornamenti software.  
  
 Le notifiche a livello di ambiente devono essere resi visibili nell'hub di notifiche di Visual Studio, non l'area di notifica Windows.  
  
####  <a name="BKMK_NotificationBubbles"></a> Fumetti notifica  
 Fumetti notifica possono apparire come informativo all'interno di un editor o la finestra di progettazione o come parte dell'area di notifica di Windows. L'utente visualizza queste bolle come i problemi che consentono di risolvere in un secondo momento, che è un vantaggio per le notifiche non critiche. Bolle non sono adatte per le informazioni critiche che l'utente deve risolvere immediatamente. Se si usa fumetti notifica in Visual Studio, seguire le [linee guida di Windows Desktop per fumetti notifica](/windows/desktop/uxguide/mess-notif).  
  
 ![Fumetto della notifica](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Fumetto della notifica nell'area di notifica di Windows usato per Visual Studio**  
  
##  <a name="BKMK_ProgressIndicators"></a> Indicatori di stato  
  
### <a name="overview"></a>Panoramica  
 Gli indicatori di stato sono una parte importante di un sistema di notifica per dare all'utente un feedback. L'utente indicano il completamento dei processi e le operazioni. Tipi di indicatori familiare includono indicatori di stato, i cursori di rotazione e icone animate. Il tipo e il posizionamento di un indicatore di stato dipende dal contesto, tra cui quello segnalato e quanto tempo il processo o un'operazione necessari per il completamento.  
  
#### <a name="factors"></a>Fattori  
 Per determinare quale tipo di indicatore è appropriato, è necessario determinare i fattori seguenti.  
  
1.  **Intervallo:** tempo richiederà l'operazione  
  
2.  **Modalità:** indica se l'operazione è modale all'ambiente (blocchi dell'interfaccia utente fino al completamento del processo)  
  
3.  **Persistent/temporaneo:** indica se il risultato finale dello stato di avanzamento deve essere segnalato e/o visualizzabile in un secondo momento  
  
4.  **Indicatore/indeterminato:** indica se l'ora di fine operazione e lo stato può essere calcolati  
  
5.  **Posizione immagine/Textual:** se lo stato di avanzamento o processo è acquisita inline, nel corpo di un messaggio o un controllo specifico, ad esempio il controllo struttura ad albero  
  
6.  **Prossimità:** se lo stato di avanzamento deve essere in stretta vicinanza all'interfaccia utente che è correlato. (Ad esempio, può essere nella barra di stato, che potrebbe essere a portata di mano, o dispone di essere quasi il pulsante che ha avviato il processo?)  
  
#### <a name="determinate-progress"></a>Indicatore di stato  
  
|Tipo di stato di avanzamento|Quando e come usare|Note|  
|-------------------|-------------------------|-----------|  
|Indicatore di stato (determinata)|Previsto la durata di > 5 secondi.<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** incorporare testo nell'animazione.|  
|Barra informazioni|Messaggistica associato con l'interfaccia utente contestuali. Visualizzare [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** usare le barre più informazioni quando è necessario indicare più processi. Usare invece le barre di avanzamento in pila.|  
|Finestra di output|Notifica temporanea: processo a livello di app che l'utente desidera **esaminare** i dettagli di dopo il completamento.|**Non** usare se l'utente dovrà fare riferimento ai dati in un secondo momento.|  
|File di log|Abbinato intransient notifica nei casi quando è importante **salvare** dettagli dopo il completamento.||  
|Barra di stato|Notifica temporanea: processo a livello di app che l'utente verrà **non è necessario** i dettagli di dopo il completamento.<br /><br /> Include una barra di stato incorporato.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
  
#### <a name="indeterminate-progress"></a>Stato di avanzamento indeterminata  
  
|Tipo di stato di avanzamento|Quando e come usare|Note|  
|-------------------|-------------------------|-----------|  
|Indicatore di stato (indeterminato)|Previsto la durata di > 5 secondi.<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** incorporare testo nell'animazione.|  
|ANTS (animate punti orizzontale)|Round trip al server.<br /><br /> Trova punto near del contesto parte superiore del contenitore padre.|**Non** usare se non associato a intero contenitore.|  
|Casella di selezione (anello di stato)|Processo associato al contesto dell'interfaccia utente oppure in cui lo spazio è un fattore importante.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
|Barra informazioni|Messaggistica associato con l'interfaccia utente contestuali. Visualizzare [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Non** usare le barre più informazioni quando è necessario indicare più processi. Usare invece le barre di avanzamento in pila.|  
|Finestra di output|Notifica temporanea: processo a livello di app che l'utente desidera **esaminare** i dettagli di dopo il completamento.|**Non** usare per ottenere informazioni che devono rimanere persistenti tra le sessioni.|  
|File di log|Abbinato intransient notifica nei casi quando è importante **salvare** dettagli dopo il completamento.||  
|Barra di stato|Notifica temporanea: processo a livello di app che l'utente verrà **non è necessario** i dettagli di dopo il completamento.<br /><br /> Include l'indicatore di stato incorporato.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
  
### <a name="progress-indicator-types"></a>Tipi di indicatori di stato di avanzamento  
  
#### <a name="progress-bars"></a>Indicatori di stato  
  
##### <a name="indeterminate"></a>Indeterminato  
 ![Indicatore di stato indeterminato](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **Indicatore di stato indeterminato**  
  
 "Indeterminato" significa che lo stato di avanzamento generale di un'operazione o non può essere determinato processo. Per le operazioni che richiedono una quantità illimitata di tempo o che accedono a un numero sconosciuto di oggetti, utilizzare le barre di stato indeterminato. Usare una descrizione testuale complemento a ciò che accade. Usare i timeout per concedere ai limiti a operazioni basate sul tempo. Indicatori di stato indeterminato usano animazioni per mostrare che lo stato di avanzamento è stata effettuata, ma non forniscono altre informazioni. Non scegliere un indicatore di stato indeterminato solo in base l'eventuale mancanza di precisione da solo.  
  
##### <a name="determinate"></a>Indicatore  
 ![Indicatore di stato](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **Indicatore di stato**  
  
 "Indicatore" significa che un'operazione o un processo richiede una quantità limitata di tempo, anche se tale quantità di tempo non è possibile prevedere con precisione. Indicare chiaramente il completamento. Non lasciare un indicatore di stato di andare fino al 100%, a meno che l'operazione è stata completata. Indicatore di stato sulla barra animazione passa da sinistra a destra da 0 a 100%.  
  
 Mai spostare l'indicatore di stato con le versioni precedenti durante un'operazione. La barra deve spostarsi in avanti costante all'inizio dell'operazione e raggiungi 100% quando termina. Il punto dell'indicatore di stato è fornire all'utente un'idea di come intera durata dell'operazione, indipendentemente dal fatto il numero di passaggi coinvolti.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultanee reporting (indicatori di stato in pila)  
 Se un'operazione potrebbe richiedere molto tempo, probabilmente diversi minuti, quindi due indicatori di stato possono essere usato, uno che mostra lo stato di avanzamento complessivo per un'operazione e l'altro per l'avanzamento del passaggio corrente. Ad esempio, se un programma di installazione è copiano molti file, quindi un indicatore di stato è utilizzabile per indicare quanto tempo l'intero processo richiede mentre un secondo può indicare la percentuale del file corrente o directory vengono copiata. Non segnala più di cinque operazioni simultanee o i processi usando le barre di avanzamento in pila. Se si dispone di più di cinque operazioni simultanee o un report dei processi, usare una finestra di dialogo modale con un pulsante di annullamento e un report i dettagli di stato di avanzamento nella finestra di Output.  
  
##### <a name="textual-descriptions"></a>Descrizioni testuali  
 Usare il tempo stimato di completamento e una descrizione testuale complemento a ciò che accade. Se è possibile determinare il tempo richiesto un'operazione, un'icona animata anziché un indicatore di stato potrebbe essere una scelta migliore per fornire commenti e suggerimenti.  
  
 Visual Studio fornisce un indicatore di stato standard nella barra di stato che può essere usato da tutti i prodotti integrati in Visual Studio. Per descrizioni testuali di ciò che accade anche se la barra di avanzamento viene animata, il testo della barra di stato può essere aggiornato.  
  
#### <a name="other-progress-indicators"></a>Altri indicatori di stato  
  
##### <a name="ants-animated-horizontal-dots"></a>ANTS (animate punti orizzontale)  
 ![Stato di avanzamento ants](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 "Ants," animati puntini orizzontali, forniscono un riferimento visivo per un processo del server eseguire il round trip indeterminato.  
  
##### <a name="spinner-progress-ring"></a>Casella di selezione (anello di stato)  
 ![Indicatore di avanzamento](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 La casella di selezione (noto anche come un "anello di stato") è un indicatore di stato indeterminato utilizzato principalmente in relazione al contesto dell'interfaccia utente. Visualizzare una casella di selezione in stretta vicinanza al relativo contenuto correlato, ad esempio un'intestazione di categoria testuale, messaggistica o controllo.  
  
##### <a name="cursor-feedback"></a>Risposta del cursore  
 Per le operazioni che richiedere da 2 a 7 secondi, fornire commenti e suggerimenti del cursore. In genere, ciò significa che tramite il cursore di attesa fornito dal sistema operativo. Per istruzioni, vedere l'articolo di MSDN [Cursors.Wait proprietà](/dotnet/api/system.windows.input.cursors.wait).  
  
#### <a name="progress-indicator-locations"></a>Percorsi di indicatore di stato di avanzamento  
  
##### <a name="status-bar"></a>Barra di stato  
 La barra di stato fornisce all'applicazione una posizione in cui visualizzare i messaggi e informazioni utili all'utente senza interrompere le attività dell'utente. In genere visualizzato nella parte inferiore di una finestra, lo stato di avanzamento sarà un riquadro di suggerimento dello strumento che include un messaggio relativo alla misura dello stato di avanzamento in combinazione con un indicatore.  
  
 ![Barra di stato con indicatore di stato](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **Barra di stato con indicatore di stato**  
  
 ![Barra di stato con messaggistica](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **Barra di stato con la descrizione testuale**  
  
##### <a name="infobar"></a>Barra informazioni  
 È simile alla barra di stato, della barra informazioni fornisce notifica contesto e messaggistica, che può essere associato anche con gli indicatori di stato indeterminato, ad esempio l'indicatore di stato o una casella di selezione. La barra informazioni non deve fornire lo stato di avanzamento a livello granulare o indicazione di indicatore di stato. Visualizzare [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barra informazioni con indicatore di stato e messaggistica](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **Barra informazioni con indicatore di stato e descrizione in formato testo**  
  
 ![Barra informazioni in una finestra](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
##### <a name="inline"></a>Inline  
 Indicazione dell'avanzamento inline può essere rappresentato da uno dei tipi di stato di avanzamento del caricatore. In genere è associata l'indicatore di stato con messaggistica, ma questo non è un requisito.  
  
 ![Indicatore di avanzamento inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **Casella combinata con la descrizione testuale di selezione**  
  
 ![Indicatori di stato in pila inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **Barre in pila indicatore di stato**  
  
 ![Messaggistica sullo stato inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **Testo inline di Esplora server: l'aggiornamento...**  
  
##### <a name="tool-windows"></a>Finestre degli strumenti  
 Indicazione dell'avanzamento globale è rappresentato da un indicatore di stato indeterminato posizionato direttamente sotto la barra degli strumenti.  
  
 ![Indicatore di stato indeterminato globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **Barra di stato indeterminato globale di Team Explorer**  
  
##### <a name="dialogs"></a>Finestre di dialogo  
 Le finestre di dialogo può contenere uno dei tipi di stato di avanzamento del caricatore. Gli indicatori di stato possono essere associati con la messaggistica nonché combinati con più livelli di indicazione dell'avanzamento per rappresentare granulare e sub-processi.  
  
 ![Finestra di dialogo con più tipi di indicatori di stato di avanzamento](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **Finestra di dialogo Visual Studio con più tipi di indicatori di stato di avanzamento e processi simultanei**  
  
 ![Finestra di dialogo con caricatore dello stato e messaggistica](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **Finestra di dialogo Visual Studio con caricatore dello stato e l'esecuzione di comandi di inline di messaggistica**  
  
##### <a name="document-well"></a>Documentare anche  
 Il documento può anche visualizzare più tipi di caricatore lo stato di avanzamento in combinazione con i controlli.  
  
 ![Lo stato di avanzamento nel documento e di messaggistica](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **Indicatore di stato indeterminato di sotto della barra degli strumenti**  
  
##### <a name="output-window"></a>Finestra di output  
 La finestra di Output è appropriata per la gestione di progressione di processo e lo stato di avanzamento tramite messaggistica testuale inline. È consigliabile usare la barra di stato e reporting per qualsiasi stato di avanzamento per la finestra Output.  
  
 ![Messaggistica sullo stato nella finestra di Output](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **Finestra di output con lo stato di processo in corso e in attesa di messaggistica**  
  
##  <a name="BKMK_Infobars"></a> Barre informazioni  
  
### <a name="overview"></a>Panoramica  
 Le barre informazioni concedere all'utente un indicatore vicino al relativo punto di attenzione e mediante il controllo barra informazioni condivisa garantisce la coerenza nell'aspetto visivo e interazione.  
  
 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **Barre informazioni in Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Usa appropriato per una barra informazioni  
  
-   Per consentire all'utente un messaggio non bloccante, ma importante rilevante per il contesto corrente  
  
-   Per indicare che l'interfaccia utente è in un determinato stato o una condizione che comporta alcune implicazioni di interazione, ad esempio il debug cronologico  
  
-   Per notificare all'utente che il sistema ha rilevato problemi, ad esempio quando un'estensione sta causando problemi di prestazioni  
  
-   Per fornire all'utente un modo per effettuare con facilità un'azione, ad esempio quando l'editor rileva che un file è misto tabulazioni e spazi  
  
##### <a name="do"></a>Eseguire:  
  
-   Mantenere il testo del messaggio nella barra informazioni brevi e concisi.  
  
-   Mantenere il testo su link e pulsanti concisa.  
  
-   Verificare le opzioni "action" è fornire agli utenti sono minime, che mostra solo le azioni necessarie.  
  
##### <a name="dont"></a>Non:  
  
-   Usare una barra informazioni per rendere disponibili i comandi standard che devono essere inseriti in una barra degli strumenti.  
  
-   Usare una barra informazioni al posto di una finestra di dialogo modale.  
  
-   Creare un messaggio a virgola mobile di fuori di una finestra.  
  
-   Usare le barre più informazioni in diverse posizioni all'interno della stessa finestra.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Le barre più informazioni possono mostrare nello stesso momento?  
 Sì, le barre più informazioni possono mostrare nello stesso momento. Vengono visualizzati in ordine cronologico primo arrivato con la prima barra informazioni che mostra in visualizzazione di barre superiore e ulteriori informazioni riportato di seguito.  
  
 L'utente visualizzerà un massimo di tre barre informazioni alla volta, dopo che, se più barre informazioni sono disponibili, l'area della barra informazioni non sarà più scorrevole.  
  
### <a name="creating-an-infobar"></a>Creazione di una barra informazioni  
 La barra informazioni include quattro sezioni, da sinistra a destra:  
  
-   **Icona:** si tratta in cui si aggiunge un'icona si desidera visualizzare per la barra informazioni, ad esempio un'icona di avviso.  
  
-   **Text:** è possibile aggiungere Trova testo per descrivere l'utente di scenario/situazione, oltre a collegamenti all'interno del testo, se necessario. Tenere presente che il testo conciso.  
  
-   **Le azioni:** questa sezione deve contenere collegamenti e i pulsanti per le azioni che l'utente può richiedere la barra informazioni.  
  
-   **Pulsante Chiudi:** nell'ultima sezione a destra può avere un pulsante Chiudi.  
  
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
  
 Ecco un esempio che crea un InfoBarModel con un testo con un collegamento ipertestuale, un pulsante di azione e un'icona.  
  
 ![Barra informazioni con collegamento ipertestuale](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
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
 Implementa l'interfaccia IVsInfoBar The per fornire una barra informazioni dal codice nativo.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Recupero di una barra informazioni UIElement da una barra informazioni  
 L'implementazione InfoBarModel o IVsInfoBar sono modelli di dati che devono essere trasformati in un oggetto UIElement per poter essere visualizzato nell'interfaccia utente. Un oggetto UIElement può essere recuperato con il servizio SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
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
 Le barre informazioni possono essere visualizzate in uno o più delle seguenti posizioni:  
  
-   Finestre degli strumenti  
  
-   All'interno di una scheda del documento  
  
> [!IMPORTANT]
>  È possibile posizionare una barra informazioni per fornire un messaggio relativo contesto globale. Questo viene visualizzato tra le barre degli strumenti e l'area dei documenti. Questa operazione è sconsigliata perché causa problemi con "passare e jerk" dell'IDE e deve essere evitata se non assolutamente necessario e appropriato.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Inserire una barra informazioni in un ToolWindowPane  
 Il metodo ToolWindowPane.AddInfoBar(IVsInfoBar) può essere utilizzato per aggiungere una barra informazioni per una finestra degli strumenti. Questa API può aggiungere un IVsInfoBar (di cui InfoBarModel è un'implementazione predefinita), o un IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Inserire una barra informazioni in un documento o non ToolWindowPane  
 Per inserire una barra informazioni in qualsiasi oggetto IVsWindowFrame, usare la proprietà VSFPROPID_InfoBarHost per ottenere il IVsInfoBarHost per il frame e quindi aggiungere la barra informazioni UIElement.  
  
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
  
#### <a name="placing-an-infobar-in-the-main-window"></a>L'inserimento di una barra informazioni nella finestra principale  
 Per inserire una barra informazioni nella finestra principale, usare il VSSPROPID_MainWindowInfoBarHost del servizio IVsShell per ottenere IVsInfoBarHost della finestra principale e quindi aggiungervi la barra informazioni UIElement.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>È possibile sapere quando l'utente esegue un'operazione nella mio barra informazioni?  
 Sì, abbiamo restituirà ogni azione dell'evento all'autore barra informazioni. È quindi responsabilità autore barra informazioni per eseguire un'azione in IDE basato sulla selezione dell'utente nella barra informazioni. Le barre informazioni verranno rimossi automaticamente dall'host è stato fatto clic sul cui pulsante chiude, ma sono necessarie altre operazioni se altre barre informazioni devono essere rimosse dopo la chiusura. I dati di telemetria inoltre dovranno essere registrati in modo indipendente da ogni barra informazioni.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Ricezione di eventi in un ToolWindowPane barra informazioni  
 ToolWindowPane dispone di due eventi per le barre informazioni. L'evento InfoBarClosed viene generato quando viene chiusa una barra informazioni nella finestra di ToolWindowPane. L'evento InfoBarActionItemClicked viene generato quando viene selezionato un collegamento ipertestuale o un pulsante all'interno la barra informazioni.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Ricezione di eventi nella barra informazioni direttamente da UIElement  
 IVsInfoBarUIElement.Advise utilizzabile per sottoscrivere gli eventi direttamente da UIElement di una barra informazioni. Implementazione IVsInfoBarUIEvents consentirà all'autore di chiusura di ricezione e gli eventi click.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> Convalida degli errori  
 Quando un utente immette informazioni che non sono accettabili, ad esempio quando un campo obbligatorio è ignorato o all'immissione di dati in formato non corretto, è preferibile usare controllo convalida o commenti e suggerimenti accanto al controllo invece di usare una finestra di dialogo di errore popup blocco.  
  
### <a name="field-validation"></a>Convalida dei campi  
 Convalida di moduli e campi è costituita da tre componenti: un controllo, un'icona e una descrizione comando. Sebbene molti tipi di controlli è possono usare questo, una casella di testo verrà utilizzata come esempio.  
  
 ![Convalida dei campi &#40;vuoto&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 Se il campo è obbligatorio, deve essere presente della filigrana indicante  **\<necessarie >** e lo sfondo del campo deve essere chiaro giallo (VSColor: `Environment.ControlEditRequiredBackground`) e in primo piano deve essere grigio (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Convalida con etichetta "Obbligatorio" dei campi](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 Il programma può determinare che il controllo è in uno stato di *il contenuto non valido inserito* quando lo stato attivo viene spostato in un altro controllo o quando l'utente fa clic su un pulsante commit [OK] o quando l'utente salva il documento o il form.  
  
 Quando viene indicato lo stato del contenuto non valido, verrà visualizzata un'icona all'interno del controllo o semplicemente accanto a esso. Una descrizione comando che descrive l'errore dovrebbe essere visualizzata sul passaggio del mouse sull'icona o il controllo. Inoltre, verrà visualizzato un bordo di 1 pixel intorno al controllo che crea lo stato non valido.  
  
 ![Campo specifiche del layout della convalida](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **Specifiche del layout per la convalida dei campi**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Variazioni accettabile per le icone  
 Esistono innumerevoli casi specifici in cui gli utenti dovranno essere informata degli errori di convalida. Se si considera il tipo di controllo e la configurazione dell'interfaccia utente, scegliere la posizione di icona appropriata alle proprie esigenze.  
  
 ![Posizioni accettabili per le icone](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **Variazioni accettabile per i percorsi di icona convalida campo**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Convalida che richiede un round trip a una connessione di rete o server  
 In alcuni casi, è necessario un round trip al server per verificare il contenuto e potrebbe essere importante mostrare l'utente lo stato di avanzamento, verificato e gli stati di errore. La figura riportata di seguito viene illustrato un esempio di questo case e l'interfaccia utente di consigliato.  
  
 ![Convalida che prevede un round trip a un server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **Convalida che prevede un round trip a un server**  
  
 Si noti che è necessario fornire spazio disponibile sufficiente a destra del controllo per adattarsi al testo "Verifica in corso" e "Riprova".  
  
#### <a name="in-place-warning-text"></a>Testo dell'avviso sul posto  
 Quando c'è spazio disponibile per inserire il messaggio di errore vicino al controllo in uno stato di errore, ciò è preferibile utilizzare la descrizione comando da solo.  
  
 ![In&#45;avviso di posizionare](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **Testo dell'avviso sul posto**  
  
#### <a name="watermarks"></a>Filigrane  
 In alcuni casi un intero controllo o finestra è in stato di errore. In questo caso, usare una filigrana per indicare l'errore.  
  
 ![Filigrana](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 07_Watermark")  
  
 **Convalida del campo della filigrana**