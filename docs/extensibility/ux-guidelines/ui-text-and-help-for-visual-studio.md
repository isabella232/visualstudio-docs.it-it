---
title: Testo dell'interfaccia utente e Guida per Visual Studio . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3247aeaa702b59722471c7d28e98957f04f3e07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698289"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Testo dell'interfaccia utente e Guida per Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>Testo dell'interfaccia utente e terminologia
 Il testo comprensibile è fondamentale per un'interfaccia utente efficace. Gli utenti di software tendono a leggere le etichette prima, vale a dire quelli più rilevanti per completare il compito a portata di mano. Il testo statico viene letto con minore frequenza. Pianificare per gli utenti di avviare le sessioni di lavoro con una rapida analisi dell'intera finestra, seguita da una lettura dell'interfaccia utente nel presente ordine approssimativo:

1. Controlli interattivi al centro

2. Pulsanti commit

3. Controlli interattivi trovati altrove

4. Istruzioni principali

5. Spiegazioni supplementari

6. Titolo della finestra

7. Altro testo statico nel corpo principale

### <a name="usage-patterns-for-ui-text"></a>Modelli di utilizzo per il testo dell'interfaccia utenteUsage patterns for UI text

#### <a name="title-bar-text"></a>Testo per la barra del titolo
 Il testo della barra del titolo deve corrispondere al comando che ha generato l'interfaccia utente.

#### <a name="instructional-text-helper-text"></a>Testo informativo (testo di supporto)
 In alcune finestre di dialogo, è utile fornire istruzioni principali importanti per spiegare cosa fare nella finestra o nella pagina. Questo è a volte indicato come "testo helper".

##### <a name="writing-style-rules-for-helper-text"></a>Regole di stile di scrittura per il testo helper

- Non spiegare l'ovvio. A meno che non sia assolutamente necessario, non includere testo informativo.

- Il testo informativo viene sempre posizionato nella parte superiore della finestra di dialogo e deve fare riferimento all'attività eseguita.

- Spiegare esattamente agli utenti cosa devono fare. Evitare comunicazioni e ridondanza eccessive.

- Esaminare ogni finestra ed eliminare le parole e le istruzioni duplicate.

- Mantenere breve il testo informativo. Se sono necessarie ulteriori informazioni per determinati utenti o scenari, fornire un collegamento a un argomento online concettuale dettagliato.

- Scrivi il tuo testo in modo che ogni parola abbia un peso ed è necessaria.

- Seguire le linee guida Microsoft esistenti per Testo e [stile e tono](/windows/desktop/uxguide/text-style-tone) [dell'interfaccia utente](/windows/desktop/uxguide/text-ui) .

#### <a name="supplemental-instructions"></a>Istruzioni supplementari
 Le istruzioni aggiuntive forniscono informazioni aggiuntive che consentono all'utente di comprendere i controlli o i raggruppamenti di controlli. Ciò potrebbe includere anche il testo del suggerimento necessario per comprendere il formato previsto dal controllo di input. Utilizzare istruzioni supplementari con parsimonia. Riservarli per i casi in cui è probabile che l'utente non comprenderà appieno le ramificazioni della scelta che stanno facendo.

 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Testo supplementare in Visual Studio**

 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Testo supplementare in Visual Studio**

#### <a name="infotips"></a>Suggerimenti informativi
 Spesso, il testo informativo potrebbe essere troppo lungo per posizionare sul posto nell'interfaccia utente o potrebbe essere utile solo per i nuovi utenti, sentendosi come disordine agli utenti esperti. In questo caso, il testo informativo/didattico deve essere inserito come descrizione comando sotto un suggerimento informativo.

 I suggerimenti informativi devono essere posizionati accanto ai controlli a cui sono correlati e devono utilizzare l'icona specifica del suggerimento informazioni, che non è ancora discreta.

 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Esempio di suggerimento informazioni in Visual StudioExample of an InfoTip in Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Scrittura delle regole di stile per i suggerimenti informativi

- Scrivere i suggerimenti informativi come frasi complete. Richiedono verbi specifici, maiuscole/minuscole e punteggiatura finale.

- Utilizzare i suggerimenti informativi per integrare le istruzioni o le informazioni principali. Se stai usando parole diverse per riformulare l'idea principale, non hai bisogno di un suggerimento informativo.

- Mantenere i suggerimenti informativi brevi e dolci. Usa parole piccole e un linguaggio semplice e quotidiano che supporti e incoraggi l'utente.

- Seguire le linee guida Microsoft esistenti per Testo e [stile e tono](/windows/desktop/uxguide/text-style-tone) [dell'interfaccia utente](/windows/desktop/uxguide/text-ui) .

#### <a name="control-labels"></a>Etichette di controllo
 Le etichette dei controlli devono essere brevi e concise e seguire le linee guida per [Windows Desktop per i controlli](/windows/desktop/uxguide/controls).

 Per ulteriori informazioni sul formato dell'etichetta del controllo e sulla posizione all'interno dell'interfaccia utente, fare riferimento a [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Collegamenti della Guida
 I collegamenti della Guida possono essere inseriti all'interno di testo informativo o nel corpo dell'interfaccia utente. Possono essere collegamenti alla Guida o avviare finestre di dialogo interne.

##### <a name="visual-style-rules-for-help-links"></a>Regole di stile di visualizzazione per i collegamenti della Guida

- Utilizzare i colori di ambiente corretti per i collegamenti ipertestuali. Un collegamento ipertestuale con uno stile corretto non lampeggia brevemente in rosso quando si fa clic. Se vedete questo, allora è un'indicazione che i colori dell'ambiente non vengono utilizzati.

- Le sottolineature devono essere utilizzate solo al passaggio del mouse o quando il collegamento è incorporato in un paragrafo.

- Per informazioni più dettagliate sugli stili visivi e di interazione per i collegamenti ipertestuali, vedere Pulsanti e collegamenti ipertestuali.

##### <a name="writing-style-rules-for-help-links"></a>Scrittura di regole di stile per i collegamenti della Guida

- Quando si avviano le finestre di dialogo, mantenere gli standard per i puntini di sospensione: senza puntini di sospensione per la navigazione, puntini di sospensione se l'attività richiede un'interfaccia utente aggiuntiva.

     ![Collegamento Guida in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **I puntini di sospensione (...) in un collegamento della Guida indicano che l'attività richiederà un'interfaccia utente aggiuntiva.**

- I collegamenti non devono iniziare con "Impara", in quanto non è questo l'intento dell'utente. L'utente desidera rispondere a una domanda specifica, non ricevere una formazione generale.

- Collegamenti di guida frase in modo che pongono la domanda che l'argomento risponderà.

     Non corretto: "Ulteriori informazioni sui prezzi dei servizi Windows Azure Mobile Services"

     Corretto: "Quali opzioni di prezzo sono disponibili per i servizi Windows Azure Mobile?"

- Non utilizzare mai *Click...* per il testo del collegamento.

- Non collegare mai solo la parola "qui". Questo è problematico per alcune utilità per la lettura dello schermo, che vocalizzerà solo la parola con collegamento ipertestuale.

     Non corretto: "Trova informazioni sui servizi Windows Azure Mobile **qui"**

     Corretto: "Quali opzioni di prezzo sono disponibili per i servizi Windows Azure Mobile?"

- Per ulteriori informazioni sullo stile di scrittura corretto per i collegamenti della Guida, vedere le linee guida di [Windows Desktop per la Guida .](/windows/desktop/uxguide/winenv-help)

#### <a name="hint-text"></a>Testo del suggerimento
 Il testo del suggerimento viene visualizzato come filigrana all'interno di un controllo o sotto il controllo. La formattazione corretta verrà applicata utilizzando `Environment.GrayText`il token VSColors appropriato, .

 Può apparire in un certo numero di forme.

- Al posto dell'etichetta di controllo:

     ![Testo del suggerimento in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Con un verbo, dando istruzioni:

     ![Testo del suggerimento in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Con testo che indica una voce obbligatoria:

     ![Testo del suggerimento in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Testo filigrana
 In un'area di progettazione vuota, il testo deve indicare cosa fare, nonché fornire collegamenti per aprire altre finestre correlate, se appropriato:On an empty design surface, the text should indicate what to do, as well as provide links to open other related windows, if appropriate:

 ![Testo filigrana in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Esempio di testo della filigrana in Visual StudioExample of watermark text in Visual Studio**

### <a name="common-terminology"></a>Terminologia comune

|Termine|Spiegazione|Comment|
|----------|-----------------|-------------|
|Accedi / Esci|Verbi utilizzati sinonimo di Web per rappresentare l'autenticazione in una proprietà web. All'interno dei client, usiamo questo una volta come nozione di primo livello per l'accesso e la disconnessione dalla connessione utente IDE, che rappresenta un'identità di primo livello che fornisce funzionalità di livello superiore, ad esempio roaming e licenze che non sono disponibili con tutte le altre connessioni.|L'utente IDE è l'unica funzionalità che deve rappresentare un verbo di accesso / disconnessione, in quanto rappresenta l'utente IDE di primo livello.|
|Connetti /Disconnetti|Utilizzare in luoghi in cui una funzionalità mantiene una singola connessione a un servizio online.|Esplora server, in cui è possibile avere una sola connessione di Azure attiva alla volta, è un esempio di connessione/disconnessione.|
|Aggiungi / Rimuovi|Non distruttivo. Utilizzare per l'aggiunta o la rimozione di un elemento da un elenco.|La finestra di dialogo elenco server di Gestione connessione TFS è un esempio di Aggiungi/Rimuovi.|
|Delete|Distruttivo. Utilizzare solo quando l'elemento da rimuovere verrà eliminato o eliminato definitivamente dal disco.|"Elimina" richiede in genere una richiesta se il risultato è l'eliminazione di un file dal disco.|

## <a name="error-messages"></a>messaggi di errore

### <a name="overview"></a>Panoramica
 Si verificano errori. L'impostazione di limitazioni su ciò che l'utente può fare è un primo passo ragionevole per evitare messaggi di errore evitabili. Tuttavia, quando si verifica un errore, un messaggio di errore ben scritto può andare un lungo cammino verso la mitigazione del problema. I messaggi di errore sono probabilmente uno dei tipi più importanti di notifica che l'utente vede, perché sono sincroni e indicano un problema che deve essere risolto. Messaggi di errore scritti in modo inadeguato lasciano gli utenti soli a decidere la causa degli errori e le possibili soluzioni.

 Gli utenti potrebbero smettere di prestare attenzione ai messaggi di errore sovrautilizzati o confusi, quindi scrivere solo i messaggi necessari che aggiungono valore all'esperienza utente. Se il messaggio è semplicemente una notifica, utilizzare una presentazione alternativa.

### <a name="rules-for-creating-an-error-message"></a>Regole per la creazione di un messaggio di errore

- Quando si creano messaggi di errore, scegliere il livello di errore appropriato per il gruppo di destinatari. Puntare a riepiloghi semplici che forniscono un'azione che l'utente può eseguire, se applicabile. Non indicare nulla che l'utente non ha bisogno di sapere.

- Fornire assistenza costruttiva. È più facile leggere e agire su un messaggio di errore che contiene istruzioni.

- Non usare doppi negativi.

- Eseguire un controllo grammaticale e ortografico automatico e manuale su qualsiasi messaggio di errore scritto.

- Per i messaggi di errore complessi, evitare le comunicazioni sequenziali. Non utilizzare mai un collegamento F1 per il messaggio di errore. Il messaggio stesso dovrebbe essere sufficiente.

- Utilizzare l'icona corretta.

- Semplifica la comprensione delle domande e usa pulsanti con scelte chiare, come "Elimina" e "Annulla".

- Per gli avvertimenti, essere chiari su quali saranno le conseguenze del procedere. I pulsanti dovrebbero indicare la conseguenza.

- Per gli errori, descrivere le operazioni che l'utente può eseguire per risolvere il problema. I pulsanti devono essere azioni o dire "Chiudi". Non utilizzare un pulsante "OK" per un messaggio di errore.

- Alcune domande da porsi durante la creazione di un messaggio di errore:Some questions to ask yourself when constructing an error message:

  - L'utente può capire come risolvere il problema con questo errore da solo?

  - L'utente utilizza lo stesso vocabolario di questo errore?

  - Questo errore è ambigious o condiviso in più situazioni? In caso affermativo, in che modo guidare gli utenti alla soluzione di cui hanno bisogno?

#### <a name="build-errors"></a>Errori di compilazione
 Poiché Visual Studio è uno strumento di sviluppo software, molti dei relativi componenti dispongono di un passaggio di compilazione, conversione o codifica per convertire il lavoro dello sviluppatore in formato binario. Queste conversioni possono causare errori quando il compilatore non è in grado di elaborare file creati in modo non corretto o quando le opzioni del compilatore non sono state impostate correttamente.

 Gli utenti di Visual Studio possono dedicare un numero enorme di ore di sviluppo per risolvere gli errori di compilazione. Questo tempo di risoluzione aumenta quando gli errori hanno dipendenze o quando i messaggi di errore sono scritti in modo non adeguato, il che può rendere difficile scoprire l'origine dell'errore.

 Gli errori di compilazione migliori sono quelli che non si verificano in primo luogo, motivo per cui Visual Studio fornisce completamento automatico e IntelliSense scarabocchi. I validatori dello schema e strumenti simili forniscono lo stesso tipo di feedback. Questi meccanismi guidano in modo proattivo l'utente a costruire codice ben formato, disgrazie alla possibilità di errori di compilazione.

 Visual Studio fornisce una finestra degli strumenti in cui gli utenti possono leggere e spostarsi tra gli errori che si sono verificati nelle finestre di documento. I tasti di scelta rapida vengono forniti in modo che l'utente possa spostarsi rapidamente in grandi quantità di codice e passare direttamente alla posizione del problema. Visual Studio consente inoltre a ogni errore di compilazione di essere collegato a una determinata parola chiave della Guida/ID di contesto in modo che l'utente possa passare direttamente a un argomento della Guida che fornisce informazioni più approfondite sull'errore.

 Scrivere errori di compilazione chiari e concisi:Write clear, concise build errors:

- Utilizzare un **linguaggio semplice** che spiega il problema con poco o nessun gergo del compilatore. Il testo di un errore di compilazione non deve essere eccessivamente tecnico.

- **Delineare le possibili cause.** Ad esempio, "Manca un segno di due punti tra la proprietà e il valore nella dichiarazione '(proprietà) : (valore)'".

- Fornire dettagli sulle potenziali correzioni. Se lo spazio disponibile non è sufficiente, è possibile inserire ulteriori dettagli nell'argomento della Guida corrispondente.

### <a name="components-of-a-well-written-error-message"></a>Componenti di un messaggio di errore ben scritto

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utilizzare il servizio di finestra di dialogo della shell per i messaggi di errore.
 L'utilizzo del servizio finestra di dialogo della shell consente di controllare l'aspetto del messaggio, in particolare dei tipi di carattere, senza apportare modifiche importanti ai singoli elementi. Utilizzare i meccanismi **IErrorInfo** e segnalarli utilizzando **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Scegli una presentazione di notifica efficace e appropriata.
 Utilizzare una finestra di dialogo modale con un avviso critico se è necessaria un'azione immediata per evitare la perdita di dati (notifica sincrona). Le icone critiche sono riservate alle situazioni in cui la chiusura del messaggio senza leggerlo può portare a conseguenze negative. La perdita di dati è una situazione critica che richiede una risposta a livello di allarme. L'uso eccessivo dell'icona critica desensibilizza gli utenti alla sua importanza. Se il messaggio di errore è di natura informativa, prendere in considerazione alternative a una finestra di dialogo modale (notifica asincrona).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fornire una spiegazione pulita e concisa del motivo per cui il problema si è verificato piuttosto che una spiegazione tecnica.
 Sovraccaricare gli utenti con dettagli tecnici nella spiegazione renderà loro più probabilità di ignorare i messaggi di errore. Esempi di buoni messaggi:

- "Impossibile aprire il file richiesto."

- "Impossibile connettersi a Internet."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fornire informazioni su come risolvere il problema.
 Offrire all'utente suggerimenti su come risolvere il problema. Sii onesto con l'utente se non ci sono suggerimenti. Fornire collegamenti diretti a fonti online alternative, ad esempio supporto tecnico o supporto della community. Provare a indirizzare gli utenti a informazioni online specifiche pertinenti al problema. Per un ID errore, è consigliabile collegare gli utenti a un thread di discussione relativo a tale errore specifico. Esempi di buoni messaggi:

- "Assicurarsi di essere connessi a Internet e ripetere l'operazione."

- "Assicurarsi che il file esista e di disporre dell'autorizzazione per aprirlo."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Scrivere un messaggio breve e al punto.
 Un messaggio di errore può notificare, spiegare e offrire una soluzione, ma comunque essere ignorato se è troppo wordy. Una soluzione consiste nell'utilizzare la divulgazione progressiva con un pulsante dei dettagli. Ad esempio, fornire una breve descrizione/soluzione e quindi inserire ulteriori dettagli sotto un pulsante dei dettagli. Se gli utenti scelgono di leggere ulteriori informazioni sull'errore, possono farlo.

 La lingua nel messaggio deve essere:

- **Adatto al dominio.** Usa la lingua che l'utente capirà. Anche se i nostri clienti sono sviluppatori, spesso non hanno il contesto e la terminologia che abbiamo.

- **Specifico.** Evitare formulazioni vaghe e fornire nomi e posizioni specifici degli oggetti coinvolti. Ad esempio, un messaggio di errore come "carattere non valido" non è utile. Quale personaggio? "File non trovato." Quale file?

- **Cortese.** Non incolpare l'utente o farli sentire stupidi. Evitare linguaggio ostile o offensivo (uccidere, eseguire, terminare, fatale, illegale). Evitare il testo in maiuscolo, che è spesso visto come grida e non è così leggibile. Non usare l'umorismo.

- **Corretta.** Usa l'ortografia e la grammatica corrette (anche negli alfa). Gli etiomi sono poco professionali e imbarazzanti.

- **Contestualmente appropriato.** Utilizzare il testo del pulsante appropriato. Evitare il pulsante "OK" e utilizzare invece "Continua" o "Sì/No".

### <a name="error-message-examples"></a>Esempi di messaggi di errore

|Buone|Non valido|
|----------|---------|
|"Il numero che hai registrato non è più in servizio. Controllare il numero e comporre di nuovo o comporre 0 per l'operatore."|- "Errore (449): numero non valido"<br />- "Questo errore di eccezione non gestita indica che l'operazione è stata completata correttamente."<br /><br /> ![Messaggio di errore non valido in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Accesso alla Guida

### <a name="overview"></a>Panoramica
 Oltre alla documentazione in MSDN, un utente di Visual Studio dispone di diversi punti di accesso per assistere l'utente durante l'interfaccia utente. Per garantire che questi punti di accesso siano costantemente disponibili, i team delle funzionalità devono sfruttare il sistema di Guida offerto dall'ambiente. Questi punti di accesso sono:These access points are:

- **Testo didattico e supplementare nelle finestre di dialogo.** Testo statico che fornisce direzione o spiegazione, sulla superficie dell'interfaccia utente o disponibile al passaggio del mouse su un'icona della descrizione informazioni.

- **F1 Aiuto** (solo editor). All'interno dell'editor di Visual Studio, un utente può considerare attendibile che in qualsiasi momento, premendo F1 verrà visualizzato un argomento della Guida specifico per la selezione corrente. Assicurarsi che gli argomenti associati a F1 siano appropriati e informativi.

- **Collegamenti ipertestuali ad argomenti della Guida.** Collegamento ipertestuale all'interno di una finestra di dialogo, una finestra degli strumenti o un'area di progettazione che avvia un argomento per aiutare l'utente a ottenere ulteriori informazioni su una tecnologia, funzionalità o informazioni su come eseguire un'attività.

- **Meccanismi dell'interfaccia utente di supporto, ad esempio smart tag e finestre di dialogo di compilazione.** Questi meccanismi consentono all'utente di comprendere un elemento dell'interfaccia utente o di facilitare un'attività, ad esempio smart tag o finestre di dialogo del generatore.

- **Pulsanti della Guida dell'interfaccia utente** (deprecati). Indicatore visibile nella barra del titolo che consente di accedere all'argomento della Guida F1 correlato.

### <a name="text"></a>Testo

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Testo informativo e supplementare nelle finestre di dialogo
 Nelle finestre di dialogo che supportano attività complesse, potrebbe essere necessario fornire testo informativo all'interno dell'interfaccia utente, spesso nella parte superiore della finestra di dialogo o quasi controlli complessi. Vedere [Testo e terminologia dell'interfaccia utente](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) per informazioni dettagliate sullo stile di scrittura.

#### <a name="infotips"></a>Suggerimenti informativi
 Spesso, il testo informativo potrebbe essere troppo lungo per essere posizionato sul posto nell'interfaccia utente o potrebbe essere utile solo per i nuovi utenti, sensazione di disordine per gli utenti esperti. In questo caso, il testo informativo/didattico deve essere inserito come descrizione comando sotto un suggerimento informativo.

 I suggerimenti informativi devono essere posizionati accanto ai controlli a cui sono correlati e devono utilizzare l'icona specifica del suggerimento informazioni, che non è ancora discreta.

 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Esempio di suggerimento informazioni in Visual StudioExample of an InfoTip in Visual Studio**

### <a name="interactive-help-mechanisms"></a>Meccanismi di aiuto interattivi

#### <a name="f1-help"></a>Guida sensibile al contesto
 La Guida F1 è necessaria all'interno di un editor o di un'area di progettazione, ma non in un'altra posizione nell'ambiente di Visual Studio.F1 Help is required within an editor or design surface, but not elsewhere in the Visual Studio environment.

#### <a name="hyperlinks-to-help-topics"></a>Collegamenti ipertestuali ad argomenti della Guida
 I collegamenti ipertestuali possono essere utilizzati per eseguire un'azione, spostarsi all'interno dell'IDE o avviare la Guida in un browser. Vedere [Testo e terminologia dell'interfaccia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) utente per informazioni dettagliate sulla lingua e 07.10.01 Pulsanti e collegamenti ipertestuali per le linee guida visive e di layout.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Pulsanti della Guida [?] nelle barre del titolo della finestra di dialogo (deprecate)
 Per la maggior parte, i pulsanti Guida [?] nella barra del titolo delle finestre di dialogo sono deprecati. Gli argomenti dell'interfaccia utente non fanno più parte del modello di documento e pertanto potrebbe non essere presente un argomento rilevante a cui collegarsi. Essenzialmente, il pulsante della barra del titolo era la stessa cosa della Guida F1 e che non è più necessario nelle finestre di dialogo. In alcuni casi, questo può ancora essere utilizzato come un indicatore che vi sono informazioni più concettuali o procedurali disponibili, anche se i collegamenti ipertestuali sono più comunemente utilizzati nell'interfaccia utente più recente.

##### <a name="dialogs-created-through-the-environment"></a>Finestre di dialogo create tramite l'ambiente
 Molte finestre di dialogo della shell vengono create tramite la funzione **VBDialogBoxParam.Many** shell dialogs are created through the VBDialogBoxParam function. Questa funzione condivisa è stata aggiornata per facilitare lo spostamento del pulsante **Guida** dalla finestra di dialogo al **?** mantenendo un'architettura compatibile con le versioni precedenti ed estensibile.

 In particolare, la funzione **VBDialogBoxParam** esamina il modello di finestra di dialogo per un pulsante il cui ID è **IDHELP** (9) o l'etichetta è **Help** o **&Help**. Se viene trovato un pulsante della Guida, questo viene nascosto e lo stile **WS_EX_CONTEXTHELP** viene aggiunto alla finestra di dialogo, che inserisce il **?** nella barra del titolo della finestra di dialogo.

 Quando viene creata, la finestra di dialogo viene inserita in uno stack e viene richiamata la finestra di dialogo con una finestra di dialogo di pre-elaborazione denominata **DialogPreProc**. Quando il **?** si fa clic, invia una **WM_SYSCOMMAND** di **SC_CONTEXTHELP** alla finestra di dialogo. **Il DialogPreProc** acquisisce questo comando e lo modifica in un **messaggio di WM_HELP,** che viene passato al proc finestra di dialogo originale.

 La maggior parte delle finestre di dialogo create dall'ambiente dispone di un pulsante ?. Quando viene visualizzata la finestra di dialogo, il pulsante Guida è nascosto automaticamente e solo il **?** funziona. Se il **?** viene mai rimosso o modificato in Windows, questa soluzione consente di tornare rapidamente ai pulsanti della Guida originale.

 Questa soluzione fa quattro presupposti che potrebbero causare bug:

- Il pulsante di aiuto della finestra di dialogo è **IDHELP** (9).

- La finestra di dialogo sembra corretta quando il pulsante Guida è nascosto.

- La finestra di dialogo non sostituisce winproc.

- La finestra di dialogo non è incorporata all'interno di un'altra finestra di dialogo.

  Se la finestra di dialogo si trova all'interno di msenv e non utilizza **VBDialogBoxParam**, esaminare l'utilizzo di **VBDialogBoxParam** prima di implementare un gestore personalizzato.

##### <a name="dialogs-created-through-other-packages"></a>Finestre di dialogo create tramite altri pacchetti
 È possibile implementare una soluzione personalizzata per le finestre di dialogo che si trovano all'esterno di msenv.You can implement your own solution for dialogs that reside outside msenv. Per una classe di finestra di dialogo condivisa nel pacchetto VSPackage, è consigliabile spostare il pulsante nella barra del titolo o implementare un gestore in ogni finestra di dialogo. Il codice seguente è uno scheletro di un'implementazione che consente di iniziare:The following code is a skeleton of an implementation to help you get started:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Pulsanti della Guida nel codice gestito
 L'override del comportamento predefinito del pulsante Guida della barra del titolo della finestra è semplice nel codice gestito. Di seguito è riportata un'applicazione dimostrativa completamente questo comportamento. In sostanza, è necessario eseguire l'override del metodo **WndProc** del form e quindi generare richieste di aiuto F1 quando viene intercettato un messaggio **SC_CONTEXTHELP.**

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Vedere anche
- [Tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Notifiche e avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
