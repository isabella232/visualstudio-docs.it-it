---
title: Testo dell'interfaccia utente e Guida per Visual Studio | Microsoft Docs
description: Informazioni sul testo e sulla terminologia dell'interfaccia utente usati nelle informazioni della Guida per Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4ca987c3f4b311b75b6a6070f8340c179c2ea6e0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709446"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Testo dell'interfaccia utente e Guida per Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Testo e terminologia dell'interfaccia utente
 Il testo comprensibile è fondamentale per un'interfaccia utente efficace. Gli utenti del software tendono a leggere prima le etichette, in modo da essere più rilevanti per completare l'attività in corso. Il testo statico viene letto con una frequenza minore. Pianificare l'avvio delle sessioni di lavoro da parte degli utenti con un'analisi rapida dell'intera finestra, seguita da una lettura dell'interfaccia utente in questo ordine approssimativo:

1. Controlli interattivi al centro

2. Pulsanti di commit

3. Controlli interattivi trovati altrove

4. Istruzioni principali

5. Spiegazioni supplementari

6. Titolo della finestra

7. Altro testo statico nel corpo principale

### <a name="usage-patterns-for-ui-text"></a>Modelli di utilizzo per il testo dell'interfaccia utente

#### <a name="title-bar-text"></a>Testo per la barra del titolo
 Il testo della barra del titolo deve corrispondere al comando che ha generato l'interfaccia utente.

#### <a name="instructional-text-helper-text"></a>Testo informativo (testo helper)
 In alcune finestre di dialogo è utile fornire istruzioni principali importanti per spiegare cosa fare nella finestra o nella pagina. Questo testo viene talvolta definito "testo helper".

##### <a name="writing-style-rules-for-helper-text"></a>Scrittura di regole di stile per il testo helper

- Non spiegare l'ovvio. A meno che non sia assolutamente necessario, non includere testo informativo.

- Il testo informativo viene sempre inserito nella parte superiore del dialogo e deve fare riferimento all'attività eseguita.

- Spiegare con precisione agli utenti cosa devono fare. Evitare comunicazioni e ridondanza eccessive.

- Esaminare ogni finestra ed eliminare le parole e le istruzioni duplicate.

- Mantenere breve il testo informativo. Se sono necessarie altre informazioni per determinati utenti o scenari, fornire un collegamento a un argomento online concettuale dettagliato.

- Scrivere il testo in modo che ogni parola sia ponderata ed è necessaria.

- Seguire le linee guida Microsoft esistenti [per Interfaccia utente testo](/windows/desktop/uxguide/text-ui) e stile e [tono.](/windows/desktop/uxguide/text-style-tone)

#### <a name="supplemental-instructions"></a>Istruzioni supplementari
 Le istruzioni supplementari forniscono informazioni aggiuntive che consentono all'utente di comprendere i controlli o i raggruppamenti di controlli. Può anche includere il testo dei suggerimenti necessario per comprendere il formato previsto dal controllo di input. Usare istruzioni supplementari solo se necessario. Riservarli per i casi in cui è probabile che l'utente non comprendi completamente le ramificazioni della scelta effettuata.

 ![Screenshot che mostra il Internet Explorer opzioni con il testo supplementare sottostante che descrive l'impatto della modifica delle impostazioni delle opzioni.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Testo supplementare in Visual Studio**

 ![Screenshot della finestra di dialogo Scegli controllo del codice sorgente Visual Studio testo supplementare che descrive ognuna delle opzioni del sistema di controllo del codice sorgente.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Testo supplementare in Visual Studio**

#### <a name="infotips"></a>Descrizioni comandi
 Spesso, il testo informativo potrebbe essere troppo lungo per essere posizionato sul posto nell'interfaccia utente o essere utile solo per i nuovi utenti, con la sensazione di creare confusione per gli utenti esperti. In questo caso, il testo informativo/informativo deve essere inserito come descrizione comando sotto una descrizione comando.

 Le descrizioni comandi devono essere posizionate accanto ai controlli a cui sono correlate e devono usare l'icona specifica della descrizione comandi, che è discreta ma evidente.

 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Esempio di suggerimento in Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Scrittura di regole di stile per le descrizioni comandi

- Scrivere descrizioni comandi come frasi complete. Richiedono verbi specifici, la distinzione tra maiuscole e minuscole e la punteggiatura finale.

- Usare le descrizioni comandi per integrare l'istruzione o le informazioni principali. Se si usano solo parole diverse per rideterminare l'idea principale, non è necessaria una descrizione comandi.

- Tenere brevi e brevi le descrizioni comandi. Usare parole piccole e linguaggio semplice e quotidiano che supporti e incoraggi l'utente.

- Seguire le linee guida Microsoft esistenti [per Interfaccia utente testo](/windows/desktop/uxguide/text-ui) e stile e [tono.](/windows/desktop/uxguide/text-style-tone)

#### <a name="control-labels"></a>Etichette dei controlli
 Le etichette dei controlli devono essere brevi, concise e seguire le linee [guida Windows Desktop per i controlli](/windows/desktop/uxguide/controls).

 Per altre informazioni sul formato dell'etichetta del controllo e sul posizionamento all'interno dell'interfaccia utente, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Collegamenti alla Guida
 I collegamenti alla Guida possono essere inseriti all'interno del testo informativo o nel corpo dell'interfaccia utente. Possono essere collegamenti alla Guida o avviare finestre di dialogo interne.

##### <a name="visual-style-rules-for-help-links"></a>Regole dello stile di visualizzazione per i collegamenti della Guida

- Usare i colori di ambiente corretti per i collegamenti ipertestuali. Quando si fa clic su un collegamento ipertestuale con uno stile corretto, il colore rosso non lampeggia brevemente. Se viene visualizzato, è un'indicazione che i colori dell'ambiente non vengono usati.

- Le sottolineature devono essere usate solo al passaggio del mouse o quando il collegamento è incorporato in un paragrafo.

- Per informazioni più dettagliate sugli stili di oggetti visivi e di interazione per i collegamenti ipertestuali, vedere Pulsanti e collegamenti ipertestuali.

##### <a name="writing-style-rules-for-help-links"></a>Scrittura di regole di stile per i collegamenti della Guida

- Quando si avviano le finestre di dialogo, mantenere gli standard per i puntini di sospensione: nessun pulsante con i puntini di sospensione per la navigazione, puntini di sospensione se l'attività richiede un'interfaccia utente aggiuntiva.

     ![Collegamento Guida in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **I puntini di sospensione (...) in un collegamento alla Guida indicano che l'attività richiederà un'interfaccia utente aggiuntiva.**

- I collegamenti non devono iniziare con "Learn", perché questa non è la finalità dell'utente. L'utente vuole rispondere a una domanda specifica, non ricevere una formazione generale.

- Collegamenti alla Guida per le frasi in modo da porre la domanda a cui risponderà l'argomento.

     Risposta errata: "Altre informazioni sui prezzi Windows azure Servizi mobili"

     Risposta corretta: "Quali opzioni di prezzo sono disponibili per Windows azure Servizi mobili?"

- Non usare mai *Click...* per il testo del collegamento.

- Non collegare mai solo la parola "qui". Ciò è problematico per alcune utilità per la lettura dello schermo, che eseranno solo la parola con collegamento ipertestuale.

     Risposta errata: "Trovare informazioni su azure Windows azure Servizi mobili **qui"**

     Risposta corretta: "Quali opzioni di prezzo sono disponibili per Windows azure Servizi mobili?"

- Per altre informazioni sullo stile di scrittura corretto per i collegamenti della Guida, vedere le linee [guida Windows Desktop per la Guida](/windows/desktop/uxguide/winenv-help)di .

#### <a name="hint-text"></a>Testo del suggerimento
 Il testo del suggerimento viene visualizzato come filigrana all'interno di un controllo o sotto il controllo. La formattazione corretta verrà applicata usando il token VSColors appropriato, `Environment.GrayText` .

 Può essere visualizzato in diversi formati.

- Al posto dell'etichetta del controllo:

     ![Screenshot di un controllo a discesa con testo del suggerimento al posto dell'etichetta del controllo con il testo "Cerca Esplora soluzioni (CTRL+;)".](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Con un verbo, fornendo istruzioni:

     ![Screenshot di una casella di testo con il testo del suggerimento nel controllo con il testo "Enter your name".](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Con testo che indica una voce obbligatoria:

     ![Screenshot di una casella di testo con il testo del suggerimento nel controllo che legge " \< \> Obbligatorio ".](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Testo della filigrana
 In un'area di progettazione vuota, il testo deve indicare le attività da eseguire e fornire collegamenti per aprire altre finestre correlate, se appropriato:

 ![Testo filigrana in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Esempio di testo della filigrana in Visual Studio**

### <a name="common-terminology"></a>Terminologia comune

|Termine|Spiegazione|Commento|
|----------|-----------------|-------------|
|Accesso/Disconnessione|Verbi usati sinonimi con il Web per rappresentare l'autenticazione in una proprietà Web. All'interno dei client viene utilizzato una sola volta come nozione di primo livello per l'accesso e la disconnessione dalla connessione utente IDE, che rappresenta un'identità di primo livello che fornisce funzionalità di livello superiore, ad esempio il roaming e le licenze, che non sono disponibili con tutte le altre connessioni.|L'utente IDE è l'unica funzionalità che deve rappresentare un verbo di accesso/disconnessione, in quanto rappresenta l'utente IDE di primo livello.|
|Connessione/Disconnetti|Usare in posizioni in cui una funzionalità mantiene una singola connessione a un servizio online.|Esplora server, in cui è possibile avere una sola connessione di Azure attiva alla volta, è un esempio Connessione/Disconnetti.|
|Aggiungi/Rimuovi|Non distruttivo. Usare quando si aggiunge o si rimuove un elemento da un elenco.|La finestra di dialogo Gestione connessioni'elenco dei server TFS è un esempio di Aggiunta/Rimozione.|
|Elimina|Distruttivo. Usare solo quando l'elemento da rimuovere verrà eliminato o rimosso definitivamente dal disco.|"Delete" richiede in genere una richiesta se il risultato è l'eliminazione di un file dal disco.|

## <a name="error-messages"></a>messaggi di errore

### <a name="overview"></a>Panoramica
 Si verificano errori. L'impostazione di limitazioni sulle possibili opzioni dell'utente è un primo passaggio ragionevole per evitare messaggi di errore evitabili. Tuttavia, quando si verifica un errore, un messaggio di errore ben scritto può essere molto utile per attenuare il problema. I messaggi di errore sono probabilmente uno dei tipi di notifica più importanti che l'utente vede, perché sono sincroni e indicano un problema che deve essere risolto. I messaggi di errore scritti in modo non necessario lasciano gli utenti in proprio a decidere la causa degli errori e le possibili soluzioni.

 Gli utenti potrebbero smettere di prestare attenzione ai messaggi di errore inutilizzati o confusi, quindi scrivere solo i messaggi necessari che aggiungono valore all'esperienza utente. Se il messaggio è semplicemente una notifica, usare una presentazione alternativa.

### <a name="rules-for-creating-an-error-message"></a>Regole per la creazione di un messaggio di errore

- Quando si creano messaggi di errore, scegliere il livello di errore appropriato per i destinatari. Puntare a riepiloghi semplici che forniscono un'azione che l'utente può eseguire, se applicabile. Non indica nulla che l'utente non deve conoscere.

- Fornire assistenza personale. È più facile leggere e agire su un messaggio di errore che contiene istruzioni.

- Non usare valori negativi doppi.

- Eseguire un controllo grammaticale e ortografico sia automatico che manuale su qualsiasi messaggio di errore scritto.

- Per i messaggi di errore complessi, evitare comunicazioni sequenziali. Non usare mai un hook F1 per il messaggio di errore. Il messaggio stesso dovrebbe essere sufficiente.

- Usare l'icona corretta.

- Creare domande facili da comprendere e usare pulsanti con scelte chiare, ad esempio "Elimina" e "Annulla".

- Per gli avvisi, è necessario sapere chiaramente quale sarà la conseguenza del processo. I pulsanti dovrebbero indicare la conseguenza.

- Per gli errori, descrivere cosa può fare l'utente per risolvere il problema. I pulsanti devono essere azioni o pronunciare "Chiudi". Non usare un pulsante "OK" per un messaggio di errore.

- Alcune domande da porsi quando si costruisce un messaggio di errore:

  - L'utente può capire come risolvere il problema solo con questo errore?

  - L'utente usa lo stesso vocabolario di questo errore?

  - Questo errore è ambiguo o condiviso in più situazioni? In tal caso, come si guidano gli utenti alla soluzione di cui hanno bisogno?

#### <a name="build-errors"></a>Errori di compilazione
 Poiché Visual Studio è uno strumento di sviluppo software, molti dei relativi componenti hanno un passaggio di compilazione, conversione o codifica per convertire il lavoro dello sviluppatore in formato binario. Queste conversioni possono causare errori quando il compilatore non è in grado di elaborare file creati in modo non corretto o quando le opzioni del compilatore non sono state impostate correttamente.

 Visual Studio utenti possono dedicare un numero enorme di ore di sviluppo alla risoluzione degli errori di compilazione. Questo tempo di risoluzione aumenta quando gli errori hanno dipendenze o quando i messaggi di errore non vengono scritti in modo notevolmente, il che può rendere difficile individuare l'origine dell'errore.

 Gli errori di compilazione migliori sono quelli che non si verificano in primo luogo, motivo per cui Visual Studio le opzioni di completamento automatico e di controllo ortografia intelliSense. I validator dello schema e strumenti simili forniscono lo stesso tipo di feedback. Questi meccanismi guidano in modo proattivo l'utente nella costruzione di codice ben formato, attenuando la possibilità di errori di compilazione.

 Visual Studio fornisce una finestra degli strumenti in cui gli utenti possono leggere e spostarsi tra gli errori che si sono verificati nelle finestre dei documenti. I tasti di scelta rapida sono disponibili in modo che l'utente possa esplorare rapidamente grandi quantità di codice e passare direttamente alla posizione del problema. Visual Studio consente inoltre a ogni errore di compilazione di essere associato a un particolare ID di parola chiave/contesto della Guida in modo che l'utente possa passare direttamente a un argomento della Guida che fornisce informazioni più dettagliate sull'errore.

 Scrivere errori di compilazione chiari e concisi:

- **Usare un linguaggio** semplice che spiega il problema con un gergo del compilatore di poco o nessun linguaggio. Il testo di un errore di compilazione non deve essere troppo tecnico.

- **Delineare le possibili cause.** Ad esempio, "Mancano i due punti tra la proprietà e il valore nella dichiarazione '(property) : (value)'".

- Fornire informazioni dettagliate sulle potenziali correzioni. Se lo spazio disponibile non è sufficiente, è possibile inserire dettagli aggiuntivi nell'argomento della Guida corrispondente.

### <a name="components-of-a-well-written-error-message"></a>Componenti di un messaggio di errore ben scritto

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Usare il servizio della finestra di dialogo della shell per i messaggi di errore.
 L'uso del servizio della finestra di dialogo della shell consente di controllare l'aspetto del messaggio, in particolare i tipi di carattere, senza modifiche importanti ai singoli elementi. Usare i **meccanismi IErrorInfo** e segnalarli usando **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Scegliere una presentazione di notifica efficace e appropriata.
 Usare una finestra di dialogo modale con un avviso critico se è necessaria un'azione immediata per evitare la perdita di dati (notifica sincrona). Le icone critiche sono riservate alle situazioni in cui la chiusura del messaggio senza leggerlo può causare conseguenze negative. La perdita di dati è una situazione critica che richiede una risposta a livello di allarme. L'uso eccessivo dell'icona critica desensibilizza gli utenti in base alla sua importanza. Se il messaggio di errore è informativo, prendere in considerazione alternative a una finestra di dialogo modale (notifica asincrona).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fornire una spiegazione pulita e concisa del motivo per cui si è verificato il problema anziché una spiegazione tecnica.
 Sovraccaricando gli utenti con i dettagli tecnici nella spiegazione, è più probabile che ignorino i messaggi di errore. Esempi di messaggistica di qualità:

- "Impossibile aprire il file richiesto".

- "Impossibile connettersi a Internet".

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fornire informazioni su come risolvere il problema.
 Offrire all'utente suggerimenti su come risolvere il problema. Se non sono presenti suggerimenti, sii disdemente dell'utente. Fornire collegamenti diretti a origini online alternative, ad esempio il supporto tecnico o il supporto della community. Provare a puntare gli utenti a informazioni online specifiche pertinenti al problema. Per un ID errore, è consigliabile collegare gli utenti a un thread di discussione sull'errore specifico. Esempi di messaggistica di qualità:

- "Assicurarsi di essere connessi a Internet e ripetere l'operazione."

- "Assicurarsi che il file esista e che si abbia l'autorizzazione per aprirlo".

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Scrivere un messaggio breve e fino al punto.
 Un messaggio di errore può notificare, spiegare e offrire una soluzione, ma può comunque essere ignorato se è troppo semplice. Una soluzione consiste nell'usare la divulgazione progressiva con un pulsante dettagli. Ad esempio, fornire una breve descrizione/soluzione e quindi inserire altri dettagli sotto un pulsante dettagli. Se gli utenti scelgono di leggere altre informazioni sull'errore, possono farlo.

 La lingua nel messaggio deve essere:

- **Appropriato per il dominio.** Usare la lingua che l'utente comprenderà. Anche se i clienti sono sviluppatori, spesso non hanno il contesto e la terminologia disponibili.

- **Specifico.** Evitare formulazioni erre e assegnare nomi e posizioni specifici degli oggetti coinvolti. Ad esempio, un messaggio di errore come "carattere non valido" non è utile. Quale carattere? "File non trovato". Quale file?

- **Cortese.** Non incolpare l'utente o farlo provare. Evitare un linguaggio offensivo o offensivo (terminare, eseguire, terminare, irreversibile, non valido). Evitare il testo in maiuscolo, che viene spesso considerato come un'eserezione e non è leggibile. Non usare l'avaio.

- **Risposta esatta.** Usare ortografia e grammatica corrette (anche in caratteri alfa). Gli errori di digitazione sono poco professionale e imbarazzanti.

- **Appropriato a livello di contesto.** Usare il testo del pulsante appropriato. Evitare il pulsante "OK" e usare invece "Continua" o "Sì/No".

### <a name="error-message-examples"></a>Esempi di messaggi di errore

|Buono|Non valido|
|----------|---------|
|"Il numero composto non è più in servizio. Controllare il numero e comporre di nuovo o comporre 0 per l'operatore."|- "Errore (449): numero non valido"<br />- "Questo errore di eccezione non gestita indica che l'operazione è stata completata correttamente".<br /><br /> ![Messaggio di errore non valido in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Accesso alla Guida

### <a name="overview"></a>Panoramica
 Oltre alla documentazione in MSDN, un utente Visual Studio dispone di diversi punti di accesso per assistere l'utente nell'interfaccia utente. Per garantire che questi punti di accesso siano disponibili in modo coerente, i team delle funzionalità devono sfruttare il sistema della Guida offerto dall'ambiente. Questi punti di accesso sono:

- **Testo informativo e supplementare nelle finestre di dialogo.** Testo statico che fornisce la direzione o la spiegazione, nell'area dell'interfaccia utente o disponibile al passaggio del mouse su un'icona di suggerimento.

- **Guida F1** (solo editor). Nell'editor Visual Studio, un utente può considerare attendibile che in qualsiasi momento premendo F1 verrà visualizzato un argomento della Guida specifico per la selezione corrente. Assicurarsi che gli argomenti associati a F1 siano appropriati e informativi.

- **Collegamenti ipertestuali agli argomenti della Guida.** Collegamento ipertestuale all'interno di una finestra di dialogo, una finestra degli strumenti o un'area di progettazione che avvia un argomento per aiutare l'utente a ottenere altre informazioni su una tecnologia, una funzionalità o informazioni su come eseguire un'attività.

- **Meccanismi dell'interfaccia utente helper, ad esempio smart tag e compilazione di finestre di dialogo.** Questi meccanismi facilitano la comprensione di un elemento dell'interfaccia utente o facilitano un'attività, ad esempio smart tag o finestre di dialogo del generatore.

- **Pulsanti della Guida dell'interfaccia** utente (deprecati). Indicatore visibile nella barra del titolo che consente di accedere all'argomento della Guida F1 correlato.

### <a name="text"></a>Testo

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Testo informativo e supplementare nelle finestre di dialogo
 Nelle finestre di dialogo che supportano attività complesse potrebbe essere necessario fornire testo informativo all'interno dell'interfaccia utente, spesso nella parte superiore della finestra di dialogo o in prossimità di controlli complessi. Per informazioni [dettagliate sullo stile di scrittura,](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) vedere Testo e terminologia dell'interfaccia utente.

#### <a name="infotips"></a>Descrizioni comandi
 Spesso, il testo informativo potrebbe essere troppo lungo per essere posizionato sul posto nell'interfaccia utente o essere utile solo per i nuovi utenti, con la sensazione di creare confusione per gli utenti esperti. In questo caso, il testo informativo/informativo deve essere inserito come descrizione comando sotto una descrizione comando.

 Le descrizioni comandi devono essere posizionate accanto ai controlli a cui sono correlate e devono usare l'icona specifica della descrizione comandi, che è discreta ma evidente.

 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Esempio di suggerimento in Visual Studio**

### <a name="interactive-help-mechanisms"></a>Meccanismi della Guida interattiva

#### <a name="f1-help"></a>Guida sensibile al contesto
 La Guida F1 è necessaria all'interno di un editor o di un'area di progettazione, ma non in altre Visual Studio ambiente.

#### <a name="hyperlinks-to-help-topics"></a>Collegamenti ipertestuali agli argomenti della Guida
 I collegamenti ipertestuali possono essere usati per eseguire un'azione, spostarsi all'interno dell'IDE o avviare la Guida in un browser. Vedere [Testo e terminologia dell'interfaccia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) utente per informazioni dettagliate sulla lingua e Pulsanti e collegamenti ipertestuali 07.10.01 per linee guida per oggetti visivi e layout.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Pulsanti della Guida [?] nelle barre del titolo della finestra di dialogo (deprecati)
 Nella maggior parte dei casi, i pulsanti della Guida [?] nella barra del titolo delle finestre di dialogo sono deprecati. Gli argomenti dell'interfaccia utente non fanno più parte del modello di documentazione e pertanto potrebbe non esserci un argomento pertinente a cui collegarsi. In sostanza, il pulsante della barra del titolo è lo stesso della Guida F1 e non è più necessario nelle finestre di dialogo. In alcuni casi, può comunque essere usato come indicatore della disponibilità di informazioni più concettuali o procedurali, anche se i collegamenti ipertestuali sono più comunemente usati nell'interfaccia utente più recente.

##### <a name="dialogs-created-through-the-environment"></a>Dialogs created through the environment
 Molte finestre di dialogo della shell vengono create tramite la **funzione VBDialogBoxParam.** Questa funzione condivisa è stata aggiornata per facilitare lo **spostamento** del pulsante ? dalla finestra di dialogo all'oggetto **?** mantenendo un'architettura compatibile con le versioni precedenti ed estendibile.

 In particolare, la **funzione VBDialogBoxParam** cerca nel modello di finestra di dialogo un pulsante il cui ID è **IDHELP** (9) o l'etichetta è **Help** **o&Help**. Se viene trovato un pulsante ?  , il pulsante viene nascosto e WS_EX_CONTEXTHELP alla finestra di dialogo viene aggiunto lo stile **?** nella barra del titolo della finestra di dialogo.

 Quando il dialogo viene creato, inserisce la procedura del dialogo in uno stack e richiama il dialogo con una procedura di dialogo di pre-elaborazione denominata **DialogPreProc.** Quando l'oggetto **?** viene fatto clic sul pulsante e viene inviato **un WM_SYSCOMMAND** di **SC_CONTEXTHELP** alla finestra di dialogo. **DialogPreProc** acquisisce questo comando e lo modifica in un messaggio **WM_HELP,** che viene passato alla procedura di dialogo originale.

 La maggior parte delle finestre di dialogo create dall'ambiente ha un pulsante ? nella finestra di dialogo. Quando viene visualizzata la finestra di dialogo, il pulsante ? viene nascosto automaticamente e solo **il pulsante ?** il pulsante funziona. Se l'oggetto **?** il pulsante viene rimosso o modificato in Windows, questa soluzione consente di tornare rapidamente ai pulsanti della Guida originali.

 Questa soluzione presuppone quattro presupposti che potrebbero causare bug:

- Il pulsante della Guida della finestra di dialogo **è IDHELP** (9).

- La finestra di dialogo ha un aspetto corretto quando il pulsante ? è nascosto.

- Il dialogo non sostituisce il relativo winproc.

- La finestra di dialogo non è incorporata all'interno di un altro dialogo.

  Se il dialogo si trova all'interno di msenv e non usa **VBDialogBoxParam,** esaminare l'uso di **VBDialogBoxParam** prima di implementare un gestore personalizzato.

##### <a name="dialogs-created-through-other-packages"></a>Finestre di dialogo create tramite altri pacchetti
 È possibile implementare una soluzione personalizzata per i dialognti che si trovano all'esterno di msenv. Per una classe di finestra di dialogo condivisa nel pacchetto VSPackage, è consigliabile spostare il pulsante sulla barra del titolo o implementare un gestore in ogni finestra di dialogo. Il codice seguente è uno scheletro di un'implementazione per iniziare:

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
 L'override del comportamento predefinito del pulsante ? della barra del titolo della finestra è semplice nel codice gestito. Di seguito è riportata un'applicazione demo completa che illustra questo comportamento. In sostanza, è necessario eseguire l'override del metodo **WndProc** del form e quindi inviare le richieste della Guida F1 quando viene intercettato **SC_CONTEXTHELP** messaggio di errore.

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

## <a name="see-also"></a>Vedi anche
- [Tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Notifiche e avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
