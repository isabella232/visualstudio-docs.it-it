---
title: Colori condivisi
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8d0dfb8a7758d0619557f6c54056cd88ec68771
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966963"
---
# <a name="shared-colors-for-visual-studio"></a>Colori condivisi per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si progetta un'interfaccia utente che usa elementi comuni della shell di Visual Studio o si vuole che gli elementi dell'interfaccia siano coerenti con funzionalità simili, usare nomi di token esistenti in file di definizione del pacchetto per scegliere e assegnare i colori. In questo modo, l'interfaccia utente resta coerente con l'intero ambiente di Visual Studio e viene aggiornata automaticamente quando vengono aggiunti o aggiornati temi.

 Questo articolo descrive gli elementi dell'interfaccia utente comuni e i nomi di token usati da questi elementi, a cui è possibile fare riferimento durante la compilazione di un'interfaccia utente simile. Per informazioni specifiche su come accedere a questi token di colore, vedere [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

 Assicurarsi di usare correttamente i nomi di token:

-   **Usare i nomi di token basati su funzione e non al colore stesso.** I colori condivisi comuni sono associati a elementi dell'interfaccia specifici e destinati solo a essere usati per le stesse funzionalità o altre simili. Ad esempio, evitare di riutilizzare il colore di una casella combinata premuta per un'animazione di stato rotante solo perché si ha una preferenza per questo colore. Le funzioni della casella combinata e dell'animazione sono diverse e se il colore associato alla casella combinata cambia, potrebbe non essere più appropriato per l'elemento animazione. Un uso coerente del colore aiuta a orientare correttamente gli utenti e a impedire confusione.

-   **Usare colori di sfondo e del testo nella combinazione corretta.** I colori di sfondo destinati a essere usati con il testo implicano un colore del testo associato. Non usare colori del testo diversi da quelli specificati per un determinato sfondo. Se non esiste un colore del testo associato, non usare il colore di sfondo per alcuna superficie in cui si prevede di visualizzare testo. Combinazioni di colori di sfondo e del testo diverse potrebbero produrre un'interfaccia illeggibile.

-   **Usare colori dei controlli appropriati per la rispettiva posizione.** In determinati stati alcuni controlli di Visual Studio non hanno colori di sfondo e dei bordi separati. Al contrario, selezionano questi colori dalle superfici sottostanti. Assicurarsi di usare sempre i nomi di token appropriati per la posizione in cui si posiziona il controllo.

> [!IMPORTANT]
>  Non usare i token trovati nelle categorie "Pagina iniziale" o "Cider".

## <a name="command-structures"></a>Strutture dei comandi

###  <a name="BKMK_CommandMenus"></a> Menus
 I menu possono trovarsi in diverse posizioni all'interno di Visual Studio: barra dei menu principale, incorporata in finestre di documento o lo strumento, o sul pulsante destro del mouse in diversi punti dell'IDE. Le implementazioni dei menu associati ad altri elementi dell'interfaccia utente vengono descritte nella sezione relativa al rispettivo elemento. È preferibile usare sempre l'implementazione dei menu standard fornita dall'ambiente di Visual Studio. Tuttavia, in alcuni casi rari si potrebbe non avere accesso ai menu standard di Visual Studio. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri menu in Visual Studio.

 ![Menu con linea rossa](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")

 Usare…
 -   Ogni volta che è necessario creare un menu personalizzato.

- Quando un nuovo componente dell'interfaccia utente deve corrispondere ai menu di Visual Studio.

  Non usare...
  Il colore di sfondo da solo. Usare sempre la combinazione sfondo/primo piano specificata.

#### <a name="menu-title"></a>Titolo del menu
 I titoli dei menu sono costituiti da uno sfondo, un bordo e il testo del titolo, nonché da un glifo facoltativo, in genere quando il menu si trova in una barra dei comandi.

 ![Titolo menu con linea rossa](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")

 Usare...
Ogni volta che si crea un titolo di menu personalizzato.

 Non usare...
 -   Per qualsiasi elemento che non deve corrispondere sempre al titolo del menu.

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Titolo menu predefinito](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")

  **Titolo menu**

  Sfondo

  nessuno

  Primo piano (testo)

  `Environment.CommandBarTextActive`

  ![Titolo menu con glifo predefinito](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")

  **Titolo menu con glifo**

  Primo piano (glifo)

  `Environment.CommandBarMenuGlyph`

  Bordo

  nessuno

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Titolo menu al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")

  **Titolo menu**

  Sfondo

  `Environment.CommandBarMouseOverBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.CommandBarTextHover`

  ![Titolo menu con glifo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")

  **Titolo menu con glifo**

  Primo piano (glifo)

  `Environment.CommandBarMenuMouseOverGlyph`

  Bordo

  `Environment.CommandBarBorder`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Titolo menu selezionato](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")

  **Titolo menu**

  Sfondo

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.CommandBarTextActive`

  ![Titolo menu con glifo premuto](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")

  **Titolo menu con glifo**

  Primo piano (glifo)

  `Environment.CommandBarMenuMouseDownGlyph`

  Bordo

  `Environment.CommandBarMenuBorder`

  Solo lati sinistro, superiore e destro.

  **Disabilitato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Titolo menu con glifo disabilitato](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")

  **Titolo menu con glifo**

  Sfondo

  nessuno

  Primo piano (testo)

  `Environment.CommandBarTextInactive`

  Primo piano (glifo)

  `Environment.CommandBarTextInactive`

  Bordo

  nessuno

#### <a name="menu"></a>Menu
 Una singola voce di menu è costituita dal testo del menu e da un'icona facoltativa, una casella di controllo o un glifo del sottomenu. Il colore di sfondo e del testo cambiano al passaggio del mouse. Questo token di colore è una coppia sfondo/primo piano.

 ![Voci di menu con linea rossa](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")

 Usare...
Per qualsiasi elenco a discesa avviato da una barra dei menu o una barra dei comandi.

 Non usare...
 -   Per qualsiasi elenco a discesa presente in un altro contesto.

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Menu predefinito](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")

  **Menu**

  Sfondo

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.CommandBarTextActive`

  Primo piano (glifo del sottomenu)

  `Environment.CommandBarMenuSubmenuGlyph`

  Bordo

  `Environment.CommandBarMenuBorder`

  Sfondo del canale delle icone

  `Environment.CommandBarMenuIconBackground`

  Separatore

  `Environment.CommandBarMenuSeparator`

  Ombreggiatura

  `Environment.DropShadowBackground`

  ![Menu scelto](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")

  **Checked**

  Segno di spunta

  `Environment.CommandBarCheckBox`

  Sfondo del segno di spunta

  `Environment.CommandBarSelectedIcon`

  ![Menu selezionato](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")

  **selezionato**

  Sfondo dell'icona

  `Environment.CommandBarSelected`

  Bordo dell'icona

  `Environment.CommandBarSelectedBorder`

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Al passaggio del mouse dal menu](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")

  **Voce di menu**

  Sfondo

  `Environment.CommandBarMenuItemMouseOver`

  Primo piano (testo)

  `Environment.CommandBarMenuItemMouseOver`

  Primo piano (glifo del sottomenu)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Al passaggio del mouse dal menu controllato](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")

  **Checked**

  Segno di spunta

  `Environment.CommandBarCheckBoxMouseOver`

  Sfondo del segno di spunta

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Al passaggio del mouse dal menu selezionato](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")

  **selezionato**

  Sfondo dell'icona

  `Environment.CommandBarHoverOverSelected`

  Bordo dell'icona

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Disabilitato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Menu disabilitato](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")

  Voce di menu

  Primo piano (testo)

  `Environment.CommandBarTextInactive`

  Primo piano (glifo del sottomenu)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Menu disabilitato selezionato](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")

  Selezionato con segno di spunta

  Segno di spunta

  `Environment.CommandBarCheckBoxDisabled`

  Sfondo del segno di spunta

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Barra dei comandi
 La barra dei comandi può essere visualizzata in più posizioni all'interno dell'IDE di Visual Studio, in particolare nello scaffale dei comandi e come incorporata nelle finestre degli strumenti e dei documenti.

 In generale, usare sempre l'implementazione della barra dei menu standard fornita dall'ambiente di Visual Studio. L'uso del meccanismo standard garantisce che tutti i dettagli visivi vengano visualizzati correttamente e che gli elementi interattivi abbiano un comportamento coerente con gli altri controlli della barra dei comandi di Visual Studio. Tuttavia, se è necessario compilare una barra dei comandi personalizzata, assicurarsi di applicare lo stile corretto usando i nomi di token seguenti.

 ![Sulla barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")

 ![Overflow button redline](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")

 Usare...
Nelle posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile usare l'implementazione della barra dei comandi standard di Visual Studio.

 Non usare...
 -   Per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi.

-   Per i componenti della barra dei comandi diversi da quelli per cui sono specificati i nomi di token.

#### <a name="command-bar-group"></a>Gruppo della barra dei comandi
 Un gruppo della barra dei comandi è costituito da un set correlato di controlli della barra dei comandi e può contenere un numero qualsiasi di pulsanti, pulsanti di menu combinato, menu a discesa, caselle combinate o menu. I colori per questi controlli sono determinati da nomi di token separati e vengono descritti singolarmente in altre sezioni di questa guida. Viene usata una linea di separazione per dividere un gruppo della barra dei comandi in sottogruppi correlati.

 ![Gruppo della barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")

 Usare...
Nelle posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile usare l'implementazione della barra dei comandi standard di Visual Studio.

 Non usare...
 -   Per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi.

- Per i componenti della barra dei comandi diversi da quelli per cui sono specificati i nomi di token.

  **Predefinito** (nessun altro stato)

  Elemento

  Nome token: Category. Color

  Sfondo

  `Environment.CommandBarGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Bordo

  `Environment.CommandBarToolBarBorder`

  Quadratino di trascinamento

  `Environment.CommandBarDragHandle`

  Separatore

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Icone dei comandi
 ![Icona del comando con linea rossa](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")

 ![Icona del comando con linea rossa](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")

 Usare...
Per qualsiasi pulsante che verrà posizionato su una barra dei comandi.

 Non usare...
 -   Per i controlli che hanno nomi di token propri.

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Icona predefinita di comando](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")

  **Default**

  Sfondo

  N/D (eredita dallo sfondo della barra dei comandi)

  Primo piano (testo)

  `Environment.CommandBarTextActive`

  Bordo

  N/D

  ![Comando icona predefinita selezionato](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")

  **selezionato**

  Sfondo

  `Environment.CommandBarSelected`

  Primo piano (testo)

  `Environment.CommandBarTextSelected`

  Bordo

  `Environment.CommandBarSelectedBorder`

  **Al passaggio del mouse e stato attivo**

  Componente

  Elemento

  Nome token: Category. Color

  ![Al passaggio del mouse sull'icona di comando](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")

  **Standard al passaggio del mouse**

  Sfondo

  `Environment.CommandBarMouseOverBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.CommandBarTextHover`

  Bordo

  `Environment.CommandBarBorder`

  ![Comando al passaggio del mouse sull'icona selezionata](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")

  **Selezionato al passaggio del mouse**

  Sfondo

  `Environment.CommandBarHoverOverSelected`

  Primo piano (testo)

  `Environment.CommandBarTextHoverOverSelected`

  Bordo

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Icona del comando selezionata](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")

  **Icona del comando premuta**

  Sfondo

  `Environment.CommandBarMouseDownBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.CommandBarTextMouseDown`

  Bordo

  `Environment.CommandBarBorder`

  **Disabilitato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Icona del comando disabilitata](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")

  **Icona del comando disabilitata**

  Sfondo

  N/D (eredita dallo sfondo della barra dei comandi)

  Primo piano (testo)

  `Environment.CommandBarTextInactive`

  Bordo

  N/D

####  <a name="BKMK_CommandComboBox"></a> Casella combinata

> [!IMPORTANT]
>  Le caselle combinate sono simili agli elenchi a discesa, ma includono un'area di testo modificabile. Se la casella di riepilogo a discesa non contiene un'area di testo modificabile, usare i token di colore indicati in [Drop-down](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

 ![Combo box redline](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")

 Usare…
 -   Quando si compilano caselle combinate personalizzate.

- Quando si crea un controllo della barra dei comandi simile a una casella combinata.

  Non usare...
  -   Per qualsiasi elemento che non deve corrispondere sempre all'interfaccia utente della barra dei comandi.

- Quando si ha accesso a una casella combinata con stile.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Campo di input di casella combinata](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")

  **Campo di input**

  Sfondo

  `Environment.ComboBoxBackground`

  Primo piano (testo)

  `Environment.ComboBoxText`

  Bordo

  `Environment.ComboBoxBorder`

  Separatore

  Nessun separatore

  ![Rilascio di casella combinata&#45;pulsante giù](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")

  **Pulsante elenco a discesa**

  Sfondo

  N/D (eredita)

  Primo piano (glifo)

  `Environment.ComboBoxGlyph`

  ![Combo box&#47;drop&#45;down list](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")

  **Elenco a discesa**

  Sfondo

  `Environment.ComboBoxPopupBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.ComboBoxItemText`

  Bordo

  `Environment.ComboBoxPopupBorder`

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Campo di input casella combinata al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")

  **Campo di input**

  Sfondo

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.ComboBoxMouseOverText`

  Bordo

  `Environment.ComboBoxMouseOverBorder`

  Separatore

  `Environment.ComboBoxMouseOverSeparator`

  ![Casella combinata&#47;drop&#45;pulsante al passaggio del mouse giù](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")

  **Pulsante elenco a discesa**

  Sfondo

  `Environment.ComboBoxButtonMouseOverBackground`

  Primo piano (glifo)

  `Environment.ComboBoxMouseOverGlyph`

  ![Casella combinata&#47;drop&#45;elenco al passaggio del mouse verso il basso](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")

  **Elenco a discesa**

  Sfondo (voce di menu)

  `Environment.ComboBoxItemMouseOverBackground`

  Primo piano (testo)

  `Environment.ComboBoxItemMouseOverText`

  Bordo (voce di menu)

  `Environment.ComboBoxItemMouseOverBorder`

  **Focused**

  Componente

  Elemento

  Nome token: Color. Category

  ![Campo di input casella combinata con stato attivato](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")

  **Campo di input**

  Sfondo

  `Environment.ComboBoxFocusedBackground`

  Primo piano (testo)

  `Environment.ComboBoxFocusedText`

  Bordo

  `Environment.ComboBoxFocusedBorder`

  Separatore

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Casella combinata&#47;drop&#45;verso il basso sul pulsante con stato attivato](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")

  **Pulsante elenco a discesa**

  Sfondo

  `Environment.ComboBoxFocusedButtonBackground`

  Primo piano (glifo)

  `Environment.ComboBoxFocusedGlyph`

  **Premuto**

  Componente

  Elemento

  Nome token: Color. Category

  ![Campo di input casella combinata premuto](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")

  **Campo di input**

  Sfondo

  `Environment.ComboBoxMouseDownBackground`

  Primo piano (testo)

  `Environment.ComboBoxMouseDownText`

  Bordo

  `Environment.ComboBoxMouseDownBorder`

  Separatore

  `Environment.ComboBoxMouseDownSeparator`

  ![Casella combinata&#47;drop&#45;verso il basso la pressione del pulsante](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")

  **Pulsante elenco a discesa**

  Sfondo

  `Environment.ComboBoxButtonMouseDownBackground`

  Primo piano (glifo)

  `Environment.ComboBoxMouseDownGlyph`

  **Disabilitato**

  ![Campo di input casella combinata disabilitata](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")

  **Campo di input**

  Sfondo

  `Environment.ComboBoxDisabledBackground`

  Primo piano (testo)

  `Environment.ComboBoxDisabledText`

  Bordo

  `Environment.ComboBoxDisabledBorder`

  Separatore

  Nessun separatore

  ![Casella combinata&#47;drop&#45;pulsante disabilitato giù](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")

  **Pulsante elenco a discesa**

  Sfondo

  nessuno

  Primo piano (glifo)

  `Environment.ComboBoxDisabledGlyph`

####  <a name="BKMK_CommandDropDown"></a> Elenco a discesa

> [!IMPORTANT]
>  Gli elenchi a discesa sono simili alle caselle combinate, ma non contengono aree di testo modificabili. Se l'elenco a discesa contiene un'area di testo modificabile, usare i token di colore indicati in [Combo box](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

 ![Drop&#45;down redline](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")

 Usare…
Quando si creano controlli elenco a discesa personalizzati.

 Non usare...
 -   Per qualsiasi elemento che non è simile a un elenco a discesa.

- Per caselle combinate o pulsanti di menu combinato.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Eliminare&#45;a discesa il campo di selezione](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")

  **Campo di selezione**

  Sfondo

  `Environment.DropDownBackground`

  Primo piano (testo)

  `DropDownText`

  Bordo

  `DropDownBorder`

  Separatore

  Nessun separatore

  ![Eliminare&#45;pulsante giù](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")

  **Pulsante elenco a discesa**

  Sfondo

  nessuno

  Primo piano (glifo)

  `Environment.DropDownGlyph`

  ![Drop&#45;down list](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")

  **Elenco a discesa**

  Sfondo

  `Environment.DropDownPopupBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.ComboBoxItemText`

  Bordo

  `Environment.DropDownPopupBorder`

  Ombreggiatura

  `Environment.DropShadowBackground`

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Eliminare&#45;a discesa il campo di selezione del mouse](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")

  **Campo di selezione**

  Sfondo

  `Environment.DropDownMouseOverBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.DropDownMouseOverText`

  Bordo

  `Environment.DropDownMouseOverBorder`

  Separatore

  `Environment.DropDownButtonMouseOverSeparator`

  ![Eliminare&#45;pulsante del mouse giù](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")

  **Pulsante elenco a discesa**

  Sfondo

  `Environment.DropDownButtonMouseOverBackground`

  Primo piano (glifo)

  `Environment.DropDownMouseOverGlyph`

  ![Eliminare&#45;elenco al passaggio del mouse verso il basso](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")

  **Elenco a discesa**

  Sfondo (voce di menu)

  `Environment.ComboBoxItemMouseOverBackground`

  Primo piano (testo)

  `Environment.ComboBoxItemMouseOverText`

  Bordo (voce di menu)

  `Environment.ComboBoxItemMouseOverBorder`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Eliminare&#45;inattivo premuto campo di selezione](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")

  **Campo di selezione**

  Sfondo

  `Environment.DropDownMouseDownBackground`

  Primo piano (testo)

  `Environment.DropDownMouseDownText`

  Bordo

  `Environment.DropDownMouseDownBorder`

  Separatore

  `Environment.DropDownButtonMouseDownSeparator`

  ![Eliminare&#45;verso il basso la pressione del pulsante](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")

  **Pulsante elenco a discesa**

  Sfondo

  `Environment.DropDownButtonMouseDownBackground`

  Primo piano (glifo)

  `Environment.DropDownMouseDownGlyph`

  **Disabilitato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Eliminare&#45;a discesa il campo di selezione disabilitato](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")

  Sfondo

  `Environment.DropDownDisabledBackground`

  Primo piano (testo)

  `Environment.DropDownDisabledText`

  Bordo

  `Environment.DropDownDisabledBorder`

  Separatore

  Nessun separatore

  ![Eliminare&#45;verso il basso sul pulsante disabilitato](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")

  Sfondo

  N/D

  Primo piano (glifo)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Pulsante di menu combinato
 I pulsanti di menu combinato condividono molti nomi di token con altri controlli della barra dei comandi, come pulsanti, menu e testo della barra dei comandi. Tutti i nomi di token dei pulsanti a discesa e di azione necessari vengono ripetuti qui per praticità. Gli elenchi a discesa dei pulsanti di menu combinato sono implementazioni dei [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)della barra dei comandi.

 ![Pulsante di menu combinato con linea rossa](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")

 Usare…
Quando si compila un pulsante di menu combinato personalizzato.

 Non usare...
 -   Per altri tipi di pulsanti.

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Pulsante di menu combinato](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")

  **Pulsante di menu combinato (predefinito)**

  Sfondo

  nessuno

  Primo piano (testo)

  `Environment.CommandBarTextActive`

  Primo piano (glifo)

  `Environment.CommandBarSplitButtonGlyph`

  Bordo

  N/D

  Separatore

  N/D

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Pulsante di menu combinato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")

  **Pulsante di menu combinato (al passaggio del mouse)**

  Sfondo

  `Environment.CommandBarMouseOverBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.CommandBarTextHover`

  Primo piano (glifo)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Bordo

  `Environment.CommandBarBorder`

  Separatore

  `Environment.CommandBarSplitButtonSeparator`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Pulsante di menu combinato premuto](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")

  **Pulsante di menu combinato (premuto)**

  Sfondo

  `Environment.CommandBarMouseDownBackgroundBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `Environment.CommandBarTextMouseDown`

  Primo piano (glifo)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Bordo

  `Environment.CommandBarBorder`

  Separatore

  N/D

  **Disabilitato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Pulsante di menu combinato disabilitato](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")

  **Pulsante di menu combinato (disabilitato)**

  Sfondo

  N/D

  Primo piano (testo)

  `Environment.ComboBoxItemTextInactive`

  Primo piano (glifo)

  `Environment.CommandBarTextInactive`

  Bordo

  N/D

  Separatore

  N/D

#### <a name="more-options-and-overflow-buttons"></a>Pulsanti "Altre opzioni" e "Overflow"
 Il pulsante "Altre opzioni" viene usato quando un gruppo della barra dei comandi può essere personalizzato aggiungendo o rimuovendo pulsanti della barra dei comandi correlati. Il pulsante "Overflow" viene visualizzato quando una barra dei comandi è troncata a causa della mancanza di spazio orizzontale e, dopo avervi fatto clic sopra, mostra un menu che contiene i pulsanti della barra dei comandi che non possono essere visualizzati. I colori per questi due pulsanti sono controllati dallo stesso set di nomi di token.

 ![Altre opzioni con linea rossa](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")

 Usare…
Per pulsanti "Altre opzioni" e "Overflow" personalizzati.

 Non usare...
Per pulsanti che non hanno una funzionalità simile ai pulsanti "Altre opzioni" e "Overflow".

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Altre opzioni](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")

 **Altre opzioni**

 ![Pulsante di overflow](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")

 **overflow**

 Sfondo

 `Environment.CommandBarOptionsBackground`

 Primo piano (glifo)

 `Environment.CommandBarOptionsGlyph`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Altre opzioni al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")

 **Altre opzioni**

 ![Overflow al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")

 **overflow**

 Sfondo

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (glifo)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Altre opzioni premuto](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")

 **Altre opzioni**

 ![Overflow premuto](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")

 **overflow**

 Sfondo

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (glifo)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Finestre dei documenti
 Non è necessario replicare le finestre dei documenti, perché vengono fornite dall'ambiente di Visual Studio. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre dei documenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.

 Quando si usano token di colore per le finestre dei documenti, è necessario fare attenzione a usarli solo per elementi simili e sempre in coppia. In caso contrario, si otterranno risultati imprevisti nell'interfaccia utente.

### <a name="document-window-frame"></a>Cornice delle finestre dei documenti
 Le finestre dei documenti possono essere ancorate nell'IDE o mobili come finestre separate. Quando la finestra di un documento è mobile al di fuori dell'IDE, si trova comunque all'interno di un'area dei documenti e ha gli stessi colori di sfondo, del bordo, del testo e delle schede di quando fa parte dell'IDE. Tuttavia, il documento si trova all'interno di una cornice che ha colori di sfondo, del bordo e del testo propri. Quando le finestre degli strumenti sono ancorate nell'area dei documenti, ereditano il comportamento e il colore per le rispettive schede dai nomi di token delle finestre dei documenti.

 ![Finestra del documento ancorata](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")

 **Finestra del documento ancorata**

 ![Finestra del documento mobile con linea rossa](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")

 **Finestra del documento mobile**

 Usare…
In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alla finestra del documento.

 Non usare...
Per qualsiasi interfaccia utente che non deve automaticamente cambiare se la shell include un aggiornamento del tema.

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 Documento: ancorato o mobile

 Sfondo

 Dipende dal tipo di documento

 Primo piano (testo)

 Dipende dal tipo di documento

 Bordo

 `Environment.ToolWindowBorder`

 ![Frame con stato attivo](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")

 **Cornice: mobile, con stato attivo**

 Sfondo

 `Environment.ToolWindowFloatingFrame`

 Primo piano (testo)

 `Environment.ToolWindowFloatingFrame`

 Primo piano (glifo)

 `Environment.RaftedWindowButtonActiveGlyph`

 Bordo

 `Environment.MainWindowActiveDefaultBorder`

 Bordo (glifo)

 `Environment.RaftedWindowButtonActiveBorder`

 Impostato su trasparente

 ![Frame con stato non attivo](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")

 **Cornice: mobile, con stato non attivo**

 Sfondo

 `Environment.ToolWindowFloatingFrameInactive`

 Primo piano (testo)

 `Environment.ToolWindowFloatingFrameInactive`

 Primo piano (glifo)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Bordo

 `Environment.MainWindowInactiveBorder`

 Bordo (glifo)

 `Environment.RaftedWindowButtonInactiveBorder`

 Impostato su trasparente

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Frame con stato attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")

 **Cornice: mobile, con stato attivo**

 Sfondo (glifo)

 `Environment.RaftedWindowButtonHoverActive`

 Primo piano (glifo)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Bordo (glifo)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Frame con stato non attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")

 **Cornice: mobile, con stato non attivo**

 Sfondo (glifo)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Primo piano (glifo)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Bordo (glifo)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Frame con stato attivo selezionato](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")

 **Cornice: mobile, con stato attivo**

 Sfondo (glifo)

 `Environment.RaftedWindowButtonDown`

 Primo piano (glifo)

 `Environment.RaftedWindowButtonDownGlyph`

 Bordo (glifo)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Schede dei documenti
 Le schede dei documenti si trovano nel canale delle schede per indicare i documenti attualmente aperti, insieme al documento selezionato o attivo corrente. Anche le finestre degli strumenti possono essere ancorate nel canale delle schede dei documenti se l'utente le aggiunge in questa posizione. In questo caso, usano gli stessi colori delle schede delle finestre dei documenti. Se si crea un'interfaccia utente che deve corrispondere sempre ai colori delle finestre dei documenti (inclusi gli aggiornamenti dei temi o se vengono installati nuovi temi), fare riferimento a questi token di colore.

 ![Scheda documento con linea rossa](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")

 Usare…
In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle schede dei documenti e in cui gli aggiornamenti dei temi o nuovi colori dei temi vengono selezionati automaticamente.

 Non usare...
Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.

#### <a name="open-document-tabs"></a>Schede dei documenti aperti
 Per ogni documento aperto è presente una scheda nel canale delle schede dei documenti che ne visualizza il nome. I documenti possono essere selezionati o aperti in background e le rispettive schede riflettono questi stati:

- La scheda selezionata rappresenta il documento attualmente visualizzato nell'area dei documenti. Una scheda selezionata ha un bordo di documento che si estende fino al bordo superiore dell'area dei documenti.

- Le schede in secondo piano sono tutte le schede dei documenti diverse da quella attualmente selezionata. Se selezionate, diventano la scheda selezionata e acquisiscono tutti i colori di sfondo, del bordo e del testo da questi nomi di token.

  ![Scheda documento aperto con linea rossa](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")

  Usare…
  Quando si creano schede dei documenti personalizzate.

  Non usare...
  -   Per schede provvisorie (anteprima).

- Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.

#### <a name="selected-tab"></a>Scheda selezionata
 **Focused**

 Componente

 Elemento

 Nome token: Category. Color

 ![Scheda selezionata con stato attivo](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")

 **Scheda di documento selezionata, con stata attivata**

 Sfondo

 `Environment.FileTabSelectedGradientTop`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (testo)

 `Environment.FileTabSelectedText`

 Bordo

 `Environment.FileTabSelectedBorder`

 Impostato sullo stesso colore dello sfondo.

 Bordo del documento

 `Environment.FileTabDocumentBorderBackground`

 **Con stato non attivo**

 Componente

 Elemento

 Nome token: Category. Color

 ![Scheda selezionata con stato non attivo](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")

 **Scheda di documento selezionata, con stato non attivo**

 Sfondo

 `Environment.FileTabInactiveGradientTop`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (testo)

 `Environment.FileTabInactiveText`

 Bordo

 `Environment.FileTabInactiveBorder`

 Impostato sullo stesso colore dello sfondo.

 Bordo del documento

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Scheda di sfondo
 **Default**

 ![Scheda sfondo](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")

 **Impostazione predefinita della scheda in background**

 Sfondo

 `Environment.FileTabBackground`

 Primo piano (testo)

 `Environment.FileTabText`

 Bordo

 `Environment.FileTabBorder`

 Impostato sullo stesso colore dello sfondo.

 **Hover**

 ![Scheda sfondo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")

 **Scheda sfondo al passaggio del mouse**

 Sfondo

 `Environment.FileTabHotGradientTop`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (testo)

 `Environment.FileTabHotText`

 Bordo

 `Environment.FileTabHotBorder`

 Impostato sullo stesso colore dello sfondo.

#### <a name="preview-tab"></a>Scheda anteprima
 La scheda anteprima è visualizzata sul lato destro del canale delle schede dei documenti quando l'utente fa clic su un elemento nella finestra degli strumenti Esplora soluzione. Questa scheda funge da anteprima del documento e offre all'utente anche l'opzione di mantenere il documento aperto sul lato sinistro del canale delle schede dei documenti. Può essere aperta una sola scheda anteprima per volta. Le schede anteprima hanno sia uno sfondo sia stati selezionati, come le schede aperte, e possono avere stato attivo o non attivo quando sono attive.

 ![Scheda Anteprima con linea rossa](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")

 Usare…
In qualsiasi punto in cui si crea un'anteprima provvisoria e alcuni elementi devono corrispondere al colore della scheda anteprima.

 Non usare...
 -   Per qualsiasi tipo di documento o scheda non provvisorio (anteprima).

- Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.

  **Scheda anteprima selezionata: Con stato attivo**

  Componente

  Elemento

  Nome token: Category. Color

  ![Scheda Anteprima con stato attivo](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")

  **Scheda Anteprima con stato attivo**

  Sfondo

  `Environment.FileTabProvisionalSelectedActive`

  Primo piano (testo)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Bordo

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Impostato sullo stesso colore dello sfondo.

  Bordo del documento

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Scheda anteprima selezionata: Con stato non attivo**

  Componente

  Elemento

  Nome token: Category. Color

  ![Scheda Anteprima con stato non attivo](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")

  **Scheda Anteprima con stato non attivo**

  Sfondo

  `Environment.FileTabProvisionalSelectedInactive`

  Primo piano (testo)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Bordo

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Bordo del documento

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Scheda Anteprima sfondo: Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Scheda Anteprima sfondo](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")

  **Scheda sfondo della scheda di anteprima**

  Sfondo

  `Environment.FileTabProvisionalInactive`

  Primo piano (testo)

  `Environment.FileTabProvisionalInactiveForeground`

  Bordo

  `Environment.FileTabProvisionalInactiveBorder`

  Impostato sullo stesso colore dello sfondo.

  **Scheda Anteprima sfondo: Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Scheda Anteprima sfondo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")

  **Scheda scheda Anteprima sfondo al passaggio del mouse**

  Sfondo

  `Environment.FileTabProvisionalHover`

  Primo piano (testo)

  `Environment.FileTabProvisionalHoverForeground`

  Bordo

  `Environment.FileTabProvisionalHoverBorder`

  Impostato sullo stesso colore dello sfondo.

#### <a name="document-overflow-button"></a>Pulsante di overflow dei documenti
 Il pulsante di overflow dei documenti è presente se ci sono uno o più documenti aperti, indipendentemente dal fatto che nella configurazione corrente sia disponibile spazio sufficiente da contenere tutte le schede dei documenti. Il menu a discesa di overflow dei documenti, controllato dai colori di **CommandBarMenu** (vedere [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)), visualizza un elenco di tutti i documenti aperti, sia visibili sia nascosti, e il glifo di overflow cambia a seconda che tutti i documenti aperti siano o meno visualizzati nel canale delle schede.

 ![Overflow redline](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")

 Usare…
Quando si crea un pulsante di overflow dei documenti personalizzato.

 Non usare...
 -   Per un'interfaccia utente che non è simile a un pulsante di overflow.

- Per i pulsanti di overflow della barra dei comandi.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")

  **Pulsante di overflow dei documenti**

  Sfondo

  `Environment.DocWellOverflowButtonBackground`

  Primo piano (glifo)

  `Environment.DocWellOverflowButtonGlyph`

  Bordo

  N/D

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Overflow al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")

  **Pulsante di overflow dei documenti al passaggio del mouse**

  Sfondo

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Primo piano (glifo)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Bordo

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Overflow premuto](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")

  **Pulsante di overflow dei documenti premuto**

  Sfondo

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Primo piano (glifo)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Bordo

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Finestre degli strumenti
 Non è necessario replicare le finestre degli strumenti, perché vengono fornite dall'ambiente di Visual Studio. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre degli strumenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.

 ![Finestra degli strumenti con linea rossa](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")

 Usare…
In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.

 Non usare...
Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.

### <a name="tool-window-frame"></a>Cornice delle finestre degli strumenti
 Le finestre degli strumenti in Visual Studio vengono usate per molte attività diverse e possono avere stati diversi. Se una finestra degli strumenti è aperta, può essere assegnata a uno qualsiasi dei quattro lati dell'area del documento. Le finestre degli strumenti possono anche essere mobili al di fuori dell'IDE, per poter essere riposizionate in qualsiasi punto dello schermo dell'utente. Le finestre mobili sono sempre in primo piano nell'IDE. Infine, le finestre degli strumenti possono essere ancorate come finestre dei documenti ed essere visualizzate come scheda nell'area dei documenti. Le finestre degli strumenti ancorate come finestre dei documenti vengono colorate in parte usando i nomi di token delle finestre dei documenti.

 ![Frame finestra degli strumenti con linea rossa](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")

 Usare…
In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.

 Non usare...
Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.

 **Docked**

 Componente

 Elemento

 Nome token: Category. Color

 ![Finestra degli strumenti ancorata](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")

 Sfondo

 `Environment.ToolWindowBackground`

 Bordo

 `Environment.ToolWindowBorder`

 **Mobile: con stato attivo**

 Componente

 Elemento

 Nome token: Category. Color

 ![Finestra degli strumenti con stato attivato](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")

 Sfondo

 `Environment.ToolWindowBackground`

 Bordo

 `Environment.MainWindowActiveDefaultBorder`

 **Mobile: con stato non attivo**

 Componente

 Elemento

 Nome token: Category. Color

 ![Finestra degli strumenti con stato non attivo](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")

 Sfondo

 `Environment.ToolWindowBackground`

 Bordo

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Barra del titolo delle finestre degli strumenti
 Il bordo della barra del titolo non è un bordo vero e proprio, ma una linea spessa lungo la parte superiore della barra del titolo. Questo elemento non ha un nome di token per il proprio stato non attivo.

 ![Barra del titolo di finestra degli strumenti con linea rossa](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")

 Usare…
In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.

 Non usare...
Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.

 **Focused**

 Componente

 Elemento

 Nome token: Category. Color

 ![Sulla barra del titolo con stato attivo](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")

 **Sulla barra del titolo con stato attivo**

 Sfondo

 `Environment.TitleBarActiveGradientBegin`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (testo)

 `Environment.TitleBarActiveText`

 Bordo

 `Environment.TitleBarActiveBorder`

 Impostato sullo stesso colore dello sfondo.

 Quadratino di trascinamento

 `Environment.TitleBarDragHandleActive`

 **Con stato non attivo**

 Componente

 Elemento

 Nome token: Category. Color

 ![Sulla barra del titolo con stato non attivo](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")

 **Sulla barra del titolo con stato non attivo**

 Sfondo

 `Environment.TitleBarInactiveGradientBegin`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (testo)

 `Environment.TitleBarInactiveText`

 Bordo

 N/D

 Quadratino di trascinamento

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Pulsanti della barra del titolo
 ![Pulsante della barra del titolo con linea rossa](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")

 Usare…
Per i pulsanti visualizzati nell'interfaccia utente che usa token di colore della barra del titolo delle finestre degli strumenti.

 Non usare...
 -   Per i pulsanti visualizzati in altre posizioni.

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Spostare il titolo della pulsante con stato attivo barra](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")

  **Focused**

  Sfondo

  N/D

  Primo piano (glifo)

  `Environment.ToolWindowButtonActiveGlyph`

  Bordo

  N/D

  ![Spostare il titolo della barra pulsante con stato non attivo](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")

  **Con stato non attivo**

  Sfondo

  N/D

  Primo piano (glifo)

  `Environment.ToolWindowButtonInactiveGlyph`

  Bordo

  N/D

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Pulsante della barra del titolo con stato attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")

  **Focused**

  Sfondo

  `Environment.ToolWindowButtonHoverActive`

  Primo piano (glifo)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Bordo

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Spostare il titolo della barra pulsante con stato non attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")

  **Con stato non attivo**

  Sfondo

  `Environment.ToolWindowButtonHoverInactive`

  Primo piano (glifo)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Bordo

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Spostare il titolo della barra sul pulsante con stato attivo e premuto](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")

  **Focused**

  Sfondo

  `Environment.ToolWindowButtonDown`

  Primo piano (glifo)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Bordo

  `Environment.ToolWindowButtonDownBorder`

  ![Pulsante della barra del titolo con stato non attivo e premuta](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")

  **Con stato non attivo**

  Sfondo

  `Environment.ToolWindowButtonDown`

  Primo piano (glifo)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Bordo

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Schede delle finestre degli strumenti
 ![Scheda casella degli strumenti con linea rossa](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")

 Usare…
In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.

 Non usare...
Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.

 **Scheda selezionata**

 Componente

 Elemento

 Nome token: Category. Color

 ![Scheda casella degli strumenti con stato attivo](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")

 **Scheda della finestra degli strumenti con stato attivo selezionata**

 Sfondo

 `Environment.ToolWindowTabSelectedTab`

 Primo piano (testo)

 `Environment.ToolWindowTabSelectedActiveText`

 Bordo

 `Environment.ToolWindowTabSelectedBorder`

 Impostato sullo stesso colore dello sfondo.

 Componente

 Elemento

 Nome token: Category. Color

 ![Scheda della finestra degli strumenti con stato non attivo](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")

 **Scheda della finestra degli strumenti con stato non attivo selezionata**

 Sfondo

 `Environment.ToolWindowTabSelectedTab`

 Primo piano (testo)

 `Environment.ToolWindowTabSelectedText`

 Bordo

 `Environment.ToolWindowTabSelectedBorder`

 Impostato sullo stesso colore dello sfondo.

 **Scheda sfondo**

 Componente

 Elemento

 Nome token: Category. Color

 ![Scheda sfondo della finestra degli strumenti](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")

 **Scheda casella degli strumenti in background**

 Sfondo

 `Environment.ToolWindowTabGradientBegin`

 Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.

 `Environment.ToolWindowTabGradientEnd`

 Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.

 Primo piano (testo)

 `Environment.ToolWindowTabText`

 Bordo

 `Environment.ToolWindowTabBorder`

 Componente

 Elemento

 Nome token: Category. Color

 ![Scheda sfondo della finestra degli strumenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")

 **Scheda della finestra degli strumenti dello sfondo al passaggio del mouse**

 Sfondo

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.

 Primo piano (testo)

 `Environment.ToolWindowTabMouseOverText`

 Bordo

 `Environment.ToolWindowTabMouseOverBorder`

 Impostato sullo stesso colore dello sfondo.

### <a name="auto-hide-tabs"></a>Schede Nascondi automaticamente
 ![Automatico&#45;Nascondi con linea rossa](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")

 Usare…
In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle schede delle finestre degli strumenti Nascondi automaticamente.

 Non usare...
Per qualsiasi interfaccia utente che non deve automaticamente cambiare se la shell prevede un aggiornamento del tema.

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Automatico&#45;Nascondi della scheda](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")

 **Scheda Nascondi automaticamente predefinita**

 Sfondo

 `Environment.AutoHideTabBackgroundBegin`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (testo)

 `Environment.AutoHideTabText`

 Bordo

 `Environment.AutoHideTabBorder`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Automatico&#45;nascondere scheda al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")

 **Scheda Nascondi automaticamente al passaggio del mouse**

 Sfondo

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

 Primo piano (testo)

 `Environment.AutoHideTabMouseOverText`

 Bordo

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Controlli condivisi comuni
 Quando si usa una barra dei comandi di Visual Studio standard nella propria funzionalità, è possibile accedere a controlli della shell con stile e non è consigliabile reimpostare come modelli questi controlli comuni. Tuttavia, se si intende compilare una barra dei comandi personalizzata, potrebbe essere necessario compilare anche controlli personalizzati. In questo caso, assicurarsi di usare i nomi di token corretti per ognuno dei controlli seguenti, in modo che l'interfaccia utente sia coerente con il resto di Visual Studio.

### <a name="search-box"></a>Casella di ricerca
 Quando è possibile, usare il controllo di ricerca comune fornito dall'ambiente di Visual Studio. I colori della casella di ricerca si trovano nella categoria "SearchControl" nel file **ShellColors.pkgdef** , che contiene i nomi di token per il campo di input, il pulsante di azione, il pulsante a discesa e il menu a discesa.

 Una casella di ricerca può avere diversi stati, alcuni dei quali si escludono a vicenda:

- "Con stato attivo" e "con stato non attivo" indicano se il cursore si trova o meno nella casella di testo.

- "Attivo" e "inattivo" indicano se l'utente ha inserito una query di ricerca nella casella di testo.

- "Passaggio del mouse" significa che l'utente ha posizionato il cursore del mouse sulla casella di ricerca (questo stato sostituisce tutti gli altri).

- "Disabilitato" significa che la funzionalità di ricerca è disattivata per il contesto corrente.

  ![Casella di ricerca con linea rossa](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")

  Usare…
  Quando si progetta una casella di ricerca personalizzata.

  Non usare...
  -   Per qualsiasi elemento diverso da una casella di ricerca.

- Per qualsiasi elemento che non deve corrispondere sempre all'interfaccia utente della casella di ricerca.

  **Focused**

  Componente

  Elemento

  Nome token: Category. Color

  ![Campo di input di ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")

  **Campo di input**

  Sfondo

  `SearchControl.FocusedBackground`

  Primo piano (testo)

  `SearchControl.FocusedBackground`

  Bordo

  `SearchControl.FocusedBorder`

  Separatore

  `SearchControl.FocusedDropDownSeparator`

  ![Pulsante di azione di ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")

  **Pulsante di azione**

  Sfondo

  nessuno

  Primo piano (glifo Cerca)

  `SearchControl.SearchGlyph`

  Primo piano (glifo Arresta)

  `SearchControl.StopGlyph`

  Primo piano (glifo Cancella)

  `SearchControl.ClearGlyph`

  Bordo

  N/D

  ![Elenco di ricerca&#45;verso il basso sul pulsante con stato attivato](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")

  **Pulsante elenco a discesa**

  Sfondo

  `SearchControl.FocusedDropDownButton`

  Primo piano (glifo)

  `SearchControl.FocusedDropDownButtonGlyph`

  Bordo

  `SearchControl.FocusedDropDownButtonBorder`

  **Con stato non attivo**

  Componente

  Elemento

  Nome token: Category. Color

  ![Campo di input ricerca con stato non attivo](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")

  **Campo di input attivo**

  Sfondo

  `SearchControl.SearchActiveBackground`

  Primo piano (testo)

  `SearchControl.SearchActiveBackground`

  Bordo

  `SearchControl.UnfocusedBorder`

  Separatore

  `SearchControl.DropDownSeparator`

  ![Campo di input di ricerca con stato non attivo e inattivo](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")

  **Campo di input inattivo**

  Sfondo

  `SearchControl.Unfocused`

  Primo piano (testo)

  `SearchControl.Unfocused`

  Bordo

  `SearchControl.UnfocusedBorder`

  Separatore

  `SearchControl.DropDownSeparator`

  ![Pulsante di azione di ricerca con stato non attivo](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")

  **Pulsante di azione**

  Sfondo

  N/D

  Primo piano (glifo Cerca)

  `SearchControl.SearchGlyph`

  Primo piano (glifo Arresta)

  `SearchControl.StopGlyph`

  Primo piano (glifo Cancella)

  `SearchControl.ClearGlyph`

  Bordo

  N/D

  ![Elenco di ricerca&#45;verso il basso sul pulsante con stato non attivo](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")

  **Pulsante elenco a discesa**

  Sfondo

  `SearchControl.UnfocusedDropDownButton`

  Primo piano (glifo)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Bordo

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Ricerca azione pulsante premuto](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")

  **Pulsante di azione**

  Sfondo

  `SearchControl.ActionButtonMouseDown`

  Primo piano (glifo)

  `SearchControl.ActionButtonMouseDownGlyph`

  Bordo

  `SearchControl.ActionButtonMouseDownBorder`

  ![Elenco di ricerca&#45;verso il basso la pressione del pulsante](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")

  **Pulsante elenco a discesa**

  Sfondo

  `SearchControl.MouseDownDropDownButton`

  Primo piano (glifo)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Bordo

  `SearchControl.MouseDownDropDownButtonBorder`

  **Evidenziato (solo testo)**

  Componente

  Elemento

  Nome token: Category. Color

  ![Evidenziazione di campo di input di ricerca](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")

  **Campo di input con testo evidenziato**

  Sfondo

  `SearchControl.Selection`

  Primo piano (testo)

  `SearchControl.FocusedBackground`

  Bordo

  nessuno

  Separatore

  `SearchControl.FocusedDropDownSeparator`

  **Disabilitato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Campo di input di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")

  **Campo di input**

  Sfondo

  `SearchControl.Disabled`

  Primo piano (testo)

  `SearchControl.Disabled`

  Bordo

  `SearchControl.DisabledBorder`

  Separatore

  `SearchControl.DropDownSeparator`

  ![Pulsante di azione di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")

  **Pulsante di azione**

  Sfondo

  nessuno

  Primo piano (glifo)

  `SearchControl.ActionButtonDisabledGlyph`

  Bordo

  nessuno

  ![Elenco di ricerca&#45;verso il basso sul pulsante disabilitato](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")

  **Pulsante elenco a discesa**

  Sfondo

  nessuno

  Primo piano (glifo)

  `SearchControl.DisabledDownButtonGlyph`

  Bordo

  nessuno

#### <a name="search-drop-down-lists"></a>Elenchi a discesa di ricerca
 Il menu a discesa della casella di ricerca può essere leggermente più complesso rispetto ad altri menu a discesa in Visual Studio. Le sezioni "ricerche suggerite" e "opzioni di ricerca" possono essere visualizzate singolarmente o insieme nel menu e ognuna ha un colore diverso. Una linea separa le due sezioni quando sono visualizzate insieme e un bordo circonda l'intero menu a discesa.

 ![Elenco di ricerca&#45;verso il basso con linea rossa](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")

 Usare…
 -   Quando si crea un elenco a discesa di ricerca personalizzato.

- I nomi di token appropriati per i componenti dell'elenco corretti.

  Non usare...
  -   Per elenchi a discesa visualizzati in altri contesti.

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.

  **Predefinito (nessun altro stato)**

  Elemento

  Nome token: Category. Color

  Bordo

  `SearchControl.PopupBorder`

  Separatore

  `SearchControl.PopupSectionHeaderSeparator`

  Ombreggiatura

  `Environment.DropShadowBackground`

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Ricerca con suggerita](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")

  **Ricerche suggerite**

  Sfondo

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `SearchControl.PopupItemText`

  ![Search check box](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")

  **Opzioni di ricerca (casella di controllo)**

  ![Le opzioni di ricerca](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")

  **Opzioni di ricerca (collegamento)**

  Sfondo

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo della casella di controllo)

  `SearchControl.PopupCheckboxText`

  Primo piano (testo del collegamento)

  `SearchControl.PopupButtonText`

  Sfondo dell'intestazione

  `SearchControl.PopupSectionHeaderGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo dell'intestazione)

  `SearchControl.PopupSectionHeaderText`

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Ricerca con suggerita al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")

  **Ricerche suggerite**

  Sfondo

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo)

  `SearchControl.PopupMouseOverItemText`

  Bordo

  `SearchControl.PopupControlMouseOverBorder`

  ![Casella di controllo di ricerca al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")

  **Ricerche suggerite (casella di controllo)**

  ![Le opzioni al passaggio del mouse di ricerca](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")

  **Opzioni di ricerca**

  Sfondo

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo della casella di controllo)

  `SearchControl.PopupCheckboxMouseDownText`

  Primo piano (testo del collegamento)

  `SearchControl.PopupButtonMouseDownText`

  Bordo

  `SearchControl.PopupControlMouseOverBorder`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Ricerca con suggerimento selezionata](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")

  **Ricerche suggerite (casella di controllo)**

  ![Cerca opzioni premute](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")

  **Opzioni di ricerca**

  Sfondo della casella di controllo

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo della casella di controllo)

  `SearchControl.PopupCheckboxMouseDownText`

  Sfondo del collegamento

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.

  Primo piano (testo del collegamento)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Collegamento ipertestuale
 Il collegamento ipertestuale è un controllo che non ha una coppia primo piano/sfondo. In tutti i casi, usare il colore primo piano del collegamento ipertestuale, visualizzato correttamente su sfondi scuri, grigi e bianchi. Se non si usa il token di colore per il controllo collegamento ipertestuale, verrà visualizzato il controllo di sistema predefinito per lo stato "premuto", che sarà di colore rosso lampeggiante. Questo comportamento segnala il fatto che il controllo non usa il token di colore dell'ambiente corretto.

 ![Collegamento ipertestuale con linea rossa](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")

 Usare…
Quando è necessario creare un collegamento ipertestuale personalizzato.

 Non usare...
Per qualsiasi elemento diverso da un collegamento ipertestuale.

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Collegamento ipertestuale predefinito](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")

 Primo piano (testo)

 `Environment.PanelHyperlink`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Collegamento ipertestuale al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")

 Primo piano (testo)

 `Environment.PanelHyperlinkHover`

 **Premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Collegamento ipertestuale selezionato](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")

 Primo piano (testo)

 `Environment.PanelHyperlinkPressed`

 **Disabilitato**

 Componente

 Elemento

 Nome token: Category. Color

 ![Collegamento ipertestuale disabilitato](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")

 Primo piano (testo)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Barra informazioni
 Le barre informazioni vengono usate per fornire altre informazioni su un contesto specifico e sono sempre visualizzate nella parte superiore della finestra di un documento o di una finestra degli strumenti.

 ![Barra informazioni con linea rossa](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")

 Usare…
Quando si creano barre informazioni personalizzate.

 Non usare...
Per gli elementi dell'interfaccia utente che non sono simili a una barra informazioni.

 Componente

 Elemento

 Nome token: Category. Color

 ![Infobar](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")

 **Infobar**

 Sfondo

 `Environment.InfoBackground`

 Primo piano (testo)

 `Environment.InfoText`

 Bordo

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Barra di scorrimento
 Le barre di scorrimento hanno uno stile che riflette l'ambiente di Visual Studio e non è necessario applicarvi un tema. Tuttavia, si potrebbe decidere che si desidera sfruttare i colori usati nelle barre di scorrimento in modo che l'interfaccia utente appaia sempre coerenza con questa parte dell'ambiente di Visual Studio.

 ![Barra di scorrimento con linea rossa](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")

 Usare…
Quando si crea un'interfaccia utente che deve corrispondere alle barre di scorrimento di Visual Studio.

 Non usare... per qualsiasi elemento desiderato non corrispondere sempre all'interfaccia utente della barra di scorrimento.

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Barra di scorrimento](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")

 **Barra di scorrimento**

 Barra di scorrimento

 `Environment.ScrollBarBackground`

 Primo piano (anteprima)

 `Environment.ScrollBarThumbBackground`

 ![Barra freccia di scorrimento](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")

 **Freccia di scorrimento**

 Sfondo

 `Environment.ScrollBarArrowBackground`

 Impostato sullo stesso colore della barra di scorrimento.

 Primo piano (glifo)

 `Environment.ScrollBarArrowGlyph`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Barra di scorrimento al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")

 **Barra di scorrimento**

 Barra di scorrimento

 `Environment.ScrollBarBackground`

 Primo piano (anteprima)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Freccia su hover delle barre di scorrimento](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")

 **Freccia di scorrimento**

 Sfondo

 `Environment.ScrollBarArrowMouseOverBackground`

 Impostato sullo stesso colore della barra di scorrimento.

 Primo piano (glifo)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Barra di scorrimento premuto](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")

 **Barra di scorrimento**

 Barra di scorrimento

 `Environment.ScrollBarBackground`

 Primo piano (anteprima)

 `Environment.ScrollBarThumbPressedBackground`

 ![Barra premuta freccia di scorrimento](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")

 **Freccia di scorrimento**

 Sfondo

 `Environment.ScrollBarArrowPressedBackground`

 Impostato sullo stesso colore della barra di scorrimento.

 Primo piano (glifo)

 `Environment.ScrollBarArrowGlyphPressed`

###  <a name="BKMK_TreeView"></a> Visualizzazione struttura ad albero
 Diverse finestre degli strumenti, tra cui Esplora soluzioni, Esplora server e Visualizzazione classi, implementano uno schema organizzativo gerarchico i cui colori sono controllati dai nomi di colore nella categoria TreeView. Tutti gli elementi in una visualizzazione albero hanno colori di sfondo e del testo. Gli elementi che hanno elementi figlio annidati hanno anche glifi che indicano se ogni elemento è espanso o compresso.

 ![Visualizzazione albero con linea rossa](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")

 Usare…
In qualsiasi punto in cui è necessario implementare una visualizzazione organizzativa gerarchica.

 Non usare...
 -   Per qualsiasi elemento che non è simile a una visualizzazione albero.

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Visualizzazione struttura ad albero](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")

  Sfondo

  `TreeView.Background`

  Primo piano (testo)

  `TreeView.Background`

  Primo piano (glifo)

  `TreeView.Glyph`

  Bordo

  nessuno

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Visualizazione al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")

  Sfondo

  `TreeView.Background`

  Primo piano (testo)

  `TreeView.Background`

  Primo piano (glifo)

  `TreeView.GlyphMouseOver`

  Bordo

  nessuno

  **Trascinare su**

  Componente

  Elemento

  Nome token: Category. Color

  ![Visualizzazione albero con trascinamento](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")

  Sfondo

  `TreeView.DragOverItem`

  Primo piano (testo)

  `TreeView.DragOverItem`

  Primo piano (glifo)

  `TreeView.DragOverItemGlyph`

  Bordo

  nessuno

  **selezionato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Con stato attivato di visualizzazione ad albero](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")

  **Focused**

  Sfondo

  `TreeView.SelectedItemActive`

  Primo piano (testo)

  `TreeView.SelectedItemActive`

  Primo piano (glifo)

  `TreeView.SelectedItemActiveGlyph`

  Bordo

  `TreeView.FocusVisualBorder`

  ![Con stato non attivo di visualizzazione ad albero](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")

  **Con stato non attivo**

  Sfondo

  `TreeView.SelectedItemInactive`

  Primo piano (testo)

  `TreeView.SelectedItemInactive`

  Primo piano (glifo)

  `TreeView.SelectedItemInactiveGlyph`

  Bordo

  nessuno

  **Selezionato al passaggio del mouse**

  Componente

  Elemento

  Nome token: Category. Color

  ![Con stato attivo al passaggio del mouse di visualizzazione ad albero](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")

  **Focused**

  Sfondo

  `TreeView.SelectedItemActive`

  Primo piano (testo)

  `TreeView.SelectedItemActive`

  Primo piano (glifo)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Bordo

  Nessuno`TreeView.FocusVisualBorder`

  ![Visualizzazione con stato non attivo al passaggio del mouse ad albero](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")

  **Con stato non attivo**

  Sfondo

  `TreeView.SelectedItemInactive`

  Primo piano (testo)

  `TreeView.SelectedItemInactive`

  Primo piano (glifo)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Bordo

  nessuno

### <a name="button-controls"></a>Controlli pulsante
 ![Controllo pulsante con linea rossa](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")

 Usare…
Per i pulsanti nell'area dei documenti da integrare con temi di Visual Studio (Chiaro, Scuro, Blu o un tema Contrasto elevato di sistema).

 Non usare...
Per i pulsanti che verranno visualizzati su uno sfondo personalizzato che non fa parte di un tema di Visual Studio.

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Button](../../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")

 Button

 `CommonControls.Button`

 Bordo del pulsante

 `CommonControls.ButtonBorder`

 **Disabilitato**

 Componente

 Elemento

 Nome token: Category. Color

 ![Pulsante disattivato](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")

 Button

 `CommonControls.ButtonDisabled`

 Bordo del pulsante

 `CommonControls.ButtonBorderDisabled`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Pulsante al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")

 Button

 `CommonControls.ButtonHover`

 Bordo del pulsante

 `CommonControls.ButtonBorderHover`

 **Premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Pulsante premuto](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")

 Button

 `CommonControls.ButtonPressed`

 Bordo del pulsante

 `CommonControls.ButtonBorderPressed`

 **Focused**

 Componente

 Elemento

 Nome token: Category. Color

 ![Pulsante con stato attivo](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")

 Button

 `CommonControls.ButtonFocused`

 Bordo del pulsante

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Controlli casella di controllo
 ![Casella di controllo con linea rossa](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")

 Usare…
Per controlli casella di controllo contenuti nell'area dei documenti.

 Non usare...
Per qualsiasi interfaccia utente diversa da un controllo casella di controllo.

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Casella di controllo](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")

 Sfondo

 `CommonControls.CheckBoxBackground`

 Bordo

 `CommonControls.CheckBoxBorder`

 Testo

 `CommonControls.CheckBoxText`

 Icona

 `CommonControls.CheckBoxGlyph`

 **Disabilitato**

 Componente

 Elemento

 Nome token: Category. Color

 ![Casella di controllo disabilitata](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")

 Sfondo

 `CommonControls.CheckBoxBackgroundDisabled`

 Bordo

 `CommonControls.CheckBoxBorderDisabled`

 Testo

 `CommonControls.CheckBoxTextDisabled`

 Icona

 `CommonControls.CheckBoxGlyphDisabled`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Casella di controllo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")

 Sfondo

 `CommonControls.CheckBoxBackgroundHover`

 Bordo

 `CommonControls.CheckBoxBorderHover`

 Testo

 `CommonControls.CheckBoxTextHover`

 Icona

 `CommonControls.CheckBoxGlyphHover`

 **Premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Casella di controllo premuta](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")

 Sfondo

 `CommonControls.CheckBoxBackgroundPressed`

 Bordo

 `CommonControls.CheckBoxBorderPressed`

 Testo

 `CommonControls.CheckBoxTextPressed`

 Icona

 `CommonControls.CheckBoxGlyphPressed`

 **Focused**

 Componente

 Elemento

 Nome token: Category. Color

 ![Casella di controllo con stato attivato](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")

 Sfondo

 `CommonControls.CheckBoxBackgroundFocused`

 Bordo

 `CommonControls.CheckBoxBorderFocused`

 Testo

 `CommonControls.CheckBoxTextFocused`

 Icona

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Controlli casella combinata/casella di riepilogo a discesa
 ![Drop&#45;down&#47;combo box redline](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")

 Usare…
Per elenchi a discesa e caselle combinate che fanno parte dell'area dei documenti.

 Non usare...
 -   Per qualsiasi interfaccia utente diversa da un elenco a discesa o una casella combinata.

- Per un controllo [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) o [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) nella barra dei comandi.

  **Default**

  Componente

  Elemento

  Nome token: Category. Color

  ![Drop&#45;down&#47;combo box](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")

  Sfondo

  `CommonControls.ComboBoxBackground`

  Bordo

  `CommonControls.ComboBoxBorder`

  Testo

  `CommonControls.ComboBoxText`

  Separatore

  `CommonControls.ComboBoxSeparator`

  Icona

  `CommonControls.ComboBoxGlyph`

  Sfondo del glifo

  `CommonControls.ComboBoxGlyphBackground`

  **Disabilitato**

  Componente

  Elemento

  Nome token: Category. Color

  ![Eliminare&#45;inattivo&#47;casella combinata disabilitata](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")

  Sfondo

  `CommonControls.ComboBoxBackgroundDisabled`

  Bordo

  `CommonControls.ComboBoxBorderDisabled`

  Testo

  `CommonControls.ComboBoxTextDisabled`

  Separatore

  `CommonControls.ComboBoxSeparatorDisabled`

  Icona

  `CommonControls.ComboBoxGlyphDisabled`

  Sfondo del glifo

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Hover**

  Componente

  Elemento

  Nome token: Category. Color

  ![Eliminare&#45;inattivo&#47;casella combinata al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")

  Sfondo

  `CommonControls.ComboBoxBackgroundHover`

  Bordo

  `CommonControls.ComboBoxBorderHover`

  Testo

  `CommonControls.ComboBoxTextHover`

  Separatore

  `CommonControls.ComboBoxSeparatorHover`

  Icona

  `CommonControls.ComboBoxGlyphHover`

  Sfondo del glifo

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Premuto**

  Componente

  Elemento

  Nome token: Category. Color

  ![Drop&#45;down&#47;combo box pressed](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")

  Sfondo

  `CommonControls.ComboBoxBackgroundPressed`

  Bordo

  `CommonControls.ComboBoxBorderPressed`

  Testo

  `CommonControls.ComboBoxTextPressed`

  Separatore

  `CommonControls.ComboBoxSeparatorPressed`

  Icona

  `CommonControls.ComboBoxGlyphPressed`

  Sfondo del glifo

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Focused**

  Componente

  Elemento

  Nome token: Category. Color

  ![Drop&#45;down&#47;combo box focused](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")

  Sfondo

  `CommonControls.ComboBoxBackgroundFocused`

  Bordo

  `CommonControls.ComboBoxBorderFocused`

  Testo

  `CommonControls.ComboBoxTextFocused`

  Separatore

  `CommonControls.ComboBoxSeparatorFocused`

  Icona

  `CommonControls.ComboBoxGlyphFocused`

  Sfondo del glifo

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Selezione di input di testo**

  Componente

  Elemento

  Nome token: Category. Color

  ![Drop&#45;down&#47;combo box text input](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")

  Evidenziazione

  `CommonControls.ComboBoxTextInputSelection`

  **Premuto-visualizzazione elementi elenco**

  ![Eliminare&#45;inattivo&#47;visualizzazione elenco della casella combinata](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")

  Sfondo

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Bordo

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  Testo dell'elemento

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  Ombreggiatura dello sfondo

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Controlli per dati tabulari (griglia)
 I controlli per dati tabulari, noti anche come controlli griglia, sono controlli comuni per Visual Studio, che possono essere usati per presentare grandi quantità di dati in più colonne. I controlli per dati tabulari standard possono trovarsi in diverse posizioni all'interno di Visual Studio, ad esempio nella finestra degli strumenti Elenco errori, nei report IntelliTrace e nella visualizzazione degli heap della memoria. Usare sempre i controlli per dati tabulari standard forniti. In alcuni casi rari, si potrebbe non avere accesso ai controlli per dati tabulari standard. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri controlli per dati tabulari in Visual Studio.

 ![Dati tabulari &#40;controllo griglia&#41; con linea rossa](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")

 Usare…
Per controlli tabulari o griglia.

 Non usare...
Per qualsiasi interfaccia utente diversa da un controllo tabulare o griglia.

#### <a name="column-headers"></a>Intestazioni di colonna
 Le intestazioni di colonna sono costituite da uno sfondo, un bordo, il testo del titolo e un glifo facoltativo, usato in genere quando una griglia viene ordinata in base alla colonna.

 Stato

 Elemento

 Nome token: Category. Color

 Impostazione predefinita

 Sfondo

 `Header.Default`

 Primo piano (testo)

 `Environment.CommandBarTextActive`

 Primo piano (glifo)

 `Header.Glyph`

 Bordo

 `Header.SeparatorLine`

 Passaggio del mouse

 Sfondo

 `Header.MouseOver`

 Primo piano (testo)

 `Environment.CommandBarTextHover`

 Primo piano (glifo)

 `Header.MouseOverGlyph`

 Bordo

 `Header.SeparatorLine`

 Premuto

 Sfondo

 `CommonControls.CheckBoxBackgroundPressed`

 Primo piano (testo)

 `CommonControls.CheckBoxBorderPressed`

 Primo piano (glifo)

 `CommonControls.CheckBoxTextPressed`

 Bordo

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Elementi della visualizzazione elenco
 Gli elementi della visualizzazione elenco sono costituiti da uno sfondo e da contenuto. Il contenuto può essere sotto forma di testo, icona o entrambi.

 Stato

 Elemento

 Nome token: Category. Color

 Impostazione predefinita

 Sfondo

 Trasparente

 Primo piano (testo)

 `Environment.CommandBarTextActive`

 Bordo

 nessuno

 Selezionato (attivo)

 Sfondo

 `TreeView.SelectedItemActive`

 Primo piano (testo)

 `TreeView.SelectedItemActiveText`

 Bordo

 nessuno

 Selezionato (inattivo)

 Sfondo

 `TreeView.SelectedItemInactive`

 Primo piano (testo)

 `TreeView.SelectedItemInactiveText`

 Bordo

 nessuno

## <a name="manifest-designer"></a>Finestra Progettazione manifesto
 La finestra Progettazione manifesto è stata progettata come strumento per semplificare la modifica del file manifesto in progetti Windows 8 e Windows Phone 8. Benché non sia disponibile per l'utilizzo alcun framework condiviso, potrebbe essere appropriato fare in modo che il layout di progettazione e i colori delle schede di orientamento/spostamento corrispondano alla struttura complessiva. Per altre informazioni sui dettagli del layout, vedere [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

 ![Finestra di progettazione manifesto con linea rossa](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")

 Usare…
 -   Per le finestre di progettazione simili alla finestra Progettazione manifesto.

- Invece di usare controlli scheda comuni nella parte superiore di un editor all'interno dell'area dei documenti.

  Non usare...
  -   Se sono presenti più di sei schede.

- Per qualsiasi interfaccia utente non strutturata come la finestra Progettazione manifesto.

  Stato

  Componente

  Elemento

  Nome token: Category. Color

  Predefinito (selezionato)

  Scheda

  Sfondo

  `ManifestDesigner.TabActive`

  Bordo

  nessuno

  Riquadro descrizione

  Sfondo

  `ManifestDesigner.DescriptionPane`

  Pagina contenuto

  Sfondo

  `ManifestDesigner.Background`

  Testo di supporto della finestra di dialogo

  `ManifestDesigner.WatermarkText`

  Questo nome di token non corrisponde alla sua funzione.

  Non selezionato

  Scheda

  Sfondo

  `ManifestDesigner.Tab.Inactive`

  Passaggio del mouse

  Scheda

  Sfondo

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Assegnazione di tag
 Visual Studio supporta l'assegnazione di tag, che permette a un utente di dichiarare parole chiave da cercare per scopi di verifica. Ad esempio, i project manager e gli sviluppatori possono usare Team Foundation Server (TFS) per assegnare tag a elementi di lavoro. La tabella seguente indica i nomi di colore per il tag stesso e il glifo dell'icona di chiusura visualizzato negli stati corrispondenti al passaggio del mouse e alla selezione.

 ![Tagging redline](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")

 Usare…
Per un'interfaccia utente che supporta l'assegnazione di tag.

 Non usare...
Per qualsiasi altro tipo di interfaccia utente.

### <a name="tag"></a>Tag
 Componente

 Elemento

 Nome token: Category. Color

 ![Tag](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")

 **Default**

 Sfondo

 `Tag.Background`

 Primo piano (testo)

 `Tag.Background`

 ![Tag al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")

 **Hover**

 Sfondo

 `Tag.HoverBackground`

 Primo piano (testo)

 `Tag.HoverBackgroundText`

 ![Tag premuto](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")

 **Premuto**

 Sfondo

 `Tag.PressedBackground`

 Primo piano (testo)

 `Tag.PressedBackgroundText`

 ![Tag selezionato](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")

 **selezionato**

 Sfondo

 `Tag.SelectedBackground`

 Primo piano (testo)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Glifo (icona di chiusura)
 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Tag &#40;glyph&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")

 **Predefinito (impostazione predefinita del tag)**

 Sfondo

 N/D

 Primo piano (glifo)

 `Tag.TagHoverGlyph`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Tag &#40;icona&#41; al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")

 **Al passaggio del mouse (impostazione predefinita del tag)**

 Sfondo

 `Tag.TagHoverGlyphHoverBackground`

 Primo piano (glifo)

 `Tag.TagHoverGlyphHover`

 Bordo

 `Tag.TagHoverGlyphHoverBorder`

 **Premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Tag &#40;glyph&#41; pressed](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")

 **Premuto (impostazione predefinita del tag)**

 Sfondo

 `Tag.TagHoverGlyphPressedBackground`

 Primo piano (glifo)

 `Tag.TagHoverGlyphPressed`

 Bordo

 `Tag.TagHoverGlyphPressedBorder`

 **Tag selezionato/glifo predefinito**

 Componente

 Elemento

 Nome token: Category. Color

 ![Tag selezionato](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")

 **Predefinito (tag selezionato)**

 Sfondo

 N/D

 Primo piano (glifo)

 `Tag.TagSelectedGlyph`

 **Tag selezionato/glifo al passaggio del mouse**

 Componente

 Elemento

 Nome token: Category. Color

 ![Tag selezionato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")

 **Al passaggio del mouse (tag selezionato)**

 Sfondo

 `Tag.TagSelectedGlyphHoverBackground`

 Primo piano (glifo)

 `Tag.TagSelectedGlyphHover`

 Bordo

 `Tag.TagSelectedGlyphHoverBorder`

 **Tag selezionato/glifo premuto**

 Componente

 Elemento

 Nome token: Category. Color

 ![Tag selezionato premuto](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")

 **Premuto (tag selezionato)**

 Sfondo

 `Tag.TagSelectedGlyphPressedBackground`

 Primo piano (glifo)

 `Tag.TagSelectedGlyphPressed`

 Bordo

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Shell

### <a name="background"></a>Sfondo
 Lo sfondo dell'ambiente è costituito da due livelli. Il livello inferiore è un colore a tinta unita che ricopre l'intero IDE. Il livello superiore si trova sotto lo scaffale dei comandi tra i canali Nascondi automaticamente della finestra degli strumenti, nei bordi destro e sinistro dell'IDE. A partire da Visual Studio 2013, i livelli superiore e inferiore dello sfondo sono impostati sullo stesso colore dei temi Chiaro e Scuro.

 ![Sfondo della shell con linea rossa](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")

 Usare…
Per i punti che devono corrispondere allo sfondo dell'ambiente di Visual Studio.

 Non usare...
 -   Come riempimento per i punti che non sono superfici di sfondo.

- Come sfondo su cui si vuole posizionare elementi in primo piano.

  Componente

  Elemento

  Nome token: Category. Color

  Livello inferiore

  Sfondo

  `Environment.EnvironmentBackground`

  Componente

  Elemento

  Nome token: Category. Color

  Livello superiore

  Sfondo

  *Cursori sfumatura impostati sullo stesso valore di colore dei temi di Visual Studio 2013 chiaro e scuro.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Scaffale dei comandi
 Due set di nomi di token vengono usati per gli sfondi dello scaffale dei comandi, uno per il punto in cui si trova la barra dei menu e l'altro per il punto in cui si trova la barra dei comandi. Un singolo gruppo della barra dei comandi ha valori di colore di sfondo propri, che vengono descritti in modo più dettagliato nella sezione "Barra dei comandi". Il testo della barra dei menu e della barra dei comandi viene descritto nelle rispettive sezioni.

 ![Scaffale dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")

 Usare…
 -   Per le aree in cui si posizionano menu o barre degli strumenti.

- con lo sfondo corretto /? corretta in primo piano.

  Non usare...
  Per aree che non sono simili a uno scaffale dei comandi.

  Componente

  Elemento

  Nome token: Category. Color

  Barra dei menu

  Sfondo

  *Cursori sfumatura impostati sullo stesso valore di colore dei temi di Visual Studio 2013 chiaro e scuro.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Barra dei comandi

  Sfondo

  *Cursori sfumatura impostati sullo stesso valore di colore dei temi di Visual Studio 2013 chiaro e scuro.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Casella degli strumenti
 La casella degli strumenti è una delle finestre degli strumenti comuni usata più di frequente in Visual Studio. Si tratta essenzialmente di un controllo albero con un tema e stili speciali applicati.

 ![Casella degli strumenti con linea rossa](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")

 Usare…
Quando si progetta una finestra degli strumenti che deve essere sempre coerente con la casella degli strumenti della shell.

 Non usare...
Per qualsiasi altro elemento diverso dall'interfaccia utente della casella degli strumenti oppure se si teme il verificarsi di problemi nell'interfaccia utente in caso di modifica dei colori della casella degli strumenti della shell.

 **Default**

 Componente

 Elemento

 Nome token: Category. Color

 ![Nodo padre della casella degli strumenti](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")

 **Nodo padre**

 ![Nodo figlio della casella degli strumenti](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")

 **Nodo figlio**

 Sfondo

 `Environment.ToolboxContent`

 Intestazioni

 `Environment.ToolWindowBackground`

 Singoli elementi o intera finestra se non è disponibile alcun controllo

 Bordo

 nessuno

 Primo piano (glifo)

 `Environment.ToolboxContent`

 Primo piano (testo)

 `Environment.ToolboxContent`

 **Hover**

 Componente

 Elemento

 Nome token: Category. Color

 ![Nodo figlio della casella degli strumenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")

 **Al passaggio del mouse della casella degli strumenti sul nodo figlio**

 Sfondo

 `Environment.ToolboxContentMouseOver`

 Solo singoli elementi

 Bordo

 nessuno

 Primo piano (testo)

 `Environment.ToolboxContentMouseOver`

 Solo singoli elementi

 **selezionato**

 Componente

 Elemento

 Nome token: Category. Color

 ![Nodo padre della casella degli strumenti con stato attivo](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")

 **Nodo padre con stato attivo**

 ![Nodo figlio della casella degli strumenti con stato attivo](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")

 **Nodo figlio con stato attivo**

 Sfondo

 `TreeView.SelectedItemActive`

 Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Bordo

 `TreeView.FocusVisualBorder`

 Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Primo piano (glifo)

 `TreeView.SelectedItemActive`

 Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Primo piano (testo)

 `TreeView.SelectedItemActive`

 Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 ![Nodo padre della casella degli strumenti con stato non attivo](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")

 **Nodo padre con stato non attivo**

 ![Nodo figlio della casella degli strumenti con stato non attivo](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")

 **Nodo figlio con stato non attivo**

 Sfondo

 `TreeView.SelectedItemInactive`

 Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Bordo

 nessuno

 Primo piano (glifo)

 `TreeView.SelectedItemInactive`

 Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Primo piano (testo)

 `TreeView.SelectedItemInactive`

 Dalla categoria [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)
