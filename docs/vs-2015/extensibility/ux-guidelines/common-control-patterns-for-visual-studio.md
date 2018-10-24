---
title: Pattern di controllo comuni per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56f1afba0db8ba213a601835ca7a8df39d56f171
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860760"
---
# <a name="common-control-patterns-for-visual-studio"></a>Pattern di controllo comuni per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Controlli comuni  
  
### <a name="overview"></a>Panoramica  
 Controlli comuni costituiscono la maggior parte dell'interfaccia utente in Visual Studio. Controlli più comuni usati nell'interfaccia di Visual Studio devono seguire le [linee guida per l'interazione di Desktop Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Questo documento è specifico di Visual Studio e descrive i casi speciali o i dettagli che aumentano le linee guida di Windows.  
  
#### <a name="common-controls-in-this-topic"></a>Controlli comuni in questo argomento  
  
-   [Barre di scorrimento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Elenchi a discesa e caselle combinate](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Pulsanti di opzione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Fotogrammi di gruppo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [I collegamenti ipertestuali e pulsanti](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Visualizzazioni dell'albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
 La prima cosa da prendere in considerazione quando lo stile di controlli è se i controlli verranno utilizzati nell'interfaccia utente con temi. Controlli dell'interfaccia utente standard sono a tema dell'interfaccia utente e deve seguire [lo stile Desktop di Windows normale](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), vale a dire che non sono basate su modelli r e verrà visualizzato il relativo aspetto del controllo predefinito.  
  
-   **Le finestre di dialogo standard (utilità):** non a tema. Eseguire operazioni non reimpostare come modelli. Usare i valori predefiniti di stile di controllo di base.  
  
-   **Strumento windows, editor di documenti, le aree di progettazione e finestre di dialogo con tema:** usare specializzato aspetto a tema usando il servizio di colore.  
  
###  <a name="BKMK_Scrollbars"></a> Barre di scorrimento  
 Le barre di scorrimento deve seguire [comuni modelli di interazione per le barre di scorrimento di Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) , a meno che essi vengono integrati con le informazioni sul contenuto, ad esempio nell'editor del codice.  
  
###  <a name="BKMK_InputFields"></a> Campi di input  
 Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per le caselle di testo](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   I campi di input non devono essere concepiti nelle finestre di dialogo utilità. Utilizzare lo stile di base intrinseco per il controllo.  
  
-   I campi di input con tema devono essere utilizzati solo nelle finestre di dialogo con tema e finestre degli strumenti.  
  
#### <a name="specialized-interactions"></a>Interazioni specializzate  
  
-   I campi di sola lettura avrà uno sfondo grigio (disattivato) ma in primo piano predefinito (attivo).  
  
-   Necessari i campi devono avere  **\<necessarie >** come filigrane al loro interno. Non è necessario modificare il colore di sfondo tranne in rare situazioni.  
  
-   Convalida degli errori: vedere [notifiche e avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   I campi di input devono essere ridimensionati per adattarsi al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza di un campo lungo, ad esempio un percorso. Lunghezza potrebbe essere un'indicazione all'utente di limitazioni per quanto riguarda il numero di caratteri è consentito nel campo.  
  
     ![Larghezza del controllo di campo di input errato](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")   
     **Lunghezza del campo di input non corretto: è improbabile che il nome sarà questa lunghezza.**  
  
     ![Larghezza del controllo di campo di input di correggere](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")   
     **Correggere la lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto.**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Elenchi a discesa e caselle combinate  
 Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per elenchi a discesa e caselle combinate](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   Nelle finestre di dialogo utilità, eseguire operazioni non reimpostare come modelli del controllo. Utilizzare lo stile di base intrinseco per il controllo.  
  
-   Nell'interfaccia utente con temi, elenchi a discesa e caselle combinate seguono i temi standard per i controlli.  
  
#### <a name="layout"></a>Layout  
 Elenchi a discesa e caselle combinate deve essere ridimensionate per adattarla al contenuto, non per adattarsi alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza di un campo lungo, ad esempio un percorso.  
  
 ![Drop non corretto&#45;layout verticale](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")  
  
 **Lunghezza di campo errato per un controllo elenco a discesa**  
  
 ![Drop corretto&#45;layout verticale](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 04_CorrectDropDownLayout")  
  
 **Lunghezza di campo corretto per un controllo elenco a discesa**  
  
###  <a name="BKMK_CheckBoxes"></a> Caselle di controllo  
 Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per le caselle di controllo](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   Nelle finestre di dialogo utilità, eseguire operazioni non reimpostare come modelli del controllo. Utilizzare lo stile di base intrinseco per il controllo.  
  
-   Nell'interfaccia utente di eventuali temi delle caselle di controllo seguono i temi standard per i controlli.  
  
#### <a name="specialized-interactions"></a>Interazioni specializzate  
  
-   L'interazione con una casella di controllo non deve mai visualizzata una finestra di dialogo o passare a un'altra area.  
  
-   Allineare le caselle di controllo con la linea di base della prima riga del testo.  
  
     ![Allineamento non corretto della casella di controllo](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")   
     **Allineamento non corretto della casella di controllo: casella di controllo coincide con il testo.**  
  
     ![Casella di controllo dell'allineamento correggere](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")   
     **Correggere l'allineamento della casella di controllo: casella di controllo è allineato con la linea di base della prima riga del testo.**  
  
###  <a name="BKMK_RadioButtons"></a> Pulsanti di opzione  
 Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per i pulsanti di opzione](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
 Nelle finestre di dialogo utilità, eseguire operazioni non pulsanti di opzione di stile. Utilizzare lo stile di base intrinseco per il controllo.  
  
#### <a name="specialized-interactions"></a>Interazioni specializzate  
 Non è necessario usare un frame di gruppo per racchiudere le scelte radio.  
  
###  <a name="BKMK_GroupFrames"></a> Fotogrammi di gruppo  
 Per la modalità di interazione tipico, seguire le [linee guida per Windows Desktop per i frame gruppo](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
 Nelle finestre di dialogo utilità, eseguire operazioni non fotogrammi di gruppo di stile. Utilizzare lo stile di base intrinseco per il controllo.  
  
#### <a name="layout"></a>Layout  
  
-   Non è necessario usare un frame di gruppo per racchiudere le opzioni di radio, a meno che non è necessario mantenere la distinzione di gruppo in un layout di una stretta.  
  
-   Non utilizzare mai una cornice di gruppo per un singolo controllo.  
  
-   Talvolta è accettabile usare un righello orizzontale invece di un contenitore di frame di gruppo.  
  
##  <a name="BKMK_TextControls"></a> Controlli testo  
  
### <a name="labels"></a>Etichette  
  
#### <a name="active-label-state"></a>Stato attivo etichetta  
  
##### <a name="utility-standard-dialogs"></a>Utilità di finestre di dialogo (standard))  
  
-   In generale, seguire le indicazioni di Windows Desktop per etichette del controllo.  
  
-   Nelle finestre di dialogo utilità, le etichette risulterà non in grassetto, il colore del tipo di carattere e testo di ambiente standard. Visualizzare [tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
-   Puntini di sospensione devono attenersi sempre le etichette.  
  
##### <a name="signature-themed-dialogs"></a>Firma (tema) le finestre di dialogo)  
 I controlli Label possono essere grigio chiaro o in grassetto.  
  
#### <a name="disabled-label-state"></a>Stato Disabled etichetta  
 Le etichette devono riflettere l'aspetto del controllo che cui sono associate. Ad esempio, se il controllo associato è disabilitato, l'etichetta deve apparire grigio e disabilitata. Questo viene in genere gestito dal sistema operativo e richiede un trattamento speciale.  
  
#### <a name="dynamic-labels"></a>Etichette dinamiche  
 Modifica di etichette dinamico in base alla selezione corrente. Se possibile, usare le etichette dinamiche nei layout master-Details per consentire all'utente di comprendere che le informazioni visualizzate sono destinate a una specifica selezione e informazioni generali non.  
  
 ![Etichetta dinamica usata con contenuto dinamico](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")  
  
 **Esempio di un'etichetta dinamica usata con contenuto dinamico**  
  
#### <a name="instructional-text"></a>Testo esplicativo  
 Alcuni elementi dell'interfaccia trarre vantaggio da testo esplicativo per consentire all'utente di comprendere lo scopo dell'interfaccia utente o per indicare l'azione da intraprendere.  
  
-   Testo esplicativo è più comune nella parte superiore delle finestre di dialogo, ma può essere visualizzati in altre aree per fornire istruzioni a un raggruppamento di controllo complessa.  
  
-   Testo esplicativo non è interattivo, ma può contenere collegamenti ipertestuali agli argomenti della Guida.  
  
-   Usare testo esplicativo sporadicamente e solo quando necessario.  
  
##### <a name="formatting"></a>Formattazione  
 Testo esplicativo deve essere di tipo di carattere ambiente, il testo di controllo standard (non a tema). Visualizzare [tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
 Per informazioni dettagliate sulla scrittura di testo delle istruzioni, vedere [interfaccia utente di testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
 ![Formattazione del testo esplicativo](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 02_InstructionalTextFormatting")  
  
 **Testo esplicativo in una finestra di dialogo di Visual Studio**  
  
#### <a name="informational-text"></a>Testo informativo  
 Testo informativo è il testo che fornisce all'utente informazioni aggiuntive. È possibile statico o dinamico o utilizzato come una notifica. È sempre di sola lettura, ma se è utile per l'utente abbia la possibilità di copiare le informazioni, testo dinamico deve essere inserito in un contenitore di controlli, ad esempio un campo di testo di sola lettura.  
  
##### <a name="dynamic-context-specific-text"></a>Testo dinamico (specifico di contesto)  
 Testo informazioni dinamiche cambia a seconda del contesto, ad esempio quando l'utente passa lo stato attivo. Spesso, ma non sempre, contenuto dinamico è associato a un'etichetta dinamica.  
  
 ![Testo delle informazioni dinamiche](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")  
  
 **Testo informativo dinamico cambia a seconda del contesto.**  
  
##### <a name="formatting"></a>Formattazione  
 Esistono due modi per visualizzare i campi di testo di sola lettura: direttamente nell'interfaccia utente della superficie di attacco (vedere sopra) o contenuta all'interno di un altro controllo, ad esempio una casella di testo o frame di gruppo. Entrambi sono corretto a seconda della situazione. È compito di progettazione di funzionalità per determinare la modalità presentare le informazioni di sola lettura.  
  
 Testo può essere all'interno di una casella di testo di sola lettura. In genere indica che il contenuto può essere selezionato e copiato, sebbene non sia modificabile.  
  
 ![Formattazione per la lettura del testo informativo&#45;solo i campi](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")  
  
 **Formattazione per i campi di sola lettura del testo informativo**  
  
#### <a name="watermarks"></a>Filigrane  
 Durante la formulazione potrebbe essere lo stesso, la differenza tra le filigrane e testo esplicativo è che le filigrane vengono sostituite con il contenuto quando il controllo o finestra non è vuota e testo esplicativo rimane visibile in qualsiasi momento.  
  
 Usare le filigrane quando una finestra o il controllo è vuoto. Essi indicano quali azioni devono essere eseguite per popolare l'area e possono includere collegamenti alle azioni per aprire finestre pertinenti, ad esempio un'origine di trascinamento.  
  
##### <a name="visual-style"></a>Stile di visualizzazione  
  
- Le filigrane devono essere centrate orizzontalmente all'interno della finestra.  
  
- Le filigrane devono essere allineato al centro, non allineata a sinistra.  
  
- Le filigrane possono essere centrate verticalmente o posizionate nella parte superiore dell'area. Se si trova nella parte superiore dell'area, è necessario sufficiente spazio di sopra in modo da evidenziare la filigrana.  
  
- Usare il `Environment.GrayText` il tipo di carattere di colore ambiente token e standard. I collegamenti ipertestuali devono usare i token standard hyperlink condiviso: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, e `Environment.PanelHyperlinkDisabled`.  
  
- Non è possibile selezionare le filigrane sullo sfondo  
  
- Se possibile, includere i collegamenti della filigrana per consentire all'utente di iniziare.  
  
  ![Il testo in una finestra di progettazione della filigrana](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")  
  
  ![Il testo in una finestra degli strumenti della filigrana](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")  
  
  **Esempi di testo della filigrana in Visual Studio**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> I collegamenti ipertestuali e pulsanti  
  
### <a name="overview"></a>Panoramica  
 I controlli di pulsanti e collegamento (i collegamenti ipertestuali) devono seguire [linee guida di Windows Desktop base sui collegamenti ipertestuali](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) per l'utilizzo, formulazione, ridimensionamento e la spaziatura.  
  
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
 ![Collegamenti ai comandi sulla barra delle informazioni seguendo un messaggio di stato](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")  
  
 **Comandi collegamenti usati nella barra delle informazioni seguendo un messaggio di stato**  
  
 ![Collegamenti usati nel popup CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")  
  
 **Collegamenti usati nel popup CodeLens**  
  
 ![Collegamenti usati come comandi secondari](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")  
  
 **Collegamenti usati per i comandi secondari in cui è opportuno considerare troppa attenzione pulsanti**  
  
### <a name="common-buttons"></a>Pulsanti comuni  
  
#### <a name="text"></a>Testo  
 Seguire le linee guida di scrittura [interfaccia utente di testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
##### <a name="standard-dialogs"></a>Finestre di dialogo standard  
 La maggior parte dei pulsanti in Visual Studio verranno visualizzati nelle finestre di dialogo standard e non devono essere applicato uno stile. Essi devono riflettere l'aspetto dei pulsanti standard come imposto dal sistema operativo.  
  
##### <a name="themed"></a>Con tema  
 In alcuni casi, i pulsanti possono essere utilizzati all'interno dell'interfaccia utente con stile e questi pulsanti devono essere applicato uno stile in modo appropriato. Visualizzare [finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) per informazioni sui controlli a tema.  
  
### <a name="special-buttons"></a>Pulsanti speciali  
  
#### <a name="browse-buttons"></a>Sfoglia... pulsanti  
 **[Sfoglia...]**  i pulsanti vengono utilizzati nelle griglie, le finestre di dialogo e finestre degli strumenti e altri elementi dell'interfaccia utente non modale. Verranno inoltre visualizzati un controllo di selezione che assiste l'utente durante la compilazione di un valore in un controllo. Esistono due varianti di questo pulsante, lungo e corti.  
  
 ![Long &#91;Sfoglia... &#93; sul pulsante](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")  
  
 **Il pulsante [Sfoglia...] lungo**  
  
 ![A breve i puntini di sospensione&#45;solo &#91;Sfoglia... &#93; sul pulsante](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")  
  
 **Pulsante con i soli puntini di sospensione breve [...]**  
  
 Quando usare il pulsante puntini di sospensione-only breve:  
  
- Se è presente più di un long **[Sfoglia...]**  pulsante in una finestra di dialogo, ad esempio quando diversi campi consentono per l'esplorazione. Usare il breve **[...]**  per ognuno evitare la confusione chiavi di accesso create da questa situazione (**& esplorare** e **esplo & ra** nella finestra di dialogo stessa).  
  
- In una finestra di dialogo stretto o quando non è possibile utilizzare per inserire il pulsante di tempo ragionevole.  
  
- Se il pulsante verrà visualizzato in un controllo griglia.  
  
  Linee guida per il pulsante:  
  
- Non usare una chiave di accesso. Per l'accesso utilizzando la tastiera, l'utente deve scheda dal controllo adiacente. Assicurarsi che l'ordine di tabulazione sia in modo che qualsiasi pulsante rientra immediatamente dopo il campo che è riempire. Non usare mai un carattere di sottolineatura seguito dal primo periodo.  
  
- Microsoft Active Accessibility (MSAA) impostata **Name** proprietà **Sfoglia...**  (tra cui i puntini di sospensione) in modo che schermata verrà letto, come "Sfoglia" e non "punto-punto-punto" o "periodo-punto-punto". Per i controlli gestiti, ciò significa impostazione il **AccessibleName** proprietà.  
  
- Non usare mai i puntini di sospensione **[...]**  pulsante esclusivamente per un'azione di esplorazione. Ad esempio, se è necessario un **[novità]**  pulsante ma non hanno spazio sufficiente per il testo, quindi la finestra di dialogo debba essere riprogettata.  
  
##### <a name="sizing-and-spacing"></a>Ridimensionamento e la spaziatura  
 ![Ridimensionamento &#91;Sfoglia... &#93; pulsanti](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")  
  
 **Il ridimensionamento di pulsanti [Sfoglia...]**  
  
 ![Spaziatura &#91;Sfoglia... &#93; pulsanti](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")  
  
 **Spaziatura tra pulsanti [Sfoglia...]**  
  
#### <a name="graphical-buttons"></a>Pulsanti con interfaccia grafici  
 Alcuni pulsanti devono sempre usare un'immagine grafica e testo per liberare spazio ed evitare problemi di localizzazione non includere mai. Questi vengono spesso usati in altri elenchi ordinabili e selezioni di campo.  
  
> [!NOTE]
>  Gli utenti devono premere tab per questi pulsanti (non sono presenti chiavi di accesso), quindi, inserirli in un ordine ragionevole. Eseguire il mapping di proprietà name del pulsante per l'azione che richiede in modo che gli screen reader interpretare correttamente l'azione sul pulsante.  
  
|||  
|-|-|  
|Aggiunta|![Pulsante grafico "Aggiungi"](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 08_ButtonAdd")|  
|Rimuovi|![Pulsante grafico "Rimuovi"](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 09_ButtonRemove")|  
|Aggiungi tutto|![Pulsante grafico "Aggiungi tutto"](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|  
|Rimuovi tutto|![Pulsante grafico "Rimuovi tutto"](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 11_ButtonRemoveAll")|  
|Sposta su|![Pulsante grafico "Sposta su"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|  
|Sposta giù|![Pulsante grafico "Sposta giù"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|  
|Eliminare|![Pulsante grafico "Elimina"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 14_ButtonDelete")|  
  
##### <a name="sizing-and-spacing"></a>Ridimensionamento e la spaziatura  
 Definizione delle dimensioni per i pulsanti con interfaccia grafico sono uguale a quella versione breve del **[Sfoglia...]**  pulsante (26 x 23 pixel):  
  
 ![Pulsante con e senza colore trasparente visualizzato](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")  
  
 **Aspetto di un'immagine grafica sul pulsante, con e senza colore trasparente visualizzato**  
  
### <a name="hyperlinks"></a>Collegamenti ipertestuali  
 I collegamenti ipertestuali sono particolarmente adatti per azioni basate su navigazione, ad esempio l'apertura di un argomento della Guida, finestra di dialogo modale o configurazione guidata. Se viene usato un collegamento ipertestuale per un comando, è necessario visualizzare sempre una modifica visibile e notevole all'interfaccia utente. In generale, le azioni che eseguono il commit a un'azione (ad esempio, salvare, Cancel ed eliminare) meglio vengono comunicate tramite un pulsante.  
  
#### <a name="writing-style"></a>Stile di scrittura  
 Seguire le [linee guida di Windows Desktop per il testo dell'interfaccia utente](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Non usare "Informazioni su altre informazioni," "Indicare mi ulteriori su" o "Get help con questo" formulazione. Al contrario, una frase di testo del collegamento della Guida in termini di una risposta dal contenuto della Guida in linea la domanda primario. Ad esempio, "**come aggiungere un server in Esplora Server?**"  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   Utilizzano sempre i collegamenti ipertestuali [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se un collegamento ipertestuale non viene applicato lo stile corretto, fa lampeggiare rosso quando è attivo o Mostra un colore diverso dopo da visitare.  
  
-   Non includere il controllo posizionato dello stato, a meno che il collegamento è un frammento di frase all'interno di una frase completa, ad esempio in una filigrana di colore.  
  
-   Sottolineature non dovrebbe essere visualizzato al passaggio del mouse. È invece il feedback all'utente che il collegamento è attivo una modifica del colore leggero e il cursore di collegamento appropriato.  
  
##  <a name="BKMK_TreeViews"></a> Visualizzazioni dell'albero  
  
### <a name="overview"></a>Panoramica  
 Visualizzazioni dell'albero forniscono un modo per organizzare complessi sono elencati in gruppi padre-figlio. Un utente può espandere o comprimere i gruppi padre e mostrare o nascondere gli elementi figlio sottostanti. È possibile selezionare ogni elemento all'interno di una visualizzazione albero per fornire un'ulteriore azione.  
  
 Questo argomento illustra l'uso accettabile, progettare in modo corretto e funzionalità delle visualizzazioni dell'albero.  
  
#### <a name="in-this-topic"></a>Contenuto dell'argomento  
  
-   [Stile di visualizzazione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [Interazioni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Stile di visualizzazione  
  
#### <a name="expanders"></a>Espansori  
 Controlli di visualizzazione albero dovrebbero essere conforme alla progettazione dell'espansore utilizzata da Windows e Visual Studio. Ogni nodo Usa un controllo expander per mostrare o nascondere gli elementi sottostanti. Utilizzo di un controllo expander offre coerenza per gli utenti che possono verificarsi visualizzazioni dell'albero diverso all'interno di Windows e Visual Studio.  
  
 ![Controllo di visualizzazione albero di correggere](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")  
  
 **Corretto: stile appropriato della visualizzazione struttura ad albero usando un controllo expander**  
  
 ![Nodi della visualizzazione albero non corretta](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")  
  
 **Non corretta: stile di visualizzazione non corretta della visualizzazione struttura ad albero**  
  
#### <a name="selection"></a>Selection  
 Quando si seleziona un nodo all'interno della visualizzazione struttura ad albero, è necessario espandere l'evidenziazione per l'intera larghezza del controllo di visualizzazione albero. Ciò consente agli utenti di identificare chiaramente quale elemento è stato selezionato. Selezione colori devono riflettere il tema di Visual Studio corrente.  
  
 ![Controllo di visualizzazione albero di correggere](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")  
  
 **Corretto: evidenziazione del nodo selezionato appropriato per l'intera larghezza del controllo di visualizzazione albero.**  
  
 ![Evidenziazione visualizzazione albero non corretta](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")  
  
 **Non corretta: evidenziazione del nodo selezionato non rientra l'intera larghezza del controllo di visualizzazione albero.**  
  
#### <a name="icons"></a>Icone  
 Le icone devono essere utilizzate solo nei controlli di visualizzazione albero se è aiutare a identificare visivamente le differenze tra gli elementi. In generale, le icone devono essere usate solo in elenchi eterogenei in cui le icone contengono informazioni per distinguere i tipi di elementi. In un elenco omogeneo mediante icone spesso può essere considerata come il rumore e deve essere evitata. In questo caso l'icona di gruppo (padre) può indicare il tipo di elementi in esso contenuti. L'eccezione a questa regola può essere se l'icona è dinamico e viene utilizzato per indicare lo stato.  
  
#### <a name="scroll-bars"></a>Barre di scorrimento  
 Le barre di scorrimento devono essere sempre nascosto se il contenuto viene adattato all'interno del controllo di visualizzazione albero. È accettabile per le barre di scorrimento per essere nascosta o semi-trasparenti in una finestra scorrevole e vengono visualizzate quando la finestra contenente la visualizzazione struttura ad albero è attiva o al momento del passaggio del mouse della struttura ad albero visualizzare se stesso.  
  
 ![Albero vista con le barre di scorrimento](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")  
  
 **Entrambe le barre di scorrimento orizzontale e verticale vengono visualizzate perché il contenuto ha superato i limiti del controllo di visualizzazione albero.**  
  
###  <a name="BKMK_TreeViewInteractions"></a> Interazioni  
  
#### <a name="context-menus"></a>Menu di scelta rapida  
 Un nodo della visualizzazione struttura ad albero possa visualizzare le opzioni di sottomenu in un menu di scelta rapida. In genere, ciò si verifica quando un utente con pulsante destro del mouse di un elemento o ha premuto il tasto di Menu su una tastiera di Windows con l'elemento selezionato. È importante che il nodo Ottiene lo stato attivo e che sia selezionato. Ciò consente di identificare quale elemento a cui appartiene il sottomenu.  
  
 ![Menu nodo e il contesto dell'albero selezionato](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")  
  
 **L'elemento che ha generato il contesto menu riceve lo stato attivo per notificare all'utente quale elemento è stata selezionata.**  
  
#### <a name="keyboard"></a>Tastiera  
 Visualizzazione albero dovrebbe offrono la possibilità di selezionare gli elementi ed Espandi/Comprimi nodi tramite la tastiera. Ciò garantisce che navigazione soddisfi i requisiti di accessibilità.  
  
##### <a name="tree-view-control"></a>Controllo di visualizzazione albero  
 Controlli dell'albero di Visual Studio devono seguire la navigazione da tastiera comuni:  
  
-   **Freccia verso l'alto:** spostando verso l'alto dell'albero per selezionare elementi  
  
-   **Freccia giù:** spostando verso il basso l'albero per selezionare elementi  
  
-   **Freccia destra:** espandere un nodo dell'albero  
  
-   **Freccia sinistra:** comprimere un nodo dell'albero  
  
-   **Immettere chiave:** avviare, caricare, eseguire l'elemento selezionato  
  
##### <a name="trid-tree-view-and-grid-view"></a>Albero (visualizzazione struttura ad albero e griglia)  
 Un controllo albero è un controllo complesso che contiene una visualizzazione albero all'interno di una griglia. Espansione e compressione di esplorazione dell'albero deve rispettare gli stessi comandi da tastiera in una visualizzazione ad albero, con le aggiunte seguenti:  
  
- **Freccia destra:** espandere un nodo. Dopo aver espanso il nodo, deve continuare passando alla colonna più vicina a destra. Navigazione deve essere interrotta alla fine della riga.  
  
- **Scheda:** consente di passare alla più vicina cella a destra.  Alla fine della riga, navigazione continua alla riga successiva.  
  
- **Maiusc + Tab:** consente di passare per la cella più vicina a sinistra.  All'inizio della riga, navigazione continua nella cella più a destra nella riga precedente.  
  
  ![Controllo albero in Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")  
  
  **Un controllo albero in Visual Studio**

