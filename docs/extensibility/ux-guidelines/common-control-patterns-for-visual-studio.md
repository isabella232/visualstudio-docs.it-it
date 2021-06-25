---
title: Pattern di controllo comuni per Visual Studio | Microsoft Docs
description: Informazioni su come Visual Studio controlli comuni seguano le linee guida per l'interazione con Windows Desktop e sulle situazioni speciali che aumentano tali linee guida.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12d514bdc0aa37598ad57e0466bf57ba75ed2601
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899303"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modelli dei controlli comuni per Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Controlli comuni

### <a name="overview"></a>Panoramica
I controlli comuni costituiscono la maggior parte dell'interfaccia utente in Visual Studio. I controlli più comuni usati nell'interfaccia Visual Studio devono seguire le linee guida per [l'interazione con Desktop di Windows.](/windows/desktop/uxguide/controls) Questo argomento è specifico per l'Visual Studio e illustra situazioni speciali o dettagli che aumentano le linee guida di Windows.

#### <a name="common-controls-in-this-topic"></a>Controlli comuni in questo argomento

- [Barre di scorrimento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Caselle combinate ed elenchi a discesa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Pulsanti di opzione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Raggruppare frame](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controlli di testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Visualizzazioni albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Stile visivo
La prima cosa da considerare quando si stilino i controlli è se i controlli verranno usati nell'interfaccia utente con testo. I controlli nell'interfaccia utente standard sono un'interfaccia utente senza titolo e devono seguire lo stile normale di Desktop di [Windows,](/windows/desktop/uxguide/controls)vale a dire che non sono ri-modelli e devono essere visualizzati nell'aspetto predefinito del controllo.

- **Finestre di dialogo standard (utilità):** non con i tipi di dati. Non ridefinire il modello. Usare i valori predefiniti dello stile di controllo di base.

- **Finestre degli strumenti, editor di documenti, superfici di progettazione e finestre di dialogo con testo:** Usare l'aspetto specifico con i colori usando il servizio colori.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Barre di scorrimento
 Le barre di scorrimento devono seguire modelli di interazione comuni per le barre di scorrimento di [Windows,](/windows/desktop/Controls/about-scroll-bars) a meno che non siano aumentate con informazioni sul contenuto, ad esempio nell'editor di codice.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Campi di input
 Per un comportamento di interazione tipico, segui le linee [guida di Desktop di Windows per le caselle di testo.](/windows/desktop/uxguide/ctrl-text-boxes)

#### <a name="visual-style"></a>Stile visivo

- Lo stile dei campi di input non deve essere applicato nelle finestre di dialogo dell'utilità. Usare lo stile di base intrinseco per il controllo.

- I campi di input con testo con testo devono essere usati solo nelle finestre degli strumenti e nelle finestre degli strumenti con testo con testo.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- I campi di sola lettura avranno uno sfondo grigio (disabilitato), ma in primo piano predefinito (attivo).

- I campi obbligatori devono **\<Required>** avere come filigrane al loro interno. È consigliabile non modificare il colore dello sfondo se non in rare situazioni.

- Convalida degli errori: vedere [Notifiche e stato di avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- I campi di input devono essere ridimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un percorso. La lunghezza può indicare all'utente le limitazioni relative al numero di caratteri consentiti nel campo.

     ![Lunghezza del campo di input non corretta: è improbabile che il nome sia così lungo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Lunghezza del campo di input non corretta: è improbabile che il nome sia così lungo.

     ![Lunghezza corretta del campo di input: la larghezza del campo di input è ragionevole per il contenuto previsto.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Lunghezza corretta del campo di input: la larghezza del campo di input è ragionevole per il contenuto previsto.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Caselle combinate ed elenchi a discesa
Per un comportamento di interazione tipico, segui le linee guida di Windows Desktop per gli elenchi a discesa e [le caselle combinate.](/windows/desktop/uxguide/ctrl-drop)

#### <a name="visual-style"></a>Stile visivo

- Nelle finestre di dialogo dell'utilità non ridefinire il modello del controllo. Usare lo stile di base intrinseco per il controllo.

- Nell'interfaccia utente a base di testo, le caselle combinate e gli elenchi a discesa seguono il testo standard per i controlli.

#### <a name="layout"></a>Layout
Le caselle combinate e gli elenchi a discesa devono essere ridimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzate, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un tracciato.

![Risposta errata: la larghezza dell'elenco a discesa è troppo lunga per il contenuto che verrà visualizzato.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Risposta errata: la larghezza dell'elenco a discesa è troppo lunga per il contenuto che verrà visualizzato.

![Risposta corretta: l'elenco a discesa viene ridimensionato per consentire la crescita della traduzione, ma non inutilmente lungo.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Risposta corretta: l'elenco a discesa viene ridimensionato per consentire la crescita della traduzione, ma non inutilmente lungo.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Caselle
Per un comportamento di interazione tipico, seguire le linee guida [di Desktop di Windows per le caselle di controllo](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Stile visivo

- Nelle finestre di dialogo dell'utilità non ridefinire il modello del controllo. Usare lo stile di base intrinseco per il controllo.

- Nell'interfaccia utente con testo a tinge, le caselle di controllo seguono il testo standard per i controlli.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- L'interazione con una casella di controllo non deve mai visualizzare una finestra di dialogo o passare a un'altra area.

- Allineare le caselle di controllo alla linea di base della prima riga di testo.

     ![Risposta errata: la casella di controllo è centrata sul testo.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Risposta errata: la casella di controllo è centrata sul testo.

     ![Risposta corretta: la casella di controllo è allineata alla prima riga del testo.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Risposta corretta: la casella di controllo è allineata alla prima riga del testo.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Pulsanti
Per un comportamento di interazione tipico, segui le linee [guida di Desktop di Windows per i pulsanti di opzione](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Stile visivo
Nelle finestre di dialogo dell'utilità non creare uno stile per i pulsanti di opzione. Usare lo stile di base intrinseco per il controllo.

#### <a name="specialized-interactions"></a>Interazioni specializzate
Non è necessario usare un frame di gruppo per racchiudere le opzioni di opzione, a meno che non sia necessario mantenere la distinzione dei gruppi in un layout stretto.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Raggruppare frame
Per un comportamento di interazione tipico, segui le linee [guida di Desktop di Windows per raggruppare i frame.](/windows/desktop/uxguide/ctrl-group-boxes)

#### <a name="visual-style"></a>Stile visivo
Nelle finestre di dialogo dell'utilità, non creare stili per i frame del gruppo. Usare lo stile di base intrinseco per il controllo.

#### <a name="layout"></a>Layout

- Non è necessario usare un frame di gruppo per racchiudere le opzioni di opzione, a meno che non sia necessario mantenere la distinzione dei gruppi in un layout stretto.

- Non usare mai un frame di gruppo per un singolo controllo.

- A volte è accettabile usare una regola orizzontale anziché un contenitore frame di gruppo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Controlli di testo

### <a name="static-text-fields"></a>Campi di testo statico

Un campo di testo statico presenta informazioni di sola lettura e non può essere selezionato dall'utente. Evitare di usarlo per qualsiasi testo che l'utente potrebbe voler copiare negli Appunti. Tuttavia, il testo statico di sola lettura può cambiare per riflettere una modifica dello stato. Nell'esempio seguente il testo statico Nome output nel gruppo Informazioni cambia in modo da riflettere tutte le modifiche apportate alla casella di testo Spazio dei nomi radice sopra di esso.

Esistono due modi per visualizzare informazioni di testo statico.

Il testo statico può essere di per sé in una finestra di dialogo senza contenimento in assenza di conflitti di raggruppamento. Decidere se le righe aggiuntive di una casella sono effettivamente necessarie. Un esempio è la visualizzazione di un percorso di directory in una sezione creata da una riga di gruppo, come illustrato di seguito:

![Informazioni di testo statico nei controlli di testo](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informazioni di testo statico nei controlli di testo

In una finestra di dialogo in cui sono presenti altre aree raggruppate e il contenimento delle informazioni può essere utile per migliorare la leggibilità e quando una sezione può essere nascosta o visualizzata (come nel riquadro di descrizione **di Finestra Proprietà)** o si vuole essere coerente con un'interfaccia utente simile, posizionare il testo statico all'interno di una casella. Questa casella di gruppo deve essere una singola regola e colorata con `ButtonShadow` :

![Testo statico nel Finestra Proprietà](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Testo statico nel Finestra Proprietà

### <a name="read-only-text-box"></a>Casella di testo di sola lettura

In questo modo l'utente può selezionare il testo all'interno del campo, ma non modificarlo. Queste caselle di testo sono bordi del consueto chisel 3D con un `ButtonShadow` riempimento.

Una casella di testo può diventare attiva (modificabile) quando un utente modifica un controllo associato, ad esempio selezionando/deselezionando una casella di controllo o selezionando o deselezionando un pulsante di opzione. Ad esempio, nella **pagina &gt; Opzioni** degli strumenti illustrata di seguito la casella di testo **Home page** diventa attiva quando la **casella** di controllo Usa impostazioni predefinite è deselezionata.

![Casella di testo di sola lettura, che mostra gli stati inattivi e attivi](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Casella di testo di sola lettura, che mostra gli stati inattivi e attivi

### <a name="using-text-in-dialogs"></a>Uso del testo nelle finestre di dialogo

Linee guida principali per il testo nei dialoghe:

- Le etichette per caselle di testo, caselle di riepilogo e frame nelle finestre di dialogo non inteme iniziano con un verbo, hanno una maiuscola iniziale solo per la prima parola e terminano con i due punti.

    > I controlli di testo nelle finestre di dialogo a sfondo seguono le linee guida dell'esperienza utente di [Windows Desktop](/windows/desktop/uxguide/top-violations) e non accettano la punteggiatura finale, ad eccezione dei punti interrogativi nei collegamenti della Guida.

- Le etichette per le caselle di controllo e i pulsanti di opzione iniziano con un verbo, una maiuscola iniziale solo per la prima parola e non hanno punteggiatura finale.

- Le etichette per pulsanti, menu, voci di menu e tabulazioni hanno iniziali maiuscole per ogni parola (maiuscole/minuscole).

- La terminologia delle etichette deve essere coerente con etichette simili in altri dialoghe.

- Se possibile, fare in modo che un writer/editor scrivo o approvi il testo prima che venga passato allo sviluppatore per l'implementazione.

- Tutti i controlli devono avere etichette tranne in casi speciali in cui la tabulazione è sufficiente.
Usare il testo helper quando appropriato.

### <a name="helper-text"></a>Testo helper

Incluso nei dialoghe per aiutare l'utente a comprendere lo scopo del dialogo o a indicare l'azione da intraprendere. Il testo dell'helper deve essere usato solo quando necessario per evitare dialoghe semplici. Le due varianti del testo helper sono dialoghe e watermark.

Seguire le posizioni comuni per il testo helper ed essere selettivi nell'introduzione di nuove aree. Gli scenari comuni per il testo helper sono:

- Testo helper nei dialoghe, per fornire una direzione aggiuntiva su come interagire con un dialogo complesso.

- Testo della filigrana nelle finestre degli strumenti vuote o nelle finestre di dialogo, per spiegare perché non è visibile alcun contenuto.

- Un riquadro di descrizione, ad esempio nella parte inferiore del **Finestra Proprietà**.

- Testo della filigrana in un editor vuoto, per spiegare quale azione deve eseguire l'utente per iniziare.

### <a name="dialog-helper-text"></a>Testo di supporto della finestra di dialogo

Una finestra di progettazione dell'esperienza utente può essere utile per determinare quando il testo dell'helper è appropriato. La finestra di progettazione può definire la posizione in cui viene visualizzato il testo dell'helper e il relativo contenuto generale. L'assistenza dell'utente può scrivere/modificare il testo effettivo.

### <a name="watermarks"></a>Filigrane

I dialoghe traggono vantaggio da linee guida leggermente diverse per il limite. Poiché un dialogo può apparire occupato con molti elementi dell'interfaccia utente (etichette, testo dei suggerimenti, pulsanti e altri controlli contenitore con testo), in particolare quando vengono visualizzati in nero, le filigrane si distinguono meglio in grigio scuro (VSColor: `ButtonShadow` ). In genere una filigrana viene visualizzata all'interno di un controllo come una casella di riepilogo con uno sfondo bianco (VSColor: `Window` ).

- Il testo viene visualizzato in grigio scuro (VSColor: `ButtonShadow` ). Tuttavia, se la filigrana viene visualizzata su uno sfondo grigio medio o di altro colore (VSColor: ) ed è preoccupata per la leggibilità, passare con testo nero `ButtonFace` (VSColor: `WindowText` ).

- Le filigrane possono essere centrate o scaricate a sinistra. Applicare regole di progettazione standard quando si prendono decisioni di allineamento. La filigrana non può essere selezionata in background.

![Esempio di testo della filigrana](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Esempio di testo della filigrana

### <a name="context-specific-dynamic-text"></a>Testo specifico del contesto (dinamico)

Il testo dinamico può essere usato in due modi in un dialogo o in un'interfaccia utente non modabile: come etichetta dinamica o come contenuto dinamico.

- Etichetta dinamica: un uso comune del testo dinamico è nei pannelli descrittivi che offrono altre informazioni per l'elemento selezionato, ad esempio in una finestra di dialogo che contiene un elenco di elementi e proprietà per gli elementi visualizzati in una griglia a destra. L'etichetta per la griglia delle proprietà può essere dinamica in modo che quando un elemento viene selezionato a sinistra, la griglia a destra mostra le informazioni per tale elemento specifico.

- Testo dinamico: può essere utile nei casi in cui è necessario visualizzare informazioni specifiche e non informazioni generali in questo modo, ma è necessario fare attenzione a non usare in modo eccessivo.

Se si vuole che gli utenti siano in grado di copiare le informazioni, il testo dinamico deve essere in un campo di testo di sola lettura.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Pulsanti e collegamenti ipertestuali

### <a name="overview"></a>Panoramica
I pulsanti e i controlli collegamento (collegamenti ipertestuali) devono seguire le linee guida di base di [Windows Desktop](/windows/desktop/uxguide/ctrl-links) sui collegamenti ipertestuali per l'utilizzo, la formulazione, il ridimensionamento e la spaziatura.

### <a name="choosing-between-buttons-and-links"></a>Scelta tra pulsanti e collegamenti
In genere, i pulsanti sono stati usati per le azioni e i collegamenti ipertestuali sono stati riservati per la navigazione. I pulsanti possono essere usati in tutti i casi, ma il ruolo dei collegamenti è stato espanso in Visual Studio in modo che pulsanti e collegamenti siano più intercambiabili in alcune condizioni.

Quando usare i pulsanti di comando:

- Comandi primari

- Visualizzazione di finestre usate per raccogliere input o effettuare scelte, anche se sono comandi secondari

- Azioni distruttive o irreversibili

- Pulsanti di impegno all'interno di procedure guidate e flussi di pagina

Evitare i pulsanti di comando nelle finestre degli strumenti o se sono necessarie più di due parole per l'etichetta. I collegamenti possono avere etichette più lunghe.

 Quando usare i collegamenti:

- Spostamento in un'altra finestra, documento o pagina Web

- Situazioni che richiedono un'etichetta più lunga o una frase breve per descrivere la finalità dell'azione

- Spazi ristretti in cui un pulsante sovraccarica l'interfaccia utente, a condizione che l'azione non sia distruttiva o irreversibile

- De-enfasizing secondary commands in situations where there are many commands (De-enfasizing secondary commands in situations where there are many commands)

#### <a name="examples"></a>Esempio
![Collegamenti di comando usati nella barra informazioni dopo un messaggio di stato](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Collegamenti di comando usati nella barra informazioni dopo un messaggio di stato

![Collegamenti usati nel popup CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Collegamenti usati nel popup CodeLens

![Collegamenti usati per i comandi secondari in cui i pulsanti attirerebbero troppo attenzione](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Collegamenti usati per i comandi secondari in cui i pulsanti attirano troppo attenzione

### <a name="common-buttons"></a>Pulsanti comuni

#### <a name="text"></a>Testo
Seguire le linee guida per la scrittura nel testo [dell'interfaccia utente e nella terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Stile visivo

##### <a name="standard-unthemed"></a>Standard (senzathemed)
La maggior parte dei pulsanti Visual Studio verrà visualizzata nelle finestre di dialogo dell'utilità e non deve essere applicato uno stile. Devono riflettere l'aspetto standard dei pulsanti come determinato dal sistema operativo.

##### <a name="themed"></a>Tema
In alcuni casi, i pulsanti possono essere usati all'interno dell'interfaccia utente con stile e questi pulsanti devono essere con stile appropriato. Vedere [Dialogs (Dialogs)](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) per informazioni sui controlli con testo a testo.

### <a name="special-buttons"></a>Pulsanti speciali

#### <a name="browse-buttons"></a>Sfoglia... Pulsanti
**[Sfoglia...]** I pulsanti vengono usati nelle griglie, nelle finestre di dialogo e nelle finestre degli strumenti e in altri elementi non modali dell'interfaccia utente. Visualizza un controllo di selezione che consente all'utente di compilare un valore in un controllo . Esistono due varianti di questo pulsante, long e short.

![Pulsante lungo [Sfoglia...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Pulsante lungo [Sfoglia...]

![Pulsante breve con solo puntini di sospensione (...)](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Pulsante breve con solo puntini di sospensione (...)

Quando usare il pulsante breve solo con i puntini di sospensione:

- Se in una finestra di dialogo è presente più di un pulsante **[Sfoglia...]** lungo, ad esempio quando sono consentiti più campi per l'esplorazione. Usare il breve **pulsante [...]** per ognuno per evitare le chiavi di accesso confusa create da questa situazione (**&Sfoglia** e B&**righe** nella stessa finestra di dialogo).

- In una finestra di dialogo stretta o quando non esiste un posto ragionevole in cui inserire il pulsante lungo.

- Se il pulsante verrà visualizzato in un controllo griglia.

Linee guida per l'uso del pulsante:

- Non usare una chiave di accesso. Per accedervi tramite la tastiera, l'utente deve premere TAB dal controllo adiacente. Assicurarsi che l'ordine di tabulazione sia tale che qualsiasi pulsante Sfoglia cada immediatamente dopo il campo che verrà riempito. Non usare mai un carattere di sottolineatura sotto il primo punto.

- Impostare la proprietà Microsoft Active Accessibility (MSAA) **Name** su **Browse...** (inclusi i puntini di sospensione) in modo che le utilità per la lettura dello schermo lo leggono come "Sfoglia" e non come "dot-dot-dot" o "period-period-period". Per i controlli gestiti, questo significa impostare la **proprietà AccessibleName.**

- Non usare mai un pulsante con i puntini **di sospensione [...]** per qualsiasi elemento, ad eccezione di un'azione di esplorazione. Ad esempio, se è necessario un **pulsante [Nuovo...]** ma non si ha spazio sufficiente per il testo, la finestra di dialogo deve essere riprogettata.

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
![Pulsanti di ridimensionamento [Sfoglia...]: la versione standard è 75x23 pixel, la versione breve è 26x23 pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Ridimensionamento dei pulsanti [Sfoglia...]

![Spaziatura [Sfoglia...]: spaziatura tra il controllo correlato e il pulsante Sfoglia standard di 7 pixel, spaziatura tra il controllo correlato e il pulsante Sfoglia breve di 5 pixel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Spaziatura dei pulsanti [Sfoglia...]

#### <a name="graphical-buttons"></a>Pulsanti grafici
Alcuni pulsanti devono sempre usare un'immagine grafica e non includere mai testo per risparmiare spazio ed evitare problemi di localizzazione. Vengono spesso usati nelle opzioni di selezione dei campi e in altri elenchi ordinabili.

> [!NOTE]
> Gli utenti devono premere TAB per questi pulsanti (non sono presenti tasti di scelta), quindi posizionarli in un ordine ragionevole. Eseguire il mapping della proprietà del pulsante all'azione eseguita in modo che le utilità per la lettura `name` dello schermo interpretino correttamente l'azione del pulsante.

| Funzione | Pulsante |
| --- | --- |
| Add | ![Pulsante grafico "Aggiungi"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Rimuovi | ![Pulsante grafico "Rimuovi"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Aggiungi tutto | ![Pulsante grafico "Aggiungi tutto"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Rimuovi tutto | ![Pulsante grafico "Rimuovi tutto"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Sposta su | ![Pulsante grafico "Sposta su"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Sposta giù | ![Pulsante grafico "Sposta giù"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Delete | ![Pulsante grafico "Elimina"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
Il ridimensionamento per i pulsanti grafici è identico a quello della versione breve del pulsante **[Sfoglia...]** (26 x 23 pixel):

![Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente visualizzato](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente visualizzato

### <a name="hyperlinks"></a>Collegamenti ipertestuali
I collegamenti ipertestuali sono particolarmente adatti per le azioni basate sulla navigazione, ad esempio l'apertura di un argomento della Guida, di una finestra di dialogo modale o di una procedura guidata. Se un collegamento ipertestuale viene usato per un comando, deve sempre visualizzare una modifica visibile e evidente all'interfaccia utente. In generale, le azioni di cui viene eseguito il commit in un'azione (ad esempio Salva, Annulla ed Elimina) vengono comunicate meglio tramite un pulsante.

#### <a name="writing-style"></a>Stile di scrittura
Seguire le linee [guida di Windows Desktop per il testo dell'interfaccia utente.](/windows/desktop/uxguide/text-ui) Non usare la formulazione "Altre informazioni su", "Altre informazioni su" o "Ottieni assistenza con questa". Al contrario, la frase Guida collega il testo in termini della domanda principale a cui risponde il contenuto della Guida. Ad esempio, "**Ricerca per categorie aggiungere un server al Esplora server?**"

#### <a name="visual-style"></a>Stile visivo

- I collegamenti ipertestuali devono sempre [usare il servizio VSColor.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService) Se lo stile di un collegamento ipertestuale non è corretto, lampeggia in rosso quando è attivo o mostra un colore diverso dopo la visita.

- Non includere sottolineature nello stato di pausa del controllo, a meno che il collegamento non sia un frammento di frase all'interno di una frase completa, ad esempio in una filigrana.

- Le sottolineature non dovrebbero essere visualizzate al passaggio del mouse. Al contrario, il feedback per l'utente che il collegamento è attivo è una lieve modifica del colore e il cursore di collegamento appropriato.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Visualizzazioni albero

Le visualizzazioni albero consentono di organizzare elenchi complessi in gruppi padre-figlio. Un utente può espandere o comprimere i gruppi padre per visualizzare o nascondere gli elementi figlio sottostanti. Ogni elemento all'interno di una visualizzazione albero può essere selezionato per fornire un'ulteriore azione.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Stile di visualizzazione della visualizzazione struttura ad albero

#### <a name="expanders"></a>Espansori
I controlli visualizzazione albero devono essere conformi alla progettazione dell'espansore usata da Windows e Visual Studio. Ogni nodo usa un controllo expander per visualizzare o nascondere gli elementi sottostanti. L'uso di un controllo expander garantisce coerenza per gli utenti che potrebbero riscontrare visualizzazioni albero diverse all'interno di Windows e Visual Studio.

![Risposta corretta: stile appropriato del nodo della visualizzazione struttura ad albero tramite un controllo expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Risposta corretta: stile appropriato del nodo della visualizzazione struttura ad albero tramite un controllo expander

![Risposta errata: stile non corretto del nodo della visualizzazione albero](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Risposta errata: stile non corretto del nodo della visualizzazione albero

#### <a name="selection"></a>Selezione
Quando viene selezionato un nodo all'interno della visualizzazione albero, l'evidenziazione deve espandersi fino all'intera larghezza del controllo di visualizzazione albero. Ciò consente agli utenti di identificare chiaramente l'elemento selezionato. I colori di selezione devono riflettere il tema Visual Studio corrente.

![Risposta corretta: l'evidenziazione del nodo selezionato si adatta all'intera larghezza del controllo di visualizzazione albero.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Risposta corretta: l'evidenziazione del nodo selezionato si adatta all'intera larghezza del controllo di visualizzazione albero.

![Risposta errata: l'evidenziazione del nodo selezionato non rientra nell'intera larghezza del controllo di visualizzazione albero.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Risposta errata: l'evidenziazione del nodo selezionato non rientra nell'intera larghezza del controllo di visualizzazione albero.

#### <a name="icons"></a>Icone
Le icone devono essere usate solo nei controlli di visualizzazione albero se consentono di identificare visivamente le differenze tra gli elementi. In generale, le icone devono essere usate solo in elenchi eterogenei in cui le icone riportano informazioni per distinguere i tipi di elementi. In un elenco omogeneo l'uso delle icone può essere spesso considerato come rumore e deve essere evitato. In tal caso, l'icona del gruppo (padre) può comunicare il tipo di elementi al suo interno. L'eccezione a questa regola è se l'icona è dinamica e viene usata per indicare lo stato.

#### <a name="scroll-bars"></a>Barre di scorrimento
Le barre di scorrimento devono essere sempre nascoste se il contenuto rientra nel controllo di visualizzazione albero. È accettabile che le barre di scorrimento siano nascoste o semitrasparenti in una finestra scorrevole e vengano visualizzate quando la finestra contenente la visualizzazione albero ha lo stato attivo o al passaggio del mouse sulla visualizzazione albero stessa.

![Le barre di scorrimento verticale e orizzontale vengono visualizzate perché il contenuto ha superato i limiti del controllo di visualizzazione albero.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Le barre di scorrimento verticale e orizzontale vengono visualizzate perché il contenuto ha superato i limiti del controllo di visualizzazione albero.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interazioni con la visualizzazione albero

#### <a name="context-menus"></a>Menu di scelta rapida
Un nodo della visualizzazione albero può visualizzare le opzioni di sottomenu in un menu di scelta rapida. In genere, ciò si verifica quando un utente ha fatto clic con il pulsante destro del mouse su un elemento o ha premuto il tasto Menu su una tastiera di Windows con l'elemento selezionato. È importante che il nodo acquisisca lo stato attivo ed sia selezionato. Ciò consente all'utente di identificare l'elemento a cui appartiene il sottomenu.

![L'elemento che ha generato il menu di scelta rapida ottiene lo stato attivo per notificare all'utente quale elemento è stato selezionato.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />L'elemento che ha generato il menu di scelta rapida ottiene lo stato attivo per notificare all'utente quale elemento è stato selezionato.

#### <a name="keyboard"></a>Tastiera
La visualizzazione albero dovrebbe offrire la possibilità di selezionare elementi ed espandere/comprimere i nodi usando la tastiera. Ciò garantisce che la navigazione soddisfi i requisiti di accessibilità.

##### <a name="tree-view-control"></a>Controllo visualizzazione struttura ad albero
Visual Studio controlli struttura ad albero devono seguire gli spostamenti comuni tramite tastiera:

- **Freccia SU:** Selezionare gli elementi spostando verso l'alto l'albero

- **Freccia GIÙ:** Selezionare gli elementi spostandosi verso il basso nell'albero

- **Freccia DESTRA:** Espandere un nodo nell'albero

- **Freccia SINISTRA:** Comprimere un nodo nell'albero

- **Immettere il tasto:** Avviare, caricare ed eseguire l'elemento selezionato

##### <a name="trid-tree-view-and-grid-view"></a>Trid (visualizzazione albero e visualizzazione griglia)
Un controllo trid è un controllo complesso che contiene una visualizzazione albero all'interno di una griglia. L'espansione, la compressione e l'esplorazione dell'albero devono rispettare gli stessi comandi della tastiera di una visualizzazione albero, con le aggiunte seguenti:

- **Freccia DESTRA:** Espandere un nodo. Dopo che il nodo è stato espanso, dovrebbe continuare a passare alla colonna più vicina a destra. La navigazione deve essere interrotta alla fine della riga.

- **Scheda:** Passa alla cella più vicina a destra.  Alla fine della riga, lo spostamento continua alla riga successiva.

- **MAIUSC+TAB:** Passa alla cella più vicina a sinistra.  All'inizio della riga, lo spostamento continua fino alla cella più a destra della riga precedente.

![Controllo trid in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Controllo trid in Visual Studio
