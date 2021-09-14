---
title: UX Essentials per Visual Studio | Microsoft Docs
description: Esaminare queste procedure consigliate per l'esperienza utente per le nuove funzionalità sviluppate per Visual Studio, inclusa la conoscenza della risoluzione dello schermo.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0124fd30f1f4c3565e0019f2f5709726f7622126
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709445"
---
# <a name="ux-essentials-for-visual-studio"></a>Nozioni fondamentali sull'esperienza utente per Visual Studio

## <a name="best-practices"></a>Procedure consigliate

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Essere coerenti all'interno Visual Studio ambiente.

- Seguire i modelli [di interazione esistenti](interaction-patterns-for-visual-studio.md) all'interno della shell.

- Progettare le funzionalità in modo che siano coerenti con il linguaggio visivo della shell e con i requisiti [di conformità.](evaluation-tools-for-visual-studio.md)

- Usare comandi e controlli condivisi quando esistono.

- Comprendere la gerarchia Visual Studio e come stabilisce il contesto e guida l'interfaccia utente.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Usare il servizio ambiente per i tipi di carattere e i colori.

- L'interfaccia utente deve rispettare [l'impostazione del](fonts-and-formatting-for-visual-studio.md) tipo di carattere dell'ambiente corrente, a meno che non sia esposta per la personalizzazione nella pagina Tipi di carattere e colori della finestra di dialogo Opzioni.

- Gli elementi dell'interfaccia utente [devono usare il servizio VSColor](colors-and-styling-for-visual-studio.md), usando token di ambiente condiviso o token specifici della funzionalità.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Rendere tutte le immagini coerenti con il nuovo stile di Visual Studio.

- Seguire Visual Studio principi di progettazione per icone, glifi e altri elementi grafici.

- Non inserire testo negli elementi grafici.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Progettare da una prospettiva incentrata sull'utente.

- Creare il flusso di attività prima delle singole funzionalità al suo interno.

- Acquisire familiarità con gli utenti e rendere esplicite le informazioni nella specifica.

- Quando si esamina l'interfaccia utente, valutare l'esperienza completa e i dettagli.

- Progettare l'interfaccia utente in modo che rimanga funzionale e interessante indipendentemente dalle impostazioni locali o dalla lingua.

## <a name="screen-resolution"></a>Risoluzione dello schermo

### <a name="minimum-resolution"></a>Risoluzione minima

- La risoluzione minima per Visual Studio 2015 è **1280x720**. Ciò significa che è *possibile usare* Visual Studio a questa risoluzione, anche se potrebbe non essere un'esperienza utente ottimale. Non è garantito che tutti gli aspetti siano utilizzabili in risoluzioni inferiori a 1280x720.

- La risoluzione di destinazione per Visual Studio **è 1366x768**. Si tratta della risoluzione più bassa alla quale si è promessa una *buona esperienza* utente.

- L'altezza iniziale del dialogo deve essere inferiore a **700 pixel,** quindi rientra nella risoluzione minima del frame IDE a 96 dpi.

### <a name="high-density-displays"></a>Display ad alta densità
 L'Visual Studio deve funzionare correttamente in tutti i fattori di scalabilità DPI supportati da Windows: 150%, 200% e 250%.

## <a name="anti-patterns"></a>Anti-pattern
 Visual Studio contiene molti esempi di interfaccia utente che seguono le linee guida e le procedure consigliate. Per essere coerenti, gli sviluppatori spesso si prestano a modelli di progettazione dell'interfaccia utente del prodotto simili a quelli che stanno creando. Anche se si tratta di un buon approccio che consente di garantire la coerenza nell'interazione dell'utente e nella progettazione visiva, a volte vengono fornite funzionalità con alcuni dettagli che non soddisfano le linee guida a causa di vincoli di pianificazione o priorità dei difetti. In questi casi, non si vuole che i team copiano uno di questi "anti-pattern" perché proliferano un'interfaccia utente non conforme o incoerente all'interno dell'Visual Studio locale.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campi/impostazioni obbligatori visualizzati nello stato di errore per impostazione predefinita

#### <a name="feature-team-goals"></a>Obiettivi del team di funzionalità

- Avvisare gli utenti che è stato aggiunto un elemento che deve essere configurato.

- Attirare l'attenzione dell'utente nelle aree che necessitano di input.

#### <a name="anti-pattern-solution"></a>Soluzione anti-pattern
 Non appena l'utente ha avviato un'azione e prima di aver completato l'attività, posizionare immediatamente le icone di arresto critico accanto alle aree che necessitano di configurazione.

#### <a name="example-manifest-designer-declarations"></a>Esempio: dichiarazioni di Progettazione manifesto
 L'aggiunta di una dichiarazione all'elenco la inserisce immediatamente in uno stato di errore, che persiste fino a quando l'utente non imposta le proprietà necessarie.

 In questo caso, esiste un problema aggiuntivo perché l'icona usata per l'avviso contiene un'icona " ", quindi non è possibile usare accanto l'icona &times; di rimozione comune. Di conseguenza, l'interfaccia utente usa un pulsante Rimuovi, un controllo più goffo.

 ![Il posizionamento dell'interfaccia utente in uno stato di errore per impostazione predefinita Visual Studio anti-pattern.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern")<br />Il posizionamento dell'interfaccia utente in uno stato di errore per impostazione predefinita Visual Studio anti-pattern.

#### <a name="alternatives"></a>Alternativi

Una soluzione migliore a questo problema è:

- Consentire all'utente di aggiungere una dichiarazione senza avviso e quindi di spostarsi immediatamente per impostare le proprietà dell'elemento.

- Aggiungere l'icona di avviso (triangolo dorato) quando lo stato attivo viene spostato dall'elemento, ad esempio per aggiungere un'altra dichiarazione all'elenco o per tentare di modificare le schede all'interno della finestra di progettazione.

- Se l'utente tenta di modificare le schede prima di impostare le proprietà in qualsiasi dichiarazione, visualizzare una finestra di dialogo che spiega che l'applicazione non verrà compilata (o qualsiasi implicazioni) fino a quando non vengono risolti gli avvisi. Se l'utente chiude la finestra di dialogo e modifica comunque le schede, viene aggiunta un'icona (critica o avviso, in base alle esigenze) alla scheda Dichiarazioni.

### <a name="multiple-clicks-to-dismiss-ui"></a>Più clic per chiudere l'interfaccia utente

#### <a name="feature-team-goals"></a>Obiettivi del team di funzionalità
 Non consentire all'utente di chiudere l'interfaccia utente senza prima visualizzare il testo della spiegazione.

#### <a name="anti-pattern"></a>Anti-pattern
 Il team che inserisce i collegamenti video in varie posizioni all'interno dell'interfaccia utente di Visual Studio ha deciso di non usare il modello comune del pulsante di chiusura e della descrizione comando, come specificato dall'esperienza utente, e ha invece implementato un elenco a discesa e un collegamento "Non visualizzare &times; più".

#### <a name="example-video-links-in-team-explorer"></a>Esempio: collegamenti video in Team Explorer
Forzare l'utente a leggere testo esplicativo prima di chiudere l'interfaccia utente è un anti-pattern all'interno Visual Studio. Progettati correttamente, i collegamenti video dovrebbero visualizzare una descrizione comando con informazioni aggiuntive al passaggio del mouse e facendo clic sul " " dovrebbe ignorare il messaggio senza la necessità &times; di un'ulteriore interazione.

 ![Modello anti-&#45;testo &#45; non corretto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Modello di collegamento video non corretto

Invece di un semplice pulsante di chiusura (un clic), l'utente è obbligato a usare due clic per chiudere semplicemente l'interfaccia utente in ogni posizione in cui vengono visualizzati i collegamenti video.

La progettazione corretta per questa situazione è seguire il modello comune a Internet Explorer, Office e Visual Studio: al passaggio del mouse, l'utente può visualizzare la descrizione comando e un clic nasconde l'interfaccia utente.

 ![Modello anti-&#45;testo &#45; corretto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Esplicativotextanti-pattern-correct")<br />Modello di collegamento video corretto

### <a name="using-command-bars-for-settings"></a>Uso delle barre dei comandi per le impostazioni

**La figura A** rappresenta questo anti-pattern: inserendo un'impostazione sotto un pulsante di comando che si applica a più di un semplice comando. In questo sketch sono disponibili comandi oltre a Avvia debug, ad esempio Visualizza nel browser, Avvia senza eseguire debug ed Esecuzione istruzione, che rispetteranno l'impostazione selezionata.

![Figura A: Anti-pattern della barra dei comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Figura A: Anti-pattern della barra dei comandi

Leggermente migliore, ma comunque indesiderato, è l'inserimento di impostazioni di questo tipo nelle barre degli strumenti, come illustrato **nella figura B**. Anche se i pulsanti di divisione hanno meno spazio e sono quindi un miglioramento rispetto agli elenchi a discesa, entrambe le progettazioni usano comunque una barra degli strumenti per alzare di livello un elemento che non è effettivamente un comando.

![Figura B: Migliore, ma ancora anti-schema della barra dei comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura B: Migliore, ma ancora anti-pattern della barra dei comandi

Nell'approccio corretto illustrato **nella figura C**, l'impostazione è associata a una serie di comandi. Non è stata impostata alcuna impostazione globale e si sta semplicemente passando da un comando all'altro. Questa è l'unica situazione in cui i comandi nella barra degli strumenti sono accettabili.

![Figura C: Uso corretto del modello Visual Studio della barra dei comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figura C: Uso corretto del modello Visual Studio della barra dei comandi

### <a name="control-anti-patterns"></a>Controllare gli anti-pattern
 Alcuni anti-pattern sono semplicemente l'utilizzo non corretto o la presentazione di un controllo o di un gruppo di controlli.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sottolineatura usata come etichetta di gruppo, non come collegamento ipertestuale
 La sottolineatura del testo deve essere usata solo per i collegamenti ipertestuali.

 **Male:**\
 ![Il testo sottolineato che non è un collegamento ipertestuale è un Visual Studio anti-pattern.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Il testo sottolineato che non è un collegamento ipertestuale è un Visual Studio anti-pattern.

 **Buono:**\
 ![Con uno stile corretto, il testo non con collegamento ipertestuale viene visualizzato senza colori nel tipo di carattere dell'ambiente.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Con uno stile corretto, il testo non con collegamento ipertestuale viene visualizzato senza colori nel tipo di carattere dell'ambiente.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Facendo clic su una casella di controllo viene visualizzata una finestra di dialogo popup
 Facendo clic sulla casella di controllo "Abilita Desktop remoto per tutti i ruoli" nella procedura guidata "Pubblica Windows applicazione Azure" viene immediatamente visualizzata una finestra di dialogo popup, un Visual Studio anti-pattern. Inoltre, il campo della casella di controllo non viene riempito con una casella di controllo dopo la selezione, un altro anti-pattern di interazione.

 ![La finestra di dialogo visualizzata dopo aver fatto clic su una casella di controllo Visual Studio anti-pattern.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />La finestra di dialogo visualizzata dopo aver fatto clic su una casella di controllo Visual Studio anti-pattern.

### <a name="hyperlink-anti-patterns"></a>Collegamenti ipertestuali per anti-pattern
 L'esempio seguente contiene due anti-pattern:

1. Il primo piano che attiva il rosso al passaggio del mouse indica che non viene usato il colore condiviso corretto dal servizio di caratteri.

2. "Altre informazioni" non è il testo appropriato per un collegamento a un argomento concettuale. L'obiettivo dell'utente non è quello di ottenere altre informazioni, ma di comprendere le ramificazioni di propria scelta.

   ![Ignorare il servizio colori e usare "Altre informazioni" per i collegamenti ipertestuali Visual Studio anti-pattern.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorare il servizio colori e usare "Altre informazioni" per i collegamenti ipertestuali Visual Studio anti-pattern.

**Soluzione migliore:** Porre la domanda che l'utente potrebbe porre facendo clic sul collegamento. Ad esempio:

- Come funzionano Windows servizi di Azure?

- Quando è necessario un progetto Windows azure Servizi mobili?

#### <a name="using-click-here-for-links"></a>Uso di "Fare clic qui" per i collegamenti
 I collegamenti ipertestuali devono essere auto descrittivi. È un anti-modello usare "Fare clic qui" o qualsiasi variazione simile.

 **Non è possibile:** "Fare clic qui per istruzioni su come creare un nuovo progetto".

 **Buona:** "Ricerca per categorie creare un nuovo progetto?"
