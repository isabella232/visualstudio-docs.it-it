---
title: Fondamentali sull'esperienza utente per Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac8fdabc54965d521df2552ad4f152b53a7be70a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997182"
---
# <a name="ux-essentials-for-visual-studio"></a>Fondamentali sull'esperienza utente per Visual Studio
## <a name="best-practices"></a>Procedure consigliate  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. La coerenza all'interno dell'ambiente di Visual Studio.  
  
-   Seguire esistente [modelli di interazione](interaction-patterns-for-visual-studio.md) all'interno della shell.  
  
-   Progettare le funzionalità siano coerenti con linguaggio visivo della shell e [requisiti maestria](evaluation-tools-for-visual-studio.md).  
  
-   Usare i controlli e comandi condivisi quando sono presenti.  
  
-   Comprendere la gerarchia di Visual Studio e come stabilisce contesto e le unità dell'interfaccia utente.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Usare il servizio di ambiente per i tipi di carattere e colori.  
  
-   Interfaccia utente deve rispettare corrente [tipo di carattere ambiente](fonts-and-formatting-for-visual-studio.md) impostazione a meno che non viene esposta per la personalizzazione nella pagina tipi di carattere e colori nella finestra di dialogo Opzioni.  
  
-   Elementi dell'interfaccia utente devono usare la [VSColor Service](colors-and-styling-for-visual-studio.md), utilizzare condivisi i token di ambiente o i token specifici delle funzionalità.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Apportare tutte le immagini coerenti con il nuovo stile Visual Studio.  
  
-   Seguire i principi di progettazione di Visual Studio per le icone, glifi e altri elementi grafici.  
  
-   Non inserire testo in elementi grafici.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Progettare una prospettiva incentrata sull'utente.  
  
-   Creare il flusso di attività prima le singole funzionalità all'interno di esso.  
  
-   Acquisire familiarità con gli utenti e rendere espliciti nelle specifiche di tali informazioni.  
  
-   Esaminare l'interfaccia utente, valutare l'esperienza completa, nonché i dettagli.  
  
-   Progettare l'interfaccia utente in modo che rimanga funzionali e accattivanti indipendentemente dal linguaggio o delle impostazioni locali.  
  
## <a name="screen-resolution"></a>Risoluzione dello schermo  
  
### <a name="minimum-resolution"></a>Risoluzione minima  
 - È la risoluzione minima per Visual Studio Dev14 **1280 x 720**. Ciò significa che è *possibili* usare Visual Studio questa risoluzione, anche se potrebbe non essere un'esperienza utente ottimale. Non è garantito che tutti gli aspetti sarà utilizzabili con risoluzioni inferiori a 1280 x 720.  
  
 - La risoluzione di destinazione per Visual Studio viene **1366 x 768**. Questa è la soluzione più bassa in corrispondenza del quale vedrai una *buona* esperienza utente.

 - Altezza iniziale della finestra deve essere **inferiore a 700 pixel**, in modo che rientri nella risoluzione minima del frame IDE 96 DPI.
  
### <a name="high-density-displays"></a>Display ad alta densità  
 Interfaccia utente in Visual Studio deve funzionare correttamente in tutti i fattori di scala DPI che Windows supportate per impostazione predefinita: 150%, 200% e % a 250.  
  
## <a name="anti-patterns"></a>Anti-modelli  
 Visual Studio contiene molti esempi dell'interfaccia utente che seguono le linee guida e procedure consigliate. Favorire la coerenza, gli sviluppatori spesso prestito da modelli di progettazione dell'interfaccia utente del prodotto simili a ciò che sta creando. Anche se questo è un buon approccio che consente di noi maggiore coerenza nella progettazione visiva e l'interazione dell'utente, in alcuni casi messa a disposizione le funzionalità con alcuni dettagli che non soddisfa le linee guida a causa dei vincoli di pianificazione o l'esclusione di assegnazione delle priorità. In questi casi, non vogliamo ai team di copiare uno di questi "anti-modelli" poiché essi proliferare dell'interfaccia utente non valido o non coerente nell'ambiente di Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>I campi/le impostazioni necessarie in stato di errore visualizzate per impostazione predefinita  
  
#### <a name="feature-team-goals"></a>Funzionalità degli obiettivi del team  
  
-   Avvisare gli utenti che è stato aggiunto un elemento che deve essere configurato.  
  
-   Attirare l'attenzione dell'utente per le aree che richiedono input.  
  
#### <a name="anti-pattern-solution"></a>Soluzione anti-pattern  
 Non appena l'utente ha avviato un'azione e prima che è stata completata l'attività, inserire immediatamente arresto critico icone accanto alle aree che richiedono una configurazione.  
  
#### <a name="example-manifest-designer-declarations"></a>Esempio: Dichiarazioni di progettazione manifesto  
 Aggiunta di una dichiarazione all'elenco immediatamente, lo inserisce in uno stato di errore, che persiste fino a quando l'utente imposta le proprietà necessarie.  
  
 In questo caso, è presente una preoccupazione aggiuntiva perché l'icona utilizzata per l'avviso contiene un "&times;" sull'icona, non è possibile usare l'icona Rimuovi comuni accanto a esso. Di conseguenza, l'interfaccia utente usa un pulsante Rimuovi, un controllo più difficili.  
  
 ![Inserimento dell'interfaccia utente in uno stato di errore per impostazione predefinita è un antipattern di Visual Studio. ](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern")<br />Inserimento dell'interfaccia utente in uno stato di errore per impostazione predefinita è un antipattern di Visual Studio.
  
#### <a name="alternatives"></a>Alternative  
 Una soluzione migliore a questo problema, è possibile:  
  
-   Consentire all'utente di aggiungere una dichiarazione senza avviso e quindi spostare immediatamente impostare le proprietà sull'elemento.  
  
-   Aggiungere l'icona di avviso (triangolo gold) quando lo stato attivo viene spostata dall'elemento, ad esempio per aggiungere un'altra dichiarazione all'elenco o per tentare di modificare le tabulazioni all'interno della finestra di progettazione.  
  
-   Se l'utente tenta di modificare le schede prima di impostare le proprietà per tutte le dichiarazioni, visualizzata una finestra di dialogo che spiega che l'applicazione non verrà compilato (o qualsiasi le implicazioni) fino a quando non vengono risolti gli avvisi. Se l'utente chiude la finestra di dialogo e sostituisce le tabulazioni comunque, un'icona (critica o avviso, come appropriata) viene aggiunto alla scheda dichiarazioni.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Diversi clic per chiudere l'interfaccia utente  
  
#### <a name="feature-team-goals"></a>Funzionalità degli obiettivi del team  
 Non consentire all'utente di ignorare l'interfaccia utente senza prima di visualizzare il testo di spiegazione.  
  
#### <a name="anti-pattern"></a>Anti-pattern  
 Il team di inserimento di collegamenti video in diverse posizioni nell'interfaccia utente di Visual Studio ha deciso rispetto al pattern comune del "&times;" chiude spiegazione pulsante e la descrizione comando come specificato dall'esperienza utente e invece implementato un elenco a discesa e "Non visualizzare più" Crea un collegamento.  

#### <a name="example-video-links-in-team-explorer"></a>Esempio: collegamenti video in Team Explorer
L'utente leggere testo esplicativo prima dell'eliminazione dell'interfaccia utente sia un antipattern all'interno di Visual Studio. Collegamenti correttamente progettati, un video devono visualizzare una descrizione comando con informazioni aggiuntive sul passaggio del mouse e scegliendo la "&times;" deve chiudere il messaggio senza necessità di ulteriore interazione.


 ![Testo esplicativo anti-&#45;modello &#45; errato](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Modello di collegamento video non corretto
  
#### <a name="result"></a>Risultato  
 Invece di un semplice pulsante Chiudi (un solo clic), l'utente è obbligato a usare due clic per chiudere l'interfaccia utente in ogni punto in cui vengono visualizzati i collegamenti video.  
  
#### <a name="alternatives"></a>Alternative  
 La progettazione corretta questa situazione, è possibile seguire il modello comune per Internet Explorer, Office e Visual Studio: al passaggio del mouse, l'utente può visualizzare la descrizione della descrizione e un solo clic consente di nascondere l'interfaccia utente.  
  
 ![Testo esplicativo anti-&#45;modello &#45; corretta](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-pattern-correggere")<br />Modello corretto collegamento video
  
### <a name="using-command-bars-for-settings"></a>Utilizzo di barre dei comandi per le impostazioni  
 **Figura A** rappresenta questo antipattern: inserimento di un'impostazione di sotto di un pulsante di comando che si applica solo al comando. In questo esercizio sono disponibili comandi oltre a Avvia debug, ovvero come visualizzazione nel Browser, Avvia senza eseguire debug ed Esegui istruzione, che verrà rispettata l'impostazione selezionata.  

  ![Figura a: Anti-pattern barra dei comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Figura a: Anti-pattern barra dei comandi
  
 Scherzo leggermente migliore, ma è ancora, è inserire le impostazioni di questo tipo nelle barre degli strumenti, come illustrato nella **Figura B**. Anche se i pulsanti di suddivisione richiede meno spazio e sono pertanto un miglioramento su elenchi a discesa, entrambi i progetti siano ancora usando una barra degli strumenti per promuovere un elemento che non è davvero un comando.  
 
 ![Figura b: Migliore, ma comunque un anti-pattern della barra di comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura b: Migliore, ma comunque un anti-pattern della barra di comandi
 
  L'approccio corretto illustrato nella **figura C**, l'impostazione è collegata a una serie di comandi. È disponibile alcuna impostazione globale viene impostata e si passa semplicemente tra quattro comandi. Si tratta dell'unica situazione in cui i comandi sulla barra degli strumenti sono accettabili. 

 ![Figura c: Correzione uso di pattern della barra dei comandi di Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figura c: Uso corretto del pattern della barra dei comandi di Visual Studio
   
### <a name="control-anti-patterns"></a>Anti-pattern di controllo  
 Alcuni anti-modelli sono utilizzo semplicemente non corretto o la presentazione di un controllo o un gruppo di controlli.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sottolineatura usata come etichetta di gruppo, non un collegamento ipertestuale  
 Sottolineare il testo deve essere utilizzato solo per i collegamenti ipertestuali.  
  
 **Non valido:**    
 ![Testo sottolineato che non è un collegamento ipertestuale è un antipattern di Visual Studio. ](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />Testo sottolineato che non è un collegamento ipertestuale è un antipattern di Visual Studio.
  
 **Buona:**   
 ![Applicato lo stile corretto, non hyperlink testo viene visualizzato solo nel tipo di carattere ambiente. ](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />Applicato lo stile corretto, non hyperlink testo viene visualizzato solo nel tipo di carattere ambiente.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Facendo clic su una casella di controllo di risultati in una finestra di dialogo popup  
 Scegliere la casella di controllo "Abilita Desktop remoto per tutti i ruoli" della procedura guidata "Pubblica l'applicazione Windows Azure" immediatamente viene visualizzata una finestra di dialogo popup, un antipattern di Visual Studio. Inoltre, il campo casella di controllo non viene riempita con una casella di controllo dopo la selezione, anti-modello di un'altra interazione.  
  
 ![Richiama una finestra di dialogo al termine fare clic su una casella di controllo un antipattern di Visual Studio. ](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Richiama una finestra di dialogo al termine fare clic su una casella di controllo un antipattern di Visual Studio.
  
### <a name="hyperlink-anti-patterns"></a>Collegamenti ipertestuali per anti-pattern  
 L'esempio seguente contiene due anti-modelli.  
  
1. In primo piano rosso attivando al passaggio del mouse significa che non viene utilizzato il corretto colore condiviso dal servizio del tipo di carattere.  
  
2. "Altre informazioni" non è il testo appropriato per un collegamento a un argomento concettuale. Obiettivo il suo non è altre informazioni, che consiste nel comprendere le implicazioni di propria scelta.  
  
   ![Ignorando il servizio di colore e l'utilizzo di "Informazioni" per i collegamenti ipertestuali sono anti-modelli di Visual Studio. ](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />Ignorando il servizio di colore e l'utilizzo di "Informazioni" per i collegamenti ipertestuali sono anti-modelli di Visual Studio.  
  
   **Soluzione migliore:** Porre la domanda che sarebbe chiedere all'utente, selezionando il collegamento.  
  
-   Come funzionano i servizi di Azure?  
  
-   Quando è necessario un progetto di servizi mobili di Azure?  
  
#### <a name="using-click-here-for-links"></a>Utilizzando "Fare clic qui" per i collegamenti  
 I collegamenti ipertestuali dovrebbero essere autodescrittivi. È un antipattern usare "Fare clic qui" o qualsiasi variazione simili.  
  
 **Non valido:** "Fare clic qui per istruzioni su come creare un nuovo progetto."
  
 **Buona:** "Come si crea un nuovo progetto?"