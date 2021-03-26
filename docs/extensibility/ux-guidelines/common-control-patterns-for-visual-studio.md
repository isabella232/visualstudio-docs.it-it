---
title: Pattern di controllo comuni per Visual Studio | Microsoft Docs
description: Informazioni sul modo in cui i controlli comuni di Visual Studio seguono le linee guida per l'interazione con il desktop di Windows e le situazioni speciali che aumentano tali linee
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e55bb5f4473971f99ce04f9e48b7e05ec13f94c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090109"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modelli dei controlli comuni per Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Controlli comuni

### <a name="overview"></a>Panoramica
I controlli comuni costituiscono la maggior parte dell'interfaccia utente in Visual Studio. La maggior parte dei controlli comuni usati nell'interfaccia di Visual Studio deve seguire le [linee guida](/windows/desktop/uxguide/controls)per l'interazione con il desktop di Windows. Questo argomento è specifico di Visual Studio e illustra le situazioni speciali o i dettagli che aumentano le linee guida di Windows.

#### <a name="common-controls-in-this-topic"></a>Controlli comuni in questo argomento

- [Barre di scorrimento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Caselle combinate ed elenchi a discesa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Pulsanti di opzione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Raggruppare i frame](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controlli di testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Visualizzazioni albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Stile visivo
Il primo aspetto da considerare quando i controlli di stile è se i controlli verranno utilizzati nell'interfaccia utente con tema. I controlli nell'interfaccia utente standard sono interfaccia utente senza tema e devono seguire il [normale stile di desktop di Windows](/windows/desktop/uxguide/controls), ovvero non vengono ribasati su modelli e dovrebbero apparire nell'aspetto del controllo predefinito.

- **Finestre di dialogo standard (Utility):** non con tema. Non ricreare il modello. Usare le impostazioni predefinite dello stile del controllo di base.

- **Finestre degli strumenti, editor di documenti, aree di progettazione e finestre di dialogo con tema:** Usare l'aspetto con tema specializzato usando il servizio color.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Barre di scorrimento
 Le barre di scorrimento devono seguire [modelli di interazione comuni per le barre di scorrimento di Windows](/windows/desktop/Controls/about-scroll-bars) a meno che non siano state ampliate con informazioni sul contenuto, come nell'editor di codice.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Campi di input
 Per un comportamento di interazione tipico, seguire le [linee guida per i desktop di Windows per le caselle di testo](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Stile visivo

- Non è possibile applicare uno stile ai campi di input nelle finestre di dialogo dell'utilità. Utilizzare lo stile di base intrinseco al controllo.

- I campi di input con tema devono essere usati solo nelle finestre di dialogo e negli strumenti con tema.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- I campi di sola lettura avranno uno sfondo grigio (disabilitato), ma il primo piano predefinito (attivo).

- I campi obbligatori devono avere **\<Required>** come filigrane al suo interno. Non modificare il colore dello sfondo tranne che in rari casi.

- Convalida degli errori: vedere [notifiche e stato di avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- I campi di input devono essere dimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un percorso. La lunghezza può indicare all'utente le limitazioni relative al numero di caratteri consentiti nel campo.

     ![Lunghezza del campo di input non corretta: è improbabile che il nome sia lungo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Lunghezza del campo di input non corretta: è improbabile che il nome sia lungo.

     ![Corretta lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Corretta lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Caselle combinate ed elenchi a discesa
Per un comportamento di interazione tipico, seguire le [linee guida per i desktop di Windows per elenchi a discesa e caselle combinate](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Stile visivo

- Nelle finestre di dialogo dell'utilità non ricreare il modello del controllo. Utilizzare lo stile di base intrinseco al controllo.

- Nell'interfaccia utente con tema, le caselle combinate e gli elenchi a discesa seguono i temi standard per i controlli.

#### <a name="layout"></a>Layout
Le caselle combinate e gli elenchi a discesa devono essere dimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui sono visualizzati, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un percorso.

![Errato: la larghezza a discesa è troppo lunga per il contenuto che verrà visualizzato.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Errato: la larghezza a discesa è troppo lunga per il contenuto che verrà visualizzato.

![Corretto: l'elenco a discesa è dimensionato in modo da consentire la crescita della conversione, ma non necessariamente lungo.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Corretto: l'elenco a discesa è dimensionato in modo da consentire la crescita della conversione, ma non necessariamente lungo.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Caselle di controllo
Per un comportamento di interazione tipico, seguire le [linee guida per il desktop di Windows per le caselle di controllo](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Stile visivo

- Nelle finestre di dialogo dell'utilità non ricreare il modello del controllo. Utilizzare lo stile di base intrinseco al controllo.

- Nell'interfaccia utente con tema le caselle di controllo seguono i temi standard per i controlli.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- L'interazione con una casella di controllo non deve mai far apparire una finestra di dialogo o passare a un'altra area.

- Allinea le caselle di controllo con la linea di base della prima riga di testo.

     ![Errato: la casella di controllo è centrata sul testo.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Errato: la casella di controllo è centrata sul testo.

     ![Corretto: la casella di controllo è allineata con la prima riga del testo.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Corretto: la casella di controllo è allineata con la prima riga del testo.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Pulsanti di opzione
Per un comportamento di interazione tipico, seguire le [linee guida per il desktop di Windows per i pulsanti di opzione](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Stile visivo
Nelle finestre di dialogo dell'utilità non applicare uno stile ai pulsanti di opzione. Utilizzare lo stile di base intrinseco al controllo.

#### <a name="specialized-interactions"></a>Interazioni specializzate
Non è necessario usare un frame di gruppo per racchiudere le scelte radiofoniche, a meno che non sia necessario mantenere la distinzione tra gruppi in un layout limitato.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Raggruppare i frame
Per un comportamento di interazione tipico, seguire le [linee guida per il desktop di Windows per i frame del gruppo](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Stile visivo
Nelle finestre di dialogo dell'utilità non applicare lo stile ai frame del gruppo. Utilizzare lo stile di base intrinseco al controllo.

#### <a name="layout"></a>Layout

- Non è necessario usare un frame di gruppo per racchiudere le scelte radiofoniche, a meno che non sia necessario mantenere la distinzione tra gruppi in un layout limitato.

- Non usare mai un frame di gruppo per un singolo controllo.

- A volte è accettabile usare una regola orizzontale anziché un contenitore di frame del gruppo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Controlli testo

### <a name="static-text-fields"></a>Campi di testo statici

Un campo di testo statico presenta informazioni di sola lettura e non può essere selezionato dall'utente. Evitare di utilizzarlo per qualsiasi testo che l'utente potrebbe voler copiare negli Appunti. Tuttavia, il testo statico di sola lettura può essere modificato in modo da riflettere una modifica dello stato. Nell'esempio seguente il nome di output testo statico sotto il gruppo informativo viene modificato in modo da riflettere le modifiche apportate alla casella di testo spazio dei nomi radice.

Esistono due modi per visualizzare le informazioni statiche del testo.

Il testo statico può essere autonomo in una finestra di dialogo senza alcuna indipendenza in caso di conflitto di raggruppamento. Decidere se le righe aggiuntive di una casella sono effettivamente necessarie. Un esempio è la visualizzazione di un percorso di directory in una sezione creata da una riga di gruppo, come illustrato di seguito:

![Informazioni sul testo statico nei controlli testo](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informazioni sul testo statico nei controlli testo

In una finestra di dialogo in cui sono presenti altre aree raggruppate e il contenimento delle informazioni consente la leggibilità e quando una sezione può essere nascosta o visualizzata (come nel riquadro Descrizione **finestra Proprietà** ) o si vuole essere coerente con un'interfaccia utente simile, inserire il testo statico all'interno di una casella. Questa casella di gruppo deve essere una singola regola e colorata con `ButtonShadow` :

![Testo statico nell'Finestra Proprietà](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Testo statico nell'Finestra Proprietà

### <a name="read-only-text-box"></a>Casella di testo di sola lettura

Ciò consente all'utente di selezionare il testo all'interno del campo, ma non di modificarlo. Queste caselle di testo sono delimitate dal solito scalpello 3D con un `ButtonShadow` riempimento.

Una casella di testo può diventare attiva (modificabile) quando un utente modifica un controllo associato, ad esempio selezionando/deselezionando una casella di controllo o selezionando o deselezionando un pulsante di opzione. Ad esempio, nella pagina **&gt; Opzioni strumenti** mostrata di seguito, la casella di testo **Home page** diventa attiva quando la casella di controllo **Usa predefinito** è deselezionata.

![Casella di testo di sola lettura, che Mostra gli stati inattivi e attivi](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Casella di testo di sola lettura, che Mostra gli stati inattivi e attivi

### <a name="using-text-in-dialogs"></a>Uso del testo nelle finestre di dialogo

Linee guida principali per il testo nelle finestre di dialogo:

- Le etichette per caselle di testo, caselle di riepilogo e frame nelle finestre di dialogo senza tema iniziano con un verbo, hanno un valore maiuscolo iniziale solo per la prima parola e terminano con i due punti.

    > I controlli testo nelle finestre di dialogo con tema seguono le linee guida sull'esperienza utente di [Windows Desktop](/windows/desktop/uxguide/top-violations) e non accettano la punteggiatura finale, ad eccezione dei punti interrogativi nei collegamenti della guida.

- Le etichette per le caselle di controllo e i pulsanti di opzione iniziano con un verbo, un maiuscolo iniziale solo per la prima parola e senza punteggiatura finale.

- Le etichette per i pulsanti, i menu, le voci di menu e le schede hanno maiuscole iniziali per ogni parola (maiuscole/minuscole).

- La terminologia delle etichette deve essere coerente con etichette simili in altre finestre di dialogo.

- Se possibile, chiedere a un writer o un editor di scrivere o approvare il testo prima di passare allo sviluppatore per l'implementazione.

- Tutti i controlli devono avere etichette tranne che in casi speciali in cui la tabulazione è sufficiente.
Usare il testo Helper quando appropriato.

### <a name="helper-text"></a>Testo Helper

Incluso nelle finestre di dialogo per consentire all'utente di comprendere lo scopo della finestra di dialogo o di indicare l'azione da eseguire. Il testo dell'helper deve essere usato solo quando è necessario per evitare confusione nelle finestre di dialogo semplici. Le due varianti del testo helper sono la finestra di dialogo e la filigrana.

Segui i percorsi comuni per il testo dell'helper ed è selettivo per l'introduzione di nuove aree. Gli scenari comuni per il testo dell'helper sono:

- Testo Helper nelle finestre di dialogo, per fornire indicazioni aggiuntive su come interagire con un dialogo complesso.

- Testo della filigrana nelle finestre degli strumenti vuote o nelle finestre di dialogo per spiegare il motivo per cui non è visibile alcun contenuto.

- Un riquadro Descrizione, ad esempio nella parte inferiore del **finestra Proprietà**.

- Testo della filigrana in un editor vuoto, per spiegare l'azione che l'utente deve intraprendere per iniziare.

### <a name="dialog-helper-text"></a>Testo di supporto della finestra di dialogo

Un progettista dell'esperienza utente può contribuire A determinare quando il testo dell'helper è appropriato. La finestra di progettazione può definire il punto in cui viene visualizzato il testo di supporto e il relativo contenuto generale. L'assistenza utente può scrivere/modificare il testo effettivo.

### <a name="watermarks"></a>Filigrane

I dialoghi traggono vantaggio da linee guida per la filigrana leggermente diverse. Poiché una finestra di dialogo può apparire occupata con molti elementi dell'interfaccia utente (etichette, testo di suggerimento, pulsanti e altri controlli contenitore con testo), in particolare quando vengono visualizzati in nero, le filigrane si distinguono meglio nel grigio scuro (VSColor: `ButtonShadow` ). In genere viene visualizzata una filigrana all'interno di un controllo, ad esempio una casella di riepilogo con uno sfondo bianco (VSColor: `Window` ).

- Il testo viene visualizzato in grigio scuro (VSColor: `ButtonShadow` ). Tuttavia, se la filigrana viene visualizzata in uno sfondo di colore grigio medio o altro (VSColor: `ButtonFace` ) ed è problematica la leggibilità, usare il testo nero (VSColor: `WindowText` ).

- Le filigrane possono essere centrate o scaricate verso sinistra. Applicare le regole di progettazione standard quando si prendono decisioni di allineamento. Non è possibile selezionare la filigrana in background.

![Esempio di testo della filigrana](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Esempio di testo della filigrana

### <a name="context-specific-dynamic-text"></a>Testo specifico del contesto (dinamico)

Il testo dinamico può essere usato in uno dei due modi in una finestra di dialogo o in un'interfaccia utente non modale, ovvero come etichetta dinamica o come contenuto dinamico.

- Etichetta dinamica: un uso comune del testo dinamico è nei pannelli descrittivi che offrono ulteriori informazioni per l'elemento selezionato, ad esempio in una finestra di dialogo che contiene un elenco di elementi e proprietà per gli elementi visualizzati in una griglia a destra. L'etichetta della griglia delle proprietà può essere dinamica, in modo che quando viene selezionato un elemento a sinistra, la griglia a destra mostra le informazioni relative a tale elemento specifico.

- Testo dinamico: può essere utile nelle istanze in cui è necessario visualizzare informazioni specifiche e non le informazioni generali in questo modo, ma è necessario prestare attenzione a non utilizzare un utilizzo eccessivo.

Se si desidera che gli utenti siano in grado di copiare le informazioni, il testo dinamico deve essere in un campo di testo di sola lettura.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Pulsanti e collegamenti ipertestuali

### <a name="overview"></a>Panoramica
I pulsanti e i controlli dei collegamenti (collegamenti ipertestuali) devono seguire le [indicazioni di base sul desktop di Windows sui collegamenti ipertestuali](/windows/desktop/uxguide/ctrl-links) per l'utilizzo, il wording, il ridimensionamento e la spaziatura.

### <a name="choosing-between-buttons-and-links"></a>Scelta tra pulsanti e collegamenti
Tradizionalmente, i pulsanti sono stati usati per le azioni e i collegamenti ipertestuali sono stati riservati per la navigazione. I pulsanti possono essere usati in tutti i casi, ma il ruolo dei collegamenti è stato espanso in Visual Studio in modo che i pulsanti e i collegamenti siano più intercambiabili in alcune condizioni.

Quando usare i pulsanti di comando:

- Comandi primari

- Visualizzazione di finestre utilizzate per raccogliere input o opzioni, anche se si tratta di comandi secondari

- Azioni distruttive o irreversibili

- Pulsanti di impegno nelle procedure guidate e nei flussi di pagina

Evitare i pulsanti di comando nelle finestre degli strumenti o se sono necessarie più di due parole per l'etichetta. I collegamenti possono avere etichette più lunghe.

 Quando usare i collegamenti:

- Spostamento a un'altra finestra, a un documento o a una pagina Web

- Situazioni che richiedono un'etichetta più lunga o una frase breve per descrivere lo scopo dell'azione

- Spazi stretti in cui un pulsante sovraccarica l'interfaccia utente, purché l'azione non sia distruttiva o irreversibile

- Deaccentuare i comandi secondari nelle situazioni in cui sono presenti molti comandi

#### <a name="examples"></a>Esempio
![Collegamenti ai comandi usati nella barra informazioni dopo un messaggio di stato](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Collegamenti ai comandi usati nella barra informazioni dopo un messaggio di stato

![Collegamenti usati nel popup CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Collegamenti usati nel popup CodeLens

![Collegamenti utilizzati per i comandi secondari in cui i pulsanti attraggono troppa attenzione](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Collegamenti utilizzati per i comandi secondari in cui i pulsanti attraggono troppa attenzione

### <a name="common-buttons"></a>Pulsanti comuni

#### <a name="text"></a>Testo
Seguire le linee guida per la scrittura nel [testo e nella terminologia dell'interfaccia utente](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Stile visivo

##### <a name="standard-unthemed"></a>Standard (non con tema)
La maggior parte dei pulsanti in Visual Studio verrà visualizzata nelle finestre di dialogo dell'utilità e non deve avere uno stile. Devono riflettere l'aspetto standard dei pulsanti come stabilito dal sistema operativo.

##### <a name="themed"></a>Tema
In alcuni casi, i pulsanti possono essere utilizzati all'interno dell'interfaccia utente con stile e questi pulsanti devono avere uno stile appropriato. Per informazioni sui controlli con tema, vedere [dialoghi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Pulsanti speciali

#### <a name="browse-buttons"></a>Sfoglia... pulsanti
**[Sfoglia...]** i pulsanti vengono utilizzati in griglie, finestre di dialogo e finestre degli strumenti e altri elementi dell'interfaccia utente non modale. Visualizzano una selezione che assiste l'utente nella compilazione di un valore in un controllo. Sono disponibili due varianti di questo pulsante, Long e short.

![Pulsante Long [Browse...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Pulsante Long [Browse...]

![Pulsante con i puntini di sospensione-solo short [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Pulsante con i puntini di sospensione-solo short [...]

Quando usare il pulsante con i puntini di sospensione-solo breve:

- Se è presente più di un pulsante Long **[Browse...]** in una finestra di dialogo, ad esempio quando più campi consentono l'esplorazione. Usare il pulsante Short **[...]** per ogni per evitare le chiavi di accesso confuse create da questa situazione (**&browse** e **B&Rows** nella stessa finestra di dialogo).

- In una finestra di dialogo stretta o quando non è disponibile un punto ragionevole per inserire il pulsante lungo.

- Se il pulsante verrà visualizzato in un controllo griglia.

Linee guida per l'uso del pulsante:

- Non usare una chiave di accesso. Per accedervi utilizzando la tastiera, è necessario che l'utente Tab dal controllo adiacente. Verificare che l'ordine di tabulazione sia tale che qualsiasi pulsante Sfoglia si trovi immediatamente dopo il campo da riempire. Non usare mai un carattere di sottolineatura al di sotto del primo periodo.

- Impostare la proprietà **nome** di Microsoft Active ACCESSIBILITY (MSAA) su **Sfoglia...** (inclusi i puntini di sospensione) in modo che lo screen reader lo legga come "Browse" e non "dot-dot-dot" o "period-period-period". Per i controlli gestiti, questo significa impostare la proprietà **AccessibleName** .

- Non usare mai un pulsante con i puntini di sospensione **[...]** per qualsiasi elemento tranne un'azione browse. Se, ad esempio, è necessario un pulsante **[nuovo...]** senza spazio sufficiente per il testo, è necessario riprogettare la finestra di dialogo.

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
![Ridimensionamento dei pulsanti [Sfoglia...]: la versione standard è 75x23 pixel, la versione breve è 26x23 pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Ridimensionamento dei pulsanti [Sfoglia...]

![Spaziatura [Sfoglia...] pulsanti: spaziatura tra il controllo correlato e il pulsante Sfoglia standard 7 pixel, la spaziatura tra il controllo correlato e il pulsante di ricerca breve 5 pixel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Spaziatura dei pulsanti [Sfoglia...]

#### <a name="graphical-buttons"></a>Pulsanti grafici
Alcuni pulsanti devono sempre usare un'immagine grafica e non includono mai testo per conservare spazio ed evitare problemi di localizzazione. Questi vengono spesso usati nei selezionatori dei campi e in altri elenchi ordinabili.

> [!NOTE]
> Gli utenti devono premere TAB per questi pulsanti (non sono presenti chiavi di accesso), quindi inserirli in un ordine ragionevole. Eseguire il mapping della `name` proprietà del pulsante all'azione necessaria in modo che le utilità per la lettura dello schermo interpretino correttamente l'azione del pulsante.

| Funzione | Pulsante |
| --- | --- |
| Add | ![Pulsante grafico "Aggiungi"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Rimuovi | ![Pulsante grafico "Rimuovi"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Aggiungi tutto | ![Pulsante grafico "Aggiungi tutto"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Rimuovi tutto | ![Pulsante grafico "Rimuovi tutto"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Sposta su | ![Pulsante grafico "Sposta su"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Sposta giù | ![Pulsante grafico "Sposta giù"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Elimina | ![Pulsante grafico "Elimina"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
Il dimensionamento dei pulsanti grafici è uguale a quello per la versione breve del pulsante **[Sfoglia...]** (26x23 pixel):

![Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente che Mostra](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente che Mostra

### <a name="hyperlinks"></a>Collegamenti ipertestuali
I collegamenti ipertestuali sono ideali per le azioni basate sull'esplorazione, ad esempio l'apertura di un argomento della guida, una finestra di dialogo modale o una procedura guidata. Se per un comando viene usato un collegamento ipertestuale, deve sempre visualizzare una modifica visibile e percettibile per l'interfaccia utente. In generale, le azioni di cui viene eseguito il commit in un'azione (ad esempio, Salva, Annulla ed Elimina) vengono comunicate con un pulsante.

#### <a name="writing-style"></a>Stile di scrittura
Seguire le [indicazioni sul desktop di Windows per il testo dell'interfaccia utente](/windows/desktop/uxguide/text-ui). Non usare "ulteriori informazioni su", "ulteriori informazioni su" o "ottenere assistenza per questo". Al contrario, frasere il testo del collegamento alla Guida in termini di domanda principale fornita dal contenuto della guida. Ad esempio, "**ricerca per categorie aggiungere un server al Esplora server?**"

#### <a name="visual-style"></a>Stile visivo

- I collegamenti ipertestuali devono sempre usare [il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se lo stile di un collegamento ipertestuale non è corretto, il colore rosso viene attivato quando attivo o viene visualizzato un colore diverso dopo la visita.

- Non includere sottolineature nello stato di riposo del controllo, a meno che il collegamento non sia un frammento di frase all'interno di una frase completa, ad esempio in una filigrana.

- Le sottolineature non devono essere visualizzate al passaggio del mouse. Al contrario, il feedback all'utente che il collegamento è attivo è un lieve cambiamento di colore e il cursore di collegamento appropriato.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Visualizzazioni ad albero

Le visualizzazioni ad albero forniscono un modo per organizzare elenchi complessi in gruppi padre-figlio. Un utente può espandere o comprimere i gruppi padre per visualizzare o nascondere gli elementi figlio sottostanti. Ogni elemento all'interno di una visualizzazione albero può essere selezionato per fornire ulteriori azioni.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Stile di visualizzazione struttura ad albero

#### <a name="expanders"></a>Espansori
I controlli di visualizzazione albero devono essere conformi alla progettazione dell'espansore utilizzata da Windows e Visual Studio. Ogni nodo utilizza un controllo Expander per rivelare o nascondere gli elementi sottostanti. L'uso di un controllo Expander garantisce la coerenza per gli utenti che potrebbero incontrare visualizzazioni ad albero diverse all'interno di Windows e Visual Studio.

![Corretto: stile appropriato del nodo della visualizzazione albero usando un controllo Expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Corretto: stile appropriato del nodo della visualizzazione albero usando un controllo Expander

![Errato: stile non corretto del nodo della visualizzazione albero](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Errato: stile non corretto del nodo della visualizzazione albero

#### <a name="selection"></a>Selezione
Quando si seleziona un nodo nella visualizzazione albero, l'evidenziazione deve espandersi fino alla larghezza massima del controllo di visualizzazione albero. Ciò consente agli utenti di identificare chiaramente l'elemento selezionato. I colori di selezione riflettono il tema corrente di Visual Studio.

![Corretto: l'evidenziazione del nodo selezionato corrisponde all'intera larghezza del controllo di visualizzazione albero.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Corretto: l'evidenziazione del nodo selezionato corrisponde all'intera larghezza del controllo di visualizzazione albero.

![Errato: l'evidenziazione del nodo selezionato non rientra nell'intera larghezza del controllo di visualizzazione albero.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Errato: l'evidenziazione del nodo selezionato non rientra nell'intera larghezza del controllo di visualizzazione albero.

#### <a name="icons"></a>Icone
Le icone devono essere usate solo nei controlli di visualizzazione albero se assistono nell'identificazione visiva delle differenze tra gli elementi. In generale, le icone devono essere usate solo in elenchi eterogenei in cui le icone contengono informazioni per distinguere i tipi di elementi. In un elenco omogeneo l'uso delle icone può essere spesso visualizzato come rumore e deve essere evitato. In tal caso, l'icona del gruppo (padre) può indicare il tipo di elementi al suo interno. L'eccezione a questa regola è se l'icona è dinamica e viene utilizzata per indicare lo stato.

#### <a name="scroll-bars"></a>Barre di scorrimento
Le barre di scorrimento devono essere sempre nascoste se il contenuto rientra nel controllo di visualizzazione albero. È accettabile che le barre di scorrimento siano nascoste o semi-trasparenti in una finestra scorrevole e visualizzate quando la finestra contenente la visualizzazione albero ha lo stato attivo o al passaggio del mouse sulla visualizzazione albero stessa.

![Vengono visualizzate le barre di scorrimento verticali e orizzontali perché il contenuto ha superato i limiti del controllo di visualizzazione albero.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Vengono visualizzate le barre di scorrimento verticali e orizzontali perché il contenuto ha superato i limiti del controllo di visualizzazione albero.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interazioni visualizzazione albero

#### <a name="context-menus"></a>Menu di scelta rapida
Un nodo della visualizzazione albero può rivelare le opzioni del sottomenu in un menu di scelta rapida. Questa situazione si verifica in genere quando un utente ha fatto clic con il pulsante destro del mouse su un elemento o ha premuto il tasto menu su una tastiera di Windows con l'elemento selezionato. È importante che il nodo ottenga lo stato attivo ed è selezionato. Ciò consente all'utente di identificare l'elemento a cui appartiene il sottomenu.

![L'elemento che ha generato il menu di scelta rapida acquisisce lo stato attivo per notificare all'utente l'elemento selezionato.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />L'elemento che ha generato il menu di scelta rapida acquisisce lo stato attivo per notificare all'utente l'elemento selezionato.

#### <a name="keyboard"></a>Tastiera
La visualizzazione albero deve consentire di selezionare elementi ed espandere/comprimere i nodi utilizzando la tastiera. Ciò garantisce che la navigazione soddisfi i requisiti di accessibilità.

##### <a name="tree-view-control"></a>Controllo di visualizzazione albero
I controlli albero di Visual Studio devono seguire la navigazione da tastiera comune:

- **Freccia su:** Selezionare gli elementi Spostandosi verso l'alto nell'albero

- **Freccia giù:** Selezionare gli elementi spostando verso il basso l'albero

- **Freccia destra:** Espandere un nodo nell'albero

- **Freccia sinistra:** Comprimere un nodo nell'albero

- **Immettere il tasto:** Avvia, carica, Esegui elemento selezionato

##### <a name="trid-tree-view-and-grid-view"></a>Tridente (visualizzazione albero e visualizzazione griglia)
Un controllo tridente è un controllo complesso che contiene una visualizzazione struttura ad albero all'interno di una griglia. L'espansione, il collasso e lo spostamento nell'albero devono rispettare gli stessi comandi della tastiera di una visualizzazione albero, con le aggiunte seguenti:

- **Freccia destra:** Espandere un nodo. Dopo aver espanso il nodo, è necessario continuare a spostarsi sulla colonna più vicina a destra. La navigazione dovrebbe arrestarsi alla fine della riga.

- **Scheda:** Passa alla cella più vicina a destra.  Alla fine della riga, la navigazione continua fino alla riga successiva.

- **MAIUSC + TAB:** Passa alla cella più vicina a sinistra.  All'inizio della riga, la navigazione continua fino alla cella più a destra nella riga precedente.

![Un controllo tridente in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Un controllo tridente in Visual Studio
