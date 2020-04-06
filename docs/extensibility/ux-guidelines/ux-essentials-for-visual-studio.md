---
title: 'UX Essentials per Visual Studio : Documenti Microsoft'
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698335"
---
# <a name="ux-essentials-for-visual-studio"></a>Nozioni fondamentali sull'esperienza utente per Visual Studio

## <a name="best-practices"></a>Procedure consigliate

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Essere coerenti all'interno dell'ambiente di Visual Studio.

- Seguire i modelli di [interazione](interaction-patterns-for-visual-studio.md) esistenti all'interno della shell.

- Caratteristiche di progettazione per essere coerenti con il linguaggio visivo della shell e [i requisiti di artigianato.](evaluation-tools-for-visual-studio.md)

- Utilizzare i comandi e i controlli condivisi quando esistono.

- Comprendere la gerarchia di Visual Studio e come stabilisce il contesto e guida l'interfaccia utente.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utilizzare il servizio ambiente per i caratteri e colori.

- L'interfaccia utente deve rispettare l'impostazione del tipo di [carattere dell'ambiente](fonts-and-formatting-for-visual-studio.md) corrente, a meno che non sia esposta per la personalizzazione nella pagina Tipi di carattere e colori della finestra di dialogo Opzioni.UI should respect the current environment font setting unless it is exposed for customization in the Fonts and Colors page in the Options dialog.

- Gli elementi dell'interfaccia utente devono utilizzare il [servizio VSColor](colors-and-styling-for-visual-studio.md), utilizzando token di ambiente condiviso o token specifici della funzionalità.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Rendere tutte le immagini coerenti con il nuovo stile VS.

- Seguire i principi di progettazione di Visual Studio per icone, glifi e altri elementi grafici.

- Non inserire testo negli elementi grafici.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Progettare da una prospettiva incentrata sull'utente.

- Creare il flusso di attività prima delle singole entità geografiche al suo interno.

- Acquisire familiarità con gli utenti e rendere esplicita tale conoscenza nelle specifiche.

- Quando esamini l'interfaccia utente, valuta l'esperienza completa e i dettagli.

- Progetta l'interfaccia utente in modo che rimanga funzionale e attraente indipendentemente dalle impostazioni locali o dalla lingua.

## <a name="screen-resolution"></a>Risoluzione dello schermo

### <a name="minimum-resolution"></a>Risoluzione minima

- La risoluzione minima per Visual Studio 2015 è **1280x720**. Ciò significa che è *possibile* utilizzare Visual Studio con questa risoluzione, anche se potrebbe non essere un'esperienza utente ottimale. Non vi è alcuna garanzia che tutti gli aspetti saranno utilizzabili con risoluzioni inferiori a 1280x720.

- La risoluzione di destinazione per Visual Studio è **1366x768**. Questa è la risoluzione più bassa alla quale promettiamo una *buona* esperienza utente.

- L'altezza iniziale della finestra di dialogo deve essere inferiore a **700 pixel,** pertanto rientra nella risoluzione minima del frame IDE a 96 dpi.

### <a name="high-density-displays"></a>Display ad alta densità
 Interfaccia utente in Visual Studio deve funzionare correttamente in tutti i fattori di ridimensionamento DPI supportati da Windows: 150%, 200% e 250%.

## <a name="anti-patterns"></a>Anti-modelli
 Visual Studio contiene molti esempi di interfaccia utente che seguono le linee guida e le procedure consigliate. Nel tentativo di essere coerenti, gli sviluppatori spesso prendono in prestito da modelli di progettazione dell'interfaccia utente del prodotto simili a quello che stanno creando. Anche se questo è un buon approccio che ci aiuta a promuovere la coerenza nell'interazione dell'utente e nella progettazione visiva, a volte spediamo funzionalità con alcuni dettagli che non soddisfano le nostre linee guida a causa di vincoli di pianificazione o di definizione delle priorità dei difetti. In questi casi, non vogliamo che i team di copiare uno di questi "anti-modelli" perché proliferano cattiva o incoerente dell'interfaccia utente all'interno dell'ambiente di Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campi obbligatori/impostazioni visualizzati nello stato di errore per impostazione predefinitaRequired fields/settings shown in error state by default

#### <a name="feature-team-goals"></a>Obiettivi del team di funzionalità

- Avvisare gli utenti che hanno aggiunto un elemento che deve essere configurato.

- Attirare l'attenzione dell'utente alle aree che devono essere immesse.

#### <a name="anti-pattern-solution"></a>Soluzione anti-modello
 Non appena l'utente ha avviato un'azione e prima di aver completato l'attività, posizionare immediatamente le icone di arresto critico accanto alle aree che richiedono la configurazione.

#### <a name="example-manifest-designer-declarations"></a>Esempio: dichiarazioni di Progettazione manifestoExample: Manifest Designer declarations
 L'aggiunta di una dichiarazione all'elenco lo colloca immediatamente in uno stato di errore, che persiste fino a quando l'utente non imposta le proprietà necessarie.

 In questo caso, c'è un ulteriore problema perché&times;l'icona utilizzata per l'avviso contiene un' icona " ", quindi l'icona di rimozione comune non può essere utilizzata accanto ad essa. Di conseguenza, l'interfaccia utente usa un pulsante Rimuovi, un controllo più goffo.

 ![L'inserimento dell'interfaccia utente in uno stato di errore per impostazione predefinita è un anti-modello di Visual Studio.Placing UI in an error state by default is a Visual Studio anti-pattern.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern")<br />L'inserimento dell'interfaccia utente in uno stato di errore per impostazione predefinita è un anti-modello di Visual Studio.Placing UI in an error state by default is a Visual Studio anti-pattern.

#### <a name="alternatives"></a>Alternativi

Una soluzione migliore a questo problema è:

- Consentire all'utente di aggiungere una dichiarazione senza avviso e quindi spostarsi immediatamente per impostare le proprietà dell'elemento.

- Aggiungere l'icona di avviso (triangolo d'oro) quando lo stato attivo si sposta dall'elemento, ad esempio per aggiungere un'altra dichiarazione all'elenco o per tentare di modificare le schede all'interno della finestra di progettazione.

- Se l'utente tenta di modificare le schede prima di impostare le proprietà in tutte le dichiarazioni, aprire una finestra di dialogo che spiega che l'applicazione non verrà compilata (o qualunque siano le implicazioni) fino a quando non vengono risolti gli avvisi. Se l'utente chiude la finestra di dialogo e cambia comunque le schede, viene aggiunta un'icona (critica o di avviso, a seconda dei casi) alla scheda Dichiarazioni.

### <a name="multiple-clicks-to-dismiss-ui"></a>Più clic per chiudere l'interfaccia utenteMultiple clicks to dismiss UI

#### <a name="feature-team-goals"></a>Obiettivi del team di funzionalità
 Non consentire all'utente di chiudere l'interfaccia utente senza prima visualizzare il testo della spiegazione.

#### <a name="anti-pattern"></a>Anti-modello
 Il team che inserisce i collegamenti video in vari punti all'interno dell'interfaccia utente di VS ha deciso contro il modello comune del pulsante di chiusura "&times;" e descrizione comando come specificato dall'esperienza utente, e invece implementato un elenco a discesa e "Non mostrare più".

#### <a name="example-video-links-in-team-explorer"></a>Esempio: collegamenti video in Team Explorer
Forzare l'utente a leggere il testo esplicativo prima di chiudere l'interfaccia utente è un anti-modello all'interno di Visual Studio.Forcing the user to read eplanatory text before dismissing UI is an anti-pattern within Visual Studio. Progettati correttamente, i collegamenti video dovrebbero visualizzare una descrizione&times;comando con informazioni aggiuntive al passaggio del mouse e facendo clic su " " dovrebbe ignorare il messaggio senza bisogno di ulteriori interazioni.

 ![Testo esplicativo anti&#45;modello &#45; errato](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Uso erratodi più clic")<br />Modello di collegamento video errato

Invece di un semplice pulsante di chiusura (un clic), l'utente è costretto a utilizzare due clic per chiudere semplicemente l'interfaccia utente in ogni luogo in cui vengono visualizzati i collegamenti video.

La progettazione corretta per questa situazione consiste nel seguire il modello comune a Internet Explorer, Office e Visual Studio: al passaggio del mouse, l'utente può visualizzare la descrizione comando e un clic nasconde l'interfaccia utente.

 ![Testo esplicativo anti&#45;modello &#45; corretto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Esplicativotestoanti-pattern-corretto")<br />Correggere il modello di collegamento video

### <a name="using-command-bars-for-settings"></a>Utilizzo delle barre dei comandi per le impostazioni

**Figura A** rappresenta questo anti-modello: l'inserimento di un'impostazione sotto un pulsante di comando che si applica a più di un semplice comando. In questo schizzo sono disponibili comandi oltre a Avvia debug, ad esempio Visualizza nel browser, Avvia senza eseguire debug ed Esegui istruzione, che rispetteranno l'impostazione selezionata.

![Figura A: Anti-modello della barra dei comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Figura A: Anti-modello della barra dei comandi

Leggermente migliore, ma ancora indesiderabile, sta mettendo le impostazioni di questo tipo nelle barre degli strumenti, come mostrato Figura **B**. Mentre i pulsanti di divisione occupano meno spazio e sono quindi un miglioramento rispetto ai menu a discesa, entrambi i disegni utilizzano ancora una barra degli strumenti per promuovere qualcosa che non è realmente un comando.

![Figura B: Meglio, ma ancora un anti-modello della barra dei comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura B: Meglio, ma ancora un anti-modello della barra dei comandi

Nell'approccio corretto illustrato nella **Figura C**, l'impostazione è legata a una serie di comandi. Non è stata impostata alcuna impostazione globale e stiamo solo passando da un comando all'altro. Questa è l'unica situazione in cui i comandi nella barra degli strumenti sono accettabili.

![Figura C: Utilizzo corretto del modello della barra dei comandi di Visual StudioFigure C: Correct use of Visual Studio command bar pattern](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figura C: Utilizzo corretto del modello della barra dei comandi di Visual StudioFigure C: Correct use of Visual Studio command bar pattern

### <a name="control-anti-patterns"></a>Controllare gli anti-modelli
 Alcuni anti-pattern sono semplicemente l'utilizzo non corretto o la presentazione di un controllo o un gruppo di controlli.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sottolineatura utilizzata come etichetta di gruppo, non come collegamento ipertestuale
 Il testo di sottolineatura deve essere utilizzato solo per i collegamenti ipertestuali.

 **Male:**\
 ![Il testo sottolineato che non è un collegamento ipertestuale è un anti-modello di Visual Studio.Underlineed text that is not a hyperlink is a Visual Studio anti-pattern.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Il testo sottolineato che non è un collegamento ipertestuale è un anti-modello di Visual Studio.Underlineed text that is not a hyperlink is a Visual Studio anti-pattern.

 **Buono:**\
 ![Con uno stile corretto, il testo non del collegamento ipertestuale appare disadorno nel tipo di carattere dell'ambiente.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Con uno stile corretto, il testo non del collegamento ipertestuale appare disadorno nel tipo di carattere dell'ambiente.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Facendo clic su una casella di controllo si ottiene una finestra di dialogo popup
 Facendo clic sulla casella di controllo "Abilita Desktop remoto per tutti i ruoli" nella procedura guidata "Pubblica applicazione Windows Azure" viene visualizzata immediatamente una finestra di dialogo popup, un anti-modello di Visual Studio. Inoltre, il campo della casella di controllo non viene compilato con una casella di controllo dopo essere stato selezionato, un'altra interazione anti-modello.

 ![La visualizzazione di una finestra di dialogo dopo aver fatto clic su una casella di controllo è un anti-modello di Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />La visualizzazione di una finestra di dialogo dopo aver fatto clic su una casella di controllo è un anti-modello di Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Collegamenti ipertestuali per anti-pattern
 L'esempio seguente contiene due anti-pattern:The following example contains two anti-patterns:

1. Il primo piano che gira il rosso al passaggio del mouse indica che il colore condiviso corretto dal servizio tipi di carattere non viene utilizzato.

2. "Ulteriori informazioni" non è il testo appropriato per un collegamento a un argomento concettuale. L'obiettivo dell'utente non è quello di imparare di più, è quello di capire le ramificazioni della loro scelta.

   ![Ignorando il servizio colore e utilizzando "Ulteriori informazioni" per i collegamenti ipertestuali sono anti-modelli di Visual Studio.Ignoring the color service and using "Learn more" for hyperlinks are Visual Studio anti-patterns.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorando il servizio colore e utilizzando "Ulteriori informazioni" per i collegamenti ipertestuali sono anti-modelli di Visual Studio.Ignoring the color service and using "Learn more" for hyperlinks are Visual Studio anti-patterns.

**Soluzione migliore:** Porre la domanda che l'utente sarebbe chiedere facendo clic sul collegamento. Ad esempio:

- Come funzionano i servizi di Windows Azure?

- Quando è necessario un progetto Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Utilizzo di "Clicca qui" per i link
 I collegamenti ipertestuali devono essere autodescrittivi. Si tratta di un anti-modello per utilizzare "Clicca qui" o qualsiasi variazione simile.

 **Non valido:** "Fare clic qui per istruzioni su come creare un nuovo progetto."

 **Bene:** "Come faccio a creare un nuovo progetto?"
