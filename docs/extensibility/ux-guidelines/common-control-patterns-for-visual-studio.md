---
title: Pattern di controllo comuni per Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33becb67adb0453adef111ca2c8fb0d2b2e6edfc
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890977"
---
# <a name="common-control-patterns-for-visual-studio"></a>Pattern di controllo comuni per Visual Studio
## <a name="BKMK_CommonControls"></a> Controlli comuni

### <a name="overview"></a>Panoramica
Controlli comuni costituiscono la maggior parte dell'interfaccia utente in Visual Studio. Controlli più comuni usati nell'interfaccia di Visual Studio devono seguire le [linee guida per l'interazione di Desktop Windows](/windows/desktop/uxguide/controls). In questo argomento è specifico di Visual Studio e descrive i casi speciali o i dettagli che aumentano le linee guida di Windows.

#### <a name="common-controls-in-this-topic"></a>Controlli comuni in questo argomento

- [Barre di scorrimento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Elenchi a discesa e caselle combinate](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Pulsanti di opzione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Fotogrammi di gruppo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [I collegamenti ipertestuali e pulsanti](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Visualizzazioni dell'albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Stile di visualizzazione
La prima cosa da prendere in considerazione quando lo stile di controlli è se i controlli verranno utilizzati nell'interfaccia utente con temi. Controlli dell'interfaccia utente standard sono a tema dell'interfaccia utente e deve seguire [lo stile Desktop di Windows normale](/windows/desktop/uxguide/controls), vale a dire che non sono basate su modelli r e verrà visualizzato il relativo aspetto del controllo predefinito.

- **Le finestre di dialogo standard (utilità):** non a tema. Non reimpostare come modelli. Usare i valori predefiniti di stile di controllo di base.

- **Finestre degli strumenti, editor di documenti, le aree di progettazione e finestre di dialogo con tema:** Usare specializzato aspetto a tema usando il servizio di colore.

### <a name="BKMK_Scrollbars"></a> Barre di scorrimento
 Le barre di scorrimento devono seguire [barre di scorrimento comuni modelli di interazione per Windows](/windows/desktop/Controls/about-scroll-bars) a meno che non si è ampliate con informazioni sul contenuto, come illustrato nell'editor del codice.

### <a name="BKMK_InputFields"></a> Campi di input
 Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per le caselle di testo](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Stile di visualizzazione

- I campi di input non devono essere applicato uno stile nelle finestre di dialogo utilità. Utilizzare lo stile di base intrinseco per il controllo.

- I campi di input con tema devono essere utilizzati solo nelle finestre di dialogo con tema e finestre degli strumenti.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- I campi di sola lettura avrà uno sfondo grigio (disattivato) ma in primo piano predefinito (attivo).

- Necessari i campi devono avere  **\<necessarie >** come filigrane al loro interno. Non è necessario modificare il colore di sfondo tranne in rare situazioni.

- Convalida degli errori: Vedere [notifiche e avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- I campi di input devono essere ridimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza di un campo lungo, ad esempio un percorso. Lunghezza potrebbe essere un'indicazione all'utente di limitazioni per quanto riguarda il numero di caratteri è consentito nel campo.

     ![Lunghezza del campo di input non corretto: è improbabile che il nome sarà questa lunghezza. ](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Lunghezza del campo di input non corretto: è improbabile che il nome sarà questa lunghezza.

     ![Correggere la lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto. ](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Correggere la lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto.

### <a name="BKMK_ComboBoxesAndDropDowns"></a> Elenchi a discesa e caselle combinate
Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per elenchi a discesa e caselle combinate](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Stile di visualizzazione

- Nelle finestre di dialogo utilità, non reimpostare come modelli del controllo. Utilizzare lo stile di base intrinseco per il controllo.

- Nell'interfaccia utente con temi, elenchi a discesa e caselle combinate seguono i temi standard per i controlli.

#### <a name="layout"></a>Layout
Elenchi a discesa e caselle combinate deve essere ridimensionate per adattarla al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza di un campo lungo, ad esempio un percorso.

![Corretto: la larghezza dell'elenco a discesa è troppo lunga per il contenuto che verrà visualizzato. ](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Corretto: la larghezza dell'elenco a discesa è troppo lunga per il contenuto che verrà visualizzato.

![Corretto: l'elenco a discesa viene ridimensionato per consentire la crescita di traduzione, ma non eccessivamente lunghe. ](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Corretto: l'elenco a discesa viene ridimensionato per consentire la crescita di traduzione, ma non eccessivamente lunghe.

### <a name="BKMK_CheckBoxes"></a> Caselle di controllo
Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per le caselle di controllo](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Stile di visualizzazione

- Nelle finestre di dialogo utilità, non reimpostare come modelli del controllo. Utilizzare lo stile di base intrinseco per il controllo.

- Nell'interfaccia utente di eventuali temi delle caselle di controllo seguono i temi standard per i controlli.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- L'interazione con una casella di controllo non deve mai visualizzata una finestra di dialogo o passare a un'altra area.

- Allineare le caselle di controllo con la linea di base della prima riga del testo.

     ![Corretto: la casella di controllo coincide con il testo. ](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Corretto: la casella di controllo coincide con il testo.

     ![Corretto: la casella di controllo è allineata con la prima riga del testo. ](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Corretto: la casella di controllo è allineata con la prima riga del testo.

### <a name="BKMK_RadioButtons"></a> Pulsanti di opzione
Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per i pulsanti di opzione](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Stile di visualizzazione
Nelle finestre di dialogo utilità, eseguire operazioni non pulsanti di opzione di stile. Utilizzare lo stile di base intrinseco per il controllo.

#### <a name="specialized-interactions"></a>Interazioni specializzate
Non è necessario usare un frame di gruppo per racchiudere le opzioni di radio, a meno che non è necessario mantenere la distinzione di gruppo in un layout di una stretta.

### <a name="BKMK_GroupFrames"></a> Fotogrammi di gruppo
Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per i frame gruppo](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Stile di visualizzazione
Nelle finestre di dialogo utilità, non applicare lo stile frame di gruppo. Utilizzare lo stile di base intrinseco per il controllo.

#### <a name="layout"></a>Layout

- Non è necessario usare un frame di gruppo per racchiudere le opzioni di radio, a meno che non è necessario mantenere la distinzione di gruppo in un layout di una stretta.

- Non utilizzare mai una cornice di gruppo per un singolo controllo.

- Talvolta è accettabile usare un righello orizzontale invece di un contenitore di frame di gruppo.

## <a name="BKMK_TextControls"></a> Controlli testo

### <a name="static-text-fields"></a>Campi di testo statico

Un campo di testo statico vengono presentate le informazioni di sola lettura e non può essere selezionato dall'utente. Evitare di utilizzarla per qualsiasi utente potrebbe scegliere di copiare negli Appunti il testo. Testo statico di sola lettura possa tuttavia modificare in modo da riflettere una modifica nello stato. Nell'esempio seguente, il testo statico nome Output sotto le modifiche di gruppo di informazioni in modo da riflettere le modifiche apportate alla casella di testo radice Namespace sopra di esso.

Esistono due modi per visualizzare le informazioni di testo statico.

Testo statico può essere su un proprio in una finestra di dialogo senza eventuali contenimento quando non siano presenti conflitti di raggruppamento. Decidere se le righe aggiuntive di una casella sono davvero necessarie. Un esempio è la visualizzazione di un percorso di directory in una sezione creato da una riga di gruppo, come illustrato di seguito:

![Le informazioni di testo statico in controlli di testo](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informazioni di testo statico in controlli testo

In una finestra di dialogo in cui esistono altre aree raggruppate e contenimento delle informazioni consente di migliorare la leggibilità, e quando una sezione può essere nascosta o visualizzata (come nel **finestra proprietà** riquadro Descrizione) o si desidera siano coerenti con l'interfaccia utente simile, Inserire il testo statico in una casella. Questa casella di gruppo deve essere una singola regola e colorati con la `ButtonShadow`:

![Testo statico nella finestra proprietà](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Testo statico nella finestra proprietà

### <a name="read-only-text-box"></a>Casella di testo di sola lettura

Ciò consente all'utente di selezionare il testo all'interno del campo, ma non modificarlo. Queste caselle di testo vengono delimitate dal consueto Scalpello 3D con una `ButtonShadow` riempimento.

Una casella di testo può diventare attiva (modificabile) quando un utente modifica un controllo associato, ad esempio una casella di controllo di selezione/deselezione o la selezione/deselezione di un pulsante di opzione. Ad esempio, nel **strumenti &gt; opzioni** pagina mostrata di seguito, il **Home Page** casella di testo diventa attivo quando la **utilizza impostazioni predefinite** casella di controllo è deselezionata.

![Casella di testo di sola lettura, che mostra gli stati attivi e inattivi](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Casella di testo di sola lettura, che mostra gli stati attivi e inattivi

### <a name="using-text-in-dialogs"></a>Utilizzando il testo nelle finestre di dialogo

Linee guida fondamentali per il testo nelle finestre di dialogo:

- Le etichette per le caselle di testo, caselle di riepilogo e i frame nelle finestre di dialogo unthemed iniziano con un verbo, attiva l'iniziale maiuscola solo la prima parola e terminano con un carattere due punti.

    > Seguono i controlli di testo nelle finestre di dialogo con tema [linee guida UX desktop Windows](/windows/desktop/uxguide/top-violations) e non accettano la punteggiatura finale, ad eccezione dei punti interrogativi in collegamenti alla Guida.

- Le etichette per i pulsanti di opzione e caselle di controllo iniziano con un verbo, l'iniziale maiuscola in, solo la prima parola e non avere punteggiatura finale.

- Etichette per i pulsanti, menu, le voci di menu e le schede hanno lettere maiuscole iniziali su ogni parola (iniziali maiuscole).

- Terminologia di etichetta deve essere coerente con le etichette simili nelle altre finestre di dialogo.

- Se possibile, avere un agente di scrittura/editor di scrivere o approvare il testo prima di passare allo sviluppatore per l'implementazione.

- Tutti i controlli devono avere etichette tranne in casi speciali in cui la tabulazione è sufficiente.
Usare il testo di supporto quando appropriato.

### <a name="helper-text"></a>Testo di supporto

Incluse nelle finestre di dialogo per consentire all'utente di comprendere scopo della finestra di dialogo o per indicare l'azione da intraprendere. Testo di supporto deve essere usato solo quando è necessario per evitare di sovraccaricare le finestre di dialogo semplice. Le possibili varianti di testo di supporto sono finestra di dialogo e filigrana.

Seguire percorsi comuni di testo di supporto e in modo selettivo nell'introduzione di nuove aree. Scenari comuni per il testo di supporto sono:

- Testo di supporto nelle finestre di dialogo, per offrire direzione aggiuntive su come interagire con una finestra di dialogo complessa.

- Testo della filigrana in finestre degli strumenti vuoto o le finestre di dialogo per spiegare il motivo per cui non è contenuto visibile.

- Un riquadro Descrizione, come in fondo il **finestra proprietà**.

- Il testo della filigrana in un editor vuoto, per illustrare l'azione che l'utente deve intraprendere per iniziare.

### <a name="dialog-helper-text"></a>Testo di supporto della finestra di dialogo

Una finestra di progettazione di esperienze utente può aiutare a determinare quando il testo di supporto è appropriato. La finestra di progettazione è possibile definire in cui viene visualizzato testo di supporto, nonché il relativo contenuto generale. Documentazione per gli utenti possa scrittura/modifica il testo effettivo.

### <a name="watermarks"></a>Filigrane

Finestre di dialogo di trarre vantaggio da linee guida per la filigrana leggermente diversa. Poiché una finestra di dialogo può apparire occupato con molti elementi dell'interfaccia utente (etichette, testo di suggerimento, pulsanti e altri controlli contenitore con testo), in particolare quando questi vengono visualizzati in nero, filigrane evidenti in grigio scuro (VSColor: `ButtonShadow`). In genere una filigrana viene visualizzato all'interno di un controllo, ad esempio una casella di riepilogo con uno sfondo bianco (VSColor: `Window`).

- Il testo viene visualizzato in grigio scuro (VSColor: `ButtonShadow`). Tuttavia, se viene visualizzata la filigrana in un grigio medio o altri colori (VSColor: `ButtonFace`) in background ed è presente riguardano sulla leggibilità, passare con testo nero (VSColor: `WindowText`).

- Le filigrane possono essere centrate o allineamento a sinistra. Applicare le regole di progettazione standard quando si effettuano le decisioni di allineamento. La filigrana non è possibile selezionare in background.

![Esempio di testo della filigrana](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Esempio di testo della filigrana

### <a name="context-specific-dynamic-text"></a>Testo (dinamico) specifici del contesto

Testo dinamico può essere usato da uno dei due modi in una finestra di dialogo o non modale dell'interfaccia utente: come un'etichetta dinamica o contenuto dinamico.

- Etichetta dinamica: è un uso comune del testo dinamico nei pannelli descrittivi che offrono informazioni aggiuntive per l'elemento selezionato, ad esempio in una finestra di dialogo che contiene un elenco di elementi e proprietà per gli elementi visualizzati in una griglia a destra. L'etichetta per la griglia delle proprietà può essere dinamico, in modo che quando viene selezionato un elemento a sinistra, nella griglia a destra vengono visualizzate le informazioni per quell'elemento specifico.

- Testo dinamico: può essere molto utile nei casi in cui è necessario visualizzare informazioni specifiche e informazioni generali non in questo modo, ma dovrebbe prestare attenzione a non abusare.

Se si desidera che gli utenti hanno la possibilità di copiare le informazioni, deve essere testo dinamico in un campo di testo di sola lettura.

## <a name="BKMK_ButtonsAndHyperlinks"></a> I collegamenti ipertestuali e pulsanti

### <a name="overview"></a>Panoramica
I controlli di pulsanti e collegamento (i collegamenti ipertestuali) devono seguire [linee guida di Windows Desktop base sui collegamenti ipertestuali](/windows/desktop/uxguide/ctrl-links) per l'utilizzo, formulazione, ridimensionamento e la spaziatura.

### <a name="choosing-between-buttons-and-links"></a>Scelta tra i pulsanti e collegamenti
Tradizionalmente, i pulsanti sono stati utilizzati per le azioni e i collegamenti ipertestuali sono stati riservati per la navigazione. Pulsanti possono essere usati in tutti i casi, ma il ruolo dei collegamenti è stata estesa in Visual Studio in modo che i pulsanti e i collegamenti sono più intercambiabili in alcune condizioni.

Quando utilizzare i pulsanti di comando:

- Comandi principali

- Attivazione di windows usato per raccogliere l'input o scelte, anche se sono comandi secondari

- Azioni distruttive o irreversibili

- Pulsanti di impegno all'interno di procedure guidate e flussi di pagina

Evitare di pulsanti di comando nelle finestre degli strumenti, oppure se è necessario più di due parole per l'etichetta. I collegamenti possono avere più etichette.

 Quando usare i collegamenti:

- Navigazione verso un'altra finestra, documento o pagina web

- Situazioni che richiedono un'etichetta più lungo o breve frase per descrivere lo scopo dell'azione

- Una stretta spazi in cui un pulsante potrebbe sovraccaricare l'interfaccia utente, condizione che l'azione non distruttive o irreversibili

- Ridimensionando comandi secondari nelle situazioni in cui sono presenti molti comandi

#### <a name="examples"></a>Esempi
![Comando collegamenti usati nella barra delle informazioni seguendo un messaggio di stato](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Comandi collegamenti usati nella barra delle informazioni seguendo un messaggio di stato

![Collegamenti usati nel popup CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />Collegamenti usati nel popup CodeLens

![Collegamenti usati per i comandi secondari in cui è opportuno considerare i pulsanti troppa attenzione](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Collegamenti usati per i comandi secondari in cui è opportuno considerare troppa attenzione pulsanti

### <a name="common-buttons"></a>Pulsanti comuni

#### <a name="text"></a>Text
Seguire le linee guida di scrittura [interfaccia utente di testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Stile di visualizzazione

##### <a name="standard-unthemed"></a>Standard (unthemed)
La maggior parte dei pulsanti in Visual Studio verranno visualizzati nelle finestre di dialogo utilità e non devono essere applicato uno stile. Essi devono riflettere l'aspetto dei pulsanti standard come imposto dal sistema operativo.

##### <a name="themed"></a>Con tema
In alcuni casi, i pulsanti possono essere utilizzati all'interno dell'interfaccia utente con stile e questi pulsanti devono essere applicato uno stile in modo appropriato. Visualizzare [finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) per informazioni sui controlli a tema.

### <a name="special-buttons"></a>Pulsanti speciali

#### <a name="browse-buttons"></a>Sfoglia i pulsanti
**[Sfoglia...]**  i pulsanti vengono utilizzati nelle griglie, le finestre di dialogo e finestre degli strumenti e altri elementi dell'interfaccia utente non modale. Verranno inoltre visualizzati un controllo di selezione che assiste l'utente durante la compilazione di un valore in un controllo. Esistono due varianti di questo pulsante, lungo e corti.

![Il pulsante [Sfoglia...] lungo](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />Il pulsante [Sfoglia...] lungo

![Pulsante con i soli puntini di sospensione breve [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />Pulsante con i soli puntini di sospensione breve [...]

Quando usare il pulsante puntini di sospensione-only breve:

- Se è presente più di un long **[Sfoglia...]**  pulsante in una finestra di dialogo, ad esempio quando diversi campi consentono per l'esplorazione. Usare il breve **[...]**  per ognuno evitare la confusione chiavi di accesso create da questa situazione ( **& esplorare** e **esplo & ra** nella finestra di dialogo stessa).

- In una finestra di dialogo stretto o quando non è possibile utilizzare per inserire il pulsante di tempo ragionevole.

- Se il pulsante verrà visualizzato in un controllo griglia.

Linee guida per il pulsante:

- Non usare una chiave di accesso. Per l'accesso utilizzando la tastiera, l'utente deve scheda dal controllo adiacente. Assicurarsi che l'ordine di tabulazione sia in modo che qualsiasi pulsante rientra immediatamente dopo il campo che è riempire. Non usare mai un carattere di sottolineatura seguito dal primo periodo.

- Microsoft Active Accessibility (MSAA) impostata **Name** proprietà **Sfoglia...**  (tra cui i puntini di sospensione) in modo che schermata verrà letto, come "Sfoglia" e non "punto-punto-punto" o "periodo-punto-punto". Per i controlli gestiti, ciò significa impostazione il **AccessibleName** proprietà.

- Non usare mai i puntini di sospensione **[...]**  pulsante esclusivamente per un'azione di esplorazione. Ad esempio, se è necessario un **[novità]**  pulsante ma non hanno spazio sufficiente per il testo, quindi la finestra di dialogo debba essere riprogettata.

##### <a name="sizing-and-spacing"></a>Ridimensionamento e la spaziatura
![Pulsanti [Sfoglia...] di ridimensionamento: versione standard è 75 x 23 pixel, la versione breve è 26 x 23 pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Ridimensionamento dei pulsanti [Sfoglia...]

![Pulsanti [Sfoglia...] spaziatura: spaziatura tra controllo correlato e standard pixel di 7 sul pulsante Sfoglia, la spaziatura tra controllo correlato e Sfoglia breve pulsante 5 pixel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Spaziatura dei pulsanti [Sfoglia...]

#### <a name="graphical-buttons"></a>Pulsanti con interfaccia grafici
Alcuni pulsanti devono sempre usare un'immagine grafica e testo per liberare spazio ed evitare problemi di localizzazione non includere mai. Questi vengono spesso usati in altri elenchi ordinabili e selezioni di campo.

> [!NOTE]
> Gli utenti devono premere tab per questi pulsanti (non sono presenti chiavi di accesso), quindi, inserirli in un ordine ragionevole. Mappa di `name` proprietà del pulsante per l'azione che richiede in modo che gli screen reader interpretare correttamente l'azione sul pulsante.

| Funzione | Button |
| --- | --- |
| Aggiunta | ![Pulsante grafico "Aggiungi"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Rimuovi | ![Pulsante grafico "Rimuovi"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Aggiungi tutto | ![Pulsante grafico "Aggiungi tutto"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Rimuovi tutto | ![Pulsante grafico "Rimuovi tutto"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Sposta su | ![Pulsante grafico "Sposta su"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Sposta giù | ![Pulsante grafico "Sposta giù"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Eliminare | ![Pulsante grafico "Elimina"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Ridimensionamento e la spaziatura
Definizione delle dimensioni per i pulsanti con interfaccia grafico sono uguale a quella versione breve del **[Sfoglia...]**  pulsante (26 x 23 pixel):

![Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente visualizzato](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente visualizzato

### <a name="hyperlinks"></a>Collegamenti ipertestuali
I collegamenti ipertestuali sono particolarmente adatti per azioni basate sulla navigazione, ad esempio aprendo un argomento della Guida, finestra di dialogo modale o configurazione guidata. Se viene usato un collegamento ipertestuale per un comando, è necessario visualizzare sempre una modifica visibile e notevole all'interfaccia utente. In generale, le azioni che eseguono il commit a un'azione (ad esempio, salvare, Cancel ed eliminare) meglio vengono comunicate tramite un pulsante.

#### <a name="writing-style"></a>Stile di scrittura
Seguire le [linee guida di Windows Desktop per il testo dell'interfaccia utente](/windows/desktop/uxguide/text-ui). Non usare "Informazioni su altre informazioni," "Indicare mi ulteriori su" o "Get help con questo" formulazione. Al contrario, una frase di testo del collegamento della Guida in termini di una risposta dal contenuto della Guida in linea la domanda primario. Ad esempio, "**come aggiungere un server in Esplora Server?** "

#### <a name="visual-style"></a>Stile di visualizzazione

- Utilizzano sempre i collegamenti ipertestuali [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se un collegamento ipertestuale non viene applicato lo stile corretto, fa lampeggiare rosso quando è attivo o Mostra un colore diverso dopo da visitare.

- Non includere il controllo posizionato dello stato, a meno che il collegamento è un frammento di frase all'interno di una frase completa, ad esempio in una filigrana di colore.

- Sottolineature dovrebbero risultare al passaggio del mouse. È invece il feedback all'utente che il collegamento è attivo una modifica del colore leggero e il cursore di collegamento appropriato.

## <a name="BKMK_TreeViews"></a> Visualizzazioni dell'albero

Visualizzazioni dell'albero forniscono un modo per organizzare complessi sono elencati in gruppi padre-figlio. Un utente può espandere o comprimere i gruppi padre e mostrare o nascondere gli elementi figlio sottostanti. È possibile selezionare ogni elemento all'interno di una visualizzazione albero per fornire un'ulteriore azione.

### <a name="BKMK_TreeViewVisualStyle"></a> Stile di visualizzazione albero

#### <a name="expanders"></a>Espansori
Controlli di visualizzazione albero dovrebbero essere conforme alla progettazione dell'espansore utilizzata da Windows e Visual Studio. Ogni nodo Usa un controllo expander per mostrare o nascondere gli elementi sottostanti. Utilizzo di un controllo expander offre coerenza per gli utenti che possono verificarsi visualizzazioni dell'albero diverso all'interno di Windows e Visual Studio.

![Corretto: stile appropriato della visualizzazione struttura ad albero usando un controllo expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Corretto: stile appropriato della visualizzazione struttura ad albero usando un controllo expander

![Non corretta: stile di visualizzazione non corretta della visualizzazione struttura ad albero](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Non corretta: stile di visualizzazione non corretta della visualizzazione struttura ad albero

#### <a name="selection"></a>Selection
Quando si seleziona un nodo all'interno della visualizzazione struttura ad albero, è necessario espandere l'evidenziazione per l'intera larghezza del controllo di visualizzazione albero. Ciò consente agli utenti di identificare chiaramente quale elemento è stato selezionato. Selezione colori devono riflettere il tema di Visual Studio corrente.

![Corretto: evidenziazione del nodo selezionato appropriato per l'intera larghezza del controllo di visualizzazione albero. ](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Corretto: evidenziazione del nodo selezionato appropriato per l'intera larghezza del controllo di visualizzazione albero.

![Non corretta: evidenziazione del nodo selezionato non si adatta l'intera larghezza del controllo di visualizzazione albero. ](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Non corretta: evidenziazione del nodo selezionato non si adatta l'intera larghezza del controllo di visualizzazione albero.

#### <a name="icons"></a>Icone
Le icone devono essere utilizzate solo nei controlli di visualizzazione albero se è aiutare a identificare visivamente le differenze tra gli elementi. In generale, le icone devono essere usate solo in elenchi eterogenei in cui le icone contengono informazioni per distinguere i tipi di elementi. In un elenco omogeneo mediante icone spesso può essere considerata come il rumore e deve essere evitata. In questo caso l'icona di gruppo (padre) può indicare il tipo di elementi in esso contenuti. L'eccezione a questa regola può essere se l'icona è dinamico e viene utilizzato per indicare lo stato.

#### <a name="scroll-bars"></a>Barre di scorrimento
Le barre di scorrimento devono essere sempre nascosto se il contenuto viene adattato all'interno del controllo di visualizzazione albero. È accettabile per le barre di scorrimento per essere nascosta o semi-trasparenti in una finestra scorrevole e vengono visualizzate quando la finestra contenente la visualizzazione struttura ad albero è attiva o al momento del passaggio del mouse della struttura ad albero visualizzare se stesso.

![Entrambe le barre di scorrimento orizzontale e verticale vengono visualizzate perché il contenuto ha superato i limiti del controllo di visualizzazione albero. ](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Entrambe le barre di scorrimento orizzontale e verticale vengono visualizzate perché il contenuto ha superato i limiti del controllo di visualizzazione albero.

### <a name="BKMK_TreeViewInteractions"></a> Interazioni di visualizzazione albero

#### <a name="context-menus"></a>Menu di scelta rapida
Un nodo della visualizzazione struttura ad albero possa visualizzare le opzioni di sottomenu in un menu di scelta rapida. In genere, ciò si verifica quando un utente con pulsante destro del mouse di un elemento o ha premuto il tasto di Menu su una tastiera di Windows con l'elemento selezionato. È importante che il nodo Ottiene lo stato attivo e che sia selezionato. Ciò consente di identificare quale elemento a cui appartiene il sottomenu.

![L'elemento che ha generato il contesto menu riceve lo stato attivo per notificare all'utente quale elemento è stata selezionata. ](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />L'elemento che ha generato il contesto menu riceve lo stato attivo per notificare all'utente quale elemento è stata selezionata.

#### <a name="keyboard"></a>Tastiera
Visualizzazione albero dovrebbe offrono la possibilità di selezionare gli elementi ed Espandi/Comprimi nodi tramite la tastiera. Ciò garantisce che navigazione soddisfi i requisiti di accessibilità.

##### <a name="tree-view-control"></a>Controllo di visualizzazione albero
Controlli dell'albero di Visual Studio devono seguire la navigazione da tastiera comuni:

- **Freccia su:** Selezionare gli elementi spostando l'alto nell'albero

- **Freccia giù:** Selezionare gli elementi spostando verso il basso la struttura ad albero

- **Freccia destra:** Espandere un nodo dell'albero

- **Freccia sinistra:** Comprimere un nodo dell'albero

- **Immettere la chiave:** Avviare, caricare ed eseguire l'elemento selezionato

##### <a name="trid-tree-view-and-grid-view"></a>Albero (visualizzazione struttura ad albero e griglia)
Un controllo albero è un controllo complesso che contiene una visualizzazione struttura ad albero all'interno di una griglia. Espansione e compressione di esplorazione dell'albero deve rispettare gli stessi comandi da tastiera in una visualizzazione ad albero, con le aggiunte seguenti:

- **Freccia destra:** Espandere un nodo. Dopo aver espanso il nodo, deve continuare passando alla colonna più vicina a destra. Navigazione deve essere interrotta alla fine della riga.

- **Scheda:** Consente di passare alla più vicina cella a destra.  Alla fine della riga, navigazione continua alla riga successiva.

- **Maiusc + Tab:** Consente di spostarsi nella cella più vicino a sinistra.  All'inizio della riga, navigazione continua nella cella più a destra nella riga precedente.

![Un controllo albero in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Un controllo albero in Visual Studio