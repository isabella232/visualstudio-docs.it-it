---
title: Pattern di controllo comuni per Visual Studio Documenti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698705"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modelli dei controlli comuni per Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Controlli comuni

### <a name="overview"></a>Panoramica
I controlli comuni costituiscono la maggior parte dell'interfaccia utente in Visual Studio.Common controls make up the majority of the user interface in Visual Studio. I controlli più comuni utilizzati nell'interfaccia di Visual Studio devono seguire le linee guida per [l'interazione](/windows/desktop/uxguide/controls)con Windows Desktop . Questo argomento è specifico di Visual Studio e illustra situazioni speciali o dettagli che aumentano le linee guida di Windows.This topic is specific to Visual Studio and covers special situations or details that augment those Windows guidelines.

#### <a name="common-controls-in-this-topic"></a>Controlli comuni in questo argomentoCommon controls in this topic

- [Barre di scorrimento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Caselle combinate ed elenchi a discesa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Pulsanti](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Cornici di gruppo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Visualizzazioni albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Stile di visualizzazione
La prima cosa da considerare quando si applicano stili ai controlli è se i controlli verranno usati nell'interfaccia utente a tema. I controlli nell'interfaccia utente standard sono un'interfaccia utente non a tema e devono seguire lo stile normale del desktop di [Windows,](/windows/desktop/uxguide/controls)ovvero non sono basati su modelli e devono essere visualizzati nell'aspetto predefinito del controllo.

- Finestre di **dialogo standard (utilità):** non a tema. Non ri-modello. Utilizzare le impostazioni predefinite dello stile di controllo di base.

- **Finestre degli strumenti, editor di documenti, aree di progettazione e finestre di dialogo a tema:Tool windows, document editors, design surfaces and themed dialogs:** Utilizzare l'aspetto a tema specializzato utilizzando il servizio colore.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Barre di scorrimento
 Le barre di scorrimento devono seguire i modelli di [interazione comuni per](/windows/desktop/Controls/about-scroll-bars) le barre di scorrimento di Windows, a meno che non siano aumentate con informazioni sul contenuto, ad esempio nell'editor di codice.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Campi di immissione
 Per un comportamento di interazione tipico, seguire le linee guida di [Windows Desktop per le caselle di testo](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Stile di visualizzazione

- I campi di input non devono avere uno stile nelle finestre di dialogo dell'utilità. Utilizzare lo stile di base intrinseco al controllo.

- I campi di input a tema devono essere utilizzati solo nelle finestre di dialogo a tema e nelle finestre degli strumenti.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- I campi di sola lettura avranno uno sfondo grigio (disabilitato) ma il primo piano predefinito (attivo).

- I campi ** \<** obbligatori devono avere>obbligatori come filigrane al loro interno. Non si dovrebbe cambiare il colore dello sfondo tranne in rare situazioni.

- Convalida degli errori: vedere [Notifiche e stato di avanzamento per Visual StudioError](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) validation: See Notifications and Progress for Visual Studio

- I campi di input devono essere dimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un percorso. La lunghezza potrebbe essere un'indicazione per l'utente delle limitazioni relative al numero di caratteri consentiti nel campo.

     ![Lunghezza del campo di input non corretta: è improbabile che il nome sia così lungo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Lunghezza del campo di input non corretta: è improbabile che il nome sia così lungo.

     ![Correggere la lunghezza del campo di input: il campo di input ha una larghezza ragionevole per il contenuto previsto.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Correggere la lunghezza del campo di input: il campo di input ha una larghezza ragionevole per il contenuto previsto.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Caselle combinate ed elenchi a discesa
Per un comportamento di interazione tipico, seguire le linee guida di [Windows Desktop per gli elenchi a discesa e le caselle combinate.](/windows/desktop/uxguide/ctrl-drop)

#### <a name="visual-style"></a>Stile di visualizzazione

- Nelle finestre di dialogo dell'utilità, non ri-modello il controllo. Utilizzare lo stile di base intrinseco al controllo.

- Nell'interfaccia utente a tema, le caselle combinate e i menu a discesa seguono i tema standard per i controlli.

#### <a name="layout"></a>Layout
Le caselle combinate e i menu a discesa devono essere ridimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un percorso.

![Non corretto: la larghezza del menu a discesa è troppo lunga per il contenuto che verrà visualizzato.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Non corretto: la larghezza del menu a discesa è troppo lunga per il contenuto che verrà visualizzato.

![Corretto: il menu a discesa è dimensionato per consentire la crescita della traduzione, ma non inutilmente lungo.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Corretto: il menu a discesa è dimensionato per consentire la crescita della traduzione, ma non inutilmente lungo.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Caselle
Per un comportamento di interazione tipico, seguire le linee guida di Windows Desktop per le [caselle](/windows/desktop/uxguide/ctrl-check-boxes)di controllo .

#### <a name="visual-style"></a>Stile di visualizzazione

- Nelle finestre di dialogo dell'utilità, non ri-modello il controllo. Utilizzare lo stile di base intrinseco al controllo.

- Nell'interfaccia utente a tema, le caselle di controllo seguono i tipi standard per i controlli.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- L'interazione con una casella di controllo non deve mai aprire una finestra di dialogo o passare a un'altra area.

- Allineare le caselle di controllo alla linea di base della prima riga di testo.

     ![Non corretto: la casella di controllo è centrata sul testo.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Non corretto: la casella di controllo è centrata sul testo.

     ![Correggere: la casella di controllo è allineata con la prima riga del testo.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correggere: la casella di controllo è allineata con la prima riga del testo.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Pulsanti
Per un comportamento di interazione tipico, seguire le linee guida di [Windows Desktop per i pulsanti di opzione](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Stile di visualizzazione
Nelle finestre di dialogo dell'utilità, non applicare stili ai pulsanti di opzione. Utilizzare lo stile di base intrinseco al controllo.

#### <a name="specialized-interactions"></a>Interazioni specializzate
Non è necessario utilizzare una cornice di gruppo per racchiudere le scelte radio, a meno che non sia necessario mantenere la distinzione di gruppo in un layout stretto.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Cornici di gruppo
Per un comportamento di interazione tipico, seguire le linee guida di [Windows Desktop per i frame](/windows/desktop/uxguide/ctrl-group-boxes)di gruppo .

#### <a name="visual-style"></a>Stile di visualizzazione
Nelle finestre di dialogo dell'utilità, non applicare stili alle cornici di gruppo. Utilizzare lo stile di base intrinseco al controllo.

#### <a name="layout"></a>Layout

- Non è necessario utilizzare una cornice di gruppo per racchiudere le scelte radio, a meno che non sia necessario mantenere la distinzione di gruppo in un layout stretto.

- Non utilizzare mai una cornice di gruppo per un singolo controllo.

- A volte è accettabile usare una regola orizzontale anziché un contenitore di frame di gruppo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Controlli di testo

### <a name="static-text-fields"></a>Campi di testo statico

Un campo di testo statico presenta informazioni di sola lettura e non può essere selezionato dall'utente. Evitare di utilizzarlo per qualsiasi testo che l'utente potrebbe voler copiare negli Appunti. Tuttavia, il testo statico di sola lettura può cambiare per riflettere una modifica dello stato. Nell'esempio seguente, il testo statico Nome output nel gruppo Informazioni viene modificato per riflettere le modifiche apportate alla casella di testo Spazio dei nomi radice sopra di esso.

Esistono due modi per visualizzare informazioni di testo statico.

Il testo statico può trovarsi da solo in una finestra di dialogo senza alcun contenimento quando non vi è alcun conflitto di raggruppamento. Decidere se le linee extra di una scatola sono davvero necessari. Un esempio è la visualizzazione di un percorso di directory in una sezione creata da una linea di gruppo, come illustrato di seguito:

![Informazioni di testo statico nei controlli di testoStatic text info in text controls](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "Visualizzazione StaticText.png")<br />Informazioni di testo statico nei controlli di testoStatic text info in text controls

In una finestra di dialogo in cui sono presenti altre aree raggruppate e il contenimento delle informazioni consente di migliorare la leggibilità e quando una sezione può essere nascosta o visualizzata (come nel riquadro descrizione della **finestra Proprietà)** o si desidera essere coerente con un'interfaccia utente simile, inserire il testo statico all'interno di una casella. Questa casella di gruppo deve essere `ButtonShadow`una singola regola e colorata con:

![Testo statico nella finestra Proprietà](../../extensibility/ux-guidelines/media/PropertiesWindow.png "ProprietàWindow.png")<br />Testo statico nella finestra Proprietà

### <a name="read-only-text-box"></a>Casella di testo di sola lettura

Ciò consente all'utente di selezionare il testo all'interno del campo, ma non di modificarlo. Queste caselle di testo sono delimitate dal solito `ButtonShadow` scalpello 3D con un riempimento.

Una casella di testo può diventare attiva (modificabile) quando un utente modifica un controllo associato, ad esempio selezionando/deselezionando una casella di controllo o selezionando/deselezionando un pulsante di opzione. Ad esempio, nella pagina **Opzioni strumenti &gt; ** illustrata di seguito, la casella di testo Pagina **iniziale** diventa attiva quando la casella di controllo **Usa predefinito** è deselezionata.

![Casella di testo di sola lettura che mostra gli stati inattivo e attivo](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Casella di testo di sola lettura che mostra gli stati inattivo e attivo

### <a name="using-text-in-dialogs"></a>Uso del testo nelle finestre di dialogo

Linee guida chiave per il testo nelle finestre di dialogo:Key guidelines for text in dialogs:

- Le etichette per le caselle di testo, le caselle di riepilogo e le cornici nelle finestre di dialogo senza tema iniziano con un verbo, hanno una maiuscola iniziale solo sulla prima parola e terminano con i due punti.

    > I controlli di testo nelle finestre di dialogo a tema seguono le [linee guida dell'esperienza utente desktop](/windows/desktop/uxguide/top-violations) di Windows e non accettano la punteggiatura finale, ad eccezione dei punti interrogativi nei collegamenti della Guida.

- Le etichette per le caselle di controllo e i pulsanti di opzione iniziano con un verbo, una maiuscola iniziale solo sulla prima parola e non hanno punteggiatura finale.

- Le etichette per pulsanti, menu, voci di menu e schede hanno lettere maiuscole iniziali su ogni parola (maiuscole/minuscole del titolo).

- La terminologia delle etichette deve essere coerente con etichette simili in altre finestre di dialogo.

- Se possibile, chiedere a un writer/editor di scrivere o approvare il testo prima che venga passato allo sviluppatore per l'implementazione.

- Tutti i controlli devono avere etichette tranne in circostanze particolari in cui la tabulazione è sufficiente.
Utilizzare il testo dell'helper quando appropriato.

### <a name="helper-text"></a>Testo di supporto

Incluso nelle finestre di dialogo per aiutare l'utente a comprendere lo scopo della finestra di dialogo o per indicare l'azione da intraprendere. Il testo di supporto deve essere usato solo quando necessario per evitare di ingombrare semplici finestre di dialogo. Le due varianti del testo helper sono dialogo e filigrana.

Seguire le posizioni comuni per il testo di supporto ed essere selettivi nell'introduzione di nuove aree. Gli scenari comuni per il testo helper sono:Common scenarios for helper text are:

- Testo di supporto nelle finestre di dialogo, per fornire ulteriori indicazioni su come interagire con una finestra di dialogo complessa.

- Testo della filigrana in finestre degli strumenti o finestre di dialogo vuote, per spiegare perché non è visibile alcun contenuto.

- Un riquadro di descrizione, come nella parte inferiore della **finestra Proprietà**.

- Testo della filigrana in un editor vuoto, per spiegare l'azione che l'utente deve eseguire per iniziare.

### <a name="dialog-helper-text"></a>Testo di supporto della finestra di dialogo

Una finestra di progettazione dell'esperienza utente può aiutare a determinare quando il testo di supporto è appropriato. La finestra di progettazione può definire la posizione in cui viene visualizzato il testo di supporto e il relativo contenuto generale. L'assistenza utente può scrivere/modificare il testo effettivo.

### <a name="watermarks"></a>Filigrane

Le finestre di dialogo traggono vantaggio da linee guida per la filigrana leggermente diverse. Poiché una finestra di dialogo può apparire occupata con molti elementi dell'interfaccia utente (etichette, testo di suggerimento, `ButtonShadow`pulsanti e altri controlli contenitore con testo), in particolare quando questi vengono visualizzati in nero, le filigrane riperlusgono meglio in grigio scuro (VSColor: ). In genere una filigrana viene visualizzata all'interno di `Window`un controllo come una casella di riepilogo con uno sfondo bianco (VSColor: ).

- Il testo viene visualizzato in `ButtonShadow`grigio scuro (VSColor: ). Tuttavia, se la filigrana viene visualizzata su uno `ButtonFace`sfondo grigio medio o di altro colore (VSColor: `WindowText`) e vi è preoccupazione per la sua leggibilità, andare con testo nero (VSColor: ).

- Le filigrane possono essere centrate o allineate a sinistra. Applicare le regole di progettazione standard quando si prendono decisioni di allineamento. La filigrana non può essere selezionata sullo sfondo.

![Esempio di testo Filigrana](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Esempio di testo Filigrana

### <a name="context-specific-dynamic-text"></a>Testo (dinamico) specifico del contesto

Il testo dinamico può essere usato in due modi in una finestra di dialogo o in un'interfaccia utente non modale: come etichetta dinamica o come contenuto dinamico.

- Etichetta dinamica: un uso comune del testo dinamico è nei pannelli descrittivi che offrono ulteriori informazioni per l'elemento selezionato, ad esempio in una finestra di dialogo che contiene un elenco di elementi e proprietà per gli elementi visualizzati in una griglia a destra. L'etichetta per la griglia delle proprietà può essere dinamica in modo che quando un elemento viene selezionato a sinistra, la griglia a destra mostra le informazioni per l'elemento specifico.

- Testo dinamico: può essere utile nei casi in cui è necessario visualizzare informazioni specifiche e non informazioni generali in questo modo, ma è necessario prestare attenzione a non abusare.

Se si desidera che gli utenti abbiano la possibilità di copiare le informazioni, il testo dinamico deve trovarsi in un campo di testo di sola lettura.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Pulsanti e collegamenti ipertestuali

### <a name="overview"></a>Panoramica
Pulsanti e controlli di collegamento (collegamenti ipertestuali) devono seguire le indicazioni di base di [Windows Desktop sui collegamenti ipertestuali](/windows/desktop/uxguide/ctrl-links) per l'utilizzo, la formulazione, il ridimensionamento e la spaziatura.

### <a name="choosing-between-buttons-and-links"></a>Scelta tra pulsanti e collegamenti
Tradizionalmente, i pulsanti sono stati utilizzati per le azioni e i collegamenti ipertestuali sono stati riservati per la navigazione. Pulsanti possono essere utilizzati in tutti i casi, ma il ruolo dei collegamenti è stato espanso in Visual Studio in modo che i pulsanti e collegamenti sono più intercambiabili in alcune condizioni.

Quando utilizzare i pulsanti di comando:

- Comandi principali

- Visualizzazione delle finestre utilizzate per raccogliere input o effettuare scelte, anche se sono comandi secondari

- Azioni distruttive o irreversibili

- Pulsanti di impegno all'interno di procedure guidate e flussi di pagine

Evitare i pulsanti di comando nelle finestre degli strumenti o se sono necessarie più di due parole per l'etichetta. I collegamenti possono avere etichette più lunghe.

 Quando utilizzare i collegamenti:

- Navigazione in un'altra finestra, documento o pagina Web

- Situazioni che richiedono un'etichetta più lunga o una breve frase per descrivere l'intento dell'azione

- Spazi stretti in cui un pulsante sovraccarica l'interfaccia utente, a condizione che l'azione non sia distruttiva o irreversibile

- De-enfatizzare i comandi secondari in situazioni in cui sono presenti molti comandi

#### <a name="examples"></a>Esempi
![Collegamenti ai comandi utilizzati nella barra informazioni dopo un messaggio di statoCommand links used in the InfoBar following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Collegamenti ai comandi utilizzati nella barra informazioni dopo un messaggio di statoCommand links used in the InfoBar following a status message

![Collegamenti usati nel popup CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Collegamenti usati nel popup CodeLens

![Link utilizzati per i comandi secondari in cui i pulsanti attirerebbero troppa attenzione](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Link utilizzati per i comandi secondari in cui i pulsanti attirerebbero troppa attenzione

### <a name="common-buttons"></a>Pulsanti comuni

#### <a name="text"></a>Testo
Seguire le linee guida per la scrittura nel testo e nella [terminologia dell'interfaccia utente.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="visual-style"></a>Stile di visualizzazione

##### <a name="standard-unthemed"></a>Standard (senza tema)
La maggior parte dei pulsanti in Visual Studio verrà visualizzata nelle finestre di dialogo dell'utilità e non deve essere applicato lo stile. Dovrebbero riflettere l'aspetto standard dei pulsanti come dettato dal sistema operativo.

##### <a name="themed"></a>Tema
In alcuni casi, i pulsanti possono essere utilizzati all'interno di un'interfaccia utente con stili e questi pulsanti devono avere uno stile appropriato. Per informazioni sui controlli a tema, [vedere Finestre di dialogo.](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

### <a name="special-buttons"></a>Pulsanti speciali

#### <a name="browse-buttons"></a>Sfoglia... Pulsanti
**[Sfoglia...]** i pulsanti vengono utilizzati nelle griglie, nelle finestre di dialogo e nelle finestre degli strumenti e in altri elementi dell'interfaccia utente non modali. Visualizzano una selezione che assiste l'utente nella compilazione di un valore in un controllo. Ci sono due varianti di questo pulsante, lungo e corto.

![Il lungo pulsante [Sfoglia...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Il lungo pulsante [Sfoglia...]

![Il pulsante breve [...] solo con i coni con i solchi](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Il pulsante breve [...] solo con i coni con i solchi

Quando usare il pulsante breve solo con i coni ellissi:

- Se è presente più di un lungo pulsante **[Sfoglia...]** in una finestra di dialogo, ad esempio quando diversi campi consentono l'esplorazione. Utilizzare il pulsante breve **[...]** per ciascuno per evitare i tasti di scelta confusione creati da questa situazione** (&Sfoglia** e **B&righe** nella stessa finestra di dialogo).

- In una finestra di dialogo stretta, o quando non c'è un posto ragionevole per mettere il pulsante lungo.

- Se il pulsante verrà visualizzato in un controllo griglia.

Linee guida per l'utilizzo del pulsante:

- Non usare un tasto di scelta. Per accedervi utilizzando la tastiera, l'utente deve premere TAB dal controllo adiacente. Assicurarsi che l'ordine di tabulazione sia tale che qualsiasi pulsante Sfoglia cada immediatamente dopo il campo che verrà compilato. Non utilizzare mai un punteggio di sottolineatura al di sotto del primo punto.

- Impostare la proprietà Nome Microsoft Active Accessibility (MSAA) **su** **Sfoglia...** (inclusi i puntini di sospensione) in modo che le utilità per la lettura dello schermo la leggano come "Sfoglia" e non come "punto-punto-punto" o "periodo-periodo". Per i controlli gestiti, ciò significa impostare il **AccessibleName** proprietà.

- Non usare mai un pulsante con i lipsia **[...]** per qualsiasi elemento tranne un'azione di esplorazione. Ad esempio, se è necessario un pulsante **[Nuovo...]** ma non si dispone di spazio sufficiente per il testo, la finestra di dialogo deve essere riprogettata.

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
![Pulsanti di ridimensionamento [Sfoglia...]: la versione standard è 75x23 pixel, la versione breve è 26x23 pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Ridimensionamento dei pulsanti [Sfoglia...]

![Spaziatura [Sfoglia...] pulsanti: spaziatura tra il controllo correlato e il pulsante Sfoglia standard 7 pixel, spaziatura tra il controllo correlato e il pulsante Sfoglia breve 5 pixel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Spaziatura dei pulsanti [Sfoglia...]

#### <a name="graphical-buttons"></a>Pulsanti grafici
Alcuni pulsanti devono sempre utilizzare un'immagine grafica e non includere mai testo per risparmiare spazio ed evitare problemi di localizzazione. Questi sono spesso utilizzati nelle selezioni campo e in altri elenchi ordinabili.

> [!NOTE]
> Gli utenti devono scheda a questi pulsanti (non ci sono tasti di scelta), in modo da metterli in un ordine ragionevole. Eseguire `name` il mapping della proprietà del pulsante all'azione eseguita in modo che le utilità per la lettura dello schermo interpretino correttamente l'azione del pulsante.

| Funzione | Pulsante |
| --- | --- |
| Add | ![Pulsante grafico "Aggiungi"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Rimuovere | ![Pulsante grafico "Rimuovi"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Aggiungi tutto | ![Pulsante grafico "Aggiungi tutto"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Rimuovi tutto | ![Pulsante grafico "Rimuovi tutto"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Sposta su | ![Pulsante grafico "Sposta su"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Sposta giù | ![Pulsante grafico "Sposta giù"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Delete | ![Pulsante grafico "Elimina"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
Il ridimensionamento dei pulsanti grafici è lo stesso della versione breve del pulsante **[Sfoglia...]** (26x23 pixel):

![Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente che mostra](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente che mostra

### <a name="hyperlinks"></a>Collegamenti ipertestuali
I collegamenti ipertestuali sono adatti per le azioni basate sulla navigazione, ad esempio l'apertura di un argomento della Guida, una finestra di dialogo modale o una procedura guidata. Se un collegamento ipertestuale viene utilizzato per un comando, deve sempre visualizzare una modifica visibile e notevole all'interfaccia utente. In generale, le azioni che eseguono il commit di un'azione (ad esempio Salva, Annulla ed Elimina) vengono comunicate meglio tramite un pulsante.

#### <a name="writing-style"></a>Stile di scrittura
Seguire le indicazioni di Windows Desktop per il [testo dell'interfaccia utente](/windows/desktop/uxguide/text-ui). Non usare la formulazione "Ulteriori informazioni", "Informazioni su", o "Ottieni assistenza per questo". Al contrario, frase testo collegamento Guida in termini di domanda principale risposto dal contenuto della Guida. Ad esempio, "**Come si aggiunge un server a Esplora server?**"

#### <a name="visual-style"></a>Stile di visualizzazione

- I collegamenti ipertestuali devono sempre utilizzare [il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se un collegamento ipertestuale non ha uno stile corretto, lampeggia in rosso quando è attivo o mostra un colore diverso dopo essere stato visitato.

- Non includere sottolineature allo stato di riposo del controllo a meno che il collegamento non sia un frammento di frase all'interno di una frase completa, ad esempio in una filigrana.

- Le sottolineature non devono essere visualizzate al passaggio del mouse. Al contrario, il feedback all'utente che il collegamento è attivo è una leggera modifica del colore e il cursore di collegamento appropriato.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Viste ad albero

Le visualizzazioni ad albero consentono di organizzare elenchi complessi in gruppi padre-figlio. Un utente può espandere o comprimere i gruppi padre per visualizzare o nascondere gli elementi figlio sottostanti. Ogni elemento all'interno di una visualizzazione struttura ad albero può essere selezionato per fornire ulteriori azioni.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Stile di visualizzazione della visualizzazione struttura ad albero

#### <a name="expanders"></a>Espansori
I controlli di visualizzazione ad albero devono essere conformi alla progettazione dell'espansore utilizzata da Windows e Visual Studio.Tree view controls should conform to the expander design used by Windows and Visual Studio. Ogni nodo utilizza un controllo di espansione per rivelare o nascondere gli elementi sottostanti. L'utilizzo di un controllo expander garantisce la coerenza per gli utenti che potrebbero riscontrare visualizzazioni struttura ad albero diverse all'interno di Windows e Visual Studio.Using an expander control provides consistency for users who might encounter different tree views within Windows and Visual Studio.

![Corretto: stile corretto del nodo della visualizzazione struttura ad albero utilizzando un controllo di espansione](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Corretto: stile corretto del nodo della visualizzazione struttura ad albero utilizzando un controllo di espansione

![Non corretto: stile non corretto del nodo della visualizzazione struttura ad albero](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Non corretto: stile non corretto del nodo della visualizzazione struttura ad albero

#### <a name="selection"></a>Selezione
Quando si seleziona un nodo all'interno della visualizzazione struttura ad albero, l'evidenziazione deve espandersi fino all'intera larghezza del controllo di visualizzazione ad albero. Ciò consente agli utenti di identificare chiaramente l'elemento selezionato. I colori di selezione devono riflettere il tema di Visual Studio corrente.

![Corretto: l'evidenziazione del nodo selezionato si adatta all'intera larghezza del controllo di visualizzazione ad albero.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Corretto: l'evidenziazione del nodo selezionato si adatta all'intera larghezza del controllo di visualizzazione ad albero.

![Non corretto: l'evidenziazione del nodo selezionato non corrisponde all'intera larghezza del controllo di visualizzazione ad albero.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Non corretto: l'evidenziazione del nodo selezionato non corrisponde all'intera larghezza del controllo di visualizzazione ad albero.

#### <a name="icons"></a>Icone
Le icone devono essere utilizzate nei controlli della visualizzazione struttura ad albero solo se consentono di identificare visivamente le differenze tra gli elementi. In generale, le icone devono essere utilizzate solo in elenchi eterogenei in cui le icone contengono informazioni per differenziare i tipi di elementi. In un elenco omogeneo l'uso delle icone può essere spesso visto come rumore e deve essere evitato. In tal caso l'icona del gruppo (padre) può trasmettere il tipo di elementi al suo interno. L'eccezione a questa regola sarebbe se l'icona è dinamica e viene utilizzata per indicare lo stato.

#### <a name="scroll-bars"></a>Barre di scorrimento
Le barre di scorrimento devono essere sempre nascoste se il contenuto si adatta al controllo di visualizzazione ad albero. È accettabile che le barre di scorrimento siano nascoste o semitrasparenti in una finestra scorrevole e vengano visualizzate quando la finestra contenente la visualizzazione struttura ad albero ha lo stato attivo o al passaggio del mouse sulla visualizzazione struttura ad albero.

![Vengono visualizzate entrambe le barre di scorrimento verticale e orizzontale perché il contenuto ha superato i limiti del controllo di visualizzazione ad albero.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Vengono visualizzate entrambe le barre di scorrimento verticale e orizzontale perché il contenuto ha superato i limiti del controllo di visualizzazione ad albero.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interazioni con la visualizzazione ad albero

#### <a name="context-menus"></a>Menu di scelta rapida
Un nodo della vista ad albero può visualizzare le opzioni di sottomenu in un menu di scelta rapida. In genere, ciò si verifica quando un utente ha fatto clic con il pulsante destro del mouse su un elemento o ha premuto il tasto Menu su una tastiera Windows con l'elemento selezionato. È importante che il nodo acquisisca lo stato attivo e sia selezionato. Ciò consente all'utente di identificare l'elemento a cui appartiene il sottomenu.

![L'elemento che genera il menu di scelta rapida ottiene lo stato attivo per notificare all'utente quale elemento è stato selezionato.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />L'elemento che genera il menu di scelta rapida ottiene lo stato attivo per notificare all'utente quale elemento è stato selezionato.

#### <a name="keyboard"></a>Tastiera
La visualizzazione struttura ad albero deve fornire la possibilità di selezionare elementi ed espandere/comprimere i nodi utilizzando la tastiera. Ciò garantisce che la navigazione soddisfi i nostri requisiti di accessibilità.

##### <a name="tree-view-control"></a>Controllo struttura ad albero
I controlli albero di Visual Studio devono seguire la navigazione da tastiera comune:Visual Studio tree controls should follow common keyboard navigation:

- **Freccia su:** Selezionare gli elementi spostandolo verso l'alto nell'albero

- **Freccia giù:** Selezionare gli elementi spostandosi lungo l'albero

- **Freccia destra:** Espandere un nodo nell'albero

- **Freccia SINISTRA:** Comprimere un nodo nell'albero

- **Tasto Invio:** Avviare, caricare, eseguire l'elemento selezionato

##### <a name="trid-tree-view-and-grid-view"></a>Trid (visualizzazione albero e visualizzazione griglia)
Un controllo trid è un controllo complesso che contiene una visualizzazione struttura ad albero all'interno di una griglia. L'espansione, la compressione e la navigazione nell'albero devono rispettare gli stessi comandi da tastiera di una visualizzazione albero, con le seguenti aggiunte:

- **Freccia destra:** Espandere un nodo. Dopo aver espanso, il nodo deve continuare a spostarsi alla colonna più vicina a destra. La navigazione dovrebbe interrompersi alla fine della riga.

- **Scheda:** Consente di passare alla cella più vicina a destra.  Alla fine della riga, la navigazione continua alla riga successiva.

- **Maiusc e Tab:** Passa alla cella più vicina a sinistra.  All'inizio della riga, lo spostamento continua fino alla cella più a destra nella riga precedente.

![Controllo trid in Visual StudioA trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Controllo trid in Visual StudioA trid control in Visual Studio
