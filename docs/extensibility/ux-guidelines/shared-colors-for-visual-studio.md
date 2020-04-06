---
title: Colori condivisi per Visual Studio . Documenti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699936"
---
# <a name="shared-colors-for-visual-studio"></a>Colori condivisi per Visual StudioShared colors for Visual Studio
Quando si progetta un'interfaccia utente che usa elementi comuni della shell di Visual Studio o si desidera che l'elemento dell'interfaccia sia coerente con funzionalità simili, usare i nomi di token esistenti nei file di definizione del pacchetto per scegliere e assegnare colori. In questo modo, l'interfaccia utente resta coerente con l'intero ambiente di Visual Studio e viene aggiornata automaticamente quando vengono aggiunti o aggiornati temi.

Questo articolo descrive gli elementi dell'interfaccia utente comuni e i nomi di token usati da questi elementi, a cui è possibile fare riferimento durante la compilazione di un'interfaccia utente simile. Per informazioni specifiche su come accedere a questi token di colore, vedere [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Assicurarsi di usare correttamente i nomi di token:

- **Usare i nomi di token in base alla funzione e non al colore stesso.** I colori condivisi comuni sono associati a elementi dell'interfaccia specifici e destinati solo a essere usati per le stesse funzionalità o altre simili. Ad esempio, evitare di riutilizzare il colore di una casella combinata premuta per un'animazione di stato rotante solo perché si ha una preferenza per questo colore. Le funzioni della casella combinata e dell'animazione sono diverse e se il colore associato alla casella combinata cambia, potrebbe non essere più un colore appropriato per l'elemento di animazione. Un uso coerente del colore aiuta a orientare correttamente gli utenti e a impedire confusione.

- **Usare colori di sfondo e del testo nella combinazione corretta.** I colori di sfondo destinati a essere usati con il testo implicano un colore del testo associato. Non usare colori del testo diversi da quelli specificati per un determinato sfondo. Se non è presente un colore di testo associato, non utilizzare tale colore di sfondo per qualsiasi superficie in cui si prevede di visualizzare il testo. Altre combinazioni di colori di testo e di sfondo potrebbero generare un'interfaccia illeggibile.

- **Usare colori dei controlli appropriati per la rispettiva posizione.** In alcuni stati, alcuni controlli di Visual Studio non hanno colori bordo e sfondo separati. Al contrario, selezionano questi colori dalle superfici sottostanti. Assicurarsi di usare sempre i nomi di token appropriati per la posizione in cui si posiziona il controllo.

> [!IMPORTANT]
> Non utilizzare i token trovati nelle categorie "Pagina iniziale" o "Cider".

## <a name="common-shared-controls"></a>Controlli condivisi comuni

Quando si utilizza una barra dei comandi standard di Visual Studio nella funzionalità, si avrà accesso ai controlli della shell con stile. Non è consigliabile rimodello di questi controlli comuni. Tuttavia, se si intende compilare una barra dei comandi personalizzata, potrebbe essere necessario compilare anche controlli personalizzati. In questo caso, assicurarsi di usare i nomi di token corretti per ognuno dei controlli seguenti, in modo che l'interfaccia utente sia coerente con il resto di Visual Studio.

### <a name="button-controls"></a>Controlli pulsante

![Controllo pulsante con linea rossa](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i pulsanti nel documento e che si desidera integrare con i temi di Visual Studio (tema Chiaro, Scuro, Blu o un tema a contrasto elevato del sistema). | ... per i pulsanti che verranno visualizzati su uno sfondo personalizzato che non fa parte di un tema di Visual Studio. |

**Pulsante: stato standard**

![Pulsante standard](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Pulsante standard

| Elemento | Nome token: Category.color |
| --- | --- |
| Pulsante | `CommonControls.Button` |
| Bordo del pulsante | `CommonControls.ButtonBorder` |

**Pulsante: stato predefinito**

![Pulsante predefinito](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Predefinito")<br />Pulsante predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Pulsante | `CommonControls.ButtonDefault` |
| Bordo del pulsante | `CommonControls.ButtonBorderDefault` |

**Pulsante: stato disabilitato**

![Pulsante Disabilitato](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabilitato")<br />Pulsante Disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Pulsante | `CommonControls.ButtonDisabled` |
| Bordo del pulsante | `CommonControls.ButtonBorderDisabled` |

**Pulsante: stato al passaggio del mouse**

![Pulsante al passaggio del mouse](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Pulsante al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Pulsante | `CommonControls.ButtonHover` |
| Bordo del pulsante | `CommonControls.ButtonBorderHover` |

**Pulsante: stato premuto**

![Pulsante premuto](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Pulsante premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Pulsante | `CommonControls.ButtonPressed` |
| Bordo del pulsante | `CommonControls.ButtonBorderPressed` |

**Pulsante: stato attivo**

![Pulsante con stato attivo](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Pulsante con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Pulsante | `CommonControls.ButtonFocused` |
| Bordo del pulsante | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controlli casella di controllo
![Casella di controllo (linea rossa)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Casella di controllo (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i controlli casella di controllo contenuti nel documento. | ... per qualsiasi interfaccia utente che non sia un controllo casella di controllo. |

**Casella di controllo: stato predefinito**

![Casella di controllo](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Casella di controllo predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.CheckBoxBackground` |
| Bordo | `CommonControls.CheckBoxBorder` |
| Testo | `CommonControls.CheckBoxText` |
| Icona | `CommonControls.CheckBoxGlyph` |

**Casella di controllo: stato disabilitato**

![Casella di controllo Disabilitata](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Casella di controllo Disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.CheckBoxBackgroundDisabled` |
| Bordo | `CommonControls.CheckBoxBorderDisabled` |
| Testo | `CommonControls.CheckBoxTextDisabled` |
| Icona | `CommonControls.CheckBoxGlyphDisabled` |

**Casella di controllo: stato al passaggio del mouse**

 ![Casella di controllo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Casella di controllo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.CheckBoxBackgroundHover` |
| Bordo | `CommonControls.CheckBoxBorderHover` |
| Testo | `CommonControls.CheckBoxTextHover` |
| Icona | `CommonControls.CheckBoxGlyphHover` |

**Casella di controllo: stato premuto**

![Casella di controllo premuta](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Casella di controllo premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.CheckBoxBackgroundPressed` |
| Bordo | `CommonControls.CheckBoxBorderPressed` |
| Testo | `CommonControls.CheckBoxTextPressed` |
| Icona | `CommonControls.CheckBoxGlyphPressed` |

**Casella di controllo: stato attivo**

![Casella di controllo con lo stato attivo](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Casella di controllo con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.CheckBoxBackgroundFocused` |
| Bordo | `CommonControls.CheckBoxBorderFocused` |
| Testo | `CommonControls.CheckBoxTextFocused` |
| Icona | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Menu a discesa e caselle combinate
![Casella combinata/elenco a discesa (linea rossa)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Casella combinata/elenco a discesa (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i menu a discesa e le caselle combinate nel documento. | ... per qualsiasi interfaccia utente che non sia una casella a discesa o combinata. |
| | ... per [i menu a discesa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) o le [caselle combinate](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)della barra dei comandi. |

**Menu a discesa e caselle combinate: stato predefinito**

![Casella di riepilogo a discesa/casella combinata predefinita](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Casella di riepilogo a discesa/casella combinata predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.ComboBoxBackground` |
| Bordo | `CommonControls.ComboBoxBorder` |
| Testo | `CommonControls.ComboBoxText` |
| Separatore | `CommonControls.ComboBoxSeparator` |
| Icona | `CommonControls.ComboBoxGlyph` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackground` |

**Menu a discesa e caselle combinate: stato disabilitato**

![Casella di riepilogo a discesa/casella combinata disabilitata](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Casella di riepilogo a discesa/casella combinata disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.ComboBoxBackgroundDisabled` |
| Bordo | `CommonControls.ComboBoxBorderDisabled` |
| Testo | `CommonControls.ComboBoxTextDisabled` |
| Separatore | `CommonControls.ComboBoxSeparatorDisabled` |
| Icona | `CommonControls.ComboBoxGlyphDisabled` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Menu a discesa e caselle combinate: stato al passaggio del mouse**

![Casella combinata/a discesa al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Casella combinata/a discesa al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.ComboBoxBackgroundHover` |
| Bordo | `CommonControls.ComboBoxBorderHover` |
| Testo | `CommonControls.ComboBoxTextHover` |
| Separatore | `CommonControls.ComboBoxSeparatorHover` |
| Icona | `CommonControls.ComboBoxGlyphHover` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Menu a discesa e caselle combinate: stato premuto**

![Casella di riepilogo a discesa/casella combinata premuta](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Casella di riepilogo a discesa/casella combinata premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.ComboBoxBackgroundPressed` |
| Bordo | `CommonControls.ComboBoxBorderPressed` |
| Testo | `CommonControls.ComboBoxTextPressed` |
| Separatore | `CommonControls.ComboBoxSeparatorPressed` |
| Icona | `CommonControls.ComboBoxGlyphPressed` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Elenco a discesa e visualizzazione elementi elenco caselle combinate: stato premuto**

 ![Casella a discesa/casella combinata nella visualizzazione degli elementi di elenco](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Casella a discesa/casella combinata nella visualizzazione degli elementi di elenco

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Bordo | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Testo dell'elemento | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Ombreggiatura dello sfondo | `CommonControls.ComboBoxListBackgroundShadow` |

**Menu a discesa e caselle combinate: stato attivo**

![Casella a discesa/combinata con lo stato attivo](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Casella a discesa/combinata con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.ComboBoxBackgroundFocused` |
| Bordo | `CommonControls.ComboBoxBorderFocused` |
| Testo | `CommonControls.ComboBoxTextFocused` |
| Separatore | `CommonControls.ComboBoxSeparatorFocused` |
| Icona | `CommonControls.ComboBoxGlyphFocused` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Menu a discesa e caselle combinate: selezione dell'input di testo**

![Selezione dell'input di testo a discesa/casella combinata](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Selezione dell'input di testo a discesa/casella combinata

| Elemento | Nome token: Category.color |
| --- | --- |
| Evidenziazione | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controlli per dati tabulari (griglia)
I controlli per dati tabulari, noti anche come controlli griglia, sono controlli comuni per Visual Studio, che possono essere usati per presentare grandi quantità di dati in più colonne. I controlli per dati tabulari standard possono trovarsi in diverse posizioni all'interno di Visual Studio, ad esempio nella finestra degli strumenti Elenco errori, nei report IntelliTrace e nella visualizzazione degli heap della memoria. Usare sempre i controlli per dati tabulari standard forniti. In alcuni casi rari, si potrebbe non avere accesso ai controlli per dati tabulari standard. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri controlli per dati tabulari in Visual Studio.

![Controllo griglia/dati tabulare (linea rossa)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Controllo griglia/dati tabulare (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i controlli tabulari o griglia. | ... per qualsiasi interfaccia utente che non sia un controllo tabulare o griglia. |

#### <a name="column-headers"></a>Intestazioni di colonna
Le intestazioni di colonna sono costituite da uno sfondo, un bordo, il testo del titolo e un glifo facoltativo, usato in genere quando una griglia viene ordinata in base alla colonna.

**Intestazione di colonna: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Header.Default` |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Header.Glyph` |
| Bordo | `Header.SeparatorLine` |

**Intestazione di colonna: stato al passaggio del mouse**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Header.MouseOver` |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Header.MouseOverGlyph` |
| Bordo | `Header.SeparatorLine` |

**Intestazione di colonna: stato premuto**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `CommonControls.CheckBoxBackgroundPressed` |
| Primo piano (testo) | `CommonControls.CheckBoxBorderPressed` |
| Primo piano (glifo) | `CommonControls.CheckBoxTextPressed` |
| Bordo | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementi della visualizzazione elenco
 Gli elementi della visualizzazione elenco sono costituiti da uno sfondo e da contenuto. Il contenuto può essere sotto forma di testo, icona o entrambi.

**Elementi della visualizzazione elenco: stato predefinitoList view items: default state**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | Trasparente |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Bordo | nessuno |

**Elementi della visualizzazione elenco: stato attivo**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActiveText` |
| Bordo | nessuno |

**Elementi della visualizzazione elenco: stato inattivoList view items: inactive state**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactiveText` |
| Bordo | nessuno |

### <a name="ui-text"></a>Testo dell'interfaccia utente

#### <a name="instructional-text"></a>Testo informativo
Il testo didattico fornisce una spiegazione principale importante di cosa fare in una finestra di dialogo o in una pagina del documento.

![Testo informativo predefinito](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Testo informativo predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Testo secondario informativo
Nelle pagine del documento con molto testo e controlli, alcuni testi didattici utilizzano un valore di colore diverso. Ciò consente di trasmettere quali informazioni sono più importanti e ridurre la densità complessiva degli elementi dell'interfaccia utente. (Vedere anche la sezione seguente sul testo di suggerimento.)

![Testo secondario informativo](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Testo secondario informativo

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Testo del suggerimento
Il testo del suggerimento viene visualizzato in un controllo vuoto, sotto un controllo o su una superficie del documento vuota per mostrare all'utente cosa fare successivamente. È possibile utilizzare il testo dei suggerimenti con gli sfondi della finestra o del controllo.

**Testo di suggerimento predefinito**

![Testo di suggerimento predefinito](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Testo di suggerimento predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlEditHintText` |

**Testo del suggerimento richiesto**

![Testo del suggerimento richiesto](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Testo del suggerimento richiesto

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.ControlRequiredHintText` |
| Background | `Environment.ControlRequiredBackground` |

**Testo del controllo Casella di ricerca**

> Vedere [Caselle di ricerca](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) per altri token di colore correlati al controllo di ricerca.

![Testo del controllo Casella di ricerca](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Testo del controllo Casella di ricerca

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Il collegamento ipertestuale è un controllo che non dispone di una coppia primo piano/sfondo. In tutti i casi, utilizzare il colore del collegamento ipertestuale di primo piano, che verrà visualizzato correttamente su sfondi scuri, grigi e bianchi. Se non si utilizza il token di colore per il controllo collegamento ipertestuale, verrà visualizzato il colore di sistema predefinito per "premuto", che lampeggia in rosso. Questo è il segnale che il controllo non utilizza il token di colore di ambiente corretto.

![Collegamento ipertestuale (linea rossa)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Collegamento ipertestuale (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando è necessario creare un collegamento ipertestuale personalizzato. | ... per tutto ciò che non è un collegamento ipertestuale. |

**Collegamento ipertestuale: stato predefinito**

![Collegamento ipertestuale predefinito](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Collegamento ipertestuale predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlink` |

**Collegamento ipertestuale: stato al passaggio del mouse**

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
| Background | `InfoBar.InfoBarBackground` |
| Primo piano (testo) | `InfoBar.InfoBar` |
| Bordo | `InfoBar.InfoBarBorder` |

**Pulsante Chiudi&times;barra informazioni ( ) : stato predefinito**

![Pulsante Chiudi&times;predefinito della barra informazioni ( )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Pulsante Chiudi&times;predefinito della barra informazioni ( )

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.CloseButton` |
| Bordo | `InfoBar.CloseButtonBorder` |
| Icona | `InfoBar.CloseButtonGlyph` |

**Pulsante Chiudi&times;( ) della barra informazioni: stato al passaggio del mouse**

![Pulsante Chiudi&times;barra informazioni ( ) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Pulsante Chiudi&times;barra informazioni ( ) al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.CloseButtonHover` |
| Bordo | `InfoBar.CloseButtonHoverBorder` |
| Icona | `InfoBar.CloseButtonHoverGlyph` |

**Tasto Chiudi&times;( ) della barra informazioni: stato premuto**

![Pulsante Chiudi&times;barra informazioni premuto ( )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Pulsante Chiudi&times;barra informazioni premuto ( )

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.CloseButtonDown` |
| Bordo | `InfoBar.CloseButtonDownBorder` |
| Icona | `InfoBar.CloseButtonDownGlyph` |

**Pulsante collegamento ipertestuale barra informazioni: stato predefinito**

![Pulsante collegamento ipertestuale predefinito della barra informazioni](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Pulsante collegamento ipertestuale predefinito della barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `InfoBar.Hyperlink` |

**Pulsante collegamento ipertestuale barra informazioni: stato al passaggio del mouse**

![Pulsante collegamento ipertestuale barra informazioni al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Pulsante collegamento ipertestuale barra informazioni al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseOver`<br />(Con sottolineatura) |

**Pulsante collegamento ipertestuale barra informazioni: stato premuto**

![Pulsante di collegamento ipertestuale della barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Pulsante di collegamento ipertestuale della barra informazioni premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseDown`<br />(Con sottolineatura) |

**Collegamento ipertestuale in linea della barra informazioni (all'interno di una frase): stato predefinito**

![Pulsante collegamento ipertestuale predefinito della barra informazioni in linea](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Pulsante collegamento ipertestuale predefinito della barra informazioni in linea

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `InfoBar.Hyperlink` |

**Collegamento ipertestuale in linea della barra informazioni (all'interno di una frase): stato del passaggio del mouse**

![Pulsante collegamento ipertestuale in linea della barra informazioni al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Pulsante collegamento ipertestuale in linea della barra informazioni al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseOver`<br />(Con sottolineatura) |

**Collegamento ipertestuale in linea della barra informazioni (all'interno di una frase): stato premuto**

![Pulsante collegamento ipertestuale in linea barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Pulsante collegamento ipertestuale in linea barra informazioni premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Infobar.HyperlinkMouseDown`<br />(Con sottolineatura) |

**Pulsante barra informazioni: stato predefinito**

![Pulsante della barra informazioni predefinita](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Pulsante della barra informazioni predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.Button` |
| Primo piano (testo) | `InfoBar.Button` |
| Bordo | `InfoBar.ButtonBorder` |

**Pulsante della barra informazioni: stato al passaggio del mouse**

![Pulsante della barra informazioni al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Pulsante della barra informazioni al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.ButtonMouseOver` |
| Primo piano (testo) | `InfoBar.ButtonMouseOver` |
| Bordo | `InfoBar.ButtonMouseOverBorder` |

**Tasto barra informazioni: stato premuto**

![Pulsante della barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Pulsante della barra informazioni premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.ButtonMouseDown` |
| Primo piano (testo) | `InfoBar.ButtonMouseDown` |
| Bordo | `InfoBar.ButtonMouseDownBorder` |

**Pulsante barra informazioni: stato disabilitato**

![Pulsante della barra informazioni disabilitato](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Pulsante della barra informazioni disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.ButtonDisabled` |
| Primo piano (testo) | `InfoBar.ButtonDisabled` |
| Bordo | `InfoBar.ButtonDisabledBorder` |

**Pulsante della barra informazioni: stato attivo**

![Pulsante della barra informazioni con lo stato attivo](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Pulsante della barra informazioni con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `InfoBar.ButtonFocus` |
| Primo piano (testo) | `InfoBar.ButtonFocus` |
| Bordo | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barre di scorrimento
Le barre di scorrimento hanno uno stile in base all'ambiente di Visual Studio e non è necessario applicare un tema. Tuttavia, è possibile decidere che si desidera sfruttare i colori utilizzati nelle barre di scorrimento in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.However, you might decide that you want to leverage the colors used in scroll bars so that your UI always appears consistent with this part of the Visual Studio environment.

![Barra di scorrimento (linea rossa)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barra di scorrimento (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea l'interfaccia utente che si desidera associare le barre di scorrimento di Visual Studio. | ... per tutto ciò che non si desidera trovare sempre la corrispondenza con l'interfaccia utente della barra di scorrimento. |

**Barra di scorrimento: stato predefinito**

![Barra di scorrimento predefinita](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barra di scorrimento predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Barra di scorrimento | `Environment.ScrollBarBackground` |
| Primo piano (anteprima) | `Environment.ScrollBarThumbBackground` |

**Barra di scorrimento: stato al passaggio del mouse**

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

![Freccia della barra di scorrimento predefinita](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Freccia della barra di scorrimento predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ScrollBarArrowBackground`<br />(Impostare lo stesso colore della barra di scorrimento.) |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyph` |

**Freccia della barra di scorrimento: stato al passaggio del mouse**

![Freccia della barra di scorrimento al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Freccia della barra di scorrimento al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ScrollBarArrowMouseOverBackground`<br />(Impostare lo stesso colore della barra di scorrimento.) |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Freccia della barra di scorrimento: stato premuto**

![Freccia della barra di scorrimento](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Freccia della barra di scorrimento

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ScrollBarArrowPressedBackground`<br />(Impostare lo stesso colore della barra di scorrimento.) |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Caselle di ricerca
Quando è possibile, usare il controllo di ricerca comune fornito dall'ambiente di Visual Studio. I colori della casella di ricerca si trovano nella categoria "SearchControl" nel file **ShellColors.pkgdef** , che contiene i nomi di token per il campo di input, il pulsante di azione, il pulsante a discesa e il menu a discesa.

Una casella di ricerca può avere diversi stati, alcuni dei quali si escludono a vicenda:

- "Con stato attivo" e "con stato non attivo" indicano se il cursore si trova o meno nella casella di testo.

- "Attivo" e "inattivo" indicano se l'utente ha inserito una query di ricerca nella casella di testo.

- "Passaggio del mouse" significa che l'utente ha posizionato il cursore del mouse sulla casella di ricerca (questo stato sostituisce tutti gli altri).

- "Disabilitato" significa che la funzionalità di ricerca è disattivata per il contesto corrente.

![Casella di ricerca (linea rossa)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Casella di ricerca (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... durante la progettazione di una casella di ricerca personalizzata. | ... per tutto ciò che non è una casella di ricerca. |
| | ... per tutto ciò che non si desidera abbinare sempre l'interfaccia utente della casella di ricerca. |

**Campo di immissione ricerca con stato attivo**

![Campo di immissione ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Campo di immissione ricerca con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.FocusedBackground` |
| Primo piano (testo) | `SearchControl.FocusedBackground` |
| Bordo | `SearchControl.FocusedBorder` |
| Separatore | `SearchControl.FocusedDropDownSeparator` |

**Campo di immissione di ricerca attivo e non focalizzato**

![Campo di input di ricerca con stato non attivo](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Campo di immissione di ricerca attivo e non focalizzato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.SearchActiveBackground` |
| Primo piano (testo) | `SearchControl.SearchActiveBackground` |
| Bordo | `SearchControl.UnfocusedBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Campo di input di ricerca non focalizzato e inattivo**

![Campo di input di ricerca non focalizzato e inattivo](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo di input di ricerca non focalizzato e inattivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.Unfocused` |
| Primo piano (testo) | `SearchControl.Unfocused` |
| Bordo | `SearchControl.UnfocusedBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Campo di input di ricerca evidenziato (solo testo)**

![Campo di immissione ricerca evidenziato](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Campo di immissione ricerca evidenziato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.Selection` |
| Primo piano (testo) | `SearchControl.FocusedBackground` |
| Bordo | nessuno |
| Separatore | `SearchControl.FocusedDropDownSeparator` |

**Campo di immissione ricerca disabilitato**

![Campo di immissione ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Campo di immissione ricerca disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.Disabled` |
| Primo piano (testo) | `SearchControl.Disabled` |
| Bordo | `SearchControl.DisabledBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Pulsante di azione di ricerca con stato attivo**

![Pulsante di azione di ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Pulsante di azione di ricerca con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (glifo Cerca) | `SearchControl.SearchGlyph` |
| Primo piano (glifo Arresta) | `SearchControl.StopGlyph` |
| Primo piano (glifo Cancella) | `SearchControl.ClearGlyph` |
| Bordo | N/D |

**Pulsante di azione di ricerca non focalizzato**

![Pulsante di azione di ricerca non focalizzato](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Pulsante di azione di ricerca non focalizzato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D |
| Primo piano (glifo Cerca) | `SearchControl.SearchGlyph` |
| Primo piano (glifo Arresta) | `SearchControl.StopGlyph` |
| Primo piano (glifo Cancella) | `SearchControl.ClearGlyph` |
| Bordo | N/D |

**Pulsante di azione di ricerca premuto**

![Pulsante di azione di ricerca premuto](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Pulsante di azione di ricerca premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.ActionButtonMouseDown` |
| Primo piano (glifo) | `SearchControl.ActionButtonMouseDownGlyph` |
| Bordo | `SearchControl.ActionButtonMouseDownBorder` |

**Pulsante di azione di ricerca disabilitata**

![Pulsante di azione di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Pulsante di azione di ricerca disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Bordo | nessuno |

**Pulsante a discesa Ricerca con stato attivo**

![Pulsante a discesa Ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Pulsante a discesa Ricerca con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.FocusedDropDownButton` |
| Primo piano (glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Bordo | `SearchControl.FocusedDropDownButtonBorder` |

**Pulsante a discesa ricerca non focalizzata**

![Pulsante a discesa ricerca non focalizzata](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Pulsante a discesa ricerca non focalizzata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.UnfocusedDropDownButton` |
| Primo piano (glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Bordo | `SearchControl.UnfocusedDropDownButtonBorder` |

**Pulsante a discesa di ricerca premuto**

![Pulsante a discesa di ricerca premuto](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Pulsante a discesa di ricerca premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.MouseDownDropDownButton` |
| Primo piano (glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Bordo | `SearchControl.MouseDownDropDownButtonBorder` |

**Pulsante a discesa Ricerca disabilitata**

![Pulsante a discesa Ricerca disabilitata](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Pulsante a discesa Ricerca disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Bordo | nessuno |

#### <a name="search-drop-down-lists"></a>Elenchi a discesa di ricerca
The search box drop-down menu has the potential to be slightly more complex than other drop-down menus in Visual Studio. Le sezioni "ricerche suggerite" e "opzioni di ricerca" possono apparire da sole o insieme nel menu, e ciascuna di esse è colorata separatamente. Una linea separa le due sezioni quando sono visualizzate insieme e un bordo circonda l'intero menu a discesa.

![Elenco a discesa Ricerca (linea rossa)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Elenco a discesa Ricerca (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea un elenco a discesa di ricerca personalizzato. | ... per gli elenchi a discesa visualizzati in altri contesti. |
| ... i nomi di token corretti per i componenti dell'elenco corretti. | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Cerca elementi dell'elenco a discesa**

| Elemento | Nome token: Category.color |
| --- | --- |
| Bordo | `SearchControl.PopupBorder` |
| Separatore | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Ricerche suggerite: stato predefinito**

![Ricerche suggerite predefinite](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Ricerche suggerite predefinite

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `SearchControl.PopupItemText` |

**Ricerche suggerite: stato al passaggio del mouse**

![Ricerche suggerite al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Ricerche suggerite al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `SearchControl.PopupMouseOverItemText` |
| Bordo | `SearchControl.PopupControlMouseOverBorder` |

**Opzioni di ricerca: stato predefinito**

![Casella di controllo di ricerca](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Opzioni di ricerca predefinite (casella di controllo)

![Opzioni di ricerca](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Opzioni di ricerca predefinite (collegamento)

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxText` |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonText` |
| Sfondo dell'intestazione | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo dell'intestazione) | `SearchControl.PopupSectionHeaderText` |

**Opzioni di ricerca: stato al passaggio del mouse**

![Opzioni di ricerca (casella di controllo) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opzioni di ricerca (casella di controllo) al passaggio del mouse

![Opzioni di ricerca (collegamento) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opzioni di ricerca (collegamento) al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxMouseDownText` |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonMouseDownText` |
| Bordo | `SearchControl.PopupControlMouseOverBorder` |

**Opzioni di ricerca: stato premuto**

![Opzioni di ricerca premute (casella di controllo)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Opzioni di ricerca premute (casella di controllo)

![Opzioni di ricerca (collegamento)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Opzioni di ricerca (collegamento)

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo della casella di controllo | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxMouseDownText` |
| Sfondo del collegamento | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Viste ad albero
Diverse finestre degli strumenti, tra cui Esplora soluzioni, Esplora server e Visualizzazione classi, `TreeView` implementano uno schema organizzativo gerarchico i cui colori sono controllati dai nomi dei colori nella categoria. Tutti gli elementi in una visualizzazione albero hanno colori di sfondo e del testo. Gli elementi che hanno elementi figlio annidati hanno anche glifi che indicano se ogni elemento è espanso o compresso.

![Vista ad albero (linea rossa)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Vista ad albero (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque sia necessario implementare una visualizzazione organizzativa gerarchica. | ... per tutto ciò che non è simile a una vista ad albero. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Elemento della visualizzazione albero: stato predefinito**

![Elemento predefinito della visualizzazione struttura ad albero](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Elemento predefinito della visualizzazione struttura ad albero

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.Background` |
| Primo piano (testo) | `TreeView.Background` |
| Primo piano (glifo) | `TreeView.Glyph` |
| Bordo | nessuno |

**Elemento della visualizzazione albero: stato al passaggio del mouse**

![Elemento della visualizzazione albero al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Elemento della visualizzazione albero al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.Background` |
| Primo piano (testo) | `TreeView.Background` |
| Primo piano (glifo) | `TreeView.GlyphMouseOver` |
| Bordo | nessuno |

**Elemento della visualizzazione albero: trascina sullo stato**

![Elemento della visualizzazione albero durante il trascinamento](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Elemento della visualizzazione albero durante il trascinamento

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.DragOverItem` |
| Primo piano (testo) | `TreeView.DragOverItem` |
| Primo piano (glifo) | `TreeView.DragOverItemGlyph` |
| Bordo | nessuno |

**Elemento della visualizzazione albero: selezionato, stato attivo**

![Elemento della visualizzazione struttura selezionato e con lo stato attivo](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Elemento della visualizzazione struttura selezionato e con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyph` |
| Bordo | `TreeView.FocusVisualBorder` |

**Elemento della visualizzazione albero: stato selezionato e non focalizzato**

![Elemento della visualizzazione struttura selezionato e non focalizzato](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Elemento della visualizzazione struttura selezionato e non focalizzato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactive` |
| Primo piano (glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Bordo | nessuno |

**Elemento della visualizzazione albero: stato attivo, selezionato e con stato attivo**

![Elemento della visualizzazione albero selezionato e focalizzato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Elemento della visualizzazione albero selezionato e focalizzato al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordo | `TreeView.FocusVisualBorder` |

**Elemento della visualizzazione albero: stato al passaggio del mouse, selezionato e non focalizzato**

![Elemento della visualizzazione albero selezionato e non focalizzato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Elemento della visualizzazione albero selezionato e non focalizzato al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordo | nessuno |

## <a name="shell-appearance"></a>Aspetto della shell

### <a name="background"></a>Background
Lo sfondo dell'ambiente è costituito da due livelli. Il livello inferiore è un colore a tinta unita che ricopre l'intero IDE. Il livello superiore si trova sotto lo scaffale dei comandi tra i canali Nascondi automaticamente della finestra degli strumenti, nei bordi destro e sinistro dell'IDE. I livelli di sfondo superiore e inferiore sono impostati sullo stesso colore nei temi Chiaro e Scuro.

![Sfondo della shell di Visual Studio (linea rossa)Visual Studio shell background (redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Sfondo della shell di Visual Studio (linea rossa)Visual Studio shell background (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i punti in cui si desidera far corrispondere lo sfondo dell'ambiente di Visual Studio. | ... come riempimento per i punti che non sono superfici di sfondo. |
| | ... come sfondo su cui posizionare gli elementi in primo piano. |

**Aspetto della shell del livello inferiore**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.EnvironmentBackground` |

**Aspetto della shell del livello superiore**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Scaffale dei comandi
Due set di nomi di token vengono usati per gli sfondi dello scaffale dei comandi, uno per il punto in cui si trova la barra dei menu e l'altro per il punto in cui si trova la barra dei comandi. Un singolo gruppo della barra dei comandi ha valori di colore di sfondo propri, che vengono descritti in modo più dettagliato nella sezione "Barra dei comandi". Il testo della barra dei menu e della barra dei comandi viene descritto nelle rispettive sezioni.

![Ripiano dei comandi di Visual Studio (redline)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Ripiano dei comandi di Visual Studio (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per le aree in cui si posizionano i menu o le barre degli strumenti. | ... per le aree che non sono simili a uno scaffale di comando. |
|... con la combinazione corretta nome token di sfondo/primo piano. | |

**Barra del menu a scaffale dei comandi**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barra dei comandi di mensola dei comandi**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Finestra Progettazione manifesto
La finestra Progettazione manifesto è stata progettata come strumento per semplificare la modifica del file manifesto in progetti Windows 8 e Windows Phone 8. Benché non sia disponibile per l'utilizzo alcun framework condiviso, potrebbe essere appropriato fare in modo che il layout di progettazione e i colori delle schede di orientamento/spostamento corrispondano alla struttura complessiva. Per altre informazioni sui dettagli del layout, vedere [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Progettazione manifesto (linea rossa)Manifest Designer (redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Progettazione manifesto (linea rossa)Manifest Designer (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per le finestre di progettazione simili a Progettazione manifesto. | ... se si dispone di più di sei schede. |
| ... al posto dell'utilizzo di controlli struttura a schede comuni nella parte superiore di un editor all'interno del documento. | ... per qualsiasi interfaccia utente non strutturata come progettazione del manifesto. |

**Scheda selezionata di Progettazione manifesto: stato predefinitoManifest Designer selected tab: default state**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `ManifestDesigner.TabActive` |
| Bordo | nessuno |

**Riquadro di descrizione selezionato di Progettazione manifesto: stato predefinitoManifest Designer selected description pane: default state**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `ManifestDesigner.DescriptionPane` |

**Pagina di contenuto selezionata di Progettazione manifesto: stato predefinitoManifest Designer selected content page: default state**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `ManifestDesigner.Background` |
| Testo di supporto della finestra di dialogo | `ManifestDesigner.WatermarkText`<br />(Il nome del token non corrisponde alla relativa funzione.) |

**Scheda Progettazione manifesto: stato non selezionato**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `ManifestDesigner.Tab.Inactive` |

**Scheda Progettazione manifesto: stato al passaggio del mouseManifest Designer tab: hover state**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Strutture dei comandi

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menu
I menu possono verificarsi in diverse posizioni all'interno di Visual Studio: la barra dei menu principale, incorporata nelle finestre del documento o degli strumenti o fare clic con il pulsante destro del mouse in varie posizioni in tutto l'IDE. Le implementazioni dei menu associati ad altri elementi dell'interfaccia utente vengono descritte nella sezione relativa al rispettivo elemento. È preferibile usare sempre l'implementazione dei menu standard fornita dall'ambiente di Visual Studio. Tuttavia, in alcuni casi rari si potrebbe non avere accesso ai menu standard di Visual Studio. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri menu in Visual Studio.

![Menu di Visual Studio (linea rossa)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menu di Visual Studio (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando è necessario creare un menu personalizzato.| ... solo il colore di sfondo. Usare sempre la combinazione sfondo/primo piano specificata. |
| ... quando si dispone di un nuovo componente dell'interfaccia utente che si desidera associare i menu di Visual Studio.| |

#### <a name="menu-titles"></a>Titoli dei menu
I titoli dei menu sono costituiti da uno sfondo, un bordo e il testo del titolo, nonché da un glifo facoltativo, in genere quando il menu si trova in una barra dei comandi.

![Titolo del menu (linea rossa)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Titolo del menu (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ogni volta che si sta creando un titolo di menu personalizzato. | ... per tutto ciò che non si desidera abbinare sempre il titolo del menu. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Titolo menu: stato predefinito**

![Titolo predefinito del menu](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Titolo predefinito del menu

![Titolo di menu predefinito con glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Titolo di menu predefinito con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarMenuGlyph` |
| Bordo | nessuno |

**Titolo del menu: stato al passaggio del mouse**

![Titolo menu al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Titolo menu al passaggio del mouse

![Titolo menu con glifo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Titolo menu con glifo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |
| Bordo | `Environment.CommandBarBorder` |

**Titolo del menu: stato premuto**

![Titolo del menu premuto](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Titolo del menu premuto

![Titolo del menu premuto con glifo](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Titolo del menu premuto con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Bordo | `Environment.CommandBarMenuBorder`<br />(Solo lati sinistro, superiore e destro.) |

**Titolo del menu: stato disabilitato**

![Titolo del menu disabilitato con glifo](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Titolo del menu disabilitato con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Primo piano (glifo) | `Environment.CommandBarTextInactive` |
| Bordo | nessuno |

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
| Background | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Bordo | `Environment.CommandBarMenuBorder` |
| Sfondo del canale delle icone | `Environment.CommandBarMenuIconBackground` |
| Separatore | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Voci di menu: stati selezionati e selezionati**

![Menu scelto](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Voce di menu selezionata

![Menu selezionato](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Voce di menu selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Segno di spunta | `Environment.CommandBarCheckBox` |
| Sfondo del segno di spunta | `Environment.CommandBarSelectedIcon` |
| Sfondo dell'icona | `Environment.CommandBarSelected` |
| Bordo dell'icona | `Environment.CommandBarSelectedBorder` |

**Voci di menu: stato al passaggio del mouse**

![Menu al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Voce di menu al passaggio del mouse

![Menu scelto al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Voce di menu selezionata al passaggio del mouse

![Menu selezionato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Voce di menu selezionata al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarMenuItemMouseOver` |
| Primo piano (testo) | `Environment.CommandBarMenuItemMouseOverText` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Segno di spunta | `Environment.CommandBarCheckBoxMouseOver` |
| Sfondo del segno di spunta | `Environment.CommandBarHoverOverSelectedIcon` |
| Sfondo dell'icona | `Environment.CommandBarHoverOverSelected` |
| Bordo dell'icona | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Voci di menu: stato disabilitato**

![Menu disabilitato](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Voce di menu disabilitata

![Menu disabilitato selezionato](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Voce di menu Disabilitata con segno di spunta

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Segno di spunta | `Environment.CommandBarCheckBoxDisabled` |
| Sfondo del segno di spunta | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barre dei comandi
Una barra dei comandi può essere visualizzata in più posizioni all'interno dell'IDE di Visual Studio, in particolare il ripiano dei comandi e incorporato nelle finestre degli strumenti o del documento.

In generale, usare sempre l'implementazione della barra dei menu standard fornita dall'ambiente di Visual Studio. L'uso del meccanismo standard garantisce che tutti i dettagli visivi vengano visualizzati correttamente e che gli elementi interattivi abbiano un comportamento coerente con gli altri controlli della barra dei comandi di Visual Studio. Tuttavia, se è necessario compilare una barra dei comandi personalizzata, assicurarsi di applicare lo stile corretto usando i nomi di token seguenti.

![Barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barra dei comandi (linea rossa)

![Pulsante di overflow con linea rossa](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Pulsante Overflow (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... nelle posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile utilizzare l'implementazione standard della barra dei comandi di Visual Studio. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi. |
| | ... per i componenti della barra dei comandi diversi da quelli per cui vengono specificati i nomi dei token. |

#### <a name="command-bar-groups"></a>Gruppi della barra dei comandi
Un gruppo della barra dei comandi è costituito da un set correlato di controlli della barra dei comandi e può contenere un numero qualsiasi di pulsanti, pulsanti di menu combinato, menu a discesa, caselle combinate o menu. I colori per questi controlli sono determinati da nomi di token separati e vengono descritti singolarmente in altre sezioni di questa guida. Viene usata una linea di separazione per dividere un gruppo della barra dei comandi in sottogruppi correlati.

![Gruppo barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Gruppo della barra dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... nelle posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile utilizzare l'implementazione standard della barra dei comandi di Visual Studio. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi. |
| | ... per i componenti della barra dei comandi diversi da quelli per cui vengono specificati i nomi dei token. |

**Gruppo barra dei comandi: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Bordo | `Environment.CommandBarToolBarBorder` |
| Quadratino di trascinamento | `Environment.CommandBarDragHandle` |
| Separatore | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Icone dei comandi
![Icona del comando con linea rossa](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Icona comando (linea rossa)

![Icona comando con redline del testo](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Icona comando con testo (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per tutti i pulsanti che verranno posizionati su una barra dei comandi. | ... per i controlli che hanno i propri nomi di token. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Icona del comando: stato predefinito**

![Icona del comando predefinita](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Icona del comando predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Bordo | N/D |

**Icona Comando: stato predefinito, selezionato**

![Icona di comando predefinita selezionata](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Icona di comando predefinita selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarSelected` |
| Primo piano (testo) | `Environment.CommandBarTextSelected` |
| Bordo | `Environment.CommandBarSelectedBorder` |

**Icona del comando: stati di passaggio del mouse o dello stato attivo**

![Icona del comando al passaggio del mouse o dello stato attivo](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Icona del comando al passaggio del mouse o dello stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Bordo | `Environment.CommandBarBorder` |

**Icona comando: stati di passaggio del mouse o dello stato attivo, selezionati**

![Icona del comando selezionato al passaggio del mouse o dello stato attivo](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Icona del comando selezionato al passaggio del mouse o dello stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarHoverOverSelected` |
| Primo piano (testo) | `Environment.CommandBarTextHoverOverSelected` |
| Bordo | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icona del comando: stato premuto**

![Icona del comando premuta](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Icona del comando premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.CommandBarTextMouseDown` |
| Bordo | `Environment.CommandBarBorder` |

**Icona del comando: stato disabilitato**

![Icona del comando disabilitata](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Icona del comando disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Bordo | N/D |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Caselle combinate della barra dei comandi

> [!IMPORTANT]
> Le caselle combinate sono simili agli elenchi a discesa, ma includono un'area di testo modificabile. Se l'elenco a discesa non include un'area di testo modificabile, utilizzare i token di colore per [gli menu a discesa della barra](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)dei comandi .

![Casella combinata della barra dei comandi redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Casella combinata barra dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... durante la creazione di caselle combinate personalizzate. | ... per tutto ciò che non si desidera sempre corrispondere all'interfaccia utente della barra dei comandi. |
| ... quando si crea un controllo barra dei comandi simile a una casella combinata. | ... quando si ha accesso a una casella combinata con stili. |

**Campo di input casella combinata della barra dei comandi: stato predefinito**

![Campo di input casella combinata della barra dei comandi](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Campo di input casella combinata della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxBackground` |
| Primo piano (testo) | `Environment.ComboBoxText` |
| Bordo | `Environment.ComboBoxBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato predefinito**

![Casella combinata a discesa&#45;pulsante giù](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Pulsante a discesa della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (glifo) | `Environment.ComboBoxGlyph` |

**Elenco a discesa della barra dei comandi: stato predefinito**

![Elenco a discesa della barra dei comandi](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Elenco a discesa della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxPopupBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.ComboBoxItemText` |
| Bordo | `Environment.ComboBoxPopupBorder` |

**Campo di input casella combinata della barra dei comandi: stato al passaggio del mouse**

![Campo di input casella combinata della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Campo di input casella combinata della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.ComboBoxMouseOverText` |
| Bordo | `Environment.ComboBoxMouseOverBorder` |
| Separatore | `Environment.ComboBoxMouseOverSeparator` |

 **Pulsante a discesa della barra dei comandi: stato al passaggio del mouse**

![Pulsante a discesa della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Pulsante a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Elenco a discesa della barra dei comandi: stato al passaggio del mouse**

 ![Elenco a discesa della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Elenco a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (voce di menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primo piano (testo) | `Environment.ComboBoxItemMouseOverText` |
| Bordo (voce di menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo di input casella combinata della barra dei comandi: stato attivo**

![Campo di input casella combinata della barra dei comandi con stato attivo](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Campo di input casella combinata della barra dei comandi con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxFocusedBackground` |
| Primo piano (testo) | `Environment.ComboBoxFocusedText` |
| Bordo | `Environment.ComboBoxFocusedBorder` |
| Separatore | `Environment.ComboBoxFocusedButtonSeparator` |

**Pulsante a discesa della barra dei comandi: stato attivo**

![Pulsante a discesa della barra dei comandi con stato attivo](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Pulsante a discesa della barra dei comandi con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxFocusedButtonBackground` |
| Primo piano (glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Campo di input casella combinata della barra dei comandi: stato premuto**

![Campo di input casella combinata della barra dei comandi premuto](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Campo di input casella combinata della barra dei comandi premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxMouseDownBackground` |
| Primo piano (testo) | `Environment.ComboBoxMouseDownText` |
| Bordo | `Environment.ComboBoxMouseDownBorder` |
| Separatore | `Environment.ComboBoxMouseDownSeparator` |

**Pulsante a discesa della barra dei comandi: stato premuto**

![Pulsante a discesa della barra dei comandi](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Pulsante a discesa della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo di input casella combinata della barra dei comandi: stato disabilitato**

![Campo di input casella combinata della barra dei comandi disabilitata](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Campo di input casella combinata della barra dei comandi disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ComboBoxDisabledBackground` |
| Primo piano (testo) | `Environment.ComboBoxDisabledText` |
| Bordo | `Environment.ComboBoxDisabledBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato disabilitato**

![Pulsante a discesa della barra dei comandi disabilitata](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Pulsante a discesa della barra dei comandi disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (glifo) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>menu a discesa della barra dei comandi

> [!IMPORTANT]
> Gli elenchi a discesa sono simili alle caselle combinate, ma non contengono aree di testo modificabili. Se l'elenco a discesa include un'area di testo modificabile, utilizzare i token di colore per [le caselle combinate della barra](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)dei comandi.

![menu a discesa della barra dei comandi (linea rossa)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />menu a discesa della barra dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si creano controlli elenco a discesa personalizzati. | ... per tutto ciò che non è simile a un elenco a discesa. |
| | ... per caselle combinate o pulsanti dividi. |

**Campo di selezione a discesa della barra dei comandi: stato predefinito**

![Campo di selezione a discesa della barra dei comandi predefinita](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Campo di selezione a discesa della barra dei comandi predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DropDownBackground` |
| Primo piano (testo) | `DropDownText` |
| Bordo | `DropDownBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato predefinito**

![Pulsante a discesa della barra dei comandi predefinita](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Pulsante a discesa della barra dei comandi predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (glifo) | `Environment.DropDownGlyph` |

**Elenco a discesa della barra dei comandi: stato predefinito**

![Elenco a discesa della barra dei comandi predefinita](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Elenco a discesa della barra dei comandi predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DropDownPopupBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.ComboBoxItemText` |
| Bordo | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Campo di selezione a discesa della barra dei comandi: stato al passaggio del mouse**

![Campo di selezione a discesa della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Campo di selezione a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DropDownMouseOverBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.DropDownMouseOverText` |
| Bordo | `Environment.DropDownMouseOverBorder` |
| Separatore | `Environment.DropDownButtonMouseOverSeparator` |

**Pulsante a discesa della barra dei comandi: stato al passaggio del mouse**

![Pulsante a discesa della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Pulsante a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DropDownButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.DropDownMouseOverGlyph` |

**Elenco a discesa della barra dei comandi: stato al passaggio del mouse**

![Elenco a discesa della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Elenco a discesa della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (voce di menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primo piano (testo) | `Environment.ComboBoxItemMouseOverText` |
| Bordo (voce di menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo di selezione a discesa della barra dei comandi: stato premuto**

![È stato premuto il campo di selezione&#45;verso il basso](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Pressa il campo di selezione a discesa della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DropDownMouseDownBackground` |
| Primo piano (testo) | `Environment.DropDownMouseDownText` |
| Bordo | `Environment.DropDownMouseDownBorder` |
| Separatore | `Environment.DropDownButtonMouseDownSeparator` |

**Pulsante a discesa della barra dei comandi: stato premuto**

![Pulsante a discesa della barra dei comandi](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Pulsante a discesa della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DropDownButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo di selezione a discesa della barra dei comandi: stato disabilitato**

![Campo di selezione a discesa della barra dei comandi disabilitata](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Campo di selezione a discesa della barra dei comandi disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DropDownDisabledBackground` |
| Primo piano (testo) | `Environment.DropDownDisabledText` |
| Bordo | `Environment.DropDownDisabledBorder` |
| Separatore | Nessun separatore |

**Pulsante a discesa della barra dei comandi: stato disabilitato**

![Pulsante a discesa della barra dei comandi disabilitata](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Pulsante a discesa della barra dei comandi disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D |
| Primo piano (glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Pulsanti di divisione della barra dei comandi
I pulsanti di menu combinato condividono molti nomi di token con altri controlli della barra dei comandi, come pulsanti, menu e testo della barra dei comandi. Tutti i nomi di token dei pulsanti a discesa e di azione necessari vengono ripetuti qui per praticità. Gli elenchi a discesa dei [pulsanti](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)dividi sono implementazioni dei menu della barra dei comandi.

![Pulsante di menu combinato con linea rossa](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Pulsante di divisione della barra dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea un pulsante di divisione personalizzato. | ... per altri tipi di pulsanti. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Pulsante di divisione della barra dei comandi: stato predefinito**

![Pulsante di divisione della barra dei comandi predefinita](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Pulsante di divisione della barra dei comandi predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | nessuno |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Bordo | N/D |
| Separatore | N/D |

**Pulsante di divisione della barra dei comandi: stato al passaggio del mouse**

![Pulsante di divisione della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Pulsante di divisione della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Bordo | `Environment.CommandBarBorder` |
| Separatore | `Environment.CommandBarSplitButtonSeparator` |

**Pulsante di divisione della barra dei comandi: stato premuto**

![Pulsante di divisione della barra dei comandi](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Pulsante di divisione della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.CommandBarTextMouseDown` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Bordo | `Environment.CommandBarBorder` |
| Separatore | N/D |

**Pulsante di divisione della barra dei comandi: stato disabilitato**

![Pulsante di divisione della barra dei comandi disabilitato](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Pulsante di divisione della barra dei comandi disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D |
| Primo piano (testo) | `Environment.ComboBoxItemTextInactive` |
| Primo piano (glifo) | `Environment.CommandBarTextInactive` |
| Bordo | N/D |
| Separatore | N/D |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Barra dei comandi 'Altre opzioni' e pulsanti 'Overflow'
Il pulsante "Altre opzioni" viene usato quando un gruppo della barra dei comandi può essere personalizzato aggiungendo o rimuovendo pulsanti della barra dei comandi correlati. Il pulsante "Overflow" viene visualizzato quando una barra dei comandi è troncata a causa della mancanza di spazio orizzontale e, dopo avervi fatto clic sopra, mostra un menu che contiene i pulsanti della barra dei comandi che non possono essere visualizzati. I colori per questi due pulsanti sono controllati dallo stesso set di nomi di token.

![Pulsante 'Altre opzioni' della barra dei comandi (linea rossa)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Pulsante 'Altre opzioni' della barra dei comandi (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i pulsanti personalizzati 'Altre opzioni' o 'Overflow'. | ... per i pulsanti che non hanno funzionalità simili a un pulsante 'Altre opzioni' o 'Overflow'. |

**Pulsanti 'Altre opzioni' e "Overflow" della barra dei comandi: stato predefinito**

![Pulsante 'Altre opzioni' della barra dei comandi predefinita](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Pulsante 'Altre opzioni' della barra dei comandi predefinita

![Pulsante 'Overflow' della barra dei comandi predefinita](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Pulsante 'Overflow' della barra dei comandi predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarOptionsBackground` |
| Primo piano (glifo) | `Environment.CommandBarOptionsGlyph` |

**Pulsanti 'Altre opzioni' e "Overflow" della barra dei comandi: stato al passaggio del mouse**

![Barra dei comandi 'Altre opzioni' pulsante al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Barra dei comandi 'Altre opzioni' pulsante al passaggio del mouse

![Pulsante 'Overflow' della barra dei comandi al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Pulsante 'Overflow' della barra dei comandi al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Barra dei comandi 'Altre opzioni' e pulsanti 'Overflow': stato premuto**

![Pulsante 'Altre opzioni' della barra dei comandi](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Pulsante 'Altre opzioni' della barra dei comandi

![Overflow selezionato](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Pulsante 'Overflow' della barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Finestre dei documenti
Non è necessario replicare le finestre dei documenti, perché vengono fornite dall'ambiente di Visual Studio.There's no need to replicate document windows, because they're provided by the Visual Studio environment. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre dei documenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.

Quando si utilizzano i token di colore della finestra del documento, prestare attenzione a utilizzarli solo per elementi simili e sempre in coppia. Se non esegui questa operazione, potresti ottenere risultati imprevisti nell'interfaccia utente.

### <a name="document-window-frames"></a>Cornici della finestra del documento
Le finestre dei documenti possono essere ancorate nell'IDE o mobili come finestre separate. Quando una finestra del documento è mobile all'esterno dell'IDE, si trova ancora in un documento e dispone di sfondo, bordo, testo e colori di tabulazione che sono gli stessi di quando fa parte dell'IDE. Tuttavia, il documento si trova all'interno di una cornice che ha colori di sfondo, del bordo e del testo propri. Quando le finestre degli strumenti sono ancorate nell'area dei documenti, ereditano il comportamento e il colore per le rispettive schede dai nomi di token delle finestre dei documenti.

![Finestra del documento ancorata (linea rossa)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Finestra del documento ancorata (linea rossa)

![Finestra mobile del documento (linea rossa)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Finestra mobile del documento (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque si sta creando l'interfaccia utente che si desidera abbinare la finestra del documento. | ...  per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

**Finestra del documento ancorata o mobile: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | Dipende dal tipo di documento |
| Primo piano (testo) | Dipende dal tipo di documento |
| Bordo | `Environment.ToolWindowBorder` |

**Cornice della finestra del documento con stato attivo e mobile: stato predefinito**

![Cornice della finestra di documento attiva e mobile predefinita](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Cornice della finestra di documento attiva e mobile predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowFloatingFrame` |
| Primo piano (testo) | `Environment.ToolWindowFloatingFrame` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Bordo | `Environment.MainWindowActiveDefaultBorder` |
| Bordo (glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Imposta su trasparente) |

**Cornice della finestra del documento mobile non focalizzata: stato predefinito**

![Cornice predefinita della finestra del documento non focalizzata e mobile](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Cornice predefinita della finestra del documento non focalizzata e mobile

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowFloatingFrameInactive` |
| Primo piano (testo) | `Environment.ToolWindowFloatingFrameInactive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Bordo | `Environment.MainWindowInactiveBorder` |
| Bordo (glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Imposta su trasparente) |

**Cornice della finestra del documento con stato attivo e mobile: stato al passaggio del mouse**

![Cornice della finestra del documento con stato attivo e mobile al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Cornice della finestra del documento con stato attivo e mobile al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Cornice della finestra del documento mobile non focalizzata: stato al passaggio del mouse**

![Cornice della finestra del documento non focalizzata e mobile al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Cornice della finestra del documento non focalizzata e mobile al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Cornice della finestra del documento con stato attivo e mobile: stato premuto**

![Cornice della finestra del documento mobile e con stato attivo alla stampa](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Cornice della finestra del documento mobile e con stato attivo alla stampa

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `Environment.RaftedWindowButtonDown` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Schede dei documenti
Le schede dei documenti si trovano nel canale delle schede per indicare i documenti attualmente aperti, insieme al documento selezionato o attivo corrente. Anche le finestre degli strumenti possono essere ancorate nel canale delle schede dei documenti se l'utente le aggiunge in questa posizione. In questo caso, usano gli stessi colori delle schede delle finestre dei documenti. Se si crea un'interfaccia utente che deve corrispondere sempre ai colori delle finestre dei documenti (inclusi gli aggiornamenti dei temi o se vengono installati nuovi temi), fare riferimento a questi token di colore.

![Schede del documento (linea rossa)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Schede del documento (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque tu stia creando l'interfaccia utente che vuoi abbinare alle schede del documento e raccogliere automaticamente gli aggiornamenti del tema o i nuovi colori del tema. | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente quando la shell ha un aggiornamento del tema. |

#### <a name="open-document-tabs"></a>Schede dei documenti aperti
Per ogni documento aperto è presente una scheda nel canale delle schede dei documenti che ne visualizza il nome. I documenti possono essere selezionati o aperti in background e le rispettive schede riflettono questi stati:

- La scheda selezionata rappresenta il documento attualmente visualizzato nell'area dei documenti. Una scheda selezionata ha un bordo di documento che si estende fino al bordo superiore dell'area dei documenti.

- Le schede di sfondo sono tutte le schede del documento che non sono la scheda attualmente selezionata. Una volta fatto clic, diventano la scheda selezionata e acquisiscono tutti i colori dello sfondo, del bordo e del testo da tali nomi di token.

![Scheda Apri documento (linea rossa)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Scheda Apri documento (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... durante la creazione di schede documento personalizzate. | ... per le schede provvisorie (in anteprima). |
| | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

**Scheda Documento selezionato e con lo stato attivo**

![Scheda Documento selezionato e con lo stato attivo](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Scheda Documento selezionato e con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabSelectedGradientTop`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.FileTabSelectedText` |
| Bordo | `Environment.FileTabSelectedBorder`<br />(Impostare sullo stesso colore dello sfondo.) |
| Bordo del documento | `Environment.FileTabDocumentBorderBackground` |

**Scheda Documento selezionata e non messa a fuoco**

![Scheda Documento selezionata e non messa a fuoco](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Scheda Documento selezionata e non messa a fuoco

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabInactiveGradientTop`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.FileTabInactiveText` |
| Bordo | `Environment.FileTabInactiveBorder`<br />(Impostare sullo stesso colore dello sfondo.) |
| Bordo del documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Scheda Documento in background: stato predefinito**

![Scheda Documento di sfondo predefinito](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Scheda Documento di sfondo predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabBackground` |
| Primo piano (testo) | `Environment.FileTabText` |
| Bordo | `Environment.FileTabBorder`<br />(Impostare sullo stesso colore dello sfondo.) |

**Scheda Documento in background: stato al passaggio del mouse**

![Scheda Documento in background al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Scheda Documento in background al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabHotGradientTop`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.FileTabHotText` |
| Bordo | `Environment.FileTabHotBorder`<br />(Impostare sullo stesso colore dello sfondo.) |

#### <a name="preview-tab"></a>Scheda anteprima
Chiamata anche scheda "provvisoria". La scheda di anteprima viene visualizzata sul lato destro del canale della scheda del documento quando l'utente fa clic su un elemento nella finestra degli strumenti Esplora soluzioni. Questa scheda funge da anteprima del documento e offre all'utente anche l'opzione di mantenere il documento aperto sul lato sinistro del canale delle schede dei documenti. Può essere aperta una sola scheda anteprima per volta. Le schede anteprima hanno sia uno sfondo sia stati selezionati, come le schede aperte, e possono avere stato attivo o non attivo quando sono attive.

![Scheda Anteprima (linea rossa)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Scheda Anteprima (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque si stia creando l'anteprima provvisoria e si desidera che un elemento corrisponda al colore della scheda di anteprima corrente. | ... per qualsiasi tipo di documento o scheda non provvisorio (anteprima). |
| | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

**Scheda di anteprima attiva e selezionata**

![Scheda di anteprima attiva e selezionata](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Scheda di anteprima attiva e selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabProvisionalSelectedActive` |
| Primo piano (testo) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Bordo | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Impostare sullo stesso colore dello sfondo.) |
| Bordo del documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Scheda di anteprima non focalizzata e selezionata**

![Scheda di anteprima non focalizzata e selezionata](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Scheda di anteprima non focalizzata e selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabProvisionalSelectedInactive` |
| Primo piano (testo) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Bordo | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Bordo del documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Scheda Anteprima in background: stato predefinito**

![Scheda di anteprima sfondo predefinita](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Scheda di anteprima sfondo predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabProvisionalInactive` |
| Primo piano (testo) | `Environment.FileTabProvisionalInactiveForeground` |
| Bordo | `Environment.FileTabProvisionalInactiveBorder`<br />(Impostare sullo stesso colore dello sfondo.) |

**Scheda Anteprima in background: stato al passaggio del mouse**

![Scheda Anteprima in background al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Scheda Anteprima in background al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.FileTabProvisionalHover` |
| Primo piano (testo) | `Environment.FileTabProvisionalHoverForeground` |
| Bordo | `Environment.FileTabProvisionalHoverBorder`<br />(Impostare sullo stesso colore dello sfondo.) |

#### <a name="document-overflow-button"></a>Pulsante di overflow dei documenti
Il pulsante di overflow dei documenti è presente se ci sono uno o più documenti aperti, indipendentemente dal fatto che nella configurazione corrente sia disponibile spazio sufficiente da contenere tutte le schede dei documenti. Il menu a discesa di overflow del documento, controllato dai colori dei menu della barra dei [comandi,](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) visualizza un elenco di tutti i documenti aperti, sia visibili che nascosti, e il glifo di overflow cambia a seconda che tutti i documenti aperti vengano visualizzati nel canale a schede.

![Pulsante di overflow del documento (linea rossa)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Pulsante di overflow del documento (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si crea un pulsante di overflow del documento personalizzato. | ... per l'interfaccia utente che non è simile a un pulsante di overflow. |
| | ... per i pulsanti di overflow della barra dei comandi. |

**Pulsante di overflow del documento: stato predefinito**

![Pulsante di overflow del documento predefinito](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Pulsante di overflow del documento predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DocWellOverflowButtonBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Bordo | N/D |

**Pulsante di overflow del documento: stato al passaggio del mouse**

![Pulsante di overflow dei documenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Pulsante di overflow dei documenti al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Bordo | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Pulsante di overflow del documento: stato premuto**

![Pulsante di overflow del documento alla pressione](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Pulsante di overflow del documento alla pressione

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Bordo | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Assegnazione di tag
Visual Studio supporta l'assegnazione di tag, che permette a un utente di dichiarare parole chiave da cercare per scopi di verifica. Ad esempio, i project manager e gli sviluppatori possono usare Team Foundation Server (TFS) per assegnare tag a elementi di lavoro. La tabella seguente indica i nomi di colore per il tag stesso e il glifo dell'icona di chiusura visualizzato negli stati corrispondenti al passaggio del mouse e alla selezione.

![Assegnazione di tag in Visual Studio (linea rossa)Tagging in Visual Studio (redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Assegnazione di tag in Visual Studio (linea rossa)Tagging in Visual Studio (redline)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per l'interfaccia utente che supporta il tagging. | ... per qualsiasi altro tipo di interfaccia utente. |

#### <a name="tags"></a>Tag

**Tag: stato predefinito**

![Tag predefinito](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Tag predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.Background` |
| Primo piano (testo) | `Tag.Background` |

**Etichetta: stato al passaggio del mouse**

![Tag al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.HoverBackground` |
| Primo piano (testo) | `Tag.HoverBackgroundText` |

**Tag: stato premuto**

![Tag premuto](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Tag premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.PressedBackground` |
| Primo piano (testo) | `Tag.PressedBackgroundText` |

**Etichetta: stato selezionato**

![Tag selezionato](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Tag selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.SelectedBackground` |
| Primo piano (testo) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Chiudere&times;il glifo del tag ( )

**Close&times;( ) - glifo del tag: stato predefinito**

![Glifo&times;del tag Chiudi predefinito ( )](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Glifo&times;del tag Chiudi predefinito ( )

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D |
| Primo piano (glifo) | `Tag.TagHoverGlyph` |

**Chiudi&times;( ) il glifo del tag: al passaggio del mouse**

![Chiudi&times;( ) il glifo del tag al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Chiudi&times;( ) il glifo del tag al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.TagHoverGlyphHoverBackground` |
| Primo piano (glifo) | `Tag.TagHoverGlyphHover` |
| Bordo | `Tag.TagHoverGlyphHoverBorder` |

**Close&times;( ) tag glifo: stato premuto**

![Glifo&times;del tag Close ( ) premuto](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Glifo&times;del tag Close ( ) premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.TagHoverGlyphPressedBackground` |
| Primo piano (glifo) | `Tag.TagHoverGlyphPressed` |
| Bordo | `Tag.TagHoverGlyphPressedBorder` |

**Tag selezionato con&times;glifo Chiudi ( ) : stato predefinito**

![Tag selezionato predefinito&times;con glifo Chiudi ( )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Tag selezionato predefinito&times;con glifo Chiudi ( )

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D |
| Primo piano (glifo) | `Tag.TagSelectedGlyph` |

**Tag selezionato con&times;glifo Chiudi ( ): stato al passaggio del mouse**

![Tag selezionato con&times;glifo Chiudi ( ) al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Tag selezionato con&times;glifo Chiudi ( ) al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.TagSelectedGlyphHoverBackground` |
| Primo piano (glifo) | `Tag.TagSelectedGlyphHover` |
| Bordo | `Tag.TagSelectedGlyphHoverBorder` |

**Tag selezionato con&times;glifo Chiudi ( ) : stato premuto**

![Tag selezionato con glifo Di chiusura (&times;)](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Tag selezionato con glifo Di chiusura (&times;)

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Tag.TagSelectedGlyphPressedBackground` |
| Primo piano (glifo) | `Tag.TagSelectedGlyphPressed` |
| Bordo | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Finestre degli strumenti
Non è necessario replicare le finestre degli strumenti, perché vengono fornite dall'ambiente di Visual Studio.There's no need to replicate tool windows, because they're provided by the Visual Studio environment. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre degli strumenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.

![Finestra degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Finestra degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque si sta creando l'interfaccia utente che si desidera abbinare le finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

### <a name="tool-window-frame"></a>Cornice delle finestre degli strumenti
Le finestre degli strumenti in Visual Studio vengono usate per molte attività diverse e possono avere stati diversi. Se una finestra degli strumenti è aperta, può essere assegnata a uno qualsiasi dei quattro lati dell'area del documento. Le finestre degli strumenti possono anche essere mobili al di fuori dell'IDE, per poter essere riposizionate in qualsiasi punto dello schermo dell'utente. Le finestre mobili sono sempre in primo piano nell'IDE. Infine, le finestre degli strumenti possono essere ancorate come finestre dei documenti ed essere visualizzate come scheda nell'area dei documenti. Le finestre degli strumenti ancorate come finestre dei documenti vengono colorate in parte usando i nomi di token delle finestre dei documenti.

![Cornice della finestra degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Cornice della finestra degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ...  ovunque si sta creando l'interfaccia utente che si desidera abbinare le finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

**Finestra degli strumenti ancorata**

![Finestra degli strumenti ancorata](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Finestra degli strumenti ancorata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowBackground` |
| Bordo | `Environment.ToolWindowBorder` |

**Finestra degli strumenti mobile con lo stato attivo**

![Finestra degli strumenti mobile con lo stato attivo](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Finestra degli strumenti mobile con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowBackground` |
| Bordo | `Environment.MainWindowActiveDefaultBorder` |

**Finestra degli strumenti mobile non focalizzata**

![Finestra degli strumenti mobile non focalizzata](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Finestra degli strumenti mobile non focalizzata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowBackground` |
| Bordo | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Finestre simili a strumenti
The toolbox is one of the most frequently used common tool windows in Visual Studio. È essenzialmente un controllo struttura ad albero con un tema speciale e uno stile applicato.

![Finestra simile a una casella degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Finestra simile a una casella degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... quando si progetta una finestra degli strumenti che si desidera essere sempre coerente con la casella degli strumenti della shell. | ... per tutto ciò che non è simile all'interfaccia utente della casella degli strumenti o se non si è certi che l'interfaccia utente avrà problemi se i colori della casella degli strumenti della shell cambiano. |

**Nodi della casella degli strumenti: stato predefinito**

![Nodo padre predefinito della casella degli strumenti](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nodo padre predefinito della casella degli strumenti

![Nodo figlio predefinito della casella degli strumenti](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nodo figlio predefinito della casella degli strumenti

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolboxContent`<br />(Intestazioni) |
| Background | `Environment.ToolWindowBackground`<br />(Singoli elementi o intera finestra se non sono disponibili controlli) |
| Bordo | nessuno |
| Primo piano (glifo) | `Environment.ToolboxContent` |
| Primo piano (testo) | `Environment.ToolboxContent` |

**Nodi figlio della casella degli strumenti: stato al passaggio del mouse**

![Nodo figlio della casella degli strumenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nodo figlio della casella degli strumenti al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolboxContentMouseOver`<br />(Solo singoli elementi) |
| Bordo | nessuno |
| Primo piano (testo) | `Environment.ToolboxContentMouseOver`<br />(Solo singoli elementi) |

**Nodi della casella degli strumenti selezionati: stato attivo**

![Nodo padre della casella degli strumenti selezionato con lo stato attivo](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nodo padre della casella degli strumenti selezionato con lo stato attivo

![Nodo figlio della casella degli strumenti selezionato con lo stato attivo](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nodo figlio della casella degli strumenti selezionato con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemActive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordo | `TreeView.FocusVisualBorder`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primo piano (glifo) | `TreeView.SelectedItemActive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primo piano (testo) | `TreeView.SelectedItemActive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Nodi della casella degli strumenti selezionati: stato non stato attivo**

![Nodo padre della casella degli strumenti selezionato e non focalizzato](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nodo padre della casella degli strumenti selezionato e non focalizzato

![Nodo figlio della casella degli strumenti selezionato e non focalizzato](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nodo figlio della casella degli strumenti selezionato e non focalizzato

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `TreeView.SelectedItemInactive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordo | nessuno |
| Primo piano (glifo) | `TreeView.SelectedItemInactive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primo piano (testo) | `TreeView.SelectedItemInactive`<br />Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barra del titolo delle finestre degli strumenti
Il bordo della barra del titolo non è un vero bordo, è una linea spessa nella parte superiore della barra del titolo. Non ha un nome di token per il suo stato non focalizzato.

![Barra del titolo della finestra degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barra del titolo della finestra degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque si sta creando l'interfaccia utente che si desidera abbinare le finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

**Barra del titolo con stato attivo**

![Barra del titolo con stato attivo](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barra del titolo con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.TitleBarActiveGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.TitleBarActiveText` |
| Bordo | `Environment.TitleBarActiveBorder`<br />(Impostare sullo stesso colore dello sfondo.) |
| Quadratino di trascinamento | `Environment.TitleBarDragHandleActive` |

**Barra del titolo con stato non attivo**

![Barra del titolo con stato non attivo](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barra del titolo con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.TitleBarInactiveGradientBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.TitleBarInactiveText` |
| Bordo | N/D |
| Quadratino di trascinamento | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Pulsanti della barra del titolo della finestra degli strumenti
![Pulsante della barra del titolo (linea rossa)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Pulsante della barra del titolo (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... per i pulsanti visualizzati nell'interfaccia utente che usano i token di colore dalle barre del titolo della finestra degli strumenti. | ... per i pulsanti visualizzati in altre posizioni. |
| | ... in qualsiasi combinazione di sfondo/primo piano diversa da quella specificata. |

**Pulsanti della barra del titolo con stato attivo: stato predefinito**

![Pulsanti predefiniti della barra del titolo con lo stato attivo](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Pulsanti predefiniti della barra del titolo con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D |
| Primo piano (glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Bordo | N/D |

**Pulsanti della barra del titolo non focalizzati: stato predefinito**

![Pulsanti predefiniti della barra del titolo non focalizzati](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Pulsanti predefiniti della barra del titolo non focalizzati

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | N/D |
| Primo piano (glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Bordo | N/D |

**Pulsanti della barra del titolo con stato attivo: stato al passaggio del mouse**

![Pulsanti della barra del titolo con stato attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Pulsanti della barra del titolo con stato attivo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowButtonHoverActive` |
| Primo piano (glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Bordo | `Environment.ToolWindowButtonHoverActiveBorder` |

**Pulsanti della barra del titolo non focalizzati: stato al passaggio del mouse**

![Pulsanti della barra del titolo non attivati al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Pulsanti della barra del titolo non attivati al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowButtonHoverInactive` |
| Primo piano (glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Bordo | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Pulsanti della barra del titolo con stato attivo: stato premuto**

![Pulsanti della barra del titolo con stato attivo alla pressione](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Pulsanti della barra del titolo con stato attivo alla pressione

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowButtonDown` |
| Primo piano (glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Bordo | `Environment.ToolWindowButtonDownBorder` |

**Pulsanti della barra del titolo non focalizzati: stato premuto**

![Pulsanti della barra del titolo non focalizzati durante la pressione](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Pulsanti della barra del titolo non focalizzati durante la pressione

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowButtonDown` |
| Primo piano (glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Bordo | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Schede delle finestre degli strumenti
![Scheda finestra degli strumenti (linea rossa)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Scheda finestra degli strumenti (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque si sta creando l'interfaccia utente che si desidera abbinare le finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

**Scheda della finestra degli strumenti con stato attivo selezionata**

![Scheda della finestra degli strumenti con stato attivo selezionata](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Scheda della finestra degli strumenti con stato attivo selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowTabSelectedTab` |
| Primo piano (testo) | `Environment.ToolWindowTabSelectedActiveText` |
| Bordo | `Environment.ToolWindowTabSelectedBorder`<br />(Impostare sullo stesso colore dello sfondo.) |

**Scheda della finestra degli strumenti con stato non attivo selezionata**

![Scheda della finestra degli strumenti con stato non attivo selezionata](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Scheda della finestra degli strumenti con stato non attivo selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowTabSelectedTab` |
| Primo piano (testo) | `Environment.ToolWindowTabSelectedText` |
| Bordo | `Environment.ToolWindowTabSelectedBorder`<br />(Impostare sullo stesso colore dello sfondo.) |

**Scheda della finestra degli strumenti In background: stato predefinito**

![Scheda predefinita della finestra degli strumenti di sfondo](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Scheda predefinita della finestra degli strumenti di sfondo

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Interruzioni di gradiente impostate sullo stesso valore di colore in Visual Studio 2013.) |
| Primo piano (testo) | `Environment.ToolWindowTabText` |
| Bordo | `Environment.ToolWindowTabBorder` |

**Scheda della finestra degli strumenti In background: stato al passaggio del mouse**

![Scheda della finestra degli strumenti in secondo piano al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Scheda della finestra degli strumenti in secondo piano al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Interruzioni di gradiente impostate sullo stesso valore di colore in Visual Studio 2013.) |
| Primo piano (testo) | `Environment.ToolWindowTabMouseOverText` |
| Bordo | `Environment.ToolWindowTabMouseOverBorder`<br />(Impostare sullo stesso colore dello sfondo.) |

### <a name="auto-hide-tabs"></a>Schede Nascondi automaticamente

![Nascondi automaticamente le schede (linea rossa)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Nascondi automaticamente le schede (linea rossa)

| Utilizzare... | Non usare ... |
| --- | --- |
| ... ovunque si sta creando l'interfaccia utente che si desidera abbinare automaticamente nascosto schede della finestra degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera modificare automaticamente se la shell dispone di un aggiornamento del tema. |

**Nascondi automaticamente le schede: stato predefinito**

![Scheda Nascondi automaticamente predefinita](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Scheda Nascondi automaticamente predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.AutoHideTabBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.AutoHideTabText` |
| Bordo | `Environment.AutoHideTabBorder` |

**Nascondi automaticamente le schede: stato al passaggio del mouse**

![Scheda Nascondi automaticamente al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Scheda Nascondi automaticamente al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Background | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Interruzioni di gradiente per questo token non utilizzato nell'interfaccia utente a tema.) |
| Primo piano (testo) | `Environment.AutoHideTabMouseOverText` |
| Bordo | `Environment.AutoHideTabMouseOverBorder` |
