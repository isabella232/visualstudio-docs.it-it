---
title: Testo dell'interfaccia utente e guida per Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748959"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Testo dell'interfaccia utente e guida per Visual Studio
## <a name="BKMK_UITextAndTerminology"></a>Testo e terminologia dell'interfaccia utente
 Un testo comprensibile è essenziale per l'interfaccia utente efficace. Gli utenti software tendono a leggere prima le etichette, ovvero quelle più rilevanti per completare l'attività. Il testo statico viene letto con una frequenza minore. Pianificare agli utenti di avviare le sessioni di lavoro con un'analisi veloce dell'intera finestra, seguita da una lettura dell'interfaccia utente in questo ordine approssimativo:

1. Controlli interattivi al centro

2. Pulsanti di commit

3. Controlli interattivi trovati altrove

4. Istruzioni principali

5. Spiegazioni aggiuntive

6. Titolo della finestra

7. Altro testo statico nel corpo principale

### <a name="usage-patterns-for-ui-text"></a>Modelli di utilizzo per il testo dell'interfaccia utente

#### <a name="title-bar-text"></a>Testo della barra del titolo
 Il testo della barra del titolo deve corrispondere al comando che ha generato l'interfaccia utente.

#### <a name="instructional-text-helper-text"></a>Testo istruttivo (testo Helper)
 In alcune finestre di dialogo è utile fornire importanti istruzioni principali per spiegare cosa fare nella finestra o nella pagina. Questa operazione viene a volte definita "testo Helper".

##### <a name="writing-style-rules-for-helper-text"></a>Scrittura di regole di stile per il testo Helper

- Non spiegare l'ovvio. A meno che non sia assolutamente necessario, non includere il testo istruttivo.

- Il testo informativo viene sempre inserito nella parte superiore della finestra di dialogo e deve fare riferimento all'attività eseguita.

- Spiegare con precisione agli utenti le attività necessarie. Evitare una comunicazione e una ridondanza eccessive.

- Esaminare ogni finestra ed eliminare parole e istruzioni duplicate.

- Mantieni il testo dell'istruzione breve. Se sono necessarie altre informazioni per determinati utenti o scenari, fornire un collegamento a un argomento dettagliato in linea concettuale.

- Scrivere il testo in modo che ogni parola contenga peso ed è necessario.

- Seguire le indicazioni Microsoft esistenti per il [testo dell'interfaccia utente](/windows/desktop/uxguide/text-ui) e [lo stile e il tono](/windows/desktop/uxguide/text-style-tone).

#### <a name="supplemental-instructions"></a>Istruzioni supplementari
 Le istruzioni aggiuntive forniscono informazioni aggiuntive che consentono all'utente di comprendere i controlli o i raggruppamenti di controlli. Questo può includere anche testo di suggerimento necessario per comprendere il formato previsto dal controllo di input. Usare le istruzioni aggiuntive con moderazione. Riservarle per i casi in cui è probabile che l'utente non abbia compreso completamente le ramificazioni della scelta effettuata.

 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Testo supplementare in Visual Studio**

 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Testo supplementare in Visual Studio**

#### <a name="infotips"></a>Infotip
 Spesso il testo informativo potrebbe essere troppo lungo per posizionarsi sul posto nell'interfaccia utente o può essere utile solo per i nuovi utenti, in modo simile a un disordine per gli utenti esperti. In questo caso, il testo informativo/informativo deve essere inserito come descrizione comando in un InfoTip.

 Infotip deve essere posizionata vicino ai controlli a cui è correlata e deve usare l'icona InfoTip specifica, che è non intrusiva ma notabile.

 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Esempio di InfoTip in Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Scrittura di regole di stile per infotip

- Scrivere infotip come frasi complete. Richiedono verbi specifici, maiuscole e minuscole e la punteggiatura finale.

- Usare infotip per integrare le istruzioni o le informazioni principali. Se si usano solo parole diverse per riaffermare l'idea principale, non è necessario un InfoTip.

- Mantieni infotip breve e dolce. Usare parole piccole e semplici lingue che supportano e incoraggiano l'utente.

- Seguire le indicazioni Microsoft esistenti per il [testo dell'interfaccia utente](/windows/desktop/uxguide/text-ui) e [lo stile e il tono](/windows/desktop/uxguide/text-style-tone).

#### <a name="control-labels"></a>Etichette di controllo
 Le etichette dei controlli devono essere brevi, concise e seguire le [indicazioni per il desktop di Windows per i controlli](/windows/desktop/uxguide/controls).

 Per ulteriori informazioni sul formato e sul posizionamento delle etichette di controllo all'interno dell'interfaccia utente, vedere [layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Collegamenti alla guida
 I collegamenti alla guida possono essere posizionati all'interno di un testo informativo o nel corpo dell'interfaccia utente. Possono essere collegamenti per consentire o avviare finestre di dialogo interne.

##### <a name="visual-style-rules-for-help-links"></a>Regole dello stile di visualizzazione per i collegamenti della Guida

- Usare i colori di ambiente corretti per i collegamenti ipertestuali. Quando si fa clic su un collegamento ipertestuale con stile appropriato non lampeggerà brevemente il rosso. Se viene visualizzato questo, significa che i colori dell'ambiente non vengono usati.

- Le sottolineature devono essere usate solo al passaggio del mouse o quando il collegamento è incorporato in un paragrafo.

- Per informazioni più dettagliate sugli stili visivi e di interazione per i collegamenti ipertestuali, vedere pulsanti e collegamenti ipertestuali.

##### <a name="writing-style-rules-for-help-links"></a>Scrittura di regole di stile per i collegamenti della Guida

- Quando si avviano finestre di dialogo, mantenere gli standard per i puntini di sospensione: nessun ellisse per la navigazione, ellissi se l'attività richiede un'interfaccia utente aggiuntiva.

     ![Collegamento alla Guida in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **I puntini di sospensione (...) in un collegamento alla guida indicano che l'attività richiederà un'interfaccia utente aggiuntiva.**

- I collegamenti non devono iniziare con "Learn", perché questo non è lo scopo dell'utente. L'utente vuole rispondere a una domanda specifica, non ricevere una formazione generale.

- Frase collegamenti Guida in modo da porre la domanda a cui risponderà l'argomento.

     Errato: "ulteriori informazioni sui prezzi di servizi mobili di Microsoft Azure"

     Corretto: "quali opzioni di prezzo sono disponibili per i servizi mobili di Windows Azure?"

- Non usare mai *Click...* nel testo del collegamento.

- Non collegare mai solo la parola "Here". Si tratta di un problema per alcune utilità per la lettura dello schermo, che consente di esprimere solo la parola con collegamento ipertestuale.

     Errato **: "informazioni su servizi mobili**di Microsoft Azure"

     Corretto: "quali opzioni di prezzo sono disponibili per i servizi mobili di Windows Azure?"

- Per ulteriori informazioni sullo stile di scrittura corretto per i collegamenti della guida, vedere la Guida [di Windows Desktop](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Testo suggerimento
 Il testo del suggerimento viene visualizzato come filigrana all'interno di un controllo o sotto il controllo. La formattazione corretta verrà applicata utilizzando il token VSColors appropriato, `Environment.GrayText`.

 Può essere visualizzato in diversi formati.

- Al posto dell'etichetta del controllo:

     ![Testo suggerimento in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Con un verbo, che fornisce istruzioni:

     ![Testo suggerimento in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Con il testo che indica una voce obbligatoria:

     ![Testo suggerimento in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Testo filigrana
 In un'area di progettazione vuota, il testo deve indicare cosa fare e fornire collegamenti per aprire altre finestre correlate, se appropriato:

 ![Testo della filigrana in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Esempio di testo della filigrana in Visual Studio**

### <a name="common-terminology"></a>Terminologia comune

|Termine|Descrizione|Commento|
|----------|-----------------|-------------|
|Accesso/disconnessione|Verbi usati in sinonimo con il Web per la rappresentazione dell'autenticazione in una proprietà Web. Nei client viene usata una sola volta come concetto di primo livello per l'accesso e la disconnessione dell'IDE, che rappresenta un'identità di primo livello che fornisce funzionalità di livello superiore, ad esempio roaming e licenze che non sono disponibili con tutte le altre connessioni.|L'utente IDE è l'unica funzionalità che deve rappresentare un verbo di accesso/disconnessione, perché rappresenta l'utente IDE di primo livello.|
|Connetti/Disconnetti|Usare in posizioni in cui una funzionalità gestisce una singola connessione a un servizio online.|Esplora server, in cui è possibile avere una sola connessione di Azure attiva alla volta, è un esempio di connessione/disconnessione.|
|Aggiungi/Rimuovi|Non distruttivo. Usare quando si aggiunge o si rimuove un elemento da un elenco.|La finestra di dialogo elenco Server gestione connessione TFS è un esempio di aggiunta/rimozione.|
|Eliminazione|Distruttiva. Utilizzare solo quando l'elemento da rimuovere verrà rimosso definitivamente o eliminato dal disco.|"Delete" richiede in genere un prompt se il risultato è l'eliminazione di un file dal disco.|

## <a name="error-messages"></a>Messaggi di errore

### <a name="overview"></a>Panoramica
 Si verificano errori. L'impostazione di limitazioni sulle operazioni che l'utente può eseguire è un primo passaggio ragionevole nella prevenzione dei messaggi di errore evitabili. Tuttavia, quando si verifica un errore, un messaggio di errore ben scritto può andare a lungo per attenuare il problema. I messaggi di errore sono probabilmente uno dei tipi più importanti di notifica che l'utente vede, perché sono sincroni e indicano un problema che deve essere risolto. I messaggi di errore scritti in modo non corretto lasciano gli utenti da soli a decidere la cause degli errori e le possibili soluzioni.

 È possibile che gli utenti smettano di prestare attenzione ai messaggi di errore sovrautilizzati o confondenti, quindi scrivere solo i messaggi necessari che aggiungono valore all'esperienza utente. Se il messaggio è semplicemente una notifica, usare una presentazione alternativa.

### <a name="rules-for-creating-an-error-message"></a>Regole per la creazione di un messaggio di errore

- Quando si creano messaggi di errore, scegliere il livello di errore appropriato per il gruppo di destinatari. Scopo per riepiloghi semplici che forniscono un'azione che l'utente può intraprendere, se applicabile. Non dichiarare alcun elemento che l'utente non deve conoscere.

- Fornire assistenza costruttiva. È più facile leggere e agire su un messaggio di errore contenente istruzioni.

- Non usare i doppi negativi.

- Eseguire sia una grammatica automatizzata che una grammatica manuale e il controllo ortografico su tutti i messaggi di errore scritti.

- Per i messaggi di errore complessi, evitare le comunicazioni sequenziali. Non usare mai un collegamento F1 per il messaggio di errore. Il messaggio stesso dovrebbe essere sufficiente.

- Usare l'icona corretta.

- Semplifica la comprensione e l'uso di pulsanti con scelte chiare, ad esempio "Elimina" e "Annulla".

- Per gli avvisi, è chiaro quale sia la conseguenza della proseguimento. I pulsanti dovrebbero indicare la conseguenza.

- Per errori, descrivere le operazioni che l'utente può eseguire per risolvere il problema. I pulsanti devono essere azioni o pronunciare "Chiudi". Non usare un pulsante "OK" per un messaggio di errore.

- Alcune domande da porsi quando si crea un messaggio di errore:

  - L'utente può scoprire come risolvere il problema solo con questo errore?

  - L'utente usa lo stesso vocabolario di questo errore?

  - Questo errore ambigua o viene condiviso in più situazioni? In tal caso, come si guidano gli utenti alla soluzione di cui hanno bisogno?

#### <a name="build-errors"></a>Errori di compilazione
 Poiché Visual Studio è uno strumento di sviluppo software, molti dei suoi componenti hanno un passaggio di compilazione, conversione o codifica per convertire il lavoro dello sviluppatore in formato binario. Queste conversioni possono causare errori quando il compilatore non è in grado di elaborare file creati in modo errato o quando le opzioni del compilatore non sono state impostate correttamente.

 Gli utenti di Visual Studio possono dedicare un grande numero di ore di sviluppo alla risoluzione degli errori di compilazione. Questo tempo di risoluzione aumenta quando gli errori presentano dipendenze o quando i messaggi di errore vengono scritti in modo non corretto, il che può rendere difficile individuare l'origine dell'errore.

 Gli errori di compilazione migliori sono quelli che non si verificano in primo luogo, motivo per cui Visual Studio fornisce il completamento automatico e IntelliSense controllo ortografia durante. I validator dello schema e gli strumenti simili forniscono lo stesso tipo di feedback. Questi meccanismi guidano in modo proattivo l'utente per costruire codice ben formato, riducendo la possibilità di errori di compilazione.

 Visual Studio fornisce una finestra degli strumenti in cui gli utenti possono leggere e spostarsi tra gli errori che si sono verificati nelle finestre del documento. Sono disponibili tasti di scelta rapida che consentono all'utente di spostarsi rapidamente su grandi quantità di codice e passare direttamente alla posizione del problema. Visual Studio consente inoltre a ogni errore di compilazione di essere associato a una parola chiave della guida o a un ID contesto specifici, in modo che l'utente possa passare direttamente a un argomento della guida che fornisce informazioni più dettagliate sull'errore.

 Errori di compilazione chiari e concisi:

- **Usare un linguaggio semplice** che spieghi il problema con un gergo del compilatore minimo o nullo. Il testo di un errore di compilazione non deve essere troppo tecnico.

- **Delineare le possibili cause.** Ad esempio, "mancano i due punti tra la proprietà e il valore nella dichiarazione ' (Property): (value)'".

- Fornire informazioni dettagliate sulle possibili correzioni. Se lo spazio disponibile non è sufficiente, è possibile inserire dettagli aggiuntivi nell'argomento della Guida corrispondente.

### <a name="components-of-a-well-written-error-message"></a>Componenti di un messaggio di errore ben scritto

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utilizzare il servizio della finestra di dialogo Shell per i messaggi di errore.
 L'uso del servizio della finestra di dialogo della shell consente di controllare l'aspetto del messaggio, in particolare i tipi di carattere, senza modifiche sostanziali a singoli elementi. Usare i meccanismi **IErrorInfo** e segnalarli usando **IVsUIShell:: SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Scegliere una presentazione di notifica efficace e appropriata.
 Usare una finestra di dialogo modale con un avviso critico se è necessaria un'azione immediata per evitare la perdita di dati (notifica sincrona). Le icone critiche sono riservate per le situazioni in cui la chiusura del messaggio senza lettura può comportare conseguenze negative. La perdita di dati è una situazione critica che richiede una risposta a livello di allarme. L'utilizzo eccessivo dell'icona critica consente di desensibilizzare gli utenti alla sua importanza. Se il messaggio di errore è di natura informativa, prendere in considerazione le alternative a una finestra di dialogo modale (notifica asincrona).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fornire una spiegazione pulita e concisa del motivo per cui si è verificato il problema anziché una spiegazione tecnica.
 Se si sovraccaricano gli utenti con dettagli tecnici nella spiegazione, è più probabile che ignorino i messaggi di errore. Esempi di messaggistica efficace:

- "Impossibile aprire il file richiesto".

- "Impossibile connettersi a Internet".

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fornire informazioni su come risolvere il problema.
 Offrire i suggerimenti dell'utente per risolvere il problema. Se non sono presenti suggerimenti, è opportuno essere onesti con l'utente. Fornire collegamenti diretti a origini online alternative, ad esempio supporto tecnico o supporto della community. Provare a indirizzare gli utenti a specifiche informazioni online pertinenti al problema. Per un ID errore, si consiglia di collegare gli utenti a un thread di discussione sull'errore specifico. Esempi di messaggistica efficace:

- "Assicurarsi di essere connessi a Internet e riprovare."

- "Assicurarsi che il file esista e di disporre dell'autorizzazione per aprirlo."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Scrivere un messaggio che sia breve e fino al punto.
 Un messaggio di errore può notificare, spiegare e offrire una soluzione, ma viene comunque ignorato se è troppo Wordy. Una soluzione consiste nell'usare la divulgazione progressiva con un pulsante Dettagli. Ad esempio, fornire una breve descrizione/soluzione e quindi inserire altri dettagli in un pulsante Dettagli. Se gli utenti scelgono di leggere altre informazioni sull'errore, possono farlo.

 La lingua del messaggio deve essere:

- **Appropriato per il dominio.** Usa il linguaggio che l'utente può comprendere. Anche se i nostri clienti sono sviluppatori, spesso non hanno il contesto e la terminologia disponibili.

- **Specifico.** Evitare il testo vago e assegnare nomi e posizioni specifici degli oggetti. Un messaggio di errore, ad esempio "carattere non valido", non è utile. Quale carattere? "File non trovato". Quale file?

- **Utile.** Non incolpare l'utente o fare in modo che siano stupidi. Evitare il linguaggio ostile o offensivo (Kill, Execute, terminate, irreversibili, non valide). Evitare il testo in maiuscolo, che viene spesso considerato come un grido e non è leggibile. Non usare umorismo.

- **Corretto.** Usare l'ortografia e la grammatica corrette (anche in alfa). Gli errori di digitazione non sono professionali e imbarazzanti.

- **Contestualemente appropriato.** Usare il testo del pulsante appropriato. Evitare il pulsante "OK" e usare invece "continua" o "Sì/No".

### <a name="error-message-examples"></a>Esempi di messaggi di errore

|Good|Non valido|
|----------|---------|
|"Il numero di chiamate non è più disponibile nel servizio. Verificare il numero e la connessione o la connessione 0 per l'operatore ".|-"Errore (449): numero non valido"<br />-"Errore di eccezione non gestita indica che l'operazione è stata completata correttamente".<br /><br /> ![Messaggio di errore non valido in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog ")|

## <a name="accessing-help"></a>Accesso alla guida

### <a name="overview"></a>Panoramica
 Oltre alla documentazione di MSDN, un utente di Visual Studio dispone di diversi punti di accesso che assistono l'utente nell'interfaccia utente. Per assicurarsi che questi punti di accesso siano costantemente disponibili, i team di funzionalità devono avvalersi del sistema di guida offerto dall'ambiente. Questi punti di accesso sono:

- **Testo informativo e supplementare nelle finestre di dialogo.** Testo statico che fornisce una direzione o una spiegazione sulla superficie dell'interfaccia utente o disponibile al passaggio del mouse su un'icona di InfoTip.

- **Guida sensibile** al contesto (solo editor). All'interno dell'editor di Visual Studio, un utente può considerare attendibile che in qualsiasi momento, premendo F1 viene visualizzato un argomento della Guida specifico per la selezione corrente. Assicurarsi che gli argomenti associati alla F1 siano appropriati e informativi.

- **Collegamenti ipertestuali per gli argomenti della guida.** Collegamento ipertestuale all'interno di un dialogo, una finestra degli strumenti o un'area di progettazione in cui viene avviato un argomento che consente all'utente di acquisire ulteriori informazioni su una tecnologia, una funzionalità o informazioni su come eseguire un'attività.

- **Meccanismi dell'interfaccia utente helper, ad esempio smart tag e finestre di dialogo di compilazione.** Questi meccanismi consentono all'utente di comprendere un elemento dell'interfaccia utente o facilitare un'attività, ad esempio smart tag o finestre di dialogo del generatore.

- **Pulsanti della Guida dell'interfaccia utente** (deprecato). Indicatore visibile nella barra del titolo che consente di accedere all'argomento della Guida sensibile al contesto.

### <a name="text"></a>Testo

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Testo didattico e supplementare nelle finestre di dialogo
 Nelle finestre di dialogo che supportano attività complesse, potrebbe essere necessario fornire il testo di istruzioni all'interno dell'interfaccia utente, spesso nella parte superiore della finestra di dialogo o nei controlli complessi. Per informazioni dettagliate sulla scrittura dello stile, vedere [testo e terminologia dell'interfaccia utente](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>Infotip
 Spesso il testo informativo potrebbe essere troppo lungo per posizionarsi sul posto nell'interfaccia utente o può essere utile solo per i nuovi utenti, in modo simile a un disordine per gli utenti esperti. In questo caso, il testo informativo/informativo deve essere inserito come descrizione comando in un InfoTip.

 Infotip deve essere posizionata vicino ai controlli a cui è correlata e deve usare l'icona InfoTip specifica, che è non intrusiva ma notabile.

 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Esempio di InfoTip in Visual Studio**

### <a name="interactive-help-mechanisms"></a>Meccanismi di guida interattiva

#### <a name="f1-help"></a>F1 Guida
 La Guida sensibile al contesto è obbligatoria in un editor o in un'area di progettazione, ma non in un'altra posizione nell'ambiente Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Collegamenti ipertestuali per gli argomenti della Guida
 I collegamenti ipertestuali possono essere utilizzati per eseguire un'azione, spostarsi all'interno dell'IDE o avviare la Guida in un browser. Per informazioni dettagliate sui pulsanti lingua e 07.10.01 e sui collegamenti ipertestuali per le linee guida visive e layout, vedere [testo e terminologia dell'interfaccia utente](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Pulsanti della Guida [?] nelle barre del titolo della finestra di dialogo (deprecato)
 Nella maggior parte dei casi, i pulsanti della Guida [?] nella barra del titolo delle finestre di dialogo sono deprecati. Gli argomenti dell'interfaccia utente non fanno più parte del modello doc e pertanto potrebbe non essere un argomento pertinente per il collegamento. Essenzialmente, il pulsante della barra del titolo corrisponde alla Guida sensibile al contesto e non è più necessario nelle finestre di dialogo. In alcuni casi, questo può essere comunque usato come indicatore del modo in cui sono disponibili informazioni più concettuali o procedurali, anche se i collegamenti ipertestuali sono più comunemente usati nell'interfaccia utente più recente.

##### <a name="dialogs-created-through-the-environment"></a>Finestre di dialogo create tramite l'ambiente
 Molte finestre di dialogo della shell vengono create tramite la funzione **VBDialogBoxParam** . Questa funzione condivisa è stata aggiornata per **facilitare lo stato** di trasferimento del pulsante? dalla finestra di dialogo alla **?** mantenendo un'architettura con compatibilità con le versioni precedenti ed estendibile.

 In particolare, la funzione **VBDialogBoxParam** esamina il modello di finestra di dialogo per un pulsante il cui ID è **IDHELP** (9) o label è **Help** o **& Help**. Se viene trovato un pulsante della guida, questo viene nascosto e lo stile **WS_EX_CONTEXTHELP** viene aggiunto alla finestra di dialogo, che inserisce il **?** pulsante nella barra del titolo della finestra di dialogo.

 Quando viene creata, la finestra di dialogo viene spostata su uno stack e viene richiamata la finestra di dialogo con una procedura di finestra di dialogo di pre-elaborazione denominata **DialogPreProc**. Quando **?** si fa clic sul pulsante, viene inviato un **WM_SYSCOMMAND** di **SC_CONTEXTHELP** alla finestra di dialogo. Il **DialogPreProc** acquisisce questo comando e lo modifica in un messaggio **WM_HELP** , che viene passato al processo originale della finestra di dialogo.

 Per la maggior parte delle finestre di dialogo create dall'ambiente è presente un pulsante? nella finestra di dialogo. Quando viene visualizzata la finestra di dialogo, il pulsante? è nascosto automaticamente e solo il **?** il pulsante funziona. Se il **?** il pulsante viene mai rimosso o modificato in Windows. questa soluzione consente di tornare rapidamente ai pulsanti della guida originali.

 Questa soluzione prevede quattro presupposti che potrebbero causare bug:

- Il pulsante della guida della finestra di dialogo è **IDHELP** (9).

- La finestra di dialogo sembra corretta quando il pulsante della guida è nascosto.

- La finestra di dialogo non sostituisce il relativo winproc.

- La finestra di dialogo non è incorporata all'interno di un'altra finestra di dialogo.

  Se la finestra di dialogo si trova all'interno di Msenv e non usa **VBDialogBoxParam**, provare a sfruttare **VBDialogBoxParam** prima di implementare il proprio gestore.

##### <a name="dialogs-created-through-other-packages"></a>Finestre di dialogo create tramite altri pacchetti
 È possibile implementare una soluzione personalizzata per le finestre di dialogo che si trovano all'esterno di Msenv. Per una classe di finestre di dialogo condivise nel pacchetto VSPackage, provare a trasferire il pulsante sulla barra del titolo o a implementare un gestore in ogni finestra di dialogo. Il codice seguente è uno scheletro di un'implementazione che consente di iniziare:

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

##### <a name="help-buttons-in-managed-code"></a>Pulsanti della guida nel codice gestito
 L'override del comportamento predefinito del pulsante della guida della barra del titolo della finestra è facile nel codice gestito. Di seguito è riportata un'applicazione demo completa che illustra questo comportamento. In sostanza, è necessario eseguire l'override del metodo **WndProc** del modulo e quindi attivare le richieste di supporto F1 quando viene intercettato un messaggio **SC_CONTEXTHELP** .

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
