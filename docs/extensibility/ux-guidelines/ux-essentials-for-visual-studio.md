---
title: UX Essentials per Visual Studio | Microsoft Docs
description: Esaminare le procedure consigliate per le nuove funzionalità sviluppate per Visual Studio, inclusa la conoscenza della risoluzione dello schermo.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce44b9234465af6bf52ce8baa0e60e641e845d3c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052671"
---
# <a name="ux-essentials-for-visual-studio"></a>Nozioni fondamentali sull'esperienza utente per Visual Studio

## <a name="best-practices"></a>Procedure consigliate

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. essere coerenti all'interno dell'ambiente di Visual Studio.

- Seguire i [modelli di interazione](interaction-patterns-for-visual-studio.md) esistenti all'interno della shell.

- Progettare le funzionalità in modo che siano coerenti con i requisiti del linguaggio visivo e dell' [artigianato](evaluation-tools-for-visual-studio.md)della shell.

- Quando esistono, utilizzare i comandi e i controlli condivisi.

- Comprendere la gerarchia di Visual Studio e il modo in cui stabilisce il contesto e guida l'interfaccia utente.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. usare il servizio Environment per i tipi di carattere e i colori.

- L'interfaccia utente deve rispettare l'impostazione del [tipo di carattere dell'ambiente](fonts-and-formatting-for-visual-studio.md) corrente a meno che non venga esposta per la personalizzazione nella pagina tipi di carattere e colori della finestra di dialogo Opzioni.

- Gli elementi dell'interfaccia utente devono usare il [servizio VSColor](colors-and-styling-for-visual-studio.md), usando token di ambiente condivisi o token specifici della funzionalità.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. rendere tutte le immagini coerenti con il nuovo stile di Visual Studio.

- Segui i principi di progettazione di Visual Studio per icone, glifi e altri elementi grafici.

- Non inserire testo negli elementi grafici.

### <a name="4-design-from-a-user-centric-perspective"></a>4. progettazione da una prospettiva incentrata sull'utente.

- Creare il flusso attività prima delle singole funzionalità al suo interno.

- Acquisire familiarità con gli utenti e rendere esplicita la conoscenza nelle specifiche.

- Quando si esamina l'interfaccia utente, valutare l'esperienza completa, nonché i dettagli.

- Progettare l'interfaccia utente in modo che rimanga funzionale e interessante indipendentemente dalle impostazioni locali o dalla lingua.

## <a name="screen-resolution"></a>Risoluzione dello schermo

### <a name="minimum-resolution"></a>Risoluzione minima

- La risoluzione minima per Visual Studio 2015 è **1280x720**. Ciò significa che è *possibile* usare Visual Studio in questa risoluzione, anche se potrebbe non essere un'esperienza utente ottimale. Non vi è alcuna garanzia che tutti gli aspetti saranno utilizzabili alle risoluzioni inferiori a 1280x720.

- La risoluzione di destinazione per Visual Studio è **1366 x 768**. Si tratta della risoluzione più bassa a cui si promette un'esperienza utente *soddisfacente* .

- L'altezza iniziale della finestra di dialogo deve essere **inferiore a 700 pixel**, quindi rientra nella risoluzione minima del frame IDE a 96 dpi.

### <a name="high-density-displays"></a>Visualizzazioni a densità elevata
 L'interfaccia utente in Visual Studio deve funzionare correttamente in tutti i fattori di scala DPI supportati da Windows: 150%, 200% e 250%.

## <a name="anti-patterns"></a>Anti-patterns
 Visual Studio contiene molti esempi di interfaccia utente che seguono le linee guida e le procedure consigliate. Per coerenza, gli sviluppatori spesso prendono in prestito da modelli di progettazione dell'interfaccia utente del prodotto simili a quelli che stanno creando. Sebbene si tratti di un approccio efficace che ci aiuta a garantire la coerenza nell'interazione dell'utente e nella progettazione visiva, le funzionalità vengono fornite con alcuni dettagli che non soddisfano le linee guida a causa dei vincoli di pianificazione o della definizione delle priorità dei difetti. In questi casi, non si vuole che i team copino uno di questi "anti-pattern" perché proliferano interfaccia utente errata o incoerente all'interno dell'ambiente di Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campi/impostazioni obbligatori visualizzati in stato di errore per impostazione predefinita

#### <a name="feature-team-goals"></a>Obiettivi del team di funzionalità

- Avvisare gli utenti che hanno aggiunto un elemento che deve essere configurato.

- Attirare l'attenzione dell'utente sulle aree che necessitano di input.

#### <a name="anti-pattern-solution"></a>Soluzione anti-pattern
 Non appena l'utente ha iniziato un'azione e prima di aver completato l'attività, posizionare immediatamente icone di arresto critico accanto alle aree che richiedono la configurazione.

#### <a name="example-manifest-designer-declarations"></a>Esempio: dichiarazioni di Progettazione manifesto
 L'aggiunta di una dichiarazione all'elenco lo inserisce immediatamente in uno stato di errore, che viene mantenuta fino a quando l'utente non imposta le proprietà obbligatorie.

 In questo caso, esiste un ulteriore problema perché l'icona utilizzata per l'avviso contiene un'icona " &times; ", quindi non è possibile utilizzare l'icona di rimozione comune. Di conseguenza, l'interfaccia utente utilizza un pulsante Rimuovi, un controllo più goffo.

 ![Per impostazione predefinita, l'inserimento dell'interfaccia utente in uno stato di errore è un anti-pattern di Visual Studio.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "Modello ManifestDesignererrordeclarationsanti")<br />Per impostazione predefinita, l'inserimento dell'interfaccia utente in uno stato di errore è un anti-pattern di Visual Studio.

#### <a name="alternatives"></a>Alternativi

Una soluzione migliore a questo problema è:

- Consente all'utente di aggiungere una dichiarazione senza preavviso e quindi di passare immediatamente a impostare le proprietà dell'elemento.

- Aggiungere l'icona di avviso (triangolo dorato) quando lo stato attivo viene spostato dall'elemento, ad esempio per aggiungere un'altra dichiarazione all'elenco o per tentare di modificare le schede nella finestra di progettazione.

- Se l'utente tenta di modificare le schede prima di impostare le proprietà in qualsiasi dichiarazione, visualizzare una finestra di dialogo che informa che l'applicazione non verrà compilata (o qualsiasi altra implicazione) finché gli avvisi non verranno risolti. Se l'utente omette la finestra di dialogo e le schede cambiano comunque, alla scheda dichiarazioni verrà aggiunta un'icona (critico o di avviso, in base alle esigenze).

### <a name="multiple-clicks-to-dismiss-ui"></a>Più clic per chiudere l'interfaccia utente

#### <a name="feature-team-goals"></a>Obiettivi del team di funzionalità
 Non consentire all'utente di chiudere l'interfaccia utente senza visualizzare prima il testo della spiegazione.

#### <a name="anti-pattern"></a>Anti-pattern
 Il team che inserisce i collegamenti video in diverse posizioni all'interno dell'interfaccia utente di Visual Studio ha deciso di utilizzare il modello comune di " &times; " pulsante Chiudi e spiegazione descrizione comando come specificato da UX, implementando invece un collegamento a discesa e "non visualizzare più".

#### <a name="example-video-links-in-team-explorer"></a>Esempio: collegamenti video in Team Explorer
L'utilizzo forzato dell'utente per la lettura del testo esplicativo prima della chiusura dell'interfaccia utente è un anti-modello in Visual Studio. Progettato correttamente, i collegamenti video dovrebbero visualizzare una descrizione comando con informazioni aggiuntive sul passaggio del mouse e fare clic su " &times; " per ignorare il messaggio senza che sia necessario ulteriore interazione.

 ![Schema anti&#45;del testo esplicativo &#45; non corretto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Modello di collegamento video errato

Invece di un semplice pulsante Chiudi (un clic), l'utente deve usare due clic per ignorare semplicemente l'interfaccia utente in ogni punto in cui vengono visualizzati i collegamenti video.

La progettazione corretta per questa situazione consiste nel seguire il modello comune a Internet Explorer, Office e Visual Studio: al passaggio del mouse, l'utente può visualizzare la descrizione della descrizione comando e un clic nasconde l'interfaccia utente.

 ![Testo esplicativo anti&#45;modello &#45; corretto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-pattern-correct")<br />Correggere il modello di collegamento video

### <a name="using-command-bars-for-settings"></a>Uso delle barre dei comandi per le impostazioni

La **figura a** rappresenta questo anti-pattern: inserendo un'impostazione sotto un pulsante di comando che si applica solo a un comando. In questo sketch sono disponibili comandi oltre all'avvio del debug, come la visualizzazione nel browser, l'avvio senza debug e l'esecuzione di istruzioni in che rispettano l'impostazione selezionata.

![Figura A: anti-pattern della barra del comando](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-figuraa")<br />Figura A: anti-pattern della barra del comando

È leggermente più semplice, ma ancora indesiderato, inserire le impostazioni di questo tipo nelle barre degli strumenti, come illustrato nella **Figura B**. Mentre i pulsanti di suddivisione utilizzano meno spazio e sono pertanto un miglioramento rispetto agli elenchi a discesa, entrambi i progetti utilizzano ancora una barra degli strumenti per innalzare di livello un elemento che non è realmente un comando.

![Figura B: migliore, ma ancora un anti-pattern della barra di comando](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura B: migliore, ma ancora un anti-pattern della barra di comando

Nell'approccio corretto illustrato nella **Figura C**, l'impostazione è associata a una serie di comandi. Non è stata impostata alcuna impostazione globale ed è sufficiente passare tra quattro comandi. Questa è l'unica situazione in cui i comandi della barra degli strumenti sono accettabili.

![Figura C: uso corretto del modello della barra dei comandi di Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figura C: uso corretto del modello della barra dei comandi di Visual Studio

### <a name="control-anti-patterns"></a>Controllare gli anti-pattern
 Alcuni anti-modelli sono semplicemente un utilizzo errato o la presentazione di un controllo o di un gruppo di controlli.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sottostruttura utilizzata come etichetta di gruppo, non come collegamento ipertestuale
 Il testo della sottostruttura deve essere usato solo per i collegamenti ipertestuali.

 **Non valido**\
 ![Il testo sottolineato che non è un collegamento ipertestuale è un anti-pattern di Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Il testo sottolineato che non è un collegamento ipertestuale è un anti-pattern di Visual Studio.

 **Buona**\
 ![Con stile corretto, il testo non collegamento ipertestuale viene visualizzato senza ornamento nel tipo di carattere ambiente.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Con stile corretto, il testo non collegamento ipertestuale viene visualizzato senza ornamento nel tipo di carattere ambiente.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Quando si fa clic su una casella di controllo, viene visualizzata una finestra di dialogo popup
 Facendo clic sulla casella di controllo "Abilita Desktop remoto per tutti i ruoli" nella procedura guidata "pubblica applicazione Azure Windows" viene visualizzata immediatamente una finestra di dialogo popup, un anti-modello di Visual Studio. Inoltre, il campo casella di controllo non riempie una casella di controllo dopo essere stato selezionato, un altro anti-pattern di interazione.

 ![La visualizzazione di una finestra di dialogo dopo aver fatto clic su una casella di controllo è un anti-pattern di Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />La visualizzazione di una finestra di dialogo dopo aver fatto clic su una casella di controllo è un anti-pattern di Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Collegamenti ipertestuali per anti-pattern
 L'esempio seguente contiene due anti-pattern:

1. Il primo piano che diventa rosso al passaggio del mouse indica che non viene utilizzato il colore condiviso corretto dal servizio del tipo di carattere.

2. "Ulteriori informazioni" non è il testo appropriato per un collegamento a un argomento concettuale. L'obiettivo dell'utente non è di saperne di più, è comprendere le ramificazioni della loro scelta.

   ![Ignorando il servizio colori e utilizzando "ulteriori informazioni" per i collegamenti ipertestuali si trovano anti-modelli di Visual Studio.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorando il servizio colori e utilizzando "ulteriori informazioni" per i collegamenti ipertestuali si trovano anti-modelli di Visual Studio.

**Soluzione migliore:** Porre la domanda richiesta dall'utente facendo clic sul collegamento. Ad esempio:

- Come funzionano i servizi di Microsoft Azure?

- Quando è necessario un progetto di servizi mobili di Windows Azure?

#### <a name="using-click-here-for-links"></a>Uso di "fare clic qui" per i collegamenti
 I collegamenti ipertestuali devono essere autodescrittivi. Si tratta di un anti-modello da usare "fare clic qui" o qualsiasi variante simile.

 Non **valido:** "Fare clic qui per istruzioni su come creare un nuovo progetto".

 **Valido:** "Ricerca per categorie creare un nuovo progetto?"
