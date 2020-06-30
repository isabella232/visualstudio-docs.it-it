---
title: Modelli di controllo comuni
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547446"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modelli dei controlli comuni per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Controlli comuni

### <a name="overview"></a>Panoramica
 I controlli comuni costituiscono la maggior parte dell'interfaccia utente in Visual Studio. La maggior parte dei controlli comuni usati nell'interfaccia di Visual Studio deve seguire le [linee guida](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)per l'interazione con il desktop di Windows. Questo documento è specifico di Visual Studio e illustra le situazioni speciali o i dettagli che aumentano le linee guida di Windows.

#### <a name="common-controls-in-this-topic"></a>Controlli comuni in questo argomento

- [Barre](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Caselle combinate ed elenchi a discesa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Pulsanti di opzione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Raggruppare i frame](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controlli di testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Visualizzazioni albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Stile di visualizzazione
 Il primo aspetto da considerare quando i controlli di stile è se i controlli verranno utilizzati nell'interfaccia utente con tema. I controlli nell'interfaccia utente standard sono interfaccia utente senza tema e devono seguire il [normale stile di desktop di Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), ovvero non vengono ribasati su modelli e dovrebbero apparire nell'aspetto del controllo predefinito.

- **Finestre di dialogo standard (Utility):** non con tema. Non ricreare il modello. Usare le impostazioni predefinite dello stile del controllo di base.

- **Finestre degli strumenti, editor di documenti, aree di progettazione e finestre di dialogo con tema:** Usare l'aspetto con tema specializzato usando il servizio color.

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a>Barre
 Le barre di scorrimento devono seguire [modelli di interazione comuni per le barre di scorrimento di Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) a meno che non siano state ampliate con informazioni sul contenuto, ad esempio nell'editor di codice.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Campi di input
 Per un comportamento di interazione tipico, seguire le [linee guida per i desktop di Windows per le caselle di testo](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Stile di visualizzazione

- Non è possibile applicare uno stile ai campi di input nelle finestre di dialogo dell'utilità. Utilizzare lo stile di base intrinseco al controllo.

- I campi di input con tema devono essere usati solo nelle finestre di dialogo e negli strumenti con tema.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- I campi di sola lettura avranno uno sfondo grigio (disabilitato), ma il primo piano predefinito (attivo).

- I campi obbligatori devono avere **\<Required>** come filigrane al suo interno. Non modificare il colore dello sfondo tranne che in rari casi.

- Convalida degli errori: vedere [notifiche e stato di avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- I campi di input devono essere dimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui sono visualizzati, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un percorso. La lunghezza può indicare all'utente le limitazioni relative al numero di caratteri consentiti nel campo.

     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl") **Lunghezza del campo di input non corretta per la larghezza del controllo del campo di input: è improbabile che il nome sia lungo.**

     ![Correzione della larghezza](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl") del **campo di input corretta per la lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto.**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Caselle combinate ed elenchi a discesa
 Per un comportamento di interazione tipico, seguire le [linee guida per i desktop di Windows per elenchi a discesa e caselle combinate](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Stile di visualizzazione

- Nelle finestre di dialogo dell'utilità non ricreare un nuovo modello per il controllo. Utilizzare lo stile di base intrinseco al controllo.

- Nell'interfaccia utente con tema, le caselle combinate e gli elenchi a discesa seguono i temi standard per i controlli.

#### <a name="layout"></a>Layout
 Le caselle combinate e gli elenchi a discesa devono essere dimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui sono visualizzati, né per corrispondere arbitrariamente alla lunghezza di un campo lungo, ad esempio un percorso.

 ![Layout di eliminazione&#45;non corretto](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **Lunghezza di campo non corretta per un controllo a discesa**

 ![Correggere il layout del&#45;di rilascio](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **Correggere la lunghezza del campo per un controllo a discesa**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Caselle di controllo
 Per un comportamento di interazione tipico, seguire le [linee guida per il desktop di Windows per le caselle di controllo](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Stile di visualizzazione

- Nelle finestre di dialogo dell'utilità non ricreare un nuovo modello per il controllo. Utilizzare lo stile di base intrinseco al controllo.

- Nell'interfaccia utente con tema le caselle di controllo seguono i temi standard per i controlli.

#### <a name="specialized-interactions"></a>Interazioni specializzate

- L'interazione con una casella di controllo non deve mai far apparire una finestra di dialogo o passare a un'altra area.

- Allinea le caselle di controllo con la linea di base della prima riga di testo.

     Allineamento della casella di controllo non corretto ![allineamento](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign") **della casella di controllo: la casella di controllo è centrata sul testo.**

     ![Correzione](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign") allineamento casella di controllo corretto allineamento casella di controllo **: la casella di controllo è allineata con la linea di base della prima riga di testo.**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Pulsanti di opzione
 Per un comportamento di interazione tipico, seguire le [linee guida per il desktop di Windows per i pulsanti di opzione](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Stile di visualizzazione
 Nelle finestre di dialogo dell'utilità non applicare uno stile ai pulsanti di opzione. Utilizzare lo stile di base intrinseco al controllo.

#### <a name="specialized-interactions"></a>Interazioni specializzate
 Non è necessario usare un frame di gruppo per racchiudere le scelte radio.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Raggruppare i frame
 Per un comportamento di interazione tipico, seguire le [linee guida per il desktop di Windows per i frame del gruppo](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Stile di visualizzazione
 Nelle finestre di dialogo dell'utilità non applicare lo stile ai frame del gruppo. Utilizzare lo stile di base intrinseco al controllo.

#### <a name="layout"></a>Layout

- Non è necessario usare un frame di gruppo per racchiudere le scelte radiofoniche, a meno che non sia necessario mantenere la distinzione tra gruppi in un layout limitato.

- Non usare mai un frame di gruppo per un singolo controllo.

- A volte è accettabile usare una regola orizzontale anziché un contenitore di frame del gruppo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Controlli testo

### <a name="labels"></a>Etichette

#### <a name="active-label-state"></a>Stato etichetta attivo

##### <a name="utility-standard-dialogs"></a>Finestre di dialogo utilità (standard))

- In generale, seguire le indicazioni sul desktop di Windows per le etichette dei controlli.

- Nelle finestre di dialogo dell'utilità, le etichette devono essere visualizzate in formato non grassetto, nel colore del tipo di carattere e del testo dell'ambiente standard. Vedere [tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- I puntini di sospensione devono seguire sempre le etichette.

##### <a name="signature-themed-dialogs"></a>Finestre di dialogo firma (con temi))
 I controlli Label possono essere in grassetto o in grigio chiaro.

#### <a name="disabled-label-state"></a>Stato dell'etichetta disabilitato
 Le etichette devono riflettere l'aspetto del controllo a cui sono associate. Se, ad esempio, il controllo associato è disabilitato, l'etichetta viene visualizzata in grigio e disabilitata. Questa operazione viene in genere gestita dal sistema operativo e non richiede alcun trattamento speciale.

#### <a name="dynamic-labels"></a>Etichette dinamiche
 Le etichette dinamiche cambiano in base alla selezione corrente. Quando possibile, usare le etichette dinamiche nei layout master/dettagli per consentire all'utente di comprendere che le informazioni visualizzate sono rilevanti per una selezione specifica e non per informazioni generali.

 ![Etichetta dinamica usata con contenuto dinamico](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **Esempio di etichetta dinamica usata con contenuto dinamico**

#### <a name="instructional-text"></a>Testo istruzioni
 Alcuni elementi dell'interfaccia traggono vantaggio dal testo informativo per aiutare l'utente a comprendere lo scopo dell'interfaccia utente o per indicare l'azione da eseguire.

- Il testo informativo è più comune nella parte superiore delle finestre di dialogo, ma può essere visualizzato in altre aree per fornire istruzioni a un raggruppamento di controlli complessi.

- Il testo informativo non è interattivo, ma può contenere collegamenti ipertestuali per gli argomenti della guida.

- Utilizzare un testo informativo sporadicamente e solo quando necessario.

##### <a name="formatting"></a>Formattazione
 Il testo informativo deve essere un tipo di carattere ambiente, testo di controllo standard (senza tema). Vedere [tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Per informazioni dettagliate sulla scrittura di testo didattico, vedere [testo dell'interfaccia utente e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Formattazione del testo esplicativo](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Testo di istruzioni in una finestra di dialogo di Visual Studio**

#### <a name="informational-text"></a>Testo informativo
 Il testo informativo è un testo che fornisce all'utente informazioni aggiuntive. Può essere statico o dinamico oppure essere usato come notifica. È sempre di sola lettura, ma se è utile per consentire all'utente di copiare le informazioni, il testo dinamico deve essere inserito in un contenitore di controlli, ad esempio un campo di testo di sola lettura.

##### <a name="dynamic-context-specific-text"></a>Testo dinamico (specifico del contesto)
 Il testo delle informazioni dinamiche cambia a seconda del contesto, ad esempio quando l'utente passa lo stato attivo. Spesso, ma non sempre, il contenuto dinamico viene abbinato a un'etichetta dinamica.

 ![Testo delle informazioni dinamiche](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **Il testo informativo dinamico cambia a seconda del contesto.**

##### <a name="formatting"></a>Formattazione
 Esistono due modi per visualizzare i campi di testo di sola lettura: direttamente sulla superficie dell'interfaccia utente (vedere sopra) o contenuti all'interno di un altro controllo, ad esempio un frame di gruppo o una casella di testo. Uno dei due è corretto a seconda della situazione. La finestra di progettazione delle funzionalità consente di determinare come presentare le informazioni di sola lettura.

 Il testo può trovarsi all'interno di una casella di testo di sola lettura. Questo indica in genere che il contenuto può essere selezionato e copiato, anche se non può essere modificato.

 ![Formattazione del testo informativo per i campi di sola lettura&#45;](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **Formattazione del testo informativo per campi di sola lettura**

#### <a name="watermarks"></a>Filigrane
 Sebbene il wording possa essere lo stesso, la differenza tra le filigrane e il testo informativo è che le filigrane vengono sostituite con il contenuto quando il controllo o la finestra non è vuota e il testo didattico rimane sempre visibile.

 Le filigrane devono essere usate quando una finestra o un controllo è vuoto. Indicano che cosa è necessario fare per popolare l'area e possono includere collegamenti all'azione per aprire le finestre pertinenti, ad esempio un'origine di trascinamento.

##### <a name="visual-style"></a>Stile di visualizzazione

- Le filigrane devono essere centrate orizzontalmente all'interno della finestra.

- Le filigrane devono essere allineate al centro, non allineate a sinistra.

- Le filigrane possono essere centrate verticalmente o posizionate nella parte superiore dell'area. Se si trova nella parte superiore dell'area, è necessario che sia disponibile spazio sufficiente per la filigrana.

- Usare il `Environment.GrayText` token di colore e il tipo di carattere dell'ambiente standard. I collegamenti ipertestuali devono usare i token condivisi del collegamento ipertestuale standard: `Environment.PanelHyperlink` ,, `Environment.PanelHyperlinkHover` `Environment.PanelHyperlinkPressed` e `Environment.PanelHyperlinkDisabled` .

- Non è possibile selezionare le filigrane in background

- Se possibile, includere i collegamenti nella filigrana per aiutare l'utente a iniziare.

  ![Testo della filigrana in una finestra di progettazione](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![Testo della filigrana in una finestra degli strumenti](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Esempi di testo della filigrana in Visual Studio**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Pulsanti e collegamenti ipertestuali

### <a name="overview"></a>Panoramica
 I pulsanti e i controlli dei collegamenti (collegamenti ipertestuali) devono seguire le [indicazioni di base sul desktop di Windows sui collegamenti ipertestuali](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) per l'utilizzo, il wording, il ridimensionamento e la spaziatura.

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

#### <a name="examples"></a>Esempi
 ![Collegamenti ai comandi della barra informazioni in seguito a un messaggio di stato](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **Collegamenti ai comandi usati nella barra informazioni dopo un messaggio di stato**

 ![Collegamenti usati nel popup CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **Collegamenti usati nel popup CodeLens**

 ![Collegamenti usati come comandi secondari](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **Collegamenti utilizzati per i comandi secondari in cui i pulsanti attraggono troppa attenzione**

### <a name="common-buttons"></a>Pulsanti comuni

#### <a name="text"></a>Text
 Seguire le linee guida per la scrittura nel [testo e nella terminologia dell'interfaccia utente](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Stile di visualizzazione

##### <a name="standard-dialogs"></a>Finestre di dialogo standard
 La maggior parte dei pulsanti in Visual Studio verrà visualizzata nelle finestre di dialogo standard e non deve avere uno stile. Devono riflettere l'aspetto standard dei pulsanti come stabilito dal sistema operativo.

##### <a name="themed"></a>Tema
 In alcuni casi, i pulsanti possono essere utilizzati all'interno dell'interfaccia utente con stile e questi pulsanti devono avere uno stile appropriato. Per informazioni sui controlli con tema, vedere [dialoghi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Pulsanti speciali

#### <a name="browse-buttons"></a>Sfoglia... pulsanti
 **[Sfoglia...]** i pulsanti vengono utilizzati in griglie, finestre di dialogo e finestre degli strumenti e altri elementi dell'interfaccia utente non modale. Visualizzano una selezione che assiste l'utente nella compilazione di un valore in un controllo. Sono disponibili due varianti di questo pulsante, Long e short.

 ![Pulsante &#93; di esplorazione &#91;lungo](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **Pulsante Long [Browse...]**

 ![Pulsante con i puntini di sospensione brevi solo&#45;&#91;Sfoglia... &#93;](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **Pulsante con i puntini di sospensione-solo short [...]**

 Quando usare il pulsante con i puntini di sospensione-solo breve:

- Se è presente più di un pulsante Long **[Browse...]** in una finestra di dialogo, ad esempio quando più campi consentono l'esplorazione. Usare il pulsante Short **[...]** per ogni per evitare le chiavi di accesso confuse create da questa situazione (**&browse** e **B&Rows** nella stessa finestra di dialogo).

- In una finestra di dialogo stretta o quando non è disponibile un punto ragionevole per inserire il pulsante lungo.

- Se il pulsante verrà visualizzato in un controllo griglia.

  Linee guida per l'uso del pulsante:

- Non usare una chiave di accesso. Per accedervi utilizzando la tastiera, è necessario che l'utente Tab dal controllo adiacente. Verificare che l'ordine di tabulazione sia tale che qualsiasi pulsante Sfoglia si trovi immediatamente dopo il campo da riempire. Non usare mai un carattere di sottolineatura al di sotto del primo periodo.

- Impostare la proprietà **nome** di Microsoft Active ACCESSIBILITY (MSAA) su **Sfoglia...** (inclusi i puntini di sospensione) in modo che lo screen reader lo legga come "Browse" e non "dot-dot-dot" o "period-period-period". Per i controlli gestiti, questo significa impostare la proprietà **AccessibleName** .

- Non usare mai un pulsante con i puntini di sospensione **[...]** per qualsiasi elemento tranne un'azione browse. Se, ad esempio, è necessario un pulsante **[nuovo...]** senza spazio sufficiente per il testo, è necessario riprogettare la finestra di dialogo.

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
 ![Ridimensionamento &#91;pulsante Sfoglia... &#93;](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **Ridimensionamento di pulsanti [Sfoglia...]**

 ![Pulsanti di spaziatura &#91;Sfoglia... &#93;](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **Spaziatura [Sfoglia...] pulsanti**

#### <a name="graphical-buttons"></a>Pulsanti grafici
 Alcuni pulsanti devono sempre usare un'immagine grafica e non includono mai testo per conservare spazio ed evitare problemi di localizzazione. Questi vengono spesso usati nei selezionatori dei campi e in altri elenchi ordinabili.

> [!NOTE]
> Gli utenti devono premere TAB per questi pulsanti (non sono presenti chiavi di accesso), quindi inserirli in un ordine ragionevole. Eseguire il mapping della proprietà Name del pulsante all'azione necessaria in modo che le utilità per la lettura dello schermo interpretino correttamente l'azione del pulsante.

|Nome|Immagine|
|-|-|
|Aggiunta|![Pulsante grafico "Aggiungi"](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|Rimuovi|![Pulsante grafico "Rimuovi"](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|Aggiungi tutto|![Pulsante grafico "Aggiungi tutto"](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|Rimuovi tutto|![Pulsante grafico "Rimuovi tutto"](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|Sposta su|![Pulsante grafico "Sposta su"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|Sposta giù|![Pulsante grafico "Sposta giù"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|Delete|![Pulsante grafico "Elimina"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Ridimensionamento e spaziatura
 Il dimensionamento dei pulsanti grafici è uguale a quello per la versione breve del pulsante **[Sfoglia...]** (26x23 pixel):

 ![Pulsante con e senza colore trasparente visualizzato](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente che Mostra**

### <a name="hyperlinks"></a>Collegamenti ipertestuali
 I collegamenti ipertestuali sono ideali per le azioni basate sull'esplorazione, ad esempio l'apertura di un argomento della guida, una finestra di dialogo modale o una procedura guidata. Se per un comando viene usato un collegamento ipertestuale, deve sempre visualizzare una modifica visibile e percettibile per l'interfaccia utente. In generale, le azioni di cui viene eseguito il commit in un'azione (ad esempio Salva, Annulla ed Elimina) vengono comunicate con un pulsante.

#### <a name="writing-style"></a>Stile di scrittura
 Seguire le [indicazioni sul desktop di Windows per il testo dell'interfaccia utente](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Non usare "ulteriori informazioni su", "ulteriori informazioni su" o "ottenere assistenza per questo". Al contrario, frasere il testo del collegamento alla Guida in termini di domanda principale fornita dal contenuto della guida. Ad esempio, "**ricerca per categorie aggiungere un server al Esplora server?**"

#### <a name="visual-style"></a>Stile di visualizzazione

- I collegamenti ipertestuali devono sempre usare [il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se lo stile di un collegamento ipertestuale non è corretto, il colore rosso viene attivato quando attivo o viene visualizzato un colore diverso dopo la visita.

- Non includere sottolineature nello stato di riposo del controllo, a meno che il collegamento non sia un frammento di frase all'interno di una frase completa, ad esempio in una filigrana.

- Le sottolineature non devono essere visualizzate al passaggio del mouse. Al contrario, il feedback all'utente che il collegamento è attivo è un lieve cambiamento di colore e il cursore di collegamento appropriato.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Visualizzazioni ad albero

### <a name="overview"></a>Panoramica
 Le visualizzazioni ad albero forniscono un modo per organizzare elenchi complessi in gruppi padre-figlio. Un utente può espandere o comprimere i gruppi padre per visualizzare o nascondere gli elementi figlio sottostanti. Ogni elemento all'interno di una visualizzazione albero può essere selezionato per fornire ulteriori azioni.

 In questo argomento viene illustrata l'utilizzo accettabile, la progettazione corretta e la funzionalità delle visualizzazioni ad albero.

#### <a name="in-this-topic"></a>Contenuto dell'argomento

- [Stile di visualizzazione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interazioni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Stile di visualizzazione

#### <a name="expanders"></a>Espansori
 I controlli di visualizzazione albero devono essere conformi alla progettazione dell'espansore utilizzata da Windows e Visual Studio. Ogni nodo utilizza un controllo Expander per rivelare o nascondere gli elementi sottostanti. L'uso di un controllo Expander garantisce la coerenza per gli utenti che potrebbero incontrare visualizzazioni ad albero diverse all'interno di Windows e Visual Studio.

 ![Controllo visualizzazione albero corretto](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Corretto: stile appropriato del nodo della visualizzazione albero usando un controllo Expander**

 ![Nodi visualizzazione albero non corretti](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **Errato: stile non corretto del nodo della visualizzazione albero**

#### <a name="selection"></a>Selection
 Quando si seleziona un nodo nella visualizzazione albero, l'evidenziazione deve espandersi fino alla larghezza massima del controllo di visualizzazione albero. Ciò consente agli utenti di identificare chiaramente l'elemento selezionato. I colori di selezione riflettono il tema corrente di Visual Studio.

 ![Controllo visualizzazione albero corretto](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Corretto: l'evidenziazione del nodo selezionato corrisponde all'intera larghezza del controllo di visualizzazione albero.**

 ![Evidenziazione visualizzazione albero non corretta](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **Errato: l'evidenziazione del nodo selezionato non rientra nell'intera larghezza del controllo di visualizzazione albero.**

#### <a name="icons"></a>Icone
 Le icone devono essere usate solo nei controlli di visualizzazione albero se assistono nell'identificazione visiva delle differenze tra gli elementi. In generale, le icone devono essere usate solo in elenchi eterogenei in cui le icone contengono informazioni per distinguere i tipi di elementi. In un elenco omogeneo l'uso delle icone può essere spesso visualizzato come rumore e deve essere evitato. In tal caso, l'icona del gruppo (padre) può indicare il tipo di elementi al suo interno. L'eccezione a questa regola è se l'icona è dinamica e viene utilizzata per indicare lo stato.

#### <a name="scroll-bars"></a>Barre di scorrimento
 Le barre di scorrimento devono essere sempre nascoste se il contenuto rientra nel controllo di visualizzazione albero. È accettabile che le barre di scorrimento siano nascoste o semi-trasparenti in una finestra scorrevole e visualizzate quando la finestra contenente la visualizzazione albero ha lo stato attivo o al passaggio del mouse sulla visualizzazione albero stessa.

 ![Visualizzazione albero con barre di scorrimento](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **Vengono visualizzate le barre di scorrimento verticali e orizzontali perché il contenuto ha superato i limiti del controllo di visualizzazione albero.**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interazioni

#### <a name="context-menus"></a>Menu di scelta rapida
 Un nodo della visualizzazione albero può rivelare le opzioni del sottomenu in un menu di scelta rapida. Questa situazione si verifica in genere quando un utente ha fatto clic con il pulsante destro del mouse su un elemento o ha premuto il tasto menu su una tastiera di Windows con l'elemento selezionato. È importante che il nodo ottenga lo stato attivo ed è selezionato. Ciò consente all'utente di identificare l'elemento a cui appartiene il sottomenu.

 ![Nodo albero selezionato e menu di scelta rapida](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_ContextMenu")

 **L'elemento che ha generato il menu di scelta rapida acquisisce lo stato attivo per notificare all'utente l'elemento selezionato.**

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

  ![Controllo albero in Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Un controllo tridente in Visual Studio**
