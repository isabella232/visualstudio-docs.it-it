---
title: Colori condivisi per Visual Studio | Microsoft Docs
description: Informazioni su come usare elementi e temi Visual Studio shell comuni per progettare un'interfaccia utente personalizzata coerente con l'ambiente Visual Studio personalizzato.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0818826989132a67be54d8aa35db8bad69251a82
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145354"
---
# <a name="shared-colors-for-visual-studio"></a>Colori condivisi per Visual Studio
Quando si progetta un'interfaccia utente che usa elementi comuni della shell di Visual Studio o si desidera che l'elemento dell'interfaccia sia coerente con funzionalità simili, usare i nomi di token esistenti nei file di definizione del pacchetto per scegliere e assegnare i colori. In questo modo, l'interfaccia utente resta coerente con l'intero ambiente di Visual Studio e viene aggiornata automaticamente quando vengono aggiunti o aggiornati temi.

Questo articolo descrive gli elementi dell'interfaccia utente comuni e i nomi di token usati da questi elementi, a cui è possibile fare riferimento durante la compilazione di un'interfaccia utente simile. Per informazioni specifiche su come accedere a questi token di colore, vedere [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Assicurarsi di usare correttamente i nomi di token:

- **Usare i nomi di token in base alla funzione e non al colore stesso.** I colori condivisi comuni sono associati a elementi dell'interfaccia specifici e destinati solo a essere usati per le stesse funzionalità o altre simili. Ad esempio, evitare di riutilizzare il colore di una casella combinata premuta per un'animazione di stato rotante solo perché si ha una preferenza per questo colore. Le funzioni della casella combinata e dell'animazione sono diverse e, se il colore associato alla casella combinata cambia, potrebbe non essere più un colore appropriato per l'elemento dell'animazione. Un uso coerente del colore aiuta a orientare correttamente gli utenti e a impedire confusione.

- **Usare colori di sfondo e del testo nella combinazione corretta.** I colori di sfondo destinati a essere usati con il testo implicano un colore del testo associato. Non usare colori del testo diversi da quelli specificati per un determinato sfondo. Se non è presente un colore di testo associato, non usare tale colore di sfondo per qualsiasi superficie su cui si prevede di visualizzare il testo. Altre combinazioni di colori di testo e sfondo potrebbero comportare un'interfaccia illeggibile.

- **Usare colori dei controlli appropriati per la rispettiva posizione.** In alcuni stati, alcuni Visual Studio non hanno colori di bordo e di sfondo separati. Al contrario, selezionano questi colori dalle superfici sottostanti. Assicurarsi di usare sempre i nomi di token appropriati per la posizione in cui si posiziona il controllo.

> [!IMPORTANT]
> Non usare i token trovati nelle categorie "Pagina iniziale" o "Cider".

## <a name="common-shared-controls"></a>Controlli condivisi comuni

Quando si usa una barra Visual Studio standard nella funzionalità, si ha accesso ai controlli della shell con stile. Non è consigliabile ridefinire il modello di questi controlli comuni. Tuttavia, se si intende compilare una barra dei comandi personalizzata, potrebbe essere necessario compilare anche controlli personalizzati. In questo caso, assicurarsi di usare i nomi di token corretti per ognuno dei controlli seguenti, in modo che l'interfaccia utente sia coerente con il resto di Visual Studio.

### <a name="button-controls"></a>Controlli pulsante

![Controllo pulsante con linea rossa](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i pulsanti nell'well document che si vuole integrare con i temi Visual Studio (chiaro, scuro, blu o un tema di Contrasto elevato sistema). | ... per i pulsanti che verranno visualizzati su uno sfondo personalizzato che non fa parte di un Visual Studio tema. |

**Pulsante: stato standard**

![Pulsante Standard](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Pulsante Standard

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.Button` |
| Bordo del pulsante | `CommonControls.ButtonBorder` |

**Pulsante: stato predefinito**

![Pulsante Predefinito](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Pulsante Predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonDefault` |
| Bordo del pulsante | `CommonControls.ButtonBorderDefault` |

**Pulsante: stato disabilitato**

![Pulsante Disabilitato](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Pulsante Disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonDisabled` |
| Bordo del pulsante | `CommonControls.ButtonBorderDisabled` |

**Pulsante: stato del passaggio del mouse**

![Pulsante al passaggio del mouse](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Pulsante al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonHover` |
| Bordo del pulsante | `CommonControls.ButtonBorderHover` |

**Pulsante: stato premuto**

![Pulsante premuto](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Pulsante premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonPressed` |
| Bordo del pulsante | `CommonControls.ButtonBorderPressed` |

**Pulsante: stato attivo**

![Pulsante con stato attivo](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Pulsante con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonFocused` |
| Bordo del pulsante | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controlli casella di controllo
![Casella di controllo (linea rossa)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Casella di controllo (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i controlli casella di controllo contenuti nell'area del documento. | ... per qualsiasi interfaccia utente che non sia un controllo casella di controllo. |

**Casella di controllo: stato predefinito**

![Casella di controllo](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Casella di controllo Predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackground` |
| Bordo | `CommonControls.CheckBoxBorder` |
| Testo | `CommonControls.CheckBoxText` |
| Icona | `CommonControls.CheckBoxGlyph` |

**Casella di controllo: stato disabilitato**

![Casella di controllo Disabilitata](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Casella di controllo Disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundDisabled` |
| Bordo | `CommonControls.CheckBoxBorderDisabled` |
| Testo | `CommonControls.CheckBoxTextDisabled` |
| Icona | `CommonControls.CheckBoxGlyphDisabled` |

**Casella di controllo: stato del passaggio del mouse**

 ![Casella di controllo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Casella di controllo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundHover` |
| Bordo | `CommonControls.CheckBoxBorderHover` |
| Testo | `CommonControls.CheckBoxTextHover` |
| Icona | `CommonControls.CheckBoxGlyphHover` |

**Casella di controllo: stato premuto**

![Casella di controllo premuta](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Casella di controllo premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundPressed` |
| Bordo | `CommonControls.CheckBoxBorderPressed` |
| Testo | `CommonControls.CheckBoxTextPressed` |
| Icona | `CommonControls.CheckBoxGlyphPressed` |

**Casella di controllo: stato attivo**

![Casella di controllo Con stato attivo](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Casella di controllo Con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundFocused` |
| Bordo | `CommonControls.CheckBoxBorderFocused` |
| Testo | `CommonControls.CheckBoxTextFocused` |
| Icona | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Elenchi a discesa e caselle combinate
![Casella combinata/elenco a discesa (redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Casella combinata/elenco a discesa (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per gli elenchi a discesa e le caselle combinate nell'oggetto documento. | ... per qualsiasi interfaccia utente che non sia un elenco a discesa o una casella combinata. |
| | ... per gli elenchi a [discesa della barra dei comandi o](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) le [caselle combinate](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Elenchi a discesa e caselle combinate: stato predefinito**

![Casella combinata/elenco a discesa predefinita](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Casella combinata/elenco a discesa predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackground` |
| Bordo | `CommonControls.ComboBoxBorder` |
| Testo | `CommonControls.ComboBoxText` |
| Separatore | `CommonControls.ComboBoxSeparator` |
| Icona | `CommonControls.ComboBoxGlyph` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackground` |

**Elenchi a discesa e caselle combinate: stato disabilitato**

![Casella combinata/elenco a discesa disabilitata](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Casella combinata/elenco a discesa disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundDisabled` |
| Bordo | `CommonControls.ComboBoxBorderDisabled` |
| Testo | `CommonControls.ComboBoxTextDisabled` |
| Separatore | `CommonControls.ComboBoxSeparatorDisabled` |
| Icona | `CommonControls.ComboBoxGlyphDisabled` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Elenchi a discesa e caselle combinate: stato del passaggio del mouse**

![Casella combinata/a discesa al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Casella combinata/a discesa al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundHover` |
| Bordo | `CommonControls.ComboBoxBorderHover` |
| Testo | `CommonControls.ComboBoxTextHover` |
| Separatore | `CommonControls.ComboBoxSeparatorHover` |
| Icona | `CommonControls.ComboBoxGlyphHover` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Elenchi a discesa e caselle combinate: stato premuto**

![Casella combinata/elenco a discesa premuta](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Casella combinata/elenco a discesa premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundPressed` |
| Bordo | `CommonControls.ComboBoxBorderPressed` |
| Testo | `CommonControls.ComboBoxTextPressed` |
| Separatore | `CommonControls.ComboBoxSeparatorPressed` |
| Icona | `CommonControls.ComboBoxGlyphPressed` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Visualizzazione degli elementi dell'elenco a discesa e delle caselle combinate: stato premuto**

 ![Visualizzazione elemento elenco a discesa/casella combinata premuta](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Visualizzazione elemento elenco a discesa/casella combinata premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Bordo | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Testo dell'elemento | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Ombreggiatura dello sfondo | `CommonControls.ComboBoxListBackgroundShadow` |

**Elenchi a discesa e caselle combinate: stato attivo**

![Casella combinata/elenco a discesa con lo stato attivo](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Casella combinata/elenco a discesa con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundFocused` |
| Bordo | `CommonControls.ComboBoxBorderFocused` |
| Testo | `CommonControls.ComboBoxTextFocused` |
| Separatore | `CommonControls.ComboBoxSeparatorFocused` |
| Icona | `CommonControls.ComboBoxGlyphFocused` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Elenchi a discesa e caselle combinate: selezione dell'input di testo**

![Selezione input testo casella combinata/elenco a discesa](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Selezione input testo casella combinata/elenco a discesa

| Elemento | Nome token: Category.color |
| --- | --- |
| Evidenziazione | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controlli per dati tabulari (griglia)
I controlli per dati tabulari, noti anche come controlli griglia, sono controlli comuni per Visual Studio, che possono essere usati per presentare grandi quantità di dati in più colonne. I controlli per dati tabulari standard possono trovarsi in diverse posizioni all'interno di Visual Studio, ad esempio nella finestra degli strumenti Elenco errori, nei report IntelliTrace e nella visualizzazione degli heap della memoria. Usare sempre i controlli per dati tabulari standard forniti. In alcuni casi rari, si potrebbe non avere accesso ai controlli per dati tabulari standard. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri controlli per dati tabulari in Visual Studio.

![Controllo griglia/dati tabulari (linea rossa)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Controllo griglia/dati tabulari (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i controlli tabulari o griglia. | ... per qualsiasi interfaccia utente che non sia un controllo tabulare o griglia. |

#### <a name="column-headers"></a>Intestazioni di colonna
Le intestazioni di colonna sono costituite da uno sfondo, un bordo, il testo del titolo e un glifo facoltativo, usato in genere quando una griglia viene ordinata in base alla colonna.

**Intestazione di colonna: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Header.Default` |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Header.Glyph` |
| Bordo | `Header.SeparatorLine` |

**Intestazione di colonna: stato del passaggio del mouse**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Header.MouseOver` |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Header.MouseOverGlyph` |
| Bordo | `Header.SeparatorLine` |

**Intestazione di colonna: stato premuto**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundPressed` |
| Primo piano (testo) | `CommonControls.CheckBoxBorderPressed` |
| Primo piano (glifo) | `CommonControls.CheckBoxTextPressed` |
| Bordo | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementi della visualizzazione elenco
 Gli elementi della visualizzazione elenco sono costituiti da uno sfondo e da contenuto. Il contenuto può essere sotto forma di testo, icona o entrambi.

**Elementi della visualizzazione elenco: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Modalità trasparente |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Bordo | Nessuno |

**Elementi della visualizzazione elenco: stato attivo**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActiveText` |
| Bordo | Nessuno |

**Elementi della visualizzazione elenco: stato inattivo**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactiveText` |
| Bordo | Nessuno |

### <a name="ui-text"></a>Testo dell'interfaccia utente

#### <a name="instructional-text"></a>Testo informativo
Il testo informativo offre una spiegazione principale importante delle attività da eseguire in una finestra di dialogo o in una pagina del documento.

![Testo informativo predefinito](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Testo informativo predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Testo informativo secondario
Nelle pagine del documento con molto testo e controlli, un testo informativo usa un valore di colore diverso. Ciò consente di comunicare le informazioni più importanti e ridurre la densità complessiva degli elementi dell'interfaccia utente. Vedere anche la sezione seguente sul testo dei suggerimenti.

![Testo informativo secondario](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Testo informativo secondario

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Testo dei suggerimenti
Il testo del suggerimento viene visualizzato in un controllo vuoto, sotto un controllo o in un'area del documento vuota per mostrare all'utente cosa fare successivamente. È possibile usare il testo dei suggerimenti con sfondi finestra o controllo.

**Testo del suggerimento predefinito**

![Testo del suggerimento predefinito](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Testo suggerimento predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlEditHintText` |

**Testo del suggerimento obbligatorio**

![Testo del suggerimento obbligatorio](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Testo del suggerimento obbligatorio

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlRequiredHintText` |
| Sfondo | `Environment.ControlRequiredBackground` |

**Testo del controllo casella di ricerca**

> Vedere [Caselle di](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) ricerca per altri token di colore correlati al controllo Cerca.

![Testo del controllo casella di ricerca](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Testo del controllo casella di ricerca

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Il collegamento ipertestuale è un controllo che non ha una coppia primo piano/sfondo. In tutti i casi, usare il colore del collegamento ipertestuale in primo piano, che verrà visualizzato correttamente su sfondi scuro, grigio e bianco. Se non si usa il token di colore per il controllo collegamento ipertestuale, verrà visualizzato il colore di sistema predefinito per "premuto", che lampeggia in rosso. Questo è il segnale che il controllo non usa il token di colore dell'ambiente corretto.

![Collegamento ipertestuale (linea rossa)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Collegamento ipertestuale (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando è necessario creare un collegamento ipertestuale personalizzato. | ... per qualsiasi elemento che non sia un collegamento ipertestuale. |

**Collegamento ipertestuale: stato predefinito**

![Collegamento ipertestuale predefinito](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Collegamento ipertestuale predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlink` |

**Collegamento ipertestuale: stato del passaggio del mouse**

![Collegamento ipertestuale al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Collegamento ipertestuale al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlinkHover` |

**Collegamento ipertestuale: stato premuto**

![Collegamento ipertestuale premuto](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Collegamento ipertestuale premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlinkPressed` |

**Collegamento ipertestuale: stato disabilitato**

![Collegamento ipertestuale disabilitato](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Collegamento ipertestuale disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Barre informazioni
Le barre informazioni vengono usate per fornire altre informazioni su un contesto specifico e sono sempre visualizzate nella parte superiore della finestra di un documento o di una finestra degli strumenti.

![Barra informazioni (linea rossa)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Barra informazioni (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... durante la creazione di barre informazioni personalizzate. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra informazioni. |

**Barra informazioni: stato predefinito**

![Barra informazioni predefinita](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Barra informazioni predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.InfoBarBackground` |
| Primo piano (testo) | `InfoBar.InfoBar` |
| Bordo | `InfoBar.InfoBarBorder` |

**Pulsante Chiudi barra delle informazioni ( &times; ): stato predefinito**

![Pulsante Chiudi barra informazioni predefinito ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Pulsante Chiudi barra informazioni predefinito ( &times; )

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.CloseButton` |
| Bordo | `InfoBar.CloseButtonBorder` |
| Icona | `InfoBar.CloseButtonGlyph` |

**Pulsante Chiudi barra informazioni ( &times; ): stato del passaggio del mouse**

![Pulsante Chiudi barra delle informazioni ( &times; ) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Pulsante Chiudi barra delle informazioni ( &times; ) al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.CloseButtonHover` |
| Bordo | `InfoBar.CloseButtonHoverBorder` |
| Icona | `InfoBar.CloseButtonHoverGlyph` |

**Pulsante Chiudi barra delle informazioni ( &times; ): stato premuto**

![Pulsante Chiudi barra informazioni premuto ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Pulsante Chiudi barra informazioni premuto ( &times; )

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.CloseButtonDown` |
| Bordo | `InfoBar.CloseButtonDownBorder` |
| Icona | `InfoBar.CloseButtonDownGlyph` |

**Pulsante collegamento ipertestuale della barra informazioni: stato predefinito**

![Pulsante collegamento ipertestuale predefinito della barra informazioni](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Pulsante collegamento ipertestuale predefinito della barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `InfoBar.Hyperlink` |

**Pulsante collegamento ipertestuale della barra informazioni: stato del passaggio del mouse**

![Pulsante collegamento ipertestuale della barra informazioni al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Pulsante collegamento ipertestuale della barra informazioni al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseOver`<br />(Con sottolineatura) |

**Pulsante collegamento ipertestuale della barra informazioni: stato premuto**

![Pulsante di collegamento ipertestuale della barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Pulsante di collegamento ipertestuale della barra informazioni premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseDown`<br />(Con sottolineatura) |

**Collegamento ipertestuale inline della barra informazioni (all'interno di una frase): stato predefinito**

![Pulsante di collegamento ipertestuale predefinito della barra informazioni inline](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Pulsante di collegamento ipertestuale predefinito della barra informazioni inline

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `InfoBar.Hyperlink` |

**Collegamento ipertestuale inline della barra informazioni (all'interno di una frase): stato del passaggio del mouse**

![Pulsante del collegamento ipertestuale inline della barra informazioni al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Pulsante del collegamento ipertestuale inline della barra informazioni al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseOver`<br />(Con sottolineatura) |

**Collegamento ipertestuale inline della barra informazioni (all'interno di una frase): stato premuto**

![Pulsante di collegamento ipertestuale inline della barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Pulsante di collegamento ipertestuale inline della barra informazioni premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseDown`<br />(Con sottolineatura) |

**Pulsante della barra informazioni: stato predefinito**

![Pulsante predefinito della barra informazioni](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Pulsante predefinito della barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.Button` |
| Primo piano (testo) | `InfoBar.Button` |
| Bordo | `InfoBar.ButtonBorder` |

**Pulsante della barra informazioni: stato del passaggio del mouse**

![Pulsante della barra informazioni al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Pulsante della barra informazioni al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonMouseOver` |
| Primo piano (testo) | `InfoBar.ButtonMouseOver` |
| Bordo | `InfoBar.ButtonMouseOverBorder` |

**Pulsante della barra informazioni: stato premuto**

![Pulsante della barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Pulsante della barra informazioni premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonMouseDown` |
| Primo piano (testo) | `InfoBar.ButtonMouseDown` |
| Bordo | `InfoBar.ButtonMouseDownBorder` |

**Pulsante della barra informazioni: stato disabilitato**

![Pulsante della barra informazioni disabilitato](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Pulsante della barra informazioni disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonDisabled` |
| Primo piano (testo) | `InfoBar.ButtonDisabled` |
| Bordo | `InfoBar.ButtonDisabledBorder` |

**Pulsante della barra informazioni: stato attivo**

![Pulsante della barra informazioni con stato attivo](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Pulsante della barra informazioni con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonFocus` |
| Primo piano (testo) | `InfoBar.ButtonFocus` |
| Bordo | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barre di scorrimento
Lo stile delle barre di scorrimento viene applicato Visual Studio'ambiente e non è necessario che siano a colori. Tuttavia, è possibile decidere di sfruttare i colori usati nelle barre di scorrimento in modo che l'interfaccia utente appai sempre coerente con questa parte dell'Visual Studio ambiente.

![Barra di scorrimento (redline)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barra di scorrimento (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea un'interfaccia utente che si vuole associare alle Visual Studio di scorrimento. | ... per qualsiasi elemento che non si vuole sempre associare all'interfaccia utente della barra di scorrimento. |

**Barra di scorrimento: stato predefinito**

![Barra di scorrimento predefinita](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barra di scorrimento predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Barra di scorrimento | `Environment.ScrollBarBackground` |
| Primo piano (anteprima) | `Environment.ScrollBarThumbBackground` |

**Barra di scorrimento: stato del passaggio del mouse**

![Barra di scorrimento al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barra di scorrimento al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Barra di scorrimento | `Environment.ScrollBarBackground` |
| Primo piano (anteprima) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barra di scorrimento: stato premuto**

![Barra di scorrimento premuta](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Barra di scorrimento premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Barra di scorrimento | `Environment.ScrollBarBackground` |
| Primo piano (anteprima) | `Environment.ScrollBarThumbPressedBackground` |

**Freccia della barra di scorrimento: stato predefinito**

![Freccia predefinita della barra di scorrimento](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Freccia predefinita della barra di scorrimento

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ScrollBarArrowBackground`<br />Impostare lo stesso colore della barra di scorrimento. |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyph` |

**Freccia della barra di scorrimento: stato del passaggio del mouse**

![Freccia della barra di scorrimento al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Freccia della barra di scorrimento al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ScrollBarArrowMouseOverBackground`<br />Impostare lo stesso colore della barra di scorrimento. |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Freccia della barra di scorrimento: stato premuto**

![Freccia della barra di scorrimento premuta](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Freccia della barra di scorrimento premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ScrollBarArrowPressedBackground`<br />Impostare lo stesso colore della barra di scorrimento. |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Caselle di ricerca
Quando è possibile, usare il controllo di ricerca comune fornito dall'ambiente di Visual Studio. I colori della casella di ricerca si trovano nella categoria "SearchControl" nel file **ShellColors.pkgdef** , che contiene i nomi di token per il campo di input, il pulsante di azione, il pulsante a discesa e il menu a discesa.

Una casella di ricerca può avere diversi stati, alcuni dei quali si escludono a vicenda:

- "Con stato attivo" e "con stato non attivo" indicano se il cursore si trova o meno nella casella di testo.

- "Attivo" e "inattivo" indicano se l'utente ha inserito una query di ricerca nella casella di testo.

- "Passaggio del mouse" significa che l'utente ha posizionato il cursore del mouse sulla casella di ricerca (questo stato sostituisce tutti gli altri).

- "Disabilitato" significa che la funzionalità di ricerca è disattivata per il contesto corrente.

![Casella di ricerca (redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Casella di ricerca (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si progetta una casella di ricerca personalizzata. | ... per qualsiasi elemento che non sia una casella di ricerca. |
| | ... per qualsiasi elemento che non si vuole sempre associare all'interfaccia utente della casella di ricerca. |

**Campo di input per la ricerca con stato attivo**

![Campo di input per la ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Campo di input per la ricerca con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.FocusedBackground` |
| Primo piano (testo) | `SearchControl.FocusedBackground` |
| Bordo | `SearchControl.FocusedBorder` |
| Separatore | `SearchControl.FocusedDropDownSeparator` |

**Campo di input di ricerca attivo non attivo**

![Campo di input di ricerca con stato non attivo](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Campo di input di ricerca attivo senza stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.SearchActiveBackground` |
| Primo piano (testo) | `SearchControl.SearchActiveBackground` |
| Bordo | `SearchControl.UnfocusedBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Campo di input di ricerca non attivo e inattivo**

![Campo di input di ricerca non attivo e inattivo](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo di input di ricerca non attivo e inattivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.Unfocused` |
| Primo piano (testo) | `SearchControl.Unfocused` |
| Bordo | `SearchControl.UnfocusedBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Campo di input di ricerca evidenziato (solo testo)**

![Campo di input di ricerca evidenziato](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Campo di input di ricerca evidenziato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.Selection` |
| Primo piano (testo) | `SearchControl.FocusedBackground` |
| Bordo | Nessuno |
| Separatore | `SearchControl.FocusedDropDownSeparator` |

**Campo di input di ricerca disabilitato**

![Campo di input di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Campo di input di ricerca disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.Disabled` |
| Primo piano (testo) | `SearchControl.Disabled` |
| Bordo | `SearchControl.DisabledBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Pulsante azione di ricerca mirata**

![Pulsante di azione di ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Pulsante azione di ricerca mirata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo Cerca) | `SearchControl.SearchGlyph` |
| Primo piano (glifo Arresta) | `SearchControl.StopGlyph` |
| Primo piano (glifo Cancella) | `SearchControl.ClearGlyph` |
| Bordo | N/A |

**Pulsante azione di ricerca non messa a fuoco**

![Pulsante azione di ricerca non messa a fuoco](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Pulsante azione di ricerca non messa a fuoco

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/A |
| Primo piano (glifo Cerca) | `SearchControl.SearchGlyph` |
| Primo piano (glifo Arresta) | `SearchControl.StopGlyph` |
| Primo piano (glifo Cancella) | `SearchControl.ClearGlyph` |
| Bordo | N/A |

**Pulsante di azione di ricerca premuto**

![Pulsante di azione di ricerca premuto](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Pulsante di azione di ricerca premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.ActionButtonMouseDown` |
| Primo piano (glifo) | `SearchControl.ActionButtonMouseDownGlyph` |
| Bordo | `SearchControl.ActionButtonMouseDownBorder` |

**Pulsante di azione di ricerca disabilitato**

![Pulsante di azione di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Pulsante di azione di ricerca disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Bordo | Nessuno |

**Pulsante a discesa ricerca con stato attivo**

![Pulsante a discesa ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Pulsante a discesa ricerca con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.FocusedDropDownButton` |
| Primo piano (glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Bordo | `SearchControl.FocusedDropDownButtonBorder` |

**Pulsante a discesa per la ricerca con stato non in stato di a fuoco**

![Pulsante a discesa per la ricerca con stato non in stato di a fuoco](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Pulsante a discesa per la ricerca con stato non in stato di a fuoco

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.UnfocusedDropDownButton` |
| Primo piano (glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Bordo | `SearchControl.UnfocusedDropDownButtonBorder` |

**Pulsante a discesa di ricerca premuto**

![Pulsante a discesa di ricerca premuto](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Pulsante a discesa di ricerca premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.MouseDownDropDownButton` |
| Primo piano (glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Bordo | `SearchControl.MouseDownDropDownButtonBorder` |

**Pulsante a discesa di ricerca disabilitato**

![Pulsante a discesa di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Pulsante a discesa di ricerca disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Bordo | Nessuno |

#### <a name="search-drop-down-lists"></a>Elenchi a discesa di ricerca
Il menu a discesa della casella di ricerca può essere leggermente più complesso rispetto ad altri menu a discesa in Visual Studio. Le sezioni "Ricerche suggerite" e "Opzioni di ricerca" possono essere visualizzate singolarmente o insieme nel menu e ognuna viene colorata separatamente. Una linea separa le due sezioni quando sono visualizzate insieme e un bordo circonda l'intero menu a discesa.

![Elenco a discesa di ricerca (redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Elenco a discesa di ricerca (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea un elenco a discesa di ricerca personalizzato. | ... per gli elenchi a discesa visualizzati in altri contesti. |
| ... i nomi di token corretti per i componenti dell'elenco corretti. | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Elementi dell'elenco a discesa di ricerca**

| Elemento | Nome token: Category.color |
| --- | --- |
| Bordo | `SearchControl.PopupBorder` |
| Separatore | `SearchControl.PopupSectionHeaderSeparator` |
| Ombreggiatura | `Environment.DropShadowBackground` |

**Ricerche suggerite: stato predefinito**

![Ricerche suggerite predefinite](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Ricerche suggerite predefinite

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `SearchControl.PopupItemText` |

**Ricerche suggerite: stato del passaggio del mouse**

![Ricerche suggerite al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Ricerche suggerite al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `SearchControl.PopupMouseOverItemText` |
| Bordo | `SearchControl.PopupControlMouseOverBorder` |

**Opzioni di ricerca: stato predefinito**

![Casella di controllo di ricerca](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Opzioni di ricerca predefinite (casella di controllo)

![Opzioni di ricerca](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Opzioni di ricerca predefinite (collegamento)

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupSectionBackgroundGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxText` |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonText` |
| Sfondo dell'intestazione | `SearchControl.PopupSectionHeaderGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo dell'intestazione) | `SearchControl.PopupSectionHeaderText` |

**Opzioni di ricerca: stato del passaggio del mouse**

![Opzioni di ricerca (casella di controllo) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opzioni di ricerca (casella di controllo) al passaggio del mouse

![Opzioni di ricerca (collegamento) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opzioni di ricerca (collegamento) al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxMouseDownText` |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonMouseDownText` |
| Bordo | `SearchControl.PopupControlMouseOverBorder` |

**Opzioni di ricerca: stato premuto**

![Opzioni di ricerca premute (casella di controllo)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Opzioni di ricerca premute (casella di controllo)

![Opzioni di ricerca premute (collegamento)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Opzioni di ricerca premute (collegamento)

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo della casella di controllo | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxMouseDownText` |
| Sfondo del collegamento | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Visualizzazioni albero
Diverse finestre degli strumenti, tra cui Esplora soluzioni, Esplora server e Visualizzazione classi, implementano uno schema organizzativo gerarchico i cui colori sono controllati dai nomi dei colori nella `TreeView` categoria. Tutti gli elementi in una visualizzazione albero hanno colori di sfondo e del testo. Gli elementi che hanno elementi figlio annidati hanno anche glifi che indicano se ogni elemento è espanso o compresso.

![Visualizzazione albero (linea rossa)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Visualizzazione albero (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque sia necessario implementare una visualizzazione organizzativa gerarchica. | ... per qualsiasi elemento che non sia simile a una visualizzazione albero. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Elemento della visualizzazione albero: stato predefinito**

![Elemento predefinito della visualizzazione albero](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Elemento predefinito della visualizzazione albero

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.Background` |
| Primo piano (testo) | `TreeView.Background` |
| Primo piano (glifo) | `TreeView.Glyph` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: stato del passaggio del mouse**

![Elemento della visualizzazione albero al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Elemento della visualizzazione albero al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.Background` |
| Primo piano (testo) | `TreeView.Background` |
| Primo piano (glifo) | `TreeView.GlyphMouseOver` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: trascinare lo stato**

![Elemento della visualizzazione albero al trascinamento](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Elemento della visualizzazione albero al trascinamento

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.DragOverItem` |
| Primo piano (testo) | `TreeView.DragOverItem` |
| Primo piano (glifo) | `TreeView.DragOverItemGlyph` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: selezionato, stato attivo**

![Elemento della visualizzazione albero selezionato e con stato attivo](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Elemento della visualizzazione albero selezionato e con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyph` |
| Bordo | `TreeView.FocusVisualBorder` |

**Elemento della visualizzazione albero: selezionato, stato non attivo**

![Elemento della visualizzazione albero selezionato e non con stato selezionato](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Elemento della visualizzazione albero selezionato e non con stato selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactive` |
| Primo piano (glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: stato attivo, selezionato e con stato attivo**

![Elemento della visualizzazione albero selezionato e con stato attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Elemento della visualizzazione albero selezionato e con stato attivo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordo | `TreeView.FocusVisualBorder` |

**Elemento della visualizzazione albero: stato selezionato, selezionato e non attivo**

![Elemento della visualizzazione albero selezionato e non attivato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Elemento della visualizzazione albero selezionato e non attivato al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordo | Nessuno |

## <a name="shell-appearance"></a>Aspetto della shell

### <a name="background"></a>Sfondo
Lo sfondo dell'ambiente è costituito da due livelli. Il livello inferiore è un colore a tinta unita che ricopre l'intero IDE. Il livello superiore si trova sotto lo scaffale dei comandi tra i canali Nascondi automaticamente della finestra degli strumenti, nei bordi destro e sinistro dell'IDE. I livelli di sfondo superiore e inferiore sono impostati sullo stesso colore nei temi Chiaro e Scuro.

![Visual Studio sfondo della shell (linea rossa)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio sfondo della shell (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per le posizioni in cui si vuole trovare la corrispondenza con lo sfondo dell'Visual Studio ambiente. | ... come riempimento per le posizioni che non sono superfici di sfondo. |
| | ... come sfondo su cui posizionare gli elementi in primo piano. |

**Aspetto della shell del livello inferiore**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.EnvironmentBackground` |

**Aspetto della shell di livello superiore**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Scaffale dei comandi
Due set di nomi di token vengono usati per gli sfondi dello scaffale dei comandi, uno per il punto in cui si trova la barra dei menu e l'altro per il punto in cui si trova la barra dei comandi. Un singolo gruppo della barra dei comandi ha valori di colore di sfondo propri, che vengono descritti in modo più dettagliato nella sezione "Barra dei comandi". Il testo della barra dei menu e della barra dei comandi viene descritto nelle rispettive sezioni.

![Visual Studio scaffale dei comandi (linea rossa)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio scaffale dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per le aree in cui si posizionano menu o barre degli strumenti. | ... per le aree che non sono simili a uno scaffale dei comandi. |
|... con la combinazione corretta di nome di token di sfondo/primo piano. | |

**Barra dei menu a scaffale dei comandi**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barra dei comandi a scaffale dei comandi**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Finestra Progettazione manifesto
La finestra Progettazione manifesto è stata progettata come strumento per semplificare la modifica del file manifesto in progetti Windows 8 e Windows Phone 8. Benché non sia disponibile per l'utilizzo alcun framework condiviso, potrebbe essere appropriato fare in modo che il layout di progettazione e i colori delle schede di orientamento/spostamento corrispondano alla struttura complessiva. Per altre informazioni sui dettagli del layout, vedere [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Progettazione manifesto (linea rossa)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Progettazione manifesto (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per finestre di progettazione simili a Progettazione manifesto. | ... se sono disponibili più di sei schede. |
| ... al posto di usare i controlli struttura a schede comuni nella parte superiore di un editor all'interno dell'area del documento. | ... per qualsiasi interfaccia utente non strutturata come Progettazione manifesto. |

**Scheda selezionata di Progettazione manifesto: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.TabActive` |
| Bordo | Nessuno |

**Riquadro di descrizione selezionato di Progettazione manifesto: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.DescriptionPane` |

**Pagina contenuto selezionata di Progettazione manifesto: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.Background` |
| Testo di supporto della finestra di dialogo | `ManifestDesigner.WatermarkText`<br />Il nome del token non corrisponde alla relativa funzione. |

**Scheda Progettazione manifesto: stato non selezionato**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.Tab.Inactive` |

**Scheda Progettazione manifesto: stato del passaggio del mouse**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Strutture dei comandi

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menu
I menu possono essere presenti in diverse posizioni all'interno di Visual Studio: la barra dei menu principale, incorporata nelle finestre dei documenti o degli strumenti o quando si fa clic con il pulsante destro del mouse in varie posizioni dell'IDE. Le implementazioni dei menu associati ad altri elementi dell'interfaccia utente vengono descritte nella sezione relativa al rispettivo elemento. È preferibile usare sempre l'implementazione dei menu standard fornita dall'ambiente di Visual Studio. Tuttavia, in alcuni casi rari si potrebbe non avere accesso ai menu standard di Visual Studio. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri menu in Visual Studio.

![Visual Studio menu (linea rossa)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio menu (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando è necessario creare un menu personalizzato.| ... solo il colore di sfondo. Usare sempre la combinazione sfondo/primo piano specificata. |
| ... quando si ha un nuovo componente dell'interfaccia utente che si vuole associare Visual Studio menu.| |

#### <a name="menu-titles"></a>Titoli dei menu
I titoli dei menu sono costituiti da uno sfondo, un bordo e il testo del titolo, nonché da un glifo facoltativo, in genere quando il menu si trova in una barra dei comandi.

![Titolo del menu (linea rossa)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Titolo del menu (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ogni volta che si crea un titolo di menu personalizzato. | ... per qualsiasi elemento che non deve sempre corrispondere al titolo del menu. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Titolo del menu: stato predefinito**

![Titolo del menu predefinito](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Titolo del menu predefinito

![Titolo del menu predefinito con glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Titolo del menu predefinito con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarMenuGlyph` |
| Bordo | Nessuno |

**Titolo del menu: stato del passaggio del mouse**

![Titolo menu al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Titolo menu al passaggio del mouse

![Titolo menu con glifo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Titolo menu con glifo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |
| Bordo | `Environment.CommandBarBorder` |

**Titolo del menu: stato premuto**

![Titolo del menu premuto](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Titolo del menu premuto

![Titolo del menu premuto con glifo](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Titolo del menu premuto con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Bordo | `Environment.CommandBarMenuBorder`<br />(Solo i lati sinistro, superiore e destro). |

**Titolo del menu: stato disabilitato**

![Titolo del menu disabilitato con glifo](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Titolo del menu disabilitato con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Primo piano (glifo) | `Environment.CommandBarTextInactive` |
| Bordo | Nessuno |

#### <a name="menu-items"></a>Voci di menu
Una singola voce di menu è costituita dal testo del menu e da un'icona facoltativa, una casella di controllo o un glifo del sottomenu. Il colore di sfondo e del testo cambiano al passaggio del mouse. Questo token di colore è una coppia sfondo/primo piano.

![Voci di menu con linea rossa](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Utilizzare... | Non usare ... |
|---|---|
| ... per qualsiasi elenco a discesa avviato da una barra dei menu o da una barra dei comandi. | ... per qualsiasi elenco a discesa in un altro contesto. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Voci di menu: stato predefinito**

![Voci di menu predefinite](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Voci di menu predefinite

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMenuBackgroundGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Bordo | `Environment.CommandBarMenuBorder` |
| Sfondo del canale delle icone | `Environment.CommandBarMenuIconBackground` |
| Separatore | `Environment.CommandBarMenuSeparator` |
| Ombreggiatura | `Environment.DropShadowBackground` |

**Voci di menu: stati selezionati e selezionati**

![Menu scelto](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Voce di menu Selezionata

![Menu selezionato](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Voce di menu selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Segno di spunta | `Environment.CommandBarCheckBox` |
| Sfondo del segno di spunta | `Environment.CommandBarSelectedIcon` |
| Sfondo dell'icona | `Environment.CommandBarSelected` |
| Bordo dell'icona | `Environment.CommandBarSelectedBorder` |

**Voci di menu: stato del passaggio del mouse**

![Menu al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Voce di menu al passaggio del mouse

![Menu scelto al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Voce di menu selezionata al passaggio del mouse

![Menu selezionato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Voce di menu selezionata al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMenuItemMouseOver` |
| Primo piano (testo) | `Environment.CommandBarMenuItemMouseOverText` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Segno di spunta | `Environment.CommandBarCheckBoxMouseOver` |
| Sfondo del segno di spunta | `Environment.CommandBarHoverOverSelectedIcon` |
| Sfondo dell'icona | `Environment.CommandBarHoverOverSelected` |
| Bordo dell'icona | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Voci di menu: stato disabilitato**

![Menu disabilitato](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Voce di menu Disabilitata

![Menu disabilitato selezionato](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Voce di menu Disabilitata con segno di spunta

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Segno di spunta | `Environment.CommandBarCheckBoxDisabled` |
| Sfondo del segno di spunta | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barre dei comandi
Una barra dei comandi può essere visualizzata in più posizioni all'interno dell'IDE Visual Studio, in particolare lo scaffale dei comandi e incorporata nelle finestre degli strumenti o dei documenti.

In generale, usare sempre l'implementazione della barra dei menu standard fornita dall'ambiente di Visual Studio. L'uso del meccanismo standard garantisce che tutti i dettagli visivi vengano visualizzati correttamente e che gli elementi interattivi abbiano un comportamento coerente con gli altri controlli della barra dei comandi di Visual Studio. Tuttavia, se è necessario compilare una barra dei comandi personalizzata, assicurarsi di applicare lo stile corretto usando i nomi di token seguenti.

![Barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barra dei comandi (linea rossa)

![Pulsante di overflow con linea rossa](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Pulsante Overflow (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile usare l'implementazione standard Visual Studio barra dei comandi. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi. |
| | ... per i componenti della barra dei comandi diversi da quelli per i quali vengono specificati i nomi dei token. |

#### <a name="command-bar-groups"></a>Gruppi di barre dei comandi
Un gruppo della barra dei comandi è costituito da un set correlato di controlli della barra dei comandi e può contenere un numero qualsiasi di pulsanti, pulsanti di menu combinato, menu a discesa, caselle combinate o menu. I colori per questi controlli sono determinati da nomi di token separati e vengono descritti singolarmente in altre sezioni di questa guida. Viene usata una linea di separazione per dividere un gruppo della barra dei comandi in sottogruppi correlati.

![Gruppo barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Gruppo barra dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile usare l'implementazione standard Visual Studio barra dei comandi. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi. |
| | ... per i componenti della barra dei comandi diversi da quelli per i quali vengono specificati i nomi dei token. |

**Gruppo di barre dei comandi: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Bordo | `Environment.CommandBarToolBarBorder` |
| Quadratino di trascinamento | `Environment.CommandBarDragHandle` |
| Separatore | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Icone dei comandi
![Icona del comando con linea rossa](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Icona di comando (linea rossa)

![Icona di comando con testo rosso](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Icona di comando con testo (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per tutti i pulsanti che verranno posizionati su una barra dei comandi. | ... per i controlli con nomi di token propri. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Icona di comando: stato predefinito**

![Icona del comando predefinita](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Icona di comando predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Bordo | N/A |

**Icona di comando: stato predefinito, selezionato**

![Icona di comando predefinita e selezionata](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Icona di comando predefinita e selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarSelected` |
| Primo piano (testo) | `Environment.CommandBarTextSelected` |
| Bordo | `Environment.CommandBarSelectedBorder` |

**Icona di comando: stati del passaggio del mouse o dello stato attivo**

![Icona di comando al passaggio del mouse o stato attivo](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Icona di comando al passaggio del mouse o stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Bordo | `Environment.CommandBarBorder` |

**Icona di comando: stati del passaggio del mouse o dello stato attivo, selezionato**

![Icona di comando selezionata al passaggio del mouse o stato attivo](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Icona di comando selezionata al passaggio del mouse o stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarHoverOverSelected` |
| Primo piano (testo) | `Environment.CommandBarTextHoverOverSelected` |
| Bordo | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icona di comando: stato premuto**

![Icona del comando premuta](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Icona del comando premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo) | `Environment.CommandBarTextMouseDown` |
| Bordo | `Environment.CommandBarBorder` |

**Icona del comando: stato disabilitato**

![Icona del comando disabilitata](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Icona del comando disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Bordo | N/A |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Caselle combinate della barra dei comandi

> [!IMPORTANT]
> Le caselle combinate sono simili agli elenchi a discesa, ma includono un'area di testo modificabile. Se l'elenco a discesa non include un'area di testo modificabile, usare i token di colore per gli elenchi a discesa [della barra dei comandi.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)

![Riga rossa della casella combinata della barra dei comandi](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Casella combinata della barra dei comandi (riga rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si compilano caselle combinate personalizzate. | ... per qualsiasi elemento che non si vuole sempre associare all'interfaccia utente della barra dei comandi. |
| ... quando si crea un controllo barra dei comandi simile a una casella combinata. | ... quando si ha accesso a una casella combinata con stile. |

**Campo di input della casella combinata della barra dei comandi: stato predefinito**

![Campo di input della casella combinata della barra dei comandi](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Campo di input della casella combinata della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxBackground` |
| Primo piano (testo) | `Environment.ComboBoxText` |
| Bordo | `Environment.ComboBoxBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato predefinito**

![Pulsante a discesa&#45;casella combinata](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Pulsante a discesa della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (glifo) | `Environment.ComboBoxGlyph` |

**Elenco a discesa della barra dei comandi: stato predefinito**

![Elenco a discesa della barra dei comandi](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Elenco a discesa della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxPopupBackgroundBegin`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo) | `Environment.ComboBoxItemText` |
| Bordo | `Environment.ComboBoxPopupBorder` |

**Campo di input della casella combinata della barra dei comandi: stato del passaggio del mouse**

![Campo di input della casella combinata della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Campo di input della casella combinata della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo) | `Environment.ComboBoxMouseOverText` |
| Bordo | `Environment.ComboBoxMouseOverBorder` |
| Separatore | `Environment.ComboBoxMouseOverSeparator` |

 **Pulsante a discesa della barra dei comandi: stato del passaggio del mouse**

![Pulsante a discesa della casella combinata della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Pulsante a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Elenco a discesa della barra dei comandi: stato del passaggio del mouse**

 ![Elenco a discesa della casella combinata della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Elenco a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (voce di menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primo piano (testo) | `Environment.ComboBoxItemMouseOverText` |
| Bordo (voce di menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo di input della casella combinata della barra dei comandi: stato attivo**

![Campo di input della casella combinata della barra dei comandi con stato attivo](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Campo di input della casella combinata della barra dei comandi con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxFocusedBackground` |
| Primo piano (testo) | `Environment.ComboBoxFocusedText` |
| Bordo | `Environment.ComboBoxFocusedBorder` |
| Separatore | `Environment.ComboBoxFocusedButtonSeparator` |

**Pulsante a discesa della barra dei comandi: stato attivo**

![Pulsante a discesa della barra dei comandi con stato attivo](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Pulsante a discesa della barra dei comandi con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxFocusedButtonBackground` |
| Primo piano (glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Campo di input della casella combinata della barra dei comandi: stato premuto**

![Campo di input della casella combinata della barra dei comandi premuto](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Campo di input della casella combinata della barra dei comandi premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxMouseDownBackground` |
| Primo piano (testo) | `Environment.ComboBoxMouseDownText` |
| Bordo | `Environment.ComboBoxMouseDownBorder` |
| Separatore | `Environment.ComboBoxMouseDownSeparator` |

**Pulsante a discesa della barra dei comandi: stato premuto**

![Pulsante a discesa della casella combinata della barra dei comandi premuto](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Pulsante a discesa della barra dei comandi premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo di input della casella combinata della barra dei comandi: stato disabilitato**

![Campo di input della casella combinata della barra dei comandi disabilitato](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Campo di input della casella combinata della barra dei comandi disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxDisabledBackground` |
| Primo piano (testo) | `Environment.ComboBoxDisabledText` |
| Bordo | `Environment.ComboBoxDisabledBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato disabilitato**

![Pulsante a discesa della casella combinata della barra dei comandi disabilitato](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Pulsante a discesa della barra dei comandi disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Elenchi a discesa della barra dei comandi

> [!IMPORTANT]
> Gli elenchi a discesa sono simili alle caselle combinate, ma non contengono aree di testo modificabili. Se l'elenco a discesa include un'area di testo modificabile, usare i token di colore per le [caselle](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)combinate della barra dei comandi .

![Elenco a discesa della barra dei comandi (redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Elenco a discesa della barra dei comandi (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si creano controlli elenco a discesa personalizzati. | ... per qualsiasi elemento non simile a un elenco a discesa. |
| | ... per caselle combinate o pulsanti di menu combinato. |

**Campo di selezione a discesa della barra dei comandi: stato predefinito**

![Campo di selezione predefinito della barra dei comandi](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Campo di selezione predefinito della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownBackground` |
| Primo piano (testo) | `DropDownText` |
| Bordo | `DropDownBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato predefinito**

![Pulsante a discesa predefinito della barra dei comandi](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Pulsante a discesa predefinito della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo) | `Environment.DropDownGlyph` |

**Elenco a discesa della barra dei comandi: stato predefinito**

![Elenco a discesa predefinito della barra dei comandi](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Elenco a discesa predefinito della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownPopupBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.ComboBoxItemText` |
| Bordo | `Environment.DropDownPopupBorder` |
| Ombreggiatura | `Environment.DropShadowBackground` |

**Campo di selezione a discesa della barra dei comandi: stato del passaggio del mouse**

![Campo di selezione della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Campo di selezione della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownMouseOverBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.DropDownMouseOverText` |
| Bordo | `Environment.DropDownMouseOverBorder` |
| Separatore | `Environment.DropDownButtonMouseOverSeparator` |

**Pulsante a discesa della barra dei comandi: stato del passaggio del mouse**

![Pulsante a discesa della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Pulsante a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.DropDownMouseOverGlyph` |

**Elenco a discesa della barra dei comandi: stato del passaggio del mouse**

![Elenco a discesa della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Elenco a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (voce di menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primo piano (testo) | `Environment.ComboBoxItemMouseOverText` |
| Bordo (voce di menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo di selezione a discesa della barra dei comandi: stato premuto**

![Rilasciare&#45;di selezione verso il basso premuto](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Campo di selezione della barra dei comandi premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownMouseDownBackground` |
| Primo piano (testo) | `Environment.DropDownMouseDownText` |
| Bordo | `Environment.DropDownMouseDownBorder` |
| Separatore | `Environment.DropDownButtonMouseDownSeparator` |

**Pulsante a discesa della barra dei comandi: stato premuto**

![Pulsante a discesa della barra dei comandi premuto](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Pulsante a discesa della barra dei comandi premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo di selezione a discesa della barra dei comandi: stato disabilitato**

![Campo di selezione della barra dei comandi disabilitato](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Campo di selezione della barra dei comandi disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownDisabledBackground` |
| Primo piano (testo) | `Environment.DropDownDisabledText` |
| Bordo | `Environment.DropDownDisabledBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato disabilitato**

![Pulsante a discesa della barra dei comandi disabilitato](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Pulsante a discesa della barra dei comandi disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/A |
| Primo piano (glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Pulsanti di divisione della barra dei comandi
I pulsanti di menu combinato condividono molti nomi di token con altri controlli della barra dei comandi, come pulsanti, menu e testo della barra dei comandi. Tutti i nomi di token dei pulsanti a discesa e di azione necessari vengono ripetuti qui per praticità. Gli elenchi a discesa dei pulsanti di menu a discesa dei pulsanti di menu sono implementazioni [dei menu della barra dei comandi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Pulsante di menu combinato con linea rossa](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Pulsante di menu suddiviso della barra dei comandi (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea un pulsante di menu suddiviso personalizzato. | ... per altri tipi di pulsanti. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Pulsante di menu suddiviso della barra dei comandi: stato predefinito**

![Pulsante di menu suddiviso predefinito della barra dei comandi](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Pulsante di menu suddiviso predefinito della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Bordo | N/A |
| Separatore | N/A |

**Pulsante di menu suddiviso della barra dei comandi: stato del passaggio del mouse**

![Pulsante di menu suddiviso della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Pulsante di menu suddiviso della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Bordo | `Environment.CommandBarBorder` |
| Separatore | `Environment.CommandBarSplitButtonSeparator` |

**Pulsante di menu suddiviso della barra dei comandi: stato premuto**

![Pulsante di menu suddiviso della barra dei comandi premuto](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Pulsante di menu suddiviso della barra dei comandi premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseDownBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.CommandBarTextMouseDown` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Bordo | `Environment.CommandBarBorder` |
| Separatore | N/A |

**Pulsante di menu suddiviso della barra dei comandi: stato disabilitato**

![Pulsante di menu suddiviso della barra dei comandi disabilitato](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Pulsante di menu suddiviso della barra dei comandi disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/A |
| Primo piano (testo) | `Environment.ComboBoxItemTextInactive` |
| Primo piano (glifo) | `Environment.CommandBarTextInactive` |
| Bordo | N/A |
| Separatore | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Pulsanti "Altre opzioni" e "Overflow" della barra dei comandi
Il pulsante "Altre opzioni" viene usato quando un gruppo della barra dei comandi può essere personalizzato aggiungendo o rimuovendo pulsanti della barra dei comandi correlati. Il pulsante "Overflow" viene visualizzato quando una barra dei comandi è troncata a causa della mancanza di spazio orizzontale e, dopo avervi fatto clic sopra, mostra un menu che contiene i pulsanti della barra dei comandi che non possono essere visualizzati. I colori per questi due pulsanti sono controllati dallo stesso set di nomi di token.

![Pulsante "Altre opzioni" della barra dei comandi (linea rossa)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Pulsante "Altre opzioni" della barra dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i pulsanti personalizzati "Altre opzioni" o "Overflow". | ... per i pulsanti che non hanno funzionalità simili a un pulsante "Altre opzioni" o "Overflow". |

**Pulsanti "Altre opzioni" e "Overflow" della barra dei comandi: stato predefinito**

![Pulsante "Altre opzioni" della barra dei comandi predefinito](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Pulsante "Altre opzioni" della barra dei comandi predefinito

![Pulsante "Overflow" predefinito della barra dei comandi](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Pulsante "Overflow" predefinito della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarOptionsBackground` |
| Primo piano (glifo) | `Environment.CommandBarOptionsGlyph` |

**Pulsanti "Altre opzioni" e "Overflow" della barra dei comandi: stato del passaggio del mouse**

![Pulsante "Altre opzioni" della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Pulsante "Altre opzioni" della barra dei comandi al passaggio del mouse

![Pulsante "Overflow" della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Pulsante "Overflow" della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Pulsanti "Altre opzioni" e "Overflow" della barra dei comandi: stato premuto**

![Pulsante "Altre opzioni" della barra dei comandi premuto](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Pulsante "Altre opzioni" della barra dei comandi premuto

![Overflow selezionato](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Pulsante "Overflow" della barra dei comandi premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Finestre dei documenti
Non è necessario replicare le finestre dei documenti, perché sono fornite dall'Visual Studio ambiente. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre dei documenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.

Quando si usano token di colore della finestra del documento, prestare attenzione a usarli solo per elementi simili e sempre in coppie. In caso contrario, si potrebbero ottenere risultati imprevisti nell'interfaccia utente.

### <a name="document-window-frames"></a>Frame della finestra del documento
Le finestre dei documenti possono essere ancorate nell'IDE o mobili come finestre separate. Quando una finestra del documento è mobile all'esterno dell'IDE, si trova ancora in un'area del documento e ha colori di sfondo, bordo, testo e tabulazione uguali a quando fa parte dell'IDE. Tuttavia, il documento si trova all'interno di una cornice che ha colori di sfondo, del bordo e del testo propri. Quando le finestre degli strumenti sono ancorate nell'area dei documenti, ereditano il comportamento e il colore per le rispettive schede dai nomi di token delle finestre dei documenti.

![Finestra del documento ancorata (linea rossa)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Finestra del documento ancorata (redline)

![Finestra del documento mobile (linea rossa)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Finestra del documento mobile (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in qualsiasi punto in cui si sta creando l'interfaccia utente che si vuole associare alla finestra del documento. | ...  per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

**Finestra del documento ancorata o mobile: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Dipende dal tipo di documento |
| Primo piano (testo) | Dipende dal tipo di documento |
| Bordo | `Environment.ToolWindowBorder` |

**Cornice della finestra del documento mobile con stato attivo: stato predefinito**

![Cornice della finestra del documento mobile con stato attivo predefinito](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Cornice della finestra del documento mobile con stato attivo predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowFloatingFrame` |
| Primo piano (testo) | `Environment.ToolWindowFloatingFrame` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Bordo | `Environment.MainWindowActiveDefaultBorder` |
| Bordo (glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Impostata su trasparente) |

**Cornice della finestra del documento mobile non attiva: stato predefinito**

![Cornice della finestra del documento mobile non attiva predefinita](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Cornice della finestra del documento mobile non attiva predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowFloatingFrameInactive` |
| Primo piano (testo) | `Environment.ToolWindowFloatingFrameInactive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Bordo | `Environment.MainWindowInactiveBorder` |
| Bordo (glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Impostata su trasparente) |

**Cornice della finestra del documento mobile con stato attivo: stato del passaggio del mouse**

![Cornice della finestra del documento mobile con stato attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Cornice della finestra del documento mobile con stato attivo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Cornice della finestra del documento mobile non attiva: stato del passaggio del mouse**

![Cornice della finestra del documento mobile non attiva al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Cornice della finestra del documento mobile non attiva al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Cornice della finestra del documento mobile con stato attivo: stato premuto**

![Cornice della finestra del documento mobile con stato attivo alla pressione](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Cornice della finestra del documento mobile con stato attivo alla pressione

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `Environment.RaftedWindowButtonDown` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Schede dei documenti
Le schede dei documenti si trovano nel canale delle schede per indicare i documenti attualmente aperti, insieme al documento selezionato o attivo corrente. Anche le finestre degli strumenti possono essere ancorate nel canale delle schede dei documenti se l'utente le aggiunge in questa posizione. In questo caso, usano gli stessi colori delle schede delle finestre dei documenti. Se si crea un'interfaccia utente che deve corrispondere sempre ai colori delle finestre dei documenti (inclusi gli aggiornamenti dei temi o se vengono installati nuovi temi), fare riferimento a questi token di colore.

![Schede del documento (redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Schede del documento (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque si crei l'interfaccia utente che si vuole associare alle schede dei documenti e preleva automaticamente gli aggiornamenti del tema o i nuovi colori del tema. | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente quando la shell ha un aggiornamento del tema. |

#### <a name="open-document-tabs"></a>Schede dei documenti aperti
Per ogni documento aperto è presente una scheda nel canale delle schede dei documenti che ne visualizza il nome. I documenti possono essere selezionati o aperti in background e le rispettive schede riflettono questi stati:

- La scheda selezionata rappresenta il documento attualmente visualizzato nell'area dei documenti. Una scheda selezionata ha un bordo di documento che si estende fino al bordo superiore dell'area dei documenti.

- Le schede di sfondo sono tutte le schede dei documenti che non sono la scheda attualmente selezionata. Dopo aver fatto clic, diventano la scheda selezionata e acquisiscono tutti i colori di sfondo, bordo e testo dai nomi dei token.

![Aprire la scheda del documento (redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Aprire la scheda del documento (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si creano schede di documenti personalizzate. | ... per le schede provvisorie (anteprima). |
| | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

**Scheda del documento con stato attivo selezionata**

![Scheda del documento con stato attivo selezionata](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Scheda del documento con stato attivo selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabSelectedGradientTop`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo) | `Environment.FileTabSelectedText` |
| Bordo | `Environment.FileTabSelectedBorder`<br />Impostata sullo stesso colore dello sfondo. |
| Bordo del documento | `Environment.FileTabDocumentBorderBackground` |

**Scheda documento selezionata e non con stato attivo**

![Scheda documento selezionata e non con stato attivo](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Scheda documento selezionata e non con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabInactiveGradientTop`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo) | `Environment.FileTabInactiveText` |
| Bordo | `Environment.FileTabInactiveBorder`<br />Impostata sullo stesso colore dello sfondo. |
| Bordo del documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Scheda Documento in background: stato predefinito**

![Scheda predefinita del documento in background](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Scheda predefinita del documento in background

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabBackground` |
| Primo piano (testo) | `Environment.FileTabText` |
| Bordo | `Environment.FileTabBorder`<br />Impostata sullo stesso colore dello sfondo. |

**Scheda documento in background: stato del passaggio del mouse**

![Scheda Documento in background al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Scheda Documento in background al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabHotGradientTop`<br />(Cursore sfumatura per questo token non usato nell'interfaccia utente a colori. |
| Primo piano (testo) | `Environment.FileTabHotText` |
| Bordo | `Environment.FileTabHotBorder`<br />Impostata sullo stesso colore dello sfondo. |

#### <a name="preview-tab"></a>Scheda anteprima
Chiamata anche scheda "provvisoria". La scheda di anteprima viene visualizzata sul lato destro del canale della scheda del documento quando l'utente fa clic su un elemento nella Esplora soluzioni degli strumenti. Questa scheda funge da anteprima del documento e offre all'utente anche l'opzione di mantenere il documento aperto sul lato sinistro del canale delle schede dei documenti. Può essere aperta una sola scheda anteprima per volta. Le schede anteprima hanno sia uno sfondo sia stati selezionati, come le schede aperte, e possono avere stato attivo o non attivo quando sono attive.

![Scheda Anteprima (redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Scheda Anteprima (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in qualsiasi punto in cui si sta creando l'anteprima provvisoria e si vuole che un elemento corrisponda al colore della scheda dell'anteprima corrente. | ... per qualsiasi tipo di documento o scheda non provvisorio (anteprima). |
| | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

**Scheda anteprima con stato attivo e selezionato**

![Scheda anteprima con stato attivo e selezionato](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Scheda anteprima con stato attivo e selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalSelectedActive` |
| Primo piano (testo) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Bordo | `Environment.FileTabProvisionalSelectedActiveBorder`<br />Impostata sullo stesso colore dello sfondo. |
| Bordo del documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Scheda anteprima non messa a fuoco selezionata**

![Scheda anteprima non messa a fuoco selezionata](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Scheda anteprima non messa a fuoco selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalSelectedInactive` |
| Primo piano (testo) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Bordo | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Bordo del documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Scheda Anteprima in background: stato predefinito**

![Scheda Anteprima sfondo predefinita](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Scheda Anteprima sfondo predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalInactive` |
| Primo piano (testo) | `Environment.FileTabProvisionalInactiveForeground` |
| Bordo | `Environment.FileTabProvisionalInactiveBorder`<br />Impostare lo stesso colore dello sfondo. |

**Scheda Anteprima sfondo: stato del passaggio del mouse**

![Scheda Anteprima in background al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Scheda Anteprima in background al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalHover` |
| Primo piano (testo) | `Environment.FileTabProvisionalHoverForeground` |
| Bordo | `Environment.FileTabProvisionalHoverBorder`<br />Impostare lo stesso colore dello sfondo. |

#### <a name="document-overflow-button"></a>Pulsante di overflow dei documenti
Il pulsante di overflow dei documenti è presente se ci sono uno o più documenti aperti, indipendentemente dal fatto che nella configurazione corrente sia disponibile spazio sufficiente da contenere tutte le schede dei documenti. Il menu a discesa di overflow del documento, controllato dai colori del [menu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) della barra dei comandi, visualizza un elenco di tutti i documenti aperti, sia visibili che nascosti, e il glifo di overflow cambia a seconda che tutti i documenti aperti siano visualizzati nel canale della scheda.

![Pulsante di overflow del documento (redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Pulsante di overflow del documento (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea un pulsante di overflow del documento personalizzato. | ... per l'interfaccia utente che non è simile a un pulsante di overflow. |
| | ... per i pulsanti di overflow della barra dei comandi. |

**Pulsante di overflow del documento: stato predefinito**

![Pulsante di overflow del documento predefinito](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Pulsante di overflow del documento predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DocWellOverflowButtonBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Bordo | N/A |

**Pulsante di overflow del documento: stato del passaggio del mouse**

![Pulsante di overflow dei documenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Pulsante di overflow dei documenti al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Bordo | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Pulsante di overflow del documento: stato premuto**

![Pulsante di overflow del documento alla pressione](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Pulsante di overflow del documento alla pressione

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Bordo | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Assegnazione di tag
Visual Studio supporta l'assegnazione di tag, che permette a un utente di dichiarare parole chiave da cercare per scopi di verifica. Ad esempio, i project manager e gli sviluppatori possono usare Team Foundation Server (TFS) per assegnare tag a elementi di lavoro. La tabella seguente indica i nomi di colore per il tag stesso e il glifo dell'icona di chiusura visualizzato negli stati corrispondenti al passaggio del mouse e alla selezione.

![Assegnazione di tag Visual Studio (redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Assegnazione di tag Visual Studio (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per l'interfaccia utente che supporta l'assegnazione di tag. | ... per qualsiasi altro tipo di interfaccia utente. |

#### <a name="tags"></a>Tag

**Tag: stato predefinito**

![Tag predefinito](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Tag predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.Background` |
| Primo piano (testo) | `Tag.Background` |

**Tag: stato del passaggio del mouse**

![Tag al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.HoverBackground` |
| Primo piano (testo) | `Tag.HoverBackgroundText` |

**Tag: stato premuto**

![Tag premuto](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Tag premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.PressedBackground` |
| Primo piano (testo) | `Tag.PressedBackgroundText` |

**Tag: stato selezionato**

![Tag selezionato](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Tag selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.SelectedBackground` |
| Primo piano (testo) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Glifo del tag Close ( &times; )

**Glifo del tag Close ( &times; ): stato predefinito**

![Glifo del tag Close ( &times; ) predefinito](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Glifo del tag Close ( &times; ) predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/A |
| Primo piano (glifo) | `Tag.TagHoverGlyph` |

**Glifo del tag Close ( &times; ): stato del passaggio del mouse**

![Glifo del tag Close ( &times; ) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Glifo del tag Close ( &times; ) al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagHoverGlyphHoverBackground` |
| Primo piano (glifo) | `Tag.TagHoverGlyphHover` |
| Bordo | `Tag.TagHoverGlyphHoverBorder` |

**Glifo del tag Close ( &times; ): stato premuto**

![Glifo del tag Pressed Close ( &times; )](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Glifo del tag Pressed Close ( &times; )

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagHoverGlyphPressedBackground` |
| Primo piano (glifo) | `Tag.TagHoverGlyphPressed` |
| Bordo | `Tag.TagHoverGlyphPressedBorder` |

**Tag selezionato con glifo Close ( &times; ): stato predefinito**

![Tag selezionato predefinito con glifo Close ( &times; )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Tag selezionato predefinito con glifo Close ( &times; )

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/A |
| Primo piano (glifo) | `Tag.TagSelectedGlyph` |

**Tag selezionato con glifo Close ( ): stato &times; del passaggio del mouse**

![Tag selezionato con l'glifo Close ( &times; ) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Tag selezionato con l'glifo Close ( &times; ) al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagSelectedGlyphHoverBackground` |
| Primo piano (glifo) | `Tag.TagSelectedGlyphHover` |
| Bordo | `Tag.TagSelectedGlyphHoverBorder` |

**Tag selezionato con glifo Close ( &times; ): stato premuto**

![Tag selezionato e premuto con l'glifo Close ( &times; )](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Tag selezionato e premuto con l'glifo Close ( &times; )

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagSelectedGlyphPressedBackground` |
| Primo piano (glifo) | `Tag.TagSelectedGlyphPressed` |
| Bordo | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Finestre degli strumenti
Non è necessario replicare le finestre degli strumenti, perché sono fornite dall'ambiente Visual Studio servizio. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre degli strumenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.

![Finestra degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Finestra degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in qualsiasi punto in cui si sta creando l'interfaccia utente che si vuole associare alle finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

### <a name="tool-window-frame"></a>Cornice delle finestre degli strumenti
Le finestre degli strumenti in Visual Studio vengono usate per molte attività diverse e possono avere stati diversi. Se una finestra degli strumenti è aperta, può essere assegnata a uno qualsiasi dei quattro lati dell'area del documento. Le finestre degli strumenti possono anche essere mobili al di fuori dell'IDE, per poter essere riposizionate in qualsiasi punto dello schermo dell'utente. Le finestre mobili sono sempre in primo piano nell'IDE. Infine, le finestre degli strumenti possono essere ancorate come finestre dei documenti ed essere visualizzate come scheda nell'area dei documenti. Le finestre degli strumenti ancorate come finestre dei documenti vengono colorate in parte usando i nomi di token delle finestre dei documenti.

![Cornice della finestra degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Cornice della finestra degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ...  in qualsiasi punto in cui si sta creando l'interfaccia utente che si vuole associare alle finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

**Finestra degli strumenti ancorata**

![Finestra degli strumenti ancorata](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Finestra degli strumenti ancorata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowBackground` |
| Bordo | `Environment.ToolWindowBorder` |

**Finestra degli strumenti mobile con stato attivo**

![Finestra degli strumenti mobile con stato attivo](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Finestra degli strumenti mobile con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowBackground` |
| Bordo | `Environment.MainWindowActiveDefaultBorder` |

**Finestra degli strumenti mobile e non attiva**

![Finestra degli strumenti mobile e non attiva](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Finestra degli strumenti mobile e non attiva

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowBackground` |
| Bordo | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Finestre simili alla casella degli strumenti
La casella degli strumenti è una delle finestre degli strumenti più comuni usate in Visual Studio. Si tratta essenzialmente di un controllo albero con un tema e uno stile speciali applicati.

![Finestra simile a Casella degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Finestra simile a Casella degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si progetta una finestra degli strumenti che deve essere sempre coerente con la casella degli strumenti della shell. | ... per qualsiasi elemento non simile all'interfaccia utente della casella degli strumenti o se non si è certi che l'interfaccia utente avrà problemi se i colori della casella degli strumenti della shell cambiano. |

**Nodi della casella degli strumenti: stato predefinito**

![Nodo padre della casella degli strumenti predefinito](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nodo padre della casella degli strumenti predefinito

![Nodo figlio predefinito della casella degli strumenti](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nodo figlio predefinito della casella degli strumenti

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolboxContent`<br />(Intestazioni) |
| Sfondo | `Environment.ToolWindowBackground`<br />(singoli elementi o intera finestra se non sono disponibili controlli) |
| Bordo | Nessuno |
| Primo piano (glifo) | `Environment.ToolboxContent` |
| Primo piano (testo) | `Environment.ToolboxContent` |

**Nodi figlio della casella degli strumenti: stato del passaggio del mouse**

![Nodo figlio della casella degli strumenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nodo figlio della casella degli strumenti al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolboxContentMouseOver`<br />(Solo singoli elementi) |
| Bordo | Nessuno |
| Primo piano (testo) | `Environment.ToolboxContentMouseOver`<br />(Solo singoli elementi) |

**Nodi della casella degli strumenti selezionati: stato attivo**

![Nodo padre della casella degli strumenti con stato attivo e selezionato](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nodo padre della casella degli strumenti con stato attivo e selezionato

![Nodo figlio della casella degli strumenti con stato attivo e selezionato](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nodo figlio della casella degli strumenti con stato attivo e selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordo | `TreeView.FocusVisualBorder`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primo piano (glifo) | `TreeView.SelectedItemActive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primo piano (testo) | `TreeView.SelectedItemActive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Nodi della casella degli strumenti selezionati: stato non attivo**

![Nodo padre della casella degli strumenti selezionato senza stato attivo](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nodo padre della casella degli strumenti selezionato senza stato attivo

![Nodo figlio della casella degli strumenti selezionato e non attivo](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nodo figlio della casella degli strumenti selezionato e non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordo | Nessuno |
| Primo piano (glifo) | `TreeView.SelectedItemInactive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primo piano (testo) | `TreeView.SelectedItemInactive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barra del titolo delle finestre degli strumenti
Il bordo della barra del titolo non è un bordo reale, ma una linea spesso nella parte superiore della barra del titolo. Non ha un nome di token per lo stato non attivo.

![Barra del titolo della finestra degli strumenti (redline)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barra del titolo della finestra degli strumenti (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in qualsiasi punto in cui si sta creando l'interfaccia utente che si vuole associare alle finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

**Barra del titolo con stato attivo**

![Barra del titolo con stato attivo](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barra del titolo con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.TitleBarActiveGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.TitleBarActiveText` |
| Bordo | `Environment.TitleBarActiveBorder`<br />Impostare lo stesso colore dello sfondo. |
| Quadratino di trascinamento | `Environment.TitleBarDragHandleActive` |

**Barra del titolo con stato non attivo**

![Barra del titolo con stato non attivo](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barra del titolo con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.TitleBarInactiveGradientBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.TitleBarInactiveText` |
| Bordo | N/A |
| Quadratino di trascinamento | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Pulsanti della barra del titolo della finestra degli strumenti
![Pulsante della barra del titolo (redline)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Pulsante della barra del titolo (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i pulsanti visualizzati nell'interfaccia utente che usa token di colore dalle barre del titolo della finestra degli strumenti. | ... per i pulsanti visualizzati in altre posizioni. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Pulsanti della barra del titolo con stato attivo: stato predefinito**

![Pulsanti predefiniti della barra del titolo con stato attivo](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Pulsanti predefiniti della barra del titolo con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/A |
| Primo piano (glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Bordo | N/A |

**Pulsanti della barra del titolo senza stato attivo: stato predefinito**

![Pulsanti predefiniti e senza stato di avanzamento della barra del titolo](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Pulsanti predefiniti e senza stato di avanzamento della barra del titolo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/A |
| Primo piano (glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Bordo | N/A |

**Pulsanti della barra del titolo con stato attivo: stato del passaggio del mouse**

![Pulsanti della barra del titolo con stato attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Pulsanti della barra del titolo con stato attivo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonHoverActive` |
| Primo piano (glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Bordo | `Environment.ToolWindowButtonHoverActiveBorder` |

**Pulsanti della barra del titolo senza stato attivo: stato del passaggio del mouse**

![Pulsanti della barra del titolo senza stato attivato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Pulsanti della barra del titolo senza stato attivato al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonHoverInactive` |
| Primo piano (glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Bordo | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Pulsanti della barra del titolo con stato attivo: stato premuto**

![Pulsanti della barra del titolo con stato attivo sulla pressione](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Pulsanti della barra del titolo con stato attivo sulla pressione

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonDown` |
| Primo piano (glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Bordo | `Environment.ToolWindowButtonDownBorder` |

**Pulsanti della barra del titolo senza stato attivo: stato premuto**

![Pulsanti della barra del titolo senza stato premuto](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Pulsanti della barra del titolo senza stato premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonDown` |
| Primo piano (glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Bordo | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Schede delle finestre degli strumenti
![Scheda della finestra degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Scheda della finestra degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in qualsiasi punto in cui si sta creando l'interfaccia utente che si vuole associare alle finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

**Scheda della finestra degli strumenti con stato attivo selezionata**

![Scheda della finestra degli strumenti con stato attivo selezionata](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Scheda della finestra degli strumenti con stato attivo selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabSelectedTab` |
| Primo piano (testo) | `Environment.ToolWindowTabSelectedActiveText` |
| Bordo | `Environment.ToolWindowTabSelectedBorder`<br />Impostare lo stesso colore dello sfondo. |

**Scheda della finestra degli strumenti con stato non attivo selezionata**

![Scheda della finestra degli strumenti con stato non attivo selezionata](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Scheda della finestra degli strumenti con stato non attivo selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabSelectedTab` |
| Primo piano (testo) | `Environment.ToolWindowTabSelectedText` |
| Bordo | `Environment.ToolWindowTabSelectedBorder`<br />Impostare lo stesso colore dello sfondo. |

**Scheda della finestra degli strumenti in background: stato predefinito**

![Scheda predefinita della finestra degli strumenti in background](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Scheda predefinita della finestra degli strumenti in background

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013. |
| Primo piano (testo) | `Environment.ToolWindowTabText` |
| Bordo | `Environment.ToolWindowTabBorder` |

**Scheda della finestra degli strumenti in background: stato del passaggio del mouse**

![Scheda della finestra degli strumenti in secondo piano al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Scheda della finestra degli strumenti in secondo piano al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013. |
| Primo piano (testo) | `Environment.ToolWindowTabMouseOverText` |
| Bordo | `Environment.ToolWindowTabMouseOverBorder`<br />Impostare lo stesso colore dello sfondo. |

### <a name="auto-hide-tabs"></a>Schede Nascondi automaticamente

![Nascondi automaticamente le schede (linea rossa)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Nascondi automaticamente le schede (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... in qualsiasi punto in cui si sta creando l'interfaccia utente che si vuole associare alle schede delle finestre degli strumenti nascoste automaticamente. | ... per qualsiasi interfaccia utente che non si vuole modificare automaticamente se la shell ha un aggiornamento del tema. |

**Nascondi automaticamente le schede: stato predefinito**

![Scheda Nascondi automaticamente predefinita](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Scheda Nascondi automaticamente predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.AutoHideTabBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.AutoHideTabText` |
| Bordo | `Environment.AutoHideTabBorder` |

**Nascondi automaticamente le schede: stato del passaggio del mouse**

![Scheda Nascondi automaticamente al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Scheda Nascondi automaticamente al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />I cursori sfumatura per questo token non vengono usati nell'interfaccia utente con colori. |
| Primo piano (testo) | `Environment.AutoHideTabMouseOverText` |
| Bordo | `Environment.AutoHideTabMouseOverBorder` |
