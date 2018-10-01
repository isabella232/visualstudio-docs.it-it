---
title: Testo dell'interfaccia utente e la Guida di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f3e8f7541c83372c0d822c3db4bc0e20b3af1a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517038"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Testo dell'interfaccia utente e la Guida di Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [testo dell'interfaccia utente e la Guida di Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/ui-text-and-help-for-visual-studio).  
  
##  <a name="BKMK_UITextAndTerminology"></a> Testo dell'interfaccia utente e terminologia  
 Testo comprensibile è fondamentale per efficace interfaccia utente. Gli utenti di software tendono a leggere le etichette vengono in primo luogo, vale a dire quelli più importanti per il completamento dell'attività in questione. Testo statico viene letto con minore frequenza. Piano per gli utenti avviare le sessioni di lavoro con un'analisi rapida della finestra intera, seguita da una lettura dell'interfaccia utente in questo ordine approssimativo:  
  
1.  Controlli interattivi nel centro  
  
2.  Eseguire il commit di pulsanti  
  
3.  Controlli interattivi trovati altrove  
  
4.  Istruzioni principali  
  
5.  Spiegazioni aggiuntive  
  
6.  Titolo della finestra  
  
7.  Altro testo statico nel corpo principale  
  
### <a name="usage-patterns-for-ui-text"></a>Modelli di utilizzo per il testo dell'interfaccia utente  
  
#### <a name="title-bar-text"></a>Testo barra del titolo  
 Testo barra del titolo deve corrispondere il comando che ha generato l'interfaccia utente.  
  
#### <a name="instructional-text-helper-text"></a>Testo esplicativo (testo di supporto)  
 In alcune finestre di dialogo, è utile fornire istruzioni principali notificate all'utente di spiegare operazioni da eseguire nella finestra o nella pagina. Ciò è talvolta detta "testo di supporto".  
  
##### <a name="writing-style-rules-for-helper-text"></a>La scrittura di regole di stile per il testo di supporto  
  
-   Non viene illustrata l'ovvio. A meno che non sia assolutamente necessario, non includere testo esplicativo.  
  
-   Testo esplicativo è sempre posizionato nella parte superiore della finestra di dialogo e deve fare riferimento all'attività eseguita.  
  
-   Precisamente spiegare agli utenti dovranno effettuare. Evitare la ridondanza e la comunicazione eccessivo.  
  
-   Esaminare ogni finestra e disattivano le istruzioni e le parole duplicate.  
  
-   Mantenere breve testo esplicativo. Se altre informazioni sono necessarie per determinati utenti o gli scenari, quindi fornire un collegamento a un argomento online concetto dettagliato.  
  
-   Scrivere il testo in modo che ogni parola contiene peso e non è necessario.  
  
-   Segui le istruzioni di Microsoft esistente per [testo dell'interfaccia utente](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [stile e tono](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Istruzioni aggiuntive  
 Istruzioni supplementare forniscono informazioni aggiuntive che consente all'utente di comprendere i controlli o raggruppamenti di controllo. Ciò può anche includere il testo di suggerimento necessario per comprendere quale formato prevede che il controllo di input. Attenersi alle istruzioni aggiuntive solo se necessario. Riservarli per i casi in cui è probabile che l'utente non sarà aiutino a comprendere appieno le ramificazioni della scelta che stanno effettuando.  
  
 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Testo supplementare in Visual Studio**  
  
 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Testo supplementare in Visual Studio**  
  
#### <a name="infotips"></a>Infotip  
 Spesso, il testo esplicativo potrebbe essere troppo lungo per posizionare posto nell'interfaccia utente o potrebbe essere utile solo per i nuovi utenti, devono disordine agli utenti esperti. In questo caso, il testo esplicativo/informativo deve essere inserito come descrizione comando in una finestra popup.  
  
 Infotip devono essere posizionati vicino i controlli che sono correlati a e deve usare l'icona di InfoTip specifico, che è ancora unobtrusive evidenti.  
  
 ![Finestra popup in Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")  
  
 **Esempio di una finestra popup in Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Regole di stile di scrittura per Infotip  
  
-   Scrivere Infotip come frasi complete. Richiedono verbi specifici, maiuscola e la punteggiatura finale.  
  
-   Usare illustrati gli Infotip per integrare l'istruzione principale o informazioni. Se si usano solo parole diverse per ridefinire l'idea principale, non occorre una finestra popup.  
  
-   Mantenere Infotip breve e semplice. Usare parole brevi e plain, un linguaggio quotidiano che supporta e incoraggia l'utente.  
  
-   Segui le istruzioni di Microsoft esistente per [testo dell'interfaccia utente](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [stile e tono](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Etichette del controllo  
 Etichette del controllo devono essere breve e conciso e seguire le [linee guida di Windows Desktop per i controlli](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Per altre informazioni sul formato dell'etichetta di controllo e il posizionamento all'interno dell'interfaccia utente, consultare [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Collegamenti della Guida  
 I collegamenti della Guida possono essere posizionati all'interno del testo esplicativo o nel corpo dell'interfaccia utente. Possono essere collegamenti alla Guida o avviare le finestre di dialogo interni.  
  
##### <a name="visual-style-rules-for-help-links"></a>Regole di stile di visualizzazione per i collegamenti della Guida  
  
-   Utilizzare i colori ambiente corretto per i collegamenti ipertestuali. Un collegamento ipertestuale applicato correttamente uno stile non lampeggia brevemente in rosso quando si fa clic. Se si riscontra questo è un valore che indica che non vengano usati colori dell'ambiente.  
  
-   Sottolineature devono essere utilizzate solo sul passaggio del mouse o quando il collegamento è incorporato in un paragrafo.  
  
-   Per informazioni più dettagliate sugli stili di oggetto visivo e interazione dei collegamenti ipertestuali, vedere i collegamenti ipertestuali e pulsanti.  
  
##### <a name="writing-style-rules-for-help-links"></a>La scrittura di regole di stile per i collegamenti della Guida  
  
-   Quando l'avvio di finestre di dialogo, mantenere gli standard per i puntini di sospensione: nessun puntini di sospensione per la navigazione, quindi sui puntini di sospensione se l'attività richiede un'interfaccia utente aggiuntiva.  
  
     ![Collegamento alla Guida in Visual Studio](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601 e_HelpLink")  
  
     **I puntini di sospensione (...) in un collegamento alla Guida indica che l'attività richiede un'interfaccia utente aggiuntiva.**  
  
-   Collegamenti non devono iniziare con "Informazioni", questo non costituisce l'intenzione dell'utente. L'utente desidera rispondere a una domanda specifica, non riceve una formazione generale.  
  
-   Guida di frase collega in modo che essi porre la domanda che risponderà a questo argomento.  
  
     Corretto:  
     "Altre informazioni sui prezzi di servizi mobili di Windows Azure"  
  
     Corretto:  
     "Quali sono le opzioni di determinazione dei prezzi sono disponibili per servizi mobili di Windows Azure"?  
  
-   Non utilizzare mai *fare clic su...* per il testo del collegamento.  
  
-   Non collegare mai solo la parola "qui". Ciò risulta problematico per alcuni lettori dello schermo, che verranno vocali solo la parola con collegamento ipertestuale.  
  
     Corretto:  
     "Informazioni su servizi mobili di Azure **qui**"  
  
     Corretto:  
     "Quali sono le opzioni di determinazione dei prezzi sono disponibili per servizi mobili di Windows Azure"?  
  
-   Per altre informazioni sullo stile di scrittura corretti per i collegamenti della Guida, vedere la [linee guida di Windows Desktop per la Guida](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Testo di suggerimento  
 Testo del suggerimento visualizzato come filigrana all'interno di un controllo o sotto il controllo. Formattazione corretta verrà applicata utilizzando il token VSColors appropriato, `Environment.GrayText`.  
  
 Può essere visualizzato in diversi formati.  
  
-   Al posto l'etichetta del controllo:  
  
     ![Testo in Visual Studio l'hint](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601 f_HintText1")  
  
-   Con un verbo, fornendo istruzioni:  
  
     ![Testo in Visual Studio l'hint](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601 g_HintText2")  
  
-   Con il testo che indica una voce di richiesta:  
  
     ![Testo in Visual Studio l'hint](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>Testo della filigrana  
 In un'area di progettazione vuota, il testo deve indicare gli elementi da eseguire, oltre a fornire collegamenti per aprire altre finestre correlati, se appropriato:  
  
 ![Il testo in Visual Studio della filigrana](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601 i_WatermarkText")  
  
 **Esempio di testo della filigrana in Visual Studio**  
  
### <a name="common-terminology"></a>Terminologia comune  
  
|Termine|Descrizione|Commento|  
|----------|-----------------|-------------|  
|Accesso / disconnessione|Verbi usati come sinonimi con il web per la rappresentazione di autenticazione in una proprietà di web. All'interno di client, usiamo una volta come una nozione di primo livello per la firma da e verso la connessione utente IDE, che rappresenta un'identità di livello principale che fornisce funzionalità di livello superiore, ad esempio il roaming e gestione delle licenze che non sono disponibili con tutte le altre connessioni.|L'utente dell'IDE è l'unica funzionalità che dovrà rappresentare una richiesta di accesso / disconnessione verbo, perché rappresenta l'utente di primo livello dell'IDE.|  
|Connettere / disconnettere|Utilizzare in posizioni in cui una funzionalità mantiene una singola connessione a un servizio online.|Esplora server, in cui è possibile avere solo una connessione di Azure attiva alla volta, è riportato un esempio di connessione/disconnessione.|  
|Aggiungi o Rimuovi|Non distruttiva. Usare durante l'aggiunta o rimozione di un elemento da un elenco.|La finestra di dialogo Gestione connessione TFS elenco server è un esempio di Aggiungi/Rimuovi.|  
|Eliminare|Distruttive. Utilizzare questa opzione solo quando l'elemento viene rimosso verrà definitivamente eliminati o eliminati dal disco.|"Delete" in genere richiede un prompt dei comandi se il risultato è l'eliminazione di un file dal disco.|  
  
## <a name="error-messages"></a>Messaggi di errore  
  
### <a name="overview"></a>Panoramica  
 Si verificano errori. L'impostazione di limitazioni su ciò che l'utente può eseguire è ragionevole innanzitutto evitare che i messaggi di errore possibile impedire. Tuttavia, quando si verifica un errore, un messaggio di errore ben scritti possa fare molta strada verso la riduzione del rischio del problema. I messaggi di errore sono senza dubbio uno dei tipi più importanti della notifica all'utente che, in quanto sono sincroni e indicare un problema che deve essere risolto. I messaggi di errore mal lasciano gli utenti in propri per stabilire la causa degli errori e le possibili soluzioni.  
  
 Gli utenti potrebbero smettere di prestando attenzione a eccessivo o confondere i messaggi di errore, in modo che l'esperienza di scrittura necessarie solo messaggi che aggiungono valore all'utente. Se il messaggio è semplicemente una notifica, quindi usare una presentazione alternativa.  
  
### <a name="rules-for-creating-an-error-message"></a>Regole per la creazione di un messaggio di errore  
  
-   Durante la costruzione di messaggi di errore, scegliere il livello di errore appropriato per il gruppo di destinatari. Proporre riepiloghi semplice che forniscono un'azione che può richiedere all'utente, se applicabile. Non tutto ciò che l'utente non deve necessariamente conoscere lo stato.  
  
-   Fornire assistenza costruttivo. È facile leggere e agire su un messaggio di errore contenente l'istruzione.  
  
-   Non usare doppia negativi.  
  
-   Eseguire entrambi un automatizzati e manuale grammatica e ortografia controllare nei messaggi di errore che scrittura.  
  
-   Per i messaggi di errore complesse, evitare le comunicazioni sequenziale. Non utilizzare mai un'associazione F1 per il messaggio di errore. Il messaggio stesso dovrebbe essere sufficiente.  
  
-   Usare l'icona corretta.  
  
-   Porre domande facile da comprendere e usare i pulsanti con scelte non crittografate, ad esempio "Elimina" e "Annulla".  
  
-   Per gli avvisi, specificare chiaramente qual è la conseguenza di procedere. I pulsanti devono indicare la conseguenza.  
  
-   Per gli errori, descrivere ciò che l'utente può eseguire per risolvere il problema. I pulsanti devono essere azioni o pronunciare "Chiudi". Non usare un pulsante "OK" per un messaggio di errore.  
  
-   Alcune domande da porsi durante la costruzione di un messaggio di errore:  
  
    -   L'utente capisce come risolvere il problema con l'errore da solo?  
  
    -   L'utente usa il vocabolario stesso a questo errore?  
  
    -   È ambiguo questo errore o condivisi in diverse situazioni? In questo caso, come guidano gli utenti per la soluzione che ideale?  
  
#### <a name="build-errors"></a>Errori di compilazione  
 Poiché Visual Studio è uno strumento di sviluppo software, molti dei suoi componenti hanno una compilazione, conversione o la codifica di passaggio per convertire il lavoro degli sviluppatori in formato binario. Queste conversioni possono causare errori quando il compilatore non può elaborare i file creati in modo non corretto o quando le opzioni del compilatore non sono state impostate correttamente.  
  
 Gli utenti di Visual Studio è possono dedicare un enorme numero di ore di sviluppo per la risoluzione degli errori di compilazione. Questo tempo di risoluzione viene incrementato quando gli errori hanno dipendenze o quando i messaggi di errore vengono scritti in modo inadeguato, che possono renderlo difficile da individuare l'origine dell'errore.  
  
 Gli errori di compilazione migliori sono quelli che non si verificano in primo luogo, motivo per cui Visual Studio offre il completamento automatico e sottolineature a zigzag di IntelliSense. Validator di schema e gli strumenti simili offrono lo stesso tipo di commenti e suggerimenti. Questi meccanismi in modo proattivo guidano l'utente per costruire codice ben formato, riducendo la probabilità di errori di compilazione.  
  
 Visual Studio offre una finestra degli strumenti in cui gli utenti possono leggere e spostarsi tra gli errori che si è verificato nella finestra del documento. Tasti di scelta rapida vengono forniti in modo che l'utente può passare grandi quantità di codice rapidamente e andare direttamente al percorso del problema. Visual Studio consente anche di ogni errore di compilazione essere associato a un particolare ID parola chiave/contesto della Guida in modo che l'utente può passare direttamente a un argomento della Guida che fornisce informazioni più dettagliate sull'errore.  
  
 Scrivere gli errori di compilazione chiara e concisa:  
  
-   **Usare un linguaggio semplice** che spiega il problema non offrivano gergo del compilatore. Il testo di un errore di compilazione non deve essere eccessivamente tecnico.  
  
-   **Descrive le possibili cause.** Ad esempio, "manca un carattere due punti tra proprietà e il valore nel ' (proprietà): (valore)' dichiarazione."  
  
-   Fornire dettagli sulle possibili correzioni. Se non c'è spazio sufficiente, dettagli aggiuntivi possono essere inseriti nell'argomento della Guida corrispondente.  
  
### <a name="components-of-a-well-written-error-message"></a>Componenti di un messaggio di errore ben scritta  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Usare il servizio della finestra della shell per i messaggi di errore.  
 Uso del servizio di finestra di dialogo shell consente di controllare l'aspetto del messaggio, ovvero i tipi di carattere in particolare, ovvero senza modifiche rilevanti ai singoli elementi. Usare la **IErrorInfo** meccanismi e segnalali usando **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Scegliere una presentazione efficace e appropriato di notifica.  
 Usare una finestra di dialogo modale con un avviso critico se è necessario un intervento immediato per evitare la perdita di dati (la notifica sincrona). Icone critiche sono riservate per le situazioni in cui la chiusura del messaggio senza lettura può causare conseguenze negative. Perdita di dati è una situazione critica che richiede una risposta a livello di allarme. Utilizzo eccessivo dell'icona critico desensitizes agli utenti di importanza. Se il messaggio di errore è di natura informativa, prendere in considerazione alternative alla finestra di dialogo modale (notifica asincrona).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fornire una spiegazione chiara e concisa del motivo per cui si è verificato il problema piuttosto che una spiegazione.  
 Gli utenti con i dettagli tecnici la spiegazione di sovraccaricare li renderanno più possibilità di ignorare i messaggi di errore. Esempi di messaggistica ottimale:  
  
-   "Impossibile aprire il file richiesto".  
  
-   "Impossibile connettersi a Internet".  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fornire informazioni su come risolvere il problema.  
 Offrire suggerimenti utente come correggere il problema. Essere onesti con l'utente se non sono disponibili suggerimenti. Fornire collegamenti diretti a origini online alternativi, ad esempio il supporto tecnico o il supporto della community. Provare a scegliere utenti specifiche informazioni online relative al problema. Per un ID dell'errore, prendere in considerazione la connessione degli utenti a un thread di discussione sullo specifico errore. Esempi di messaggistica ottimale:  
  
-   "Verificare che si è connessi a Internet e ripetere l'operazione".  
  
-   "Assicurarsi che il file esista e di avere l'autorizzazione per aprirla."  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Scrivere un messaggio di brevi e concisi.  
 Può inviare una notifica di un messaggio di errore, descrivere e offrono una soluzione ma comunque essere ignorato se è prolisso. Un'unica soluzione consiste nell'usare la progressiva diffusione con il pulsante Dettagli. Ad esempio, viene proposta una breve descrizione/soluzione e quindi inserire altri dettagli in un pulsante Dettagli. Se gli utenti scelgono per altre informazioni sull'errore, è possibile farlo.  
  
 La lingua del messaggio deve essere:  
  
-   **Dominio appropriato.** Usare l'utente sarà in grado di linguaggio. Anche se i clienti Microsoft sono gli sviluppatori, che spesso non sono il contesto e terminologia che è disponibile.  
  
-   **Attributo specifico.** Evitare di formulazione vaga e assegnare nomi specifici e i percorsi degli oggetti coinvolti. Ad esempio, un messaggio di errore, ad esempio"carattere non valido" non è utile. Il carattere? "File non trovato". Il file?  
  
-   **Utile.** Non segnala l'errore all'utente o farlo sentire stupido. Evitare di linguaggio offensivo o ostile (kill, execute, terminare, irreversibile, non valida). Evitare di testo in maiuscolo, che è spesso considerato shouting e non è leggibile come. Non usare volgare e offensivo.  
  
-   **Correggere.** Usare la grammatica e ortografia corretta (anche in alphas). Errori di digitazione sono poco professionale e imbarazzante.  
  
-   **Contestualmente appropriate.** Usare il testo del pulsante appropriato. Evitare il pulsante "OK" e utilizzare invece "Continua" o "Yes/No".  
  
### <a name="error-message-examples"></a>Esempi di messaggi di errore  
  
|Good|non valido|  
|----------|---------|  
|"Il numero composto non è più nel servizio. Verificare il numero e Riprova o comporre 0 per l'operatore."|-"Errore (449): numero non valido"<br />-"Questo errore di eccezione non gestita indica che l'operazione completata".<br /><br /> ![Messaggio di errore non valido in Visual Studio](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Accedere alla Guida  
  
### <a name="overview"></a>Panoramica  
 Oltre alla documentazione in MSDN, un utente di Visual Studio include diversi punti di accesso per assistere l'utente mentre nell'interfaccia utente. Per garantire che i punti di accesso disponibili in modo coerente, i team delle funzionalità necessari sfruttare i vantaggi del sistema di Guida offerto dall'ambiente. Questi punti di accesso sono:  
  
-   **Testo esplicativo e supplemento nelle finestre di dialogo.** Testo statico che concede a direzione o spiegazione, sull'interfaccia utente disponibile al passaggio del mouse su un'icona InfoTip o area.  
  
-   **F1 Guida** (solo editor). All'interno dell'editor di Visual Studio, un utente può considerare attendibili che in qualsiasi momento, se si preme F1 verrà visualizzata un argomento della Guida specifiche per la selezione corrente. Assicurarsi che gli argomenti associati F1 siano appropriate e informativi.  
  
-   **Collegamenti ipertestuali agli argomenti della Guida.** Un collegamento ipertestuale all'interno di una finestra di dialogo, una finestra degli strumenti o area di progettazione che avvia un argomento per aiutare l'utente a ottenere ulteriori informazioni su una tecnologia, funzionalità o informazioni su come eseguire un'attività.  
  
-   **Meccanismi dell'interfaccia utente di helper, ad esempio gli smart tag e le finestre di dialogo di creazione.** Questi meccanismi di assistere l'utente in un elemento dell'interfaccia utente di comprendere o semplificano un'attività, ad esempio gli smart tag o le finestre di dialogo di generatore.  
  
-   **Guida dell'interfaccia utente pulsanti** (deprecato). Un indicatore visibile nella barra del titolo che fornisce l'accesso per l'argomento della Guida F1 correlato.  
  
### <a name="text"></a>Testo  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Testo esplicativo e supplemento nelle finestre di dialogo  
 Nelle finestre di dialogo che supportano attività complesse, potrebbe essere necessario per fornire testo informativo all'interno di interfaccia utente, spesso nella parte superiore della finestra di dialogo o quasi controlli complessi. Visualizzare [interfaccia utente di testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) per informazioni dettagliate sulla scrittura di stile.  
  
#### <a name="infotips"></a>Infotip  
 Testo esplicativo spesso, potrebbe essere troppo lungo per collocare nella posizione desiderata nell'interfaccia utente o potrebbe essere utile solo per i nuovi utenti, devono disordine agli utenti esperti. In questo caso, il testo esplicativo/informativo deve essere inserito come descrizione comando in una finestra popup.  
  
 Infotip devono essere posizionati vicino i controlli che sono correlati a e deve usare l'icona di InfoTip specifico, che è ancora unobtrusive evidenti.  
  
 ![Finestra popup in Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")  
  
 **Esempio di una finestra popup in Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Meccanismi di Guida interattive  
  
#### <a name="f1-help"></a>F1 Guida  
 F1 Guida in linea è necessario all'interno di un editor o nell'area di progettazione, ma non altrove nell'ambiente di Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Collegamenti ipertestuali agli argomenti della Guida  
 I collegamenti ipertestuali sono utilizzabile per eseguire un'azione, passare all'interno dell'IDE o avviare la Guida in un browser. Visualizzare [dell'interfaccia utente testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) per informazioni dettagliate sul linguaggio e 07.10.01 pulsanti e collegamenti ipertestuali per linee guida di oggetto visivo e il layout.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Pulsanti [?] le barre del titolo della finestra (deprecate)?  
 Nella maggior parte, i pulsanti [?] Guida nella barra del titolo delle finestre di dialogo sono deprecati. Argomenti dell'interfaccia utente non fanno più parte del nostro modello di documento e potrebbe pertanto non essere presente un argomento pertinente a cui collegarsi. In pratica, il pulsante della barra del titolo è stato differisce dal nome della Guida F1 e che non è più necessario nelle finestre di dialogo. In alcuni casi, questo è ancora utilizzabile come un indicatore che sia disponibile, altre informazioni procedurale o concettuali anche se i collegamenti ipertestuali vengono usati più comunemente nell'interfaccia utente più recenti.  
  
##### <a name="dialogs-created-through-the-environment"></a>Finestre di dialogo create tramite l'ambiente  
 Le finestre di dialogo di molte shell vengono creati tramite il **VBDialogBoxParam** (funzione). Questa funzione condivisa è stata aggiornata per semplificare lo spostamento di **aiutare** pulsante nella finestra di dialogo per la **?** pulsante mantenendo un'architettura che viene effettuato all'indietro compatibile ed estendibile.  
  
 In particolare, il **VBDialogBoxParam** funzione esamina il modello di finestra di dialogo per un pulsante con ID **IDHELP** (9) o un'etichetta **Guida** o **& Guida**. Se viene trovato un pulsante della Guida, è nascosta e la **WS_EX_CONTEXTHELP** stile viene aggiunta alla finestra di dialogo, che consente di collocare il **?** pulsante sulla barra del titolo della finestra di dialogo.  
  
 Quando viene creata la finestra di dialogo, inserisce la procedura di finestra di dialogo in uno stack e richiama la finestra di dialogo con una procedura di finestra di dialogo pre-elaborazione denominata **DialogPreProc**. Quando il **?** si fa clic sul pulsante, viene inviato un **WM_SYSCOMMAND** dei **SC_CONTEXTHELP** alla finestra di dialogo. Il **DialogPreProc** acquisisce questo comando e lo cambia in un **WM_HELP** messaggio, che viene passato per la procedura di finestra di dialogo originale.  
  
 La maggior parte delle finestre di dialogo Creazione ambiente dispone di un pulsante della Guida nella finestra di dialogo. Quando viene visualizzata la finestra di dialogo, il pulsante Guida è nascosta automaticamente e solo il **?** funzionamento del pulsante. Se il **?** pulsante mai rimosse o modificato in Windows, questa soluzione consente di spostare rapidamente ai pulsanti della Guida originali.  
  
 Questa soluzione quattro presupposti che potrebbero causare bug:  
  
-   Pulsante della Guida della finestra di dialogo viene **IDHELP** (9).  
  
-   La finestra di dialogo Cerca corretto quando il pulsante Guida è nascosto.  
  
-   La finestra di dialogo non sostituisce il winproc.  
  
-   La finestra di dialogo non viene incorporato all'interno di un'altra finestra di dialogo.  
  
 Se la finestra di dialogo si trova all'interno di msenv e non usa **VBDialogBoxParam**, provare a utilizzare sfruttando **VBDialogBoxParam** prima di implementare un gestore personalizzato.  
  
##### <a name="dialogs-created-through-other-packages"></a>Finestre di dialogo create tramite altri pacchetti  
 È possibile implementare una soluzione personalizzata per i dialoghi che risiedono all'esterno di msenv. Per una classe di finestra di dialogo condivise nel pacchetto VSPackage, provare a spostare il pulsante della barra del titolo o implementare un gestore in ogni finestra di dialogo. Il codice seguente è una struttura di un'implementazione che consentono di iniziare:  
  
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
 Override del comportamento predefinito del pulsante di finestra titolo barra della Guida in linea è semplice nel codice gestito. Di seguito è un'applicazione demo completo che illustra questo comportamento. In sostanza, è necessario eseguire l'override del form **WndProc** metodo e quindi attivare la Guida F1 richieste quando un' **SC_CONTEXTHELP** messaggio viene intercettato.  
  
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
 [Tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notifiche e avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

