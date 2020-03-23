---
title: Colori condivisi Documenti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302406"
---
# <a name="shared-colors"></a>Colori condivisi
Inserire qui l'introduzione.  
  
## <a name="shared-colors"></a>Colori condivisi  
 Quando si progetta un'interfaccia utente che usa elementi comuni della shell di Visual Studio o si vuole che gli elementi dell'interfaccia siano coerenti con funzionalità simili, usare nomi di token esistenti in file di definizione del pacchetto per scegliere e assegnare i colori. In questo modo, l'interfaccia utente resta coerente con l'intero ambiente di Visual Studio e viene aggiornata automaticamente quando vengono aggiunti o aggiornati temi.  
  
 Questo articolo descrive gli elementi dell'interfaccia utente comuni e i nomi di token usati da questi elementi, a cui è possibile fare riferimento durante la compilazione di un'interfaccia utente simile. Per informazioni specifiche su come accedere a questi token di colore, vedere [The VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Assicurarsi di usare correttamente i nomi di token:  
  
- **Usare i nomi di token in base alla funzione e non al colore stesso.** I colori condivisi comuni sono associati a elementi dell'interfaccia specifici e destinati solo a essere usati per le stesse funzionalità o altre simili. Ad esempio, evitare di riutilizzare il colore di una casella combinata premuta per un'animazione di stato rotante solo perché si ha una preferenza per questo colore. Le funzioni della casella combinata e dell'animazione sono diverse e se il colore associato alla casella combinata cambia, potrebbe non essere più appropriato per l'elemento animazione. Un uso coerente del colore aiuta a orientare correttamente gli utenti e a impedire confusione.  
  
- **Usare colori di sfondo e del testo nella combinazione corretta.** I colori di sfondo destinati a essere usati con il testo implicano un colore del testo associato. Non usare colori del testo diversi da quelli specificati per un determinato sfondo. Se non esiste un colore del testo associato, non usare il colore di sfondo per alcuna superficie in cui si prevede di visualizzare testo. Combinazioni di colori di sfondo e del testo diverse potrebbero produrre un'interfaccia illeggibile.  
  
- **Usare colori dei controlli appropriati per la rispettiva posizione.** In determinati stati alcuni controlli di Visual Studio non hanno colori di sfondo e dei bordi separati. Al contrario, selezionano questi colori dalle superfici sottostanti. Assicurarsi di usare sempre i nomi di token appropriati per la posizione in cui si posiziona il controllo.  
  
> [!IMPORTANT]
> Non usare i token inclusi nelle categorie "Pagina iniziale" o "Cider".  
  
### <a name="command-structures"></a>Strutture dei comandi  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menu  
 I menu possono trovarsi in diverse posizioni all'interno di Visual Studio 2013: sulla barra dei menu principale, incorporati in finestre dei documenti o degli strumenti o visualizzati tramite clic con il pulsante destro del mouse in diversi punti dell'IDE. Le implementazioni dei menu associati ad altri elementi dell'interfaccia utente vengono descritte nella sezione relativa al rispettivo elemento. È preferibile usare sempre l'implementazione dei menu standard fornita dall'ambiente di Visual Studio. Tuttavia, in alcuni casi rari si potrebbe non avere accesso ai menu standard di Visual Studio. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri menu in Visual Studio.  
  
 ![Menu con linea rossa](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Usare…  
- Ogni volta che è necessario creare un menu personalizzato.  
  
- Quando un nuovo componente dell'interfaccia utente deve corrispondere ai menu di Visual Studio.  
  
Non usare...  
Il colore di sfondo da solo. Usare sempre la combinazione sfondo/primo piano specificata.  
  
##### <a name="menu-title"></a>Titolo del menu  
 I titoli dei menu sono costituiti da uno sfondo, un bordo e il testo del titolo, nonché da un glifo facoltativo, in genere quando il menu si trova in una barra dei comandi.  
  
 ![Titolo menu con linea rossa](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Usare...  
Ogni volta che si crea un titolo di menu personalizzato.  
  
Non usare...  
- Per qualsiasi elemento che non deve corrispondere sempre al titolo del menu.  
  
- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titolo menu predefinito](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Titolo del menu**|Background|nessuno|  
|![Titolo menu predefinito](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Titolo del menu**|Primo piano (testo)|`Environment.CommandBarTextActive`|  
|![Titolo menu con glifo predefinito](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Titolo del menu con glifo**|Primo piano (glifo)|`Environment.CommandBarMenuGlyph`|  
|![Titolo menu con glifo predefinito](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Titolo del menu con glifo**|Bordo|nessuno|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titolo menu al passaggio del mouse](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Titolo del menu**|Background|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Titolo menu al passaggio del mouse](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Titolo del menu**|Primo piano (testo)|`Environment.CommandBarTextHover`|  
|![Titolo menu con glifo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Titolo del menu con glifo**|Primo piano (glifo)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Titolo menu con glifo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Titolo del menu con glifo**|Bordo|`Environment.CommandBarBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titolo menu selezionato](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Titolo del menu**|Background|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Titolo menu selezionato](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Titolo del menu**|Primo piano (testo)|`Environment.CommandBarTextActive`|  
|![Titolo menu con glifo selezionato](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Titolo del menu con glifo**|Primo piano (glifo)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Titolo menu con glifo selezionato](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Titolo del menu con glifo**|Bordo|`Environment.CommandBarMenuBorder`<br /><br /> Solo lati sinistro, superiore e destro.|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Titolo menu con glifo disabilitato](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Titolo del menu con glifo**|Background|nessuno|  
|![Titolo menu con glifo disabilitato](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Titolo del menu con glifo**|Primo piano (testo)|`Environment.CommandBarTextInactive`|  
|![Titolo menu con glifo disabilitato](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Titolo del menu con glifo**|Primo piano (glifo)|`Environment.CommandBarTextInactive`|  
|![Titolo menu con glifo disabilitato](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Titolo del menu con glifo**|Bordo|nessuno|  
  
##### <a name="menu"></a>Menu  
 Una singola voce di menu è costituita dal testo del menu e da un'icona facoltativa, una casella di controllo o un glifo del sottomenu. Il colore di sfondo e del testo cambiano al passaggio del mouse. Questo token di colore è una coppia sfondo/primo piano.  
  
 ![Voci di menu con linea rossa](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Usare...  
 Per qualsiasi elenco a discesa avviato da una barra dei menu o una barra dei comandi.  
  
Non usare...  
- Per qualsiasi elenco a discesa presente in un altro contesto.  

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menu predefinito](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Background|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Menu predefinito](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Primo piano (testo)|`Environment.CommandBarTextActive`|  
|![Menu predefinito](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Primo piano (glifo del sottomenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menu predefinito](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Bordo|`Environment.CommandBarMenuBorder`|  
|![Menu predefinito](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Sfondo del canale delle icone|`Environment.CommandBarMenuIconBackground`|  
|![Menu predefinito](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Separatore|`Environment.CommandBarMenuSeparator`|  
|![Menu predefinito](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Shadow|`Environment.DropShadowBackground`|  
|![Menu scelto](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Controllato**|Segno di spunta|`Environment.CommandBarCheckBox`|  
|![Menu scelto](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Controllato**|Sfondo del segno di spunta|`Environment.CommandBarSelectedIcon`|  
|![Menu selezionato](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selezionato**|Sfondo dell'icona|`Environment.CommandBarSelected`|  
|![Menu selezionato](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selezionato**|Bordo dell'icona|`Environment.CommandBarSelectedBorder`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menu al passaggio del mouse](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Voce di menu**|Background|`Environment.CommandBarMenuItemMouseOver`|  
|![Menu al passaggio del mouse](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Voce di menu**|Primo piano (testo)|`Environment.CommandBarMenuItemMouseOver`|  
|![Menu al passaggio del mouse](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Voce di menu**|Primo piano (glifo del sottomenu)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Menu scelto al passaggio del mouse](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Controllato**|Segno di spunta|`Environment.CommandBarCheckBoxMouseOver`|  
|![Menu scelto al passaggio del mouse](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Controllato**|Sfondo del segno di spunta|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Menu selezionato al passaggio del mouse](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selezionato**|Sfondo dell'icona|`Environment.CommandBarHoverOverSelected`|  
|![Menu selezionato al passaggio del mouse](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selezionato**|Bordo dell'icona|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menu disabilitato](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Voce di menu|Primo piano (testo)|`Environment.CommandBarTextInactive`|  
|![Menu disabilitato](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Voce di menu|Primo piano (glifo del sottomenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menu disabilitato selezionato](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Selezionato|Segno di spunta|`Environment.CommandBarCheckBoxDisabled`|  
|![Menu disabilitato selezionato](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Selezionato|Sfondo del segno di spunta|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Barra dei comandi  
 La barra dei comandi può essere visualizzata in più posizioni all'interno dell'IDE di Visual Studio, in particolare nello scaffale dei comandi e come incorporata nelle finestre degli strumenti e dei documenti.  
  
 In generale, usare sempre l'implementazione della barra dei menu standard fornita dall'ambiente di Visual Studio. L'uso del meccanismo standard garantisce che tutti i dettagli visivi vengano visualizzati correttamente e che gli elementi interattivi abbiano un comportamento coerente con gli altri controlli della barra dei comandi di Visual Studio. Tuttavia, se è necessario compilare una barra dei comandi personalizzata, assicurarsi di applicare lo stile corretto usando i nomi di token seguenti.  
  
 ![Barra dei comandi con linea rossa](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Pulsante di overflow con linea rossa](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Usare...  
 Nelle posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile usare l'implementazione della barra dei comandi standard di Visual Studio.  
  
Non usare...  
- Per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi.  

- Per i componenti della barra dei comandi diversi da quelli per cui sono specificati i nomi di token.  
  
##### <a name="command-bar-group"></a>Gruppo della barra dei comandi  
 Un gruppo della barra dei comandi è costituito da un set correlato di controlli della barra dei comandi e può contenere un numero qualsiasi di pulsanti, pulsanti di menu combinato, menu a discesa, caselle combinate o menu. I colori per questi controlli sono determinati da nomi di token separati e vengono descritti singolarmente in altre sezioni di questa guida. Viene usata una linea di separazione per dividere un gruppo della barra dei comandi in sottogruppi correlati.  
  
 ![Gruppo barra dei comandi con linea rossa](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Usare...  
 Nelle posizioni in cui è necessaria una barra dei comandi incorporata, ma non è possibile usare l'implementazione della barra dei comandi standard di Visual Studio.  
  
Non usare...  
- Per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi.  

- Per i componenti della barra dei comandi diversi da quelli per cui sono specificati i nomi di token.  
  
  **Predefinito** (nessun altro stato)  
  
|Elemento|Nome token: Category.color|  
|-------------|--------------------------------|  
|Background|`Environment.CommandBarGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|Bordo|`Environment.CommandBarToolBarBorder`|  
|Quadratino di trascinamento|`Environment.CommandBarDragHandle`|  
|Separatore|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Icone dei comandi  
 ![Icona del comando con linea rossa](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Icona del comando con linea rossa](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Usare...  
 Per qualsiasi pulsante che verrà posizionato su una barra dei comandi.  
  
Non usare...  
- Per i controlli che hanno nomi di token propri.  

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icona del comando predefinita](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Predefinito**|Background|N/D (eredita dallo sfondo della barra dei comandi)|  
|![Icona del comando predefinita](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Predefinito**|Primo piano (testo)|`Environment.CommandBarTextActive`|  
|![Icona del comando predefinita](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Predefinito**|Bordo|N/D|  
|![Icona del comando predefinita selezionata](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selezionato**|Background|`Environment.CommandBarSelected`|  
|![Icona del comando predefinita selezionata](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selezionato**|Primo piano (testo)|`Environment.CommandBarTextSelected`|  
|![Icona del comando predefinita selezionata](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selezionato**|Bordo|`Environment.CommandBarSelectedBorder`|  
  
 **Passaggio del mouse e stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icona del comando al passaggio del mouse](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard al passaggio del mouse**|Background|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Icona del comando al passaggio del mouse](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard al passaggio del mouse**|Primo piano (testo)|`Environment.CommandBarTextHover`|  
|![Icona del comando al passaggio del mouse](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard al passaggio del mouse**|Bordo|`Environment.CommandBarBorder`|  
|![Icona del comando selezionata al passaggio del mouse](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Selezionato al passaggio del mouse**|Background|`Environment.CommandBarHoverOverSelected`|  
|![Icona del comando selezionata al passaggio del mouse](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Selezionato al passaggio del mouse**|Primo piano (testo)|`Environment.CommandBarTextHoverOverSelected`|  
|![Icona del comando selezionata al passaggio del mouse](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Selezionato al passaggio del mouse**|Bordo|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icona del comando selezionata](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Icona del comando premuta**|Background|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Icona del comando selezionata](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Icona del comando premuta**|Primo piano (testo)|`Environment.CommandBarTextMouseDown`|  
|![Icona del comando selezionata](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Icona del comando premuta**|Bordo|`Environment.CommandBarBorder`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icona del comando disabilitata](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Icona del comando disabilitata**|Background|N/D (eredita dallo sfondo della barra dei comandi)|  
|![Icona del comando disabilitata](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Icona del comando disabilitata**|Primo piano (testo)|`Environment.CommandBarTextInactive`|  
|![Icona del comando disabilitata](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Icona del comando disabilitata**|Bordo|N/D|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Casella combinata  
  
> [!IMPORTANT]
> Le caselle combinate sono simili agli elenchi a discesa, ma includono un'area di testo modificabile. Se la casella di riepilogo a discesa non contiene un'area di testo modificabile, usare i token di colore indicati in [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Casella combinata con linea rossa](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Usare…  
- Quando si compilano caselle combinate personalizzate.  

- Quando si crea un controllo della barra dei comandi simile a una casella combinata.  

Non usare...  
- Per qualsiasi elemento che non deve corrispondere sempre all'interfaccia utente della barra dei comandi.  

- Quando si ha accesso a una casella combinata con stile.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo di input della casella combinata](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo di input**|Background|`Environment.ComboBoxBackground`|  
|![Campo di input della casella combinata](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo di input**|Primo piano (testo)|`Environment.ComboBoxText`|  
|![Campo di input della casella combinata](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo di input**|Bordo|`Environment.ComboBoxBorder`|  
|![Campo di input della casella combinata](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo di input**|Separatore|Nessun separatore|  
|![Casella combinata a discesa&#45;pulsante giù](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Pulsante a discesa**|Background|N/D (eredita)|  
|![Casella combinata a discesa&#45;pulsante giù](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.ComboBoxGlyph`|  
|![Elenco&#45;'elenco a discesa&#47;casella combinata](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Elenco a discesa**|Background|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Elenco&#45;'elenco a discesa&#47;casella combinata](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Elenco a discesa**|Primo piano (testo)|`Environment.ComboBoxItemText`|  
|![Elenco&#45;'elenco a discesa&#47;casella combinata](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Elenco a discesa**|Bordo|`Environment.ComboBoxPopupBorder`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo di input della casella combinata al passaggio del mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo di input**|Background|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Campo di input della casella combinata al passaggio del mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo di input**|Primo piano (testo)|`Environment.ComboBoxMouseOverText`|  
|![Campo di input della casella combinata al passaggio del mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo di input**|Bordo|`Environment.ComboBoxMouseOverBorder`|  
|![Campo di input della casella combinata al passaggio del mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo di input**|Separatore|`Environment.ComboBoxMouseOverSeparator`|  
|![Casella combinata&#47;pulsante a discesa&#45;verso il basso al passaggio del mouse](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Pulsante a discesa**|Background|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Casella combinata&#47;pulsante a discesa&#45;verso il basso al passaggio del mouse](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.ComboBoxMouseOverGlyph`|  
|![Casella combinata&#47;elenco a discesa&#45;elenco a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Elenco a discesa**|Sfondo (voce di menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Casella combinata&#47;elenco a discesa&#45;elenco a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Elenco a discesa**|Primo piano (testo)|`Environment.ComboBoxItemMouseOverText`|  
|![Casella combinata&#47;elenco a discesa&#45;elenco a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Elenco a discesa**|Bordo (voce di menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Con stato attivo**  
  
|Componente|Elemento|Nome token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo di input della casella combinata con stato attivo](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo di input**|Background|`Environment.ComboBoxFocusedBackground`|  
|![Campo di input della casella combinata con stato attivo](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo di input**|Primo piano (testo)|`Environment.ComboBoxFocusedText`|  
|![Campo di input della casella combinata con stato attivo](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo di input**|Bordo|`Environment.ComboBoxFocusedBorder`|  
|![Campo di input della casella combinata con stato attivo](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo di input**|Separatore|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Casella combinata&#47;pulsante a discesa&#45;verso il basso](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Pulsante a discesa**|Background|`Environment.ComboBoxFocusedButtonBackground`|  
|![Casella combinata&#47;pulsante a discesa&#45;verso il basso](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo di input della casella combinata selezionato](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo di input**|Background|`Environment.ComboBoxMouseDownBackground`|  
|![Campo di input della casella combinata selezionato](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo di input**|Primo piano (testo)|`Environment.ComboBoxMouseDownText`|  
|![Campo di input della casella combinata selezionato](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo di input**|Bordo|`Environment.ComboBoxMouseDownBorder`|  
|![Campo di input della casella combinata selezionato](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo di input**|Separatore|`Environment.ComboBoxMouseDownSeparator`|  
|![Pulsante a discesa&#45;&#47;casella combinata](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Pulsante a discesa**|Background|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Pulsante a discesa&#45;&#47;casella combinata](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo di input della casella combinata disabilitato](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo di input**|Background|`Environment.ComboBoxDisabledBackground`|  
|![Campo di input della casella combinata disabilitato](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo di input**|Primo piano (testo)|`Environment.ComboBoxDisabledText`|  
|![Campo di input della casella combinata disabilitato](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo di input**|Bordo|`Environment.ComboBoxDisabledBorder`|  
|![Campo di input della casella combinata disabilitato](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo di input**|Separatore|Nessun separatore|  
|![Casella combinata&#47;pulsante a discesa&#45;verso il basso disattivato](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Pulsante a discesa**|Background|nessuno|  
|![Casella combinata&#47;pulsante a discesa&#45;verso il basso disattivato](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Menu a discesa  
  
> [!IMPORTANT]
> Gli elenchi a discesa sono simili alle caselle combinate, ma non contengono aree di testo modificabili. Se l'elenco a discesa contiene un'area di testo modificabile, usare i token di colore indicati in [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Abbassare&#45;linea rossa verso il basso](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Usare…  
 Quando si creano controlli elenco a discesa personalizzati.  
  
Non usare...  
- Per qualsiasi elemento che non è simile a un elenco a discesa.  

- Per caselle combinate o pulsanti di menu combinato.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Eliminare&#45;campo di selezione verso il basso](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo di selezione**|Background|`Environment.DropDownBackground`|  
|![Eliminare&#45;campo di selezione verso il basso](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo di selezione**|Primo piano (testo)|`DropDownText`|  
|![Eliminare&#45;campo di selezione verso il basso](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo di selezione**|Bordo|`DropDownBorder`|  
|![Eliminare&#45;campo di selezione verso il basso](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo di selezione**|Separatore|Nessun separatore|  
|![Pulsante&#45;a discesa](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Pulsante a discesa**|Background|nessuno|  
|![Pulsante&#45;a discesa](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.DropDownGlyph`|  
|![Elenco a discesa&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Elenco a discesa**|Background|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Elenco a discesa&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Elenco a discesa**|Primo piano (testo)|`Environment.ComboBoxItemText`|  
|![Elenco a discesa&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Elenco a discesa**|Bordo|`Environment.DropDownPopupBorder`|  
|![Elenco a discesa&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Elenco a discesa**|Shadow|`Environment.DropShadowBackground`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rilascia&#45;campo di selezione al passaggio del mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo di selezione**|Background|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Rilascia&#45;campo di selezione al passaggio del mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo di selezione**|Primo piano (testo)|`Environment.DropDownMouseOverText`|  
|![Rilascia&#45;campo di selezione al passaggio del mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo di selezione**|Bordo|`Environment.DropDownMouseOverBorder`|  
|![Rilascia&#45;campo di selezione al passaggio del mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo di selezione**|Separatore|`Environment.DropDownButtonMouseOverSeparator`|  
|![Pulsante&#45;a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Pulsante a discesa**|Background|`Environment.DropDownButtonMouseOverBackground`|  
|![Pulsante&#45;a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.DropDownMouseOverGlyph`|  
|![Rilascia&#45;elenco a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Elenco a discesa**|Sfondo (voce di menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Rilascia&#45;elenco a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Elenco a discesa**|Primo piano (testo)|`Environment.ComboBoxItemMouseOverText`|  
|![Rilascia&#45;elenco a discesa al passaggio del mouse](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Elenco a discesa**|Bordo (voce di menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![È stato premuto il campo di selezione&#45;verso il basso](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo di selezione**|Background|`Environment.DropDownMouseDownBackground`|  
|![È stato premuto il campo di selezione&#45;verso il basso](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo di selezione**|Primo piano (testo)|`Environment.DropDownMouseDownText`|  
|![È stato premuto il campo di selezione&#45;verso il basso](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo di selezione**|Bordo|`Environment.DropDownMouseDownBorder`|  
|![È stato premuto il campo di selezione&#45;verso il basso](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo di selezione**|Separatore|`Environment.DropDownButtonMouseDownSeparator`|  
|![Pulsante a discesa&#45;premuto](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Pulsante a discesa**|Background|`Environment.DropDownButtonMouseDownBackground`|  
|![Pulsante a discesa&#45;premuto](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`Environment.DropDownMouseDownGlyph`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo di selezione&#45;verso il basso disabilitato](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Background|`Environment.DropDownDisabledBackground`|  
|![Campo di selezione&#45;verso il basso disabilitato](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Primo piano (testo)|`Environment.DropDownDisabledText`|  
|![Campo di selezione&#45;verso il basso disabilitato](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Bordo|`Environment.DropDownDisabledBorder`|  
|![Campo di selezione&#45;verso il basso disabilitato](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Separatore|Nessun separatore|  
|![Pulsante a discesa&#45;disabilitato](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Background|N/D|  
|![Pulsante a discesa&#45;disabilitato](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Primo piano (glifo)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Pulsante di menu combinato  
 I pulsanti di menu combinato condividono molti nomi di token con altri controlli della barra dei comandi, come pulsanti, menu e testo della barra dei comandi. Tutti i nomi di token dei pulsanti a discesa e di azione necessari vengono ripetuti qui per praticità. Gli elenchi a discesa dei pulsanti di menu combinato sono implementazioni dei [Menus](../misc/shared-colors.md#BKMK_CommandMenus)della barra dei comandi.  
  
 ![Pulsante di menu combinato con linea rossa](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Usare…  
 Quando si compila un pulsante di menu combinato personalizzato.  
  
Non usare...  
- Per altri tipi di pulsanti.  

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante di menu combinato](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Pulsante di menu combinato (predefinito)**|Background|nessuno|  
|![Pulsante di menu combinato](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Pulsante di menu combinato (predefinito)**|Primo piano (testo)|`Environment.CommandBarTextActive`|  
|![Pulsante di menu combinato](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Pulsante di menu combinato (predefinito)**|Primo piano (glifo)|`Environment.CommandBarSplitButtonGlyph`|  
|![Pulsante di menu combinato](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Pulsante di menu combinato (predefinito)**|Bordo|N/D|  
|![Pulsante di menu combinato](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Pulsante di menu combinato (predefinito)**|Separatore|N/D|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante Dividi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Pulsante di menu combinato (al passaggio del mouse)**|Background|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Pulsante Dividi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Pulsante di menu combinato (al passaggio del mouse)**|Primo piano (testo)|`Environment.CommandBarTextHover`|  
|![Pulsante Dividi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Pulsante di menu combinato (al passaggio del mouse)**|Primo piano (glifo)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Pulsante Dividi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Pulsante di menu combinato (al passaggio del mouse)**|Bordo|`Environment.CommandBarBorder`|  
|![Pulsante Dividi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Pulsante di menu combinato (al passaggio del mouse)**|Separatore|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante Dividi premuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Pulsante di menu combinato (premuto)**|Background|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Pulsante Dividi premuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Pulsante di menu combinato (premuto)**|Primo piano (testo)|`Environment.CommandBarTextMouseDown`|  
|![Pulsante Dividi premuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Pulsante di menu combinato (premuto)**|Primo piano (glifo)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Pulsante Dividi premuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Pulsante di menu combinato (premuto)**|Bordo|`Environment.CommandBarBorder`|  
|![Pulsante Dividi premuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Pulsante di menu combinato (premuto)**|Separatore|N/D|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante Dividi disabilitato](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Pulsante di menu combinato (disabilitato)**|Background|N/D|  
|![Pulsante Dividi disabilitato](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Pulsante di menu combinato (disabilitato)**|Primo piano (testo)|`Environment.ComboBoxItemTextInactive`|  
|![Pulsante Dividi disabilitato](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Pulsante di menu combinato (disabilitato)**|Primo piano (glifo)|`Environment.CommandBarTextInactive`|  
|![Pulsante Dividi disabilitato](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Pulsante di menu combinato (disabilitato)**|Bordo|N/D|  
|![Pulsante Dividi disabilitato](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Pulsante di menu combinato (disabilitato)**|Separatore|N/D|  
  
##### <a name="more-options-and-overflow-buttons"></a>Pulsanti "Altre opzioni" e "Overflow"  
 Il pulsante "Altre opzioni" viene usato quando un gruppo della barra dei comandi può essere personalizzato aggiungendo o rimuovendo pulsanti della barra dei comandi correlati. Il pulsante "Overflow" viene visualizzato quando una barra dei comandi è troncata a causa della mancanza di spazio orizzontale e, dopo avervi fatto clic sopra, mostra un menu che contiene i pulsanti della barra dei comandi che non possono essere visualizzati. I colori per questi due pulsanti sono controllati dallo stesso set di nomi di token.  
  
 ![Altre opzioni con linea rossa](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Usare…  
 Per pulsanti "Altre opzioni" e "Overflow" personalizzati.  
  
 Non usare...  
 Per pulsanti che non hanno una funzionalità simile ai pulsanti "Altre opzioni" e "Overflow".  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Altre opzioni](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Altre opzioni**|Background|`Environment.CommandBarOptionsBackground`|  
|![Altre opzioni](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Altre opzioni**|Primo piano (glifo)|`Environment.CommandBarOptionsGlyph`|  
|![Pulsante di overflow](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Overflow**|Background|`Environment.CommandBarOptionsBackground`|  
|![Pulsante di overflow](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Overflow**|Primo piano (glifo)|`Environment.CommandBarOptionsGlyph`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Altre opzioni al passaggio del mouse](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Altre opzioni**|Background|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Altre opzioni al passaggio del mouse](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Altre opzioni**|Primo piano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Overflow al passaggio del mouse](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Overflow**|Background|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Overflow al passaggio del mouse](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Overflow**|Primo piano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Altre opzioni selezionate](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Altre opzioni**|Background|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Altre opzioni selezionate](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Altre opzioni**|Primo piano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Overflow selezionato](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Overflow**|Background|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Overflow selezionato](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Overflow**|Primo piano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Finestre dei documenti  
 Non è necessario replicare le finestre dei documenti, perché vengono fornite dall'ambiente di Visual Studio. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre dei documenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.  
  
 Quando si usano token di colore per le finestre dei documenti, è necessario fare attenzione a usarli solo per elementi simili e sempre in coppia. In caso contrario, si otterranno risultati imprevisti nell'interfaccia utente.  
  
#### <a name="document-window-frame"></a>Cornice delle finestre dei documenti  
 Le finestre dei documenti possono essere ancorate nell'IDE o mobili come finestre separate. Quando la finestra di un documento è mobile al di fuori dell'IDE, si trova comunque all'interno di un'area dei documenti e ha gli stessi colori di sfondo, del bordo, del testo e delle schede di quando fa parte dell'IDE. Tuttavia, il documento si trova all'interno di una cornice che ha colori di sfondo, del bordo e del testo propri. Quando le finestre degli strumenti sono ancorate nell'area dei documenti, ereditano il comportamento e il colore per le rispettive schede dai nomi di token delle finestre dei documenti.  
  
 ![Finestra del documento ancorata](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Finestra del documento ancorata**  
  
 ![Finestra del documento con linea rossa](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Finestra del documento mobile**  
  
 Usare…  
 In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alla finestra del documento.  
  
 Non usare...  
 Per qualsiasi interfaccia utente che non deve automaticamente cambiare se la shell include un aggiornamento del tema.  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|Documento: ancorato o mobile|Background|Dipende dal tipo di documento|  
|Documento: ancorato o mobile|Primo piano (testo)|Dipende dal tipo di documento|  
|Documento: ancorato o mobile|Bordo|`Environment.ToolWindowBorder`|  
|![Frame con stato attivo](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Cornice: mobile, con stato attivo**|Background|`Environment.ToolWindowFloatingFrame`|  
|![Frame con stato attivo](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Cornice: mobile, con stato attivo**|Primo piano (testo)|`Environment.ToolWindowFloatingFrame`|  
|![Frame con stato attivo](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Cornice: mobile, con stato attivo**|Primo piano (glifo)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Frame con stato attivo](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Cornice: mobile, con stato attivo**|Bordo|`Environment.MainWindowActiveDefaultBorder`|  
|![Frame con stato attivo](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Cornice: mobile, con stato attivo**|Bordo (glifo)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Impostato su trasparente|  
|![Frame con stato non attivo](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Cornice: mobile, con stato non attivo**|Background|`Environment.ToolWindowFloatingFrameInactive`|  
|![Frame con stato non attivo](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Cornice: mobile, con stato non attivo**|Primo piano (testo)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Frame con stato non attivo](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Cornice: mobile, con stato non attivo**|Primo piano (glifo)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Frame con stato non attivo](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Cornice: mobile, con stato non attivo**|Bordo|`Environment.MainWindowInactiveBorder`|  
|![Frame con stato non attivo](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Cornice: mobile, con stato non attivo**|Bordo (glifo)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Impostato su trasparente|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Frame con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Cornice: mobile, con stato attivo**|Sfondo (glifo)|`Environment.RaftedWindowButtonHoverActive`|  
|![Frame con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Cornice: mobile, con stato attivo**|Primo piano (glifo)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Frame con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Cornice: mobile, con stato attivo**|Bordo (glifo)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Frame con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Cornice: mobile, con stato non attivo**|Sfondo (glifo)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Frame con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Cornice: mobile, con stato non attivo**|Primo piano (glifo)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Frame con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Cornice: mobile, con stato non attivo**|Bordo (glifo)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Frame con stato attivo selezionato](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Cornice: mobile, con stato attivo**|Sfondo (glifo)|`Environment.RaftedWindowButtonDown`|  
|![Frame con stato attivo selezionato](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Cornice: mobile, con stato attivo**|Primo piano (glifo)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Frame con stato attivo selezionato](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Cornice: mobile, con stato attivo**|Bordo (glifo)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Schede dei documenti  
 Le schede dei documenti si trovano nel canale delle schede per indicare i documenti attualmente aperti, insieme al documento selezionato o attivo corrente. Anche le finestre degli strumenti possono essere ancorate nel canale delle schede dei documenti se l'utente le aggiunge in questa posizione. In questo caso, usano gli stessi colori delle schede delle finestre dei documenti. Se si crea un'interfaccia utente che deve corrispondere sempre ai colori delle finestre dei documenti (inclusi gli aggiornamenti dei temi o se vengono installati nuovi temi), fare riferimento a questi token di colore.  
  
 ![Scheda Documento con linea rossa](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Usare…  
 In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle schede dei documenti e in cui gli aggiornamenti dei temi o nuovi colori dei temi vengono selezionati automaticamente.  
  
 Non usare...  
 Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.  
  
##### <a name="open-document-tabs"></a>Schede dei documenti aperti  
 Per ogni documento aperto è presente una scheda nel canale delle schede dei documenti che ne visualizza il nome. I documenti possono essere selezionati o aperti in background e le rispettive schede riflettono questi stati:  
  
- La scheda selezionata rappresenta il documento attualmente visualizzato nell'area dei documenti. Una scheda selezionata ha un bordo di documento che si estende fino al bordo superiore dell'area dei documenti.  
  
- Le schede di sfondo sono tutte le schede del documento che non sono la scheda attualmente selezionata. Una volta fatto clic, diventano la scheda selezionata e acquisiscono tutti i colori dello sfondo, del bordo e del testo da tali nomi di token.  
  
  ![Scheda Documento con linea rossa aperta](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Usare…  
  Quando si creano schede dei documenti personalizzate.  
  
  Non usare...  
  - Per schede provvisorie (anteprima).  
  
- Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.  
  
##### <a name="selected-tab"></a>Scheda selezionata  
 **Con stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda selezionata con stato attivo](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Scheda di documento selezionata, con stato attivo**|Background|`Environment.FileTabSelectedGradientTop`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Scheda selezionata con stato attivo](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Scheda di documento selezionata, con stato attivo**|Primo piano (testo)|`Environment.FileTabSelectedText`|  
|![Scheda selezionata con stato attivo](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Scheda di documento selezionata, con stato attivo**|Bordo|`Environment.FileTabSelectedBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
|![Scheda selezionata con stato attivo](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Scheda di documento selezionata, con stato attivo**|Bordo del documento|`Environment.FileTabDocumentBorderBackground`|  
  
 **Con stato non attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda selezionata con stato non attivo](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Scheda di documento selezionata, con stato non attivo**|Background|`Environment.FileTabInactiveGradientTop`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Scheda selezionata con stato non attivo](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Scheda di documento selezionata, con stato non attivo**|Primo piano (testo)|`Environment.FileTabInactiveText`|  
|![Scheda selezionata con stato non attivo](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Scheda di documento selezionata, con stato non attivo**|Bordo|`Environment.FileTabInactiveBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
|![Scheda selezionata con stato non attivo](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Scheda di documento selezionata, con stato non attivo**|Bordo del documento|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Scheda di sfondo  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Scheda di sfondo](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Impostazione predefinita della scheda in secondo piano**|Background|`Environment.FileTabBackground`|  
|![Scheda di sfondo](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Impostazione predefinita della scheda in secondo piano**|Primo piano (testo)|`Environment.FileTabText`|  
|![Scheda di sfondo](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Impostazione predefinita della scheda in secondo piano**|Bordo|`Environment.FileTabBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Scheda in secondo piano al passaggio del mouse](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Scheda in secondo piano al passaggio del mouse**|Background|`Environment.FileTabHotGradientTop`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Scheda in secondo piano al passaggio del mouse](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Scheda in secondo piano al passaggio del mouse**|Primo piano (testo)|`Environment.FileTabHotText`|  
|![Scheda in secondo piano al passaggio del mouse](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Scheda in secondo piano al passaggio del mouse**|Bordo|`Environment.FileTabHotBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
  
##### <a name="preview-tab"></a>Scheda anteprima  
 La scheda anteprima è visualizzata sul lato destro del canale delle schede dei documenti quando l'utente fa clic su un elemento nella finestra degli strumenti Esplora soluzione. Questa scheda funge da anteprima del documento e offre all'utente anche l'opzione di mantenere il documento aperto sul lato sinistro del canale delle schede dei documenti. Può essere aperta una sola scheda anteprima per volta. Le schede anteprima hanno sia uno sfondo sia stati selezionati, come le schede aperte, e possono avere stato attivo o non attivo quando sono attive.  
  
 ![Scheda Anteprima con linea rossa](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Usare…  
 In qualsiasi punto in cui si crea un'anteprima provvisoria e alcuni elementi devono corrispondere al colore della scheda anteprima.  
  
Non usare...  
- Per qualsiasi tipo di documento o scheda non provvisorio (anteprima).  

- Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.  
  
  **Scheda anteprima selezionata: stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda Anteprima con stato attivo](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Scheda anteprima con stato attivo**|Background|`Environment.FileTabProvisionalSelectedActive`|  
|![Scheda Anteprima con stato attivo](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Scheda anteprima con stato attivo**|Primo piano (testo)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Scheda Anteprima con stato attivo](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Scheda anteprima con stato attivo**|Bordo|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
|![Scheda Anteprima con stato attivo](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Scheda anteprima con stato attivo**|Bordo del documento|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Scheda anteprima selezionata: stato non attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda Anteprima con stato non attivo](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Scheda anteprima con stato non attivo**|Background|`Environment.FileTabProvisionalSelectedInactive`|  
|![Scheda Anteprima con stato non attivo](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Scheda anteprima con stato non attivo**|Primo piano (testo)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Scheda Anteprima con stato non attivo](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Scheda anteprima con stato non attivo**|Bordo|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Scheda Anteprima con stato non attivo](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Scheda anteprima con stato non attivo**|Bordo del documento|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Scheda anteprima di sfondo: predefinita**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda anteprima sfondo](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Scheda in secondo piano della scheda anteprima**|Background|`Environment.FileTabProvisionalInactive`|  
|![Scheda anteprima sfondo](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Scheda in secondo piano della scheda anteprima**|Primo piano (testo)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Scheda anteprima sfondo](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Scheda in secondo piano della scheda anteprima**|Bordo|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
  
 **Scheda anteprima in secondo piano: passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda anteprima sfondo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Scheda in secondo piano della scheda di anteprima al passaggio del mouse**|Background|`Environment.FileTabProvisionalHover`|  
|![Scheda anteprima sfondo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Scheda in secondo piano della scheda di anteprima al passaggio del mouse**|Primo piano (testo)|`Environment.FileTabProvisionalHoverForeground`|  
|![Scheda anteprima sfondo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Scheda in secondo piano della scheda di anteprima al passaggio del mouse**|Bordo|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
  
##### <a name="document-overflow-button"></a>Pulsante di overflow dei documenti  
 Il pulsante di overflow dei documenti è presente se ci sono uno o più documenti aperti, indipendentemente dal fatto che nella configurazione corrente sia disponibile spazio sufficiente da contenere tutte le schede dei documenti. Il menu a discesa di overflow dei documenti, controllato dai colori di **CommandBarMenu** (vedere [Menus](../misc/shared-colors.md#BKMK_CommandMenus)), visualizza un elenco di tutti i documenti aperti, sia visibili sia nascosti, e il glifo di overflow cambia a seconda che tutti i documenti aperti siano o meno visualizzati nel canale delle schede.  
  
 ![Overflow con linea rossa](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Usare…  
Quando si crea un pulsante di overflow dei documenti personalizzato.  

Non usare...  
- Per un'interfaccia utente che non è simile a un pulsante di overflow.  

- Per i pulsanti di overflow della barra dei comandi.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Pulsante di overflow dei documenti**|Background|`Environment.DocWellOverflowButtonBackground`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Pulsante di overflow dei documenti**|Primo piano (glifo)|`Environment.DocWellOverflowButtonGlyph`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Pulsante di overflow dei documenti**|Bordo|N/D|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Overflow al passaggio del mouse](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Pulsante di overflow dei documenti al passaggio del mouse**|Background|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Overflow al passaggio del mouse](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Pulsante di overflow dei documenti al passaggio del mouse**|Primo piano (glifo)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Overflow al passaggio del mouse](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Pulsante di overflow dei documenti al passaggio del mouse**|Bordo|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Overflow selezionato](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Pulsante di overflow dei documenti premuto**|Background|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Overflow selezionato](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Pulsante di overflow dei documenti premuto**|Primo piano (glifo)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Overflow selezionato](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Pulsante di overflow dei documenti premuto**|Bordo|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Finestre degli strumenti  
 Non è necessario replicare le finestre degli strumenti, perché vengono fornite dall'ambiente di Visual Studio. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre degli strumenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.  
  
 ![Finestra degli strumenti con linea rossa](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Usare…  
 In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.  
  
 Non usare...  
 Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.  
  
#### <a name="tool-window-frame"></a>Cornice delle finestre degli strumenti  
 Le finestre degli strumenti in Visual Studio vengono usate per molte attività diverse e possono avere stati diversi. Se una finestra degli strumenti è aperta, può essere assegnata a uno qualsiasi dei quattro lati dell'area del documento. Le finestre degli strumenti possono anche essere mobili al di fuori dell'IDE, per poter essere riposizionate in qualsiasi punto dello schermo dell'utente. Le finestre mobili sono sempre in primo piano nell'IDE. Infine, le finestre degli strumenti possono essere ancorate come finestre dei documenti ed essere visualizzate come scheda nell'area dei documenti. Le finestre degli strumenti ancorate come finestre dei documenti vengono colorate in parte usando i nomi di token delle finestre dei documenti.  
  
 ![Frame finestra degli strumenti con linea rossa](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Usare…  
 In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.  
  
 Non usare...  
 Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.  
  
 **Ancorato**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Finestra degli strumenti ancorata](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Background|`Environment.ToolWindowBackground`|  
|![Finestra degli strumenti ancorata](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Bordo|`Environment.ToolWindowBorder`|  
  
 **Mobile: con stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Finestra degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Background|`Environment.ToolWindowBackground`|  
|![Finestra degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Bordo|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Mobile: con stato non attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Finestra degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Background|`Environment.ToolWindowBackground`|  
|![Finestra degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Bordo|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Barra del titolo delle finestre degli strumenti  
 Il bordo della barra del titolo non è un bordo vero e proprio, ma una linea spessa lungo la parte superiore della barra del titolo. Questo elemento non ha un nome di token per il proprio stato non attivo.  
  
 ![Barra del titolo della finestra degli strumenti con linea rossa](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Usare…  
 In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.  
  
 Non usare...  
 Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.  
  
 **Con stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra del titolo con stato attivo](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra del titolo con stato attivo**|Background|`Environment.TitleBarActiveGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Barra del titolo con stato attivo](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra del titolo con stato attivo**|Primo piano (testo)|`Environment.TitleBarActiveText`|  
|![Barra del titolo con stato attivo](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra del titolo con stato attivo**|Bordo|`Environment.TitleBarActiveBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
|![Barra del titolo con stato attivo](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra del titolo con stato attivo**|Quadratino di trascinamento|`Environment.TitleBarDragHandleActive`|  
  
 **Con stato non attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra del titolo con stato non attivo](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra del titolo con stato non attivo**|Background|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Barra del titolo con stato non attivo](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra del titolo con stato non attivo**|Primo piano (testo)|`Environment.TitleBarInactiveText`|  
|![Barra del titolo con stato non attivo](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra del titolo con stato non attivo**|Bordo|N/D|  
|![Barra del titolo con stato non attivo](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra del titolo con stato non attivo**|Quadratino di trascinamento|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Pulsanti della barra del titolo  
 ![Pulsante della barra del titolo con linea rossa](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Usare…  
 Per i pulsanti visualizzati nell'interfaccia utente che usa token di colore della barra del titolo delle finestre degli strumenti.  
  
Non usare...  
- Per i pulsanti visualizzati in altre posizioni.  

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante della barra del titolo con stato attivo](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Con stato attivo**|Background|N/D|  
|![Pulsante della barra del titolo con stato attivo](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Con stato attivo**|Primo piano (glifo)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Pulsante della barra del titolo con stato attivo](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Con stato attivo**|Bordo|N/D|  
|![Pulsante della barra del titolo non stato attivo](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Con stato non attivo**|Background|N/D|  
|![Pulsante della barra del titolo non stato attivo](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Con stato non attivo**|Primo piano (glifo)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Pulsante della barra del titolo non stato attivo](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Con stato non attivo**|Bordo|N/D|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante della barra del titolo con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Con stato attivo**|Background|`Environment.ToolWindowButtonHoverActive`|  
|![Pulsante della barra del titolo con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Con stato attivo**|Primo piano (glifo)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Pulsante della barra del titolo con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Con stato attivo**|Bordo|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Pulsante della barra del titolo con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Con stato non attivo**|Background|`Environment.ToolWindowButtonHoverInactive`|  
|![Pulsante della barra del titolo con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Con stato non attivo**|Primo piano (glifo)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Pulsante della barra del titolo con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Con stato non attivo**|Bordo|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante della barra del titolo con stato attivo e selezionato](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Con stato attivo**|Background|`Environment.ToolWindowButtonDown`|  
|![Pulsante della barra del titolo con stato attivo e selezionato](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Con stato attivo**|Primo piano (glifo)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Pulsante della barra del titolo con stato attivo e selezionato](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Con stato attivo**|Bordo|`Environment.ToolWindowButtonDownBorder`|  
|![Pulsante della barra del titolo con stato non attivo e selezionato](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Con stato non attivo**|Background|`Environment.ToolWindowButtonDown`|  
|![Pulsante della barra del titolo con stato non attivo e selezionato](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Con stato non attivo**|Primo piano (glifo)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Pulsante della barra del titolo con stato non attivo e selezionato](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Con stato non attivo**|Bordo|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Schede delle finestre degli strumenti  
 ![Barra degli strumenti della scheda Redline](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Usare…  
 In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle finestre degli strumenti.  
  
 Non usare...  
 Per qualsiasi interfaccia utente che non deve cambiare automaticamente se la shell include un aggiornamento del tema.  
  
 **Scheda selezionata**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda della finestra degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Scheda della finestra degli strumenti con stato attivo selezionata**|Background|`Environment.ToolWindowTabSelectedTab`|  
|![Scheda della finestra degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Scheda della finestra degli strumenti con stato attivo selezionata**|Primo piano (testo)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Scheda della finestra degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Scheda della finestra degli strumenti con stato attivo selezionata**|Bordo|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda della finestra degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Scheda della finestra degli strumenti con stato non attivo selezionata**|Background|`Environment.ToolWindowTabSelectedTab`|  
|![Scheda della finestra degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Scheda della finestra degli strumenti con stato non attivo selezionata**|Primo piano (testo)|`Environment.ToolWindowTabSelectedText`|  
|![Scheda della finestra degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Scheda della finestra degli strumenti con stato non attivo selezionata**|Bordo|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
  
 **Scheda di sfondo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda sfondo della finestra degli strumenti](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Scheda della finestra degli strumenti in secondo piano**|Background|`Environment.ToolWindowTabGradientBegin`<br /><br /> Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.|  
|![Scheda sfondo della finestra degli strumenti](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Scheda della finestra degli strumenti in secondo piano**|Primo piano (testo)|`Environment.ToolWindowTabText`|  
|![Scheda sfondo della finestra degli strumenti](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Scheda della finestra degli strumenti in secondo piano**|Bordo|`Environment.ToolWindowTabBorder`|  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda sfondo della finestra degli strumenti al passaggio del mouse](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Scheda della finestra degli strumenti in secondo piano al passaggio del mouse**|Background|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.|  
|![Scheda sfondo della finestra degli strumenti al passaggio del mouse](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Scheda della finestra degli strumenti in secondo piano al passaggio del mouse**|Primo piano (testo)|`Environment.ToolWindowTabMouseOverText`|  
|![Scheda sfondo della finestra degli strumenti al passaggio del mouse](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Scheda della finestra degli strumenti in secondo piano al passaggio del mouse**|Bordo|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Impostato sullo stesso colore dello sfondo.|  
  
#### <a name="auto-hide-tabs"></a>Schede Nascondi automaticamente  
 ![&#45;nascondi linea rossa](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Usare…  
 In qualsiasi punto in cui si crea un'interfaccia utente che deve corrispondere alle schede delle finestre degli strumenti Nascondi automaticamente.  
  
 Non usare...  
 Per qualsiasi interfaccia utente che non deve automaticamente cambiare se la shell prevede un aggiornamento del tema.  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Scheda Nascondi automaticamente&#45;](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Scheda Nascondi automaticamente predefinita**|Background|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Scheda Nascondi automaticamente&#45;](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Scheda Nascondi automaticamente predefinita**|Primo piano (testo)|`Environment.AutoHideTabText`|  
|![Scheda Nascondi automaticamente&#45;](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Scheda Nascondi automaticamente predefinita**|Bordo|`Environment.AutoHideTabBorder`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Automaticamente&#45;nascondere la scheda al passaggio del mouse](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Scheda Nascondi automaticamente al passaggio del mouse**|Background|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Automaticamente&#45;nascondere la scheda al passaggio del mouse](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Scheda Nascondi automaticamente al passaggio del mouse**|Primo piano (testo)|`Environment.AutoHideTabMouseOverText`|  
|![Automaticamente&#45;nascondere la scheda al passaggio del mouse](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Scheda Nascondi automaticamente al passaggio del mouse**|Bordo|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Controlli condivisi comuni  
 Quando si usa una barra dei comandi di Visual Studio standard nella propria funzionalità, è possibile accedere a controlli della shell con stile e non è consigliabile reimpostare come modelli questi controlli comuni. Tuttavia, se si intende compilare una barra dei comandi personalizzata, potrebbe essere necessario compilare anche controlli personalizzati. In questo caso, assicurarsi di usare i nomi di token corretti per ognuno dei controlli seguenti, in modo che l'interfaccia utente sia coerente con il resto di Visual Studio.  
  
#### <a name="search-box"></a>Casella Cerca  
 Quando è possibile, usare il controllo di ricerca comune fornito dall'ambiente di Visual Studio. I colori della casella di ricerca si trovano nella categoria "SearchControl" nel file **ShellColors.pkgdef** , che contiene i nomi di token per il campo di input, il pulsante di azione, il pulsante a discesa e il menu a discesa.  
  
 Una casella di ricerca può avere diversi stati, alcuni dei quali si escludono a vicenda:  
  
- "Con stato attivo" e "con stato non attivo" indicano se il cursore si trova o meno nella casella di testo.  
  
- "Attivo" e "inattivo" indicano se l'utente ha inserito una query di ricerca nella casella di testo.  
  
- "Passaggio del mouse" significa che l'utente ha posizionato il cursore del mouse sulla casella di ricerca (questo stato sostituisce tutti gli altri).  
  
- "Disabilitato" significa che la funzionalità di ricerca è disattivata per il contesto corrente.  
  
  ![Casella di ricerca con linea rossa](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Usare…  
  Quando si progetta una casella di ricerca personalizzata.  
  
  Non usare...  
  - Per qualsiasi elemento diverso da una casella di ricerca.  
  
- Per qualsiasi elemento che non deve corrispondere sempre all'interfaccia utente della casella di ricerca.  
  
  **Con stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo di input di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo di input**|Background|`SearchControl.FocusedBackground`|  
|![Campo di input di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo di input**|Primo piano (testo)|`SearchControl.FocusedBackground`|  
|![Campo di input di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo di input**|Bordo|`SearchControl.FocusedBorder`|  
|![Campo di input di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo di input**|Separatore|`SearchControl.FocusedDropDownSeparator`|  
|![Pulsante di azione di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Pulsante Azione**|Background|nessuno|  
|![Pulsante di azione di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Pulsante Azione**|Primo piano (glifo Cerca)|`SearchControl.SearchGlyph`|  
|![Pulsante di azione di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Pulsante Azione**|Primo piano (glifo Arresta)|`SearchControl.StopGlyph`|  
|![Pulsante di azione di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Pulsante Azione**|Primo piano (glifo Cancella)|`SearchControl.ClearGlyph`|  
|![Pulsante di azione di ricerca con stato attivo](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Pulsante Azione**|Bordo|N/D|  
|![Pulsante&#45;a discesa di ricerca attivo](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Pulsante a discesa**|Background|`SearchControl.FocusedDropDownButton`|  
|![Pulsante&#45;a discesa di ricerca attivo](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Pulsante&#45;a discesa di ricerca attivo](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Pulsante a discesa**|Bordo|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Con stato non attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo di input di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo di input attivo**|Background|`SearchControl.SearchActiveBackground`|  
|![Campo di input di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo di input attivo**|Primo piano (testo)|`SearchControl.SearchActiveBackground`|  
|![Campo di input di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo di input attivo**|Bordo|`SearchControl.UnfocusedBorder`|  
|![Campo di input di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo di input attivo**|Separatore|`SearchControl.DropDownSeparator`|  
|![Campo di input di ricerca con stato non attivo e inattivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo di input inattivo**|Background|`SearchControl.Unfocused`|  
|![Campo di input di ricerca con stato non attivo e inattivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo di input inattivo**|Primo piano (testo)|`SearchControl.Unfocused`|  
|![Campo di input di ricerca con stato non attivo e inattivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo di input inattivo**|Bordo|`SearchControl.UnfocusedBorder`|  
|![Campo di input di ricerca con stato non attivo e inattivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo di input inattivo**|Separatore|`SearchControl.DropDownSeparator`|  
|![Pulsante di azione di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Pulsante Azione**|Background|N/D|  
|![Pulsante di azione di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Pulsante Azione**|Primo piano (glifo Cerca)|`SearchControl.SearchGlyph`|  
|![Pulsante di azione di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Pulsante Azione**|Primo piano (glifo Arresta)|`SearchControl.StopGlyph`|  
|![Pulsante di azione di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Pulsante Azione**|Primo piano (glifo Cancella)|`SearchControl.ClearGlyph`|  
|![Pulsante di azione di ricerca con stato non attivo](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Pulsante Azione**|Bordo|N/D|  
|![Menu a discesa Cerca&#45;pulsante giù non stato acletterato](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Pulsante a discesa**|Background|`SearchControl.UnfocusedDropDownButton`|  
|![Menu a discesa Cerca&#45;pulsante giù non stato acletterato](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Menu a discesa Cerca&#45;pulsante giù non stato acletterato](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Pulsante a discesa**|Bordo|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante di azione di ricerca selezionato](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Pulsante Azione**|Background|`SearchControl.ActionButtonMouseDown`|  
|![Pulsante di azione di ricerca selezionato](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Pulsante Azione**|Primo piano (glifo)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Pulsante di azione di ricerca selezionato](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Pulsante Azione**|Bordo|`SearchControl.ActionButtonMouseDownBorder`|  
|![Pulsante a discesa di ricerca&#45;premuto](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Pulsante a discesa**|Background|`SearchControl.MouseDownDropDownButton`|  
|![Pulsante a discesa di ricerca&#45;premuto](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Pulsante a discesa di ricerca&#45;premuto](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Pulsante a discesa**|Bordo|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Evidenziato (solo testo)**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo di input di ricerca evidenziato](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo di input con testo evidenziato**|Background|`SearchControl.Selection`|  
|![Campo di input di ricerca evidenziato](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo di input con testo evidenziato**|Primo piano (testo)|`SearchControl.FocusedBackground`|  
|![Campo di input di ricerca evidenziato](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo di input con testo evidenziato**|Bordo|nessuno|  
|![Campo di input di ricerca evidenziato](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo di input con testo evidenziato**|Separatore|`SearchControl.FocusedDropDownSeparator`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo di input di ricerca disabilitato](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo di input**|Background|`SearchControl.Disabled`|  
|![Campo di input di ricerca disabilitato](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo di input**|Primo piano (testo)|`SearchControl.Disabled`|  
|![Campo di input di ricerca disabilitato](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo di input**|Bordo|`SearchControl.DisabledBorder`|  
|![Campo di input di ricerca disabilitato](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo di input**|Separatore|`SearchControl.DropDownSeparator`|  
|![Pulsante di azione di ricerca disabilitato](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Pulsante Azione**|Background|nessuno|  
|![Pulsante di azione di ricerca disabilitato](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Pulsante Azione**|Primo piano (glifo)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Pulsante di azione di ricerca disabilitato](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Pulsante Azione**|Bordo|nessuno|  
|![Pulsante a discesa di ricerca&#45;verso il basso disabilitato](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Pulsante a discesa**|Background|nessuno|  
|![Pulsante a discesa di ricerca&#45;verso il basso disabilitato](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Pulsante a discesa**|Primo piano (glifo)|`SearchControl.DisabledDownButtonGlyph`|  
|![Pulsante a discesa di ricerca&#45;verso il basso disabilitato](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Pulsante a discesa**|Bordo|nessuno|  
  
##### <a name="search-drop-down-lists"></a>Elenchi a discesa di ricerca  
 Il menu a discesa della casella di ricerca può essere leggermente più complesso rispetto ad altri menu a discesa in Visual Studio. Le sezioni "ricerche suggerite" e "opzioni di ricerca" possono essere visualizzate singolarmente o insieme nel menu e ognuna ha un colore diverso. Una linea separa le due sezioni quando sono visualizzate insieme e un bordo circonda l'intero menu a discesa.  
  
 ![menu a discesa di ricerca&#45;linea rossa](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Usare…  
- Quando si crea un elenco a discesa di ricerca personalizzato.  

- I nomi di token appropriati per i componenti dell'elenco corretti.  

Non usare...  
- Per elenchi a discesa visualizzati in altri contesti.  

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.  
  
  **Predefinito (nessun altro stato)**  
  
|Elemento|Nome token: Category.color|  
|-------------|--------------------------------|  
|Bordo|`SearchControl.PopupBorder`|  
|Separatore|`SearchControl.PopupSectionHeaderSeparator`|  
|Shadow|`Environment.DropShadowBackground`|  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ricerca con suggerimento](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Ricerche suggerite**|Background|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Ricerca con suggerimento](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Ricerche suggerite**|Primo piano (testo)|`SearchControl.PopupItemText`|  
|![Casella di controllo di ricerca](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opzioni di ricerca (casella di controllo)**|Background|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Opzioni di ricerca](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opzioni di ricerca (collegamento)**|Background|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Casella di controllo di ricerca](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opzioni di ricerca (casella di controllo)**|Primo piano (testo della casella di controllo)|`SearchControl.PopupCheckboxText`|  
|![Opzioni di ricerca](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opzioni di ricerca (collegamento)**|Primo piano (testo della casella di controllo)|`SearchControl.PopupCheckboxText`|  
|![Casella di controllo di ricerca](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opzioni di ricerca (casella di controllo)**|Primo piano (testo del collegamento)|`SearchControl.PopupButtonText`|  
|![Opzioni di ricerca](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opzioni di ricerca (collegamento)**|Primo piano (testo del collegamento)|`SearchControl.PopupButtonText`|  
|![Casella di controllo di ricerca](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opzioni di ricerca (casella di controllo)**|Sfondo dell'intestazione|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Opzioni di ricerca](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opzioni di ricerca (collegamento)**|Sfondo dell'intestazione|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Casella di controllo di ricerca](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opzioni di ricerca (casella di controllo)**|Primo piano (testo dell'intestazione)|`SearchControl.PopupSectionHeaderText`|  
|![Opzioni di ricerca](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opzioni di ricerca (collegamento)**|Primo piano (testo dell'intestazione)|`SearchControl.PopupSectionHeaderText`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ricerca con suggerimento al passaggio del mouse](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Ricerche suggerite**|Background|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Ricerca con suggerimento al passaggio del mouse](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Ricerche suggerite**|Primo piano (testo)|`SearchControl.PopupMouseOverItemText`|  
|![Ricerca con suggerimento al passaggio del mouse](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Ricerche suggerite**|Bordo|`SearchControl.PopupControlMouseOverBorder`|  
|![Casella di controllo di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Ricerche suggerite (casella di controllo)**|Background|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Opzioni di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opzioni di ricerca**|Background|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Casella di controllo di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Ricerche suggerite (casella di controllo)**|Primo piano (testo della casella di controllo)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opzioni di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opzioni di ricerca**|Primo piano (testo della casella di controllo)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Casella di controllo di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Ricerche suggerite (casella di controllo)**|Primo piano (testo del collegamento)|`SearchControl.PopupButtonMouseDownText`|  
|![Opzioni di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opzioni di ricerca**|Primo piano (testo del collegamento)|`SearchControl.PopupButtonMouseDownText`|  
|![Casella di controllo di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Ricerche suggerite (casella di controllo)**|Bordo|`SearchControl.PopupControlMouseOverBorder`|  
|![Opzioni di ricerca al passaggio del mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opzioni di ricerca**|Bordo|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ricerca con suggerimento selezionata](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Ricerche suggerite (casella di controllo)**|Sfondo della casella di controllo|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Opzioni di ricerca selezionate](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opzioni di ricerca**|Sfondo della casella di controllo|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Ricerca con suggerimento selezionata](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Ricerche suggerite (casella di controllo)**|Sfondo della casella di controllo|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Opzioni di ricerca selezionate](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opzioni di ricerca**|Sfondo della casella di controllo|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Ricerca con suggerimento selezionata](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Ricerche suggerite (casella di controllo)**|Primo piano (testo della casella di controllo)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opzioni di ricerca selezionate](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opzioni di ricerca**|Primo piano (testo della casella di controllo)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Ricerca con suggerimento selezionata](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Ricerche suggerite (casella di controllo)**|Sfondo del collegamento|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Opzioni di ricerca selezionate](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opzioni di ricerca**|Sfondo del collegamento|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Benché non sia usato nella moderna interfaccia utente con temi, per questo sfondo sono disponibili cursori sfumatura e valori.|  
|![Ricerca con suggerimento selezionata](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Ricerche suggerite (casella di controllo)**|Primo piano (testo del collegamento)|`SearchControl.PopupButtonMouseDownText`|  
|![Opzioni di ricerca selezionate](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opzioni di ricerca**|Primo piano (testo del collegamento)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 Il collegamento ipertestuale è un controllo che non ha una coppia primo piano/sfondo. In tutti i casi, usare il colore primo piano del collegamento ipertestuale, visualizzato correttamente su sfondi scuri, grigi e bianchi. Se non si usa il token di colore per il controllo collegamento ipertestuale, verrà visualizzato il controllo di sistema predefinito per lo stato "premuto", che sarà di colore rosso lampeggiante. Questo comportamento segnala il fatto che il controllo non usa il token di colore dell'ambiente corretto.  
  
 ![Collegamento ipertestuale con linea rossa](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Usare…  
 Quando è necessario creare un collegamento ipertestuale personalizzato.  
  
 Non usare...  
 Per qualsiasi elemento diverso da un collegamento ipertestuale.  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Collegamento ipertestuale predefinito](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Primo piano (testo)|`Environment.PanelHyperlink`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Collegamento ipertestuale al passaggio del mouse](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Primo piano (testo)|`Environment.PanelHyperlinkHover`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Collegamento ipertestuale selezionato](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Primo piano (testo)|`Environment.PanelHyperlinkPressed`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Collegamento ipertestuale disabilitato](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Primo piano (testo)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Barra informazioni  
 Le barre informazioni vengono usate per fornire altre informazioni su un contesto specifico e sono sempre visualizzate nella parte superiore della finestra di un documento o di una finestra degli strumenti.  
  
 ![Barra informazioni con linea rossa](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Usare…  
 Quando si creano barre informazioni personalizzate.  
  
 Non usare...  
 Per gli elementi dell'interfaccia utente che non sono simili a una barra informazioni.  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra informazioni](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra informazioni**|Background|`Environment.InfoBackground`|  
|![Barra informazioni](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra informazioni**|Primo piano (testo)|`Environment.InfoText`|  
|![Barra informazioni](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra informazioni**|Bordo|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Barra di scorrimento  
 Le barre di scorrimento hanno uno stile che riflette l'ambiente di Visual Studio e non è necessario applicarvi un tema. Tuttavia, è possibile decidere che si desidera sfruttare i colori utilizzati nelle barre di scorrimento in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.However, you might decide that you want to leverage the colors used in scroll bars so that your UI always appears consistent with this part of the Visual Studio environment.  
  
 ![Barra di scorrimento con linea rossa](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Usare…  
 Quando si crea un'interfaccia utente che deve corrispondere alle barre di scorrimento di Visual Studio.  
  
 Non usare...  
 Per qualsiasi elemento che non deve corrispondere sempre all'interfaccia utente delle barre di scorrimento.  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra di scorrimento](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Barra di scorrimento|`Environment.ScrollBarBackground`|  
|![Barra di scorrimento](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Primo piano (anteprima)|`Environment.ScrollBarThumbBackground`|  
|![Freccia della barra di scorrimento](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Freccia di scorrimento**|Background|`Environment.ScrollBarArrowBackground`<br /><br /> Impostato sullo stesso colore della barra di scorrimento.|  
|![Freccia della barra di scorrimento](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Freccia di scorrimento**|Primo piano (glifo)|`Environment.ScrollBarArrowGlyph`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra di scorrimento al passaggio del mouse](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Barra di scorrimento|`Environment.ScrollBarBackground`|  
|![Barra di scorrimento al passaggio del mouse](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Primo piano (anteprima)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Freccia della barra di scorrimento al passaggio del mouse](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Freccia di scorrimento**|Background|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Impostato sullo stesso colore della barra di scorrimento.|  
|![Freccia della barra di scorrimento al passaggio del mouse](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Freccia di scorrimento**|Primo piano (glifo)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra di scorrimento selezionata](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Barra di scorrimento|`Environment.ScrollBarBackground`|  
|![Barra di scorrimento selezionata](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Primo piano (anteprima)|`Environment.ScrollBarThumbPressedBackground`|  
|![Freccia della barra di scorrimento selezionata](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Freccia di scorrimento**|Background|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Impostato sullo stesso colore della barra di scorrimento.|  
|![Freccia della barra di scorrimento selezionata](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Freccia di scorrimento**|Primo piano (glifo)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Vista ad albero  
 Diverse finestre degli strumenti, tra cui Esplora soluzioni, Esplora server e Visualizzazione classi, implementano uno schema organizzativo gerarchico i cui colori sono controllati dai nomi di colore nella categoria TreeView. Tutti gli elementi in una visualizzazione albero hanno colori di sfondo e del testo. Gli elementi che hanno elementi figlio annidati hanno anche glifi che indicano se ogni elemento è espanso o compresso.  
  
 ![Visualizzazione albero con linea rossa](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Usare…  
 In qualsiasi punto in cui è necessario implementare una visualizzazione organizzativa gerarchica.  
  
Non usare...  
- Per qualsiasi elemento che non è simile a una visualizzazione albero.  

- In qualsiasi combinazione sfondo/primo piano diversa da quella specificata.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista ad albero](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Background|`TreeView.Background`|  
|![Vista ad albero](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Primo piano (testo)|`TreeView.Background`|  
|![Vista ad albero](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Primo piano (glifo)|`TreeView.Glyph`|  
|![Vista ad albero](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Bordo|nessuno|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Visualizzazione albero al passaggio del mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Background|`TreeView.Background`|  
|![Visualizzazione albero al passaggio del mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Primo piano (testo)|`TreeView.Background`|  
|![Visualizzazione albero al passaggio del mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Primo piano (glifo)|`TreeView.GlyphMouseOver`|  
|![Visualizzazione albero al passaggio del mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Bordo|nessuno|  
  
 **Trascinamento sull'elemento**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Visualizzazione albero con trascinamento](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Background|`TreeView.DragOverItem`|  
|![Visualizzazione albero con trascinamento](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Primo piano (testo)|`TreeView.DragOverItem`|  
|![Visualizzazione albero con trascinamento](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Primo piano (glifo)|`TreeView.DragOverItemGlyph`|  
|![Visualizzazione albero con trascinamento](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Bordo|nessuno|  
  
 **Selezionato**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Visualizzazione albero con stato attivo](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Con stato attivo**|Background|`TreeView.SelectedItemActive`|  
|![Visualizzazione albero con stato attivo](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Con stato attivo**|Primo piano (testo)|`TreeView.SelectedItemActive`|  
|![Visualizzazione albero con stato attivo](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Con stato attivo**|Primo piano (glifo)|`TreeView.SelectedItemActiveGlyph`|  
|![Visualizzazione albero con stato attivo](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Con stato attivo**|Bordo|`TreeView.FocusVisualBorder`|  
|![Visualizzazione albero con stato non attivo](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Con stato non attivo**|Background|`TreeView.SelectedItemInactive`|  
|![Visualizzazione albero con stato non attivo](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Con stato non attivo**|Primo piano (testo)|`TreeView.SelectedItemInactive`|  
|![Visualizzazione albero con stato non attivo](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Con stato non attivo**|Primo piano (glifo)|`TreeView.SelectedItemInactiveGlyph`|  
|![Visualizzazione albero con stato non attivo](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Con stato non attivo**|Bordo|nessuno|  
  
 **Passaggio del mouse sull'elemento selezionato**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Visualizzazione albero con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Con stato attivo**|Background|`TreeView.SelectedItemActive`|  
|![Visualizzazione albero con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Con stato attivo**|Primo piano (testo)|`TreeView.SelectedItemActive`|  
|![Visualizzazione albero con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Con stato attivo**|Primo piano (glifo)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Visualizzazione albero con stato attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Con stato attivo**|Bordo|Nessuno`TreeView.FocusVisualBorder`|  
|![Visualizzazione albero con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Con stato non attivo**|Background|`TreeView.SelectedItemInactive`|  
|![Visualizzazione albero con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Con stato non attivo**|Primo piano (testo)|`TreeView.SelectedItemInactive`|  
|![Visualizzazione albero con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Con stato non attivo**|Primo piano (glifo)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Visualizzazione albero con stato non attivo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Con stato non attivo**|Bordo|nessuno|  
  
#### <a name="button-controls"></a>Controlli pulsante  
 ![Controllo pulsante con linea rossa](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Usare…  
 Per i pulsanti nell'area dei documenti da integrare con temi di Visual Studio (Chiaro, Scuro, Blu o un tema Contrasto elevato di sistema).  
  
 Non usare...  
 Per i pulsanti che verranno visualizzati su uno sfondo personalizzato che non fa parte di un tema di Visual Studio.  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Pulsante|`CommonControls.Button`|  
|![Pulsante](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Bordo del pulsante|`CommonControls.ButtonBorder`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante disabilitato](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Pulsante|`CommonControls.ButtonDisabled`|  
|![Pulsante disabilitato](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Bordo del pulsante|`CommonControls.ButtonBorderDisabled`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante al passaggio del mouse](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Pulsante|`CommonControls.ButtonHover`|  
|![Pulsante al passaggio del mouse](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Bordo del pulsante|`CommonControls.ButtonBorderHover`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante selezionato](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Pulsante|`CommonControls.ButtonPressed`|  
|![Pulsante selezionato](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Bordo del pulsante|`CommonControls.ButtonBorderPressed`|  
  
 **Con stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pulsante con stato attivo](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Pulsante|`CommonControls.ButtonFocused`|  
|![Pulsante con stato attivo](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Bordo del pulsante|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Controlli casella di controllo  
 ![Casella di controllo con linea rossa](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Usare…  
 Per controlli casella di controllo contenuti nell'area dei documenti.  
  
 Non usare...  
 Per qualsiasi interfaccia utente diversa da un controllo casella di controllo.  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casella di controllo](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Background|`CommonControls.CheckBoxBackground`|  
|![Casella di controllo](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Bordo|`CommonControls.CheckBoxBorder`|  
|![Casella di controllo](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Text|`CommonControls.CheckBoxText`|  
|![Casella di controllo](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Icona|`CommonControls.CheckBoxGlyph`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casella di controllo disabilitata](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Background|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Casella di controllo disabilitata](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Bordo|`CommonControls.CheckBoxBorderDisabled`|  
|![Casella di controllo disabilitata](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Text|`CommonControls.CheckBoxTextDisabled`|  
|![Casella di controllo disabilitata](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Icona|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casella di controllo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Background|`CommonControls.CheckBoxBackgroundHover`|  
|![Casella di controllo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Bordo|`CommonControls.CheckBoxBorderHover`|  
|![Casella di controllo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Text|`CommonControls.CheckBoxTextHover`|  
|![Casella di controllo al passaggio del mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Icona|`CommonControls.CheckBoxGlyphHover`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casella di controllo selezionata](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Background|`CommonControls.CheckBoxBackgroundPressed`|  
|![Casella di controllo selezionata](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Bordo|`CommonControls.CheckBoxBorderPressed`|  
|![Casella di controllo selezionata](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Text|`CommonControls.CheckBoxTextPressed`|  
|![Casella di controllo selezionata](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Icona|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Con stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casella di controllo con stato attivo](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Background|`CommonControls.CheckBoxBackgroundFocused`|  
|![Casella di controllo con stato attivo](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Bordo|`CommonControls.CheckBoxBorderFocused`|  
|![Casella di controllo con stato attivo](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Text|`CommonControls.CheckBoxTextFocused`|  
|![Casella di controllo con stato attivo](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Icona|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Controlli casella combinata/casella di riepilogo a discesa  
 ![Abbassare&#45;la linea rossa&#47;casella combinata](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Usare…  
Per elenchi a discesa e caselle combinate che fanno parte dell'area dei documenti.  

Non usare...  
- Per qualsiasi interfaccia utente diversa da un elenco a discesa o una casella combinata.  

- Per un controllo [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) o [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox) nella barra dei comandi.  
  
  **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fare clic su&#45;&#47;casella combinata casella combinata](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Background|`CommonControls.ComboBoxBackground`|  
|![Fare clic su&#45;&#47;casella combinata casella combinata](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Bordo|`CommonControls.ComboBoxBorder`|  
|![Fare clic su&#45;&#47;casella combinata casella combinata](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Text|`CommonControls.ComboBoxText`|  
|![Fare clic su&#45;&#47;casella combinata casella combinata](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Separatore|`CommonControls.ComboBoxSeparator`|  
|![Fare clic su&#45;&#47;casella combinata casella combinata](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Icona|`CommonControls.ComboBoxGlyph`|  
|![Fare clic su&#45;&#47;casella combinata casella combinata](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Sfondo del glifo|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Disabili**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Elenco a&#45;discesa&#47;casella combinata disabilitata](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Background|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Elenco a&#45;discesa&#47;casella combinata disabilitata](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Bordo|`CommonControls.ComboBoxBorderDisabled`|  
|![Elenco a&#45;discesa&#47;casella combinata disabilitata](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Text|`CommonControls.ComboBoxTextDisabled`|  
|![Elenco a&#45;discesa&#47;casella combinata disabilitata](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Separatore|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Elenco a&#45;discesa&#47;casella combinata disabilitata](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Icona|`CommonControls.ComboBoxGlyphDisabled`|  
|![Elenco a&#45;discesa&#47;casella combinata disabilitata](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Sfondo del glifo|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rilascia&#45;casella combinata&#47;al passaggio del mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Background|`CommonControls.ComboBoxBackgroundHover`|  
|![Rilascia&#45;casella combinata&#47;al passaggio del mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Bordo|`CommonControls.ComboBoxBorderHover`|  
|![Rilascia&#45;casella combinata&#47;al passaggio del mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Text|`CommonControls.ComboBoxTextHover`|  
|![Rilascia&#45;casella combinata&#47;al passaggio del mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Separatore|`CommonControls.ComboBoxSeparatorHover`|  
|![Rilascia&#45;casella combinata&#47;al passaggio del mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Icona|`CommonControls.ComboBoxGlyphHover`|  
|![Rilascia&#45;casella combinata&#47;al passaggio del mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Sfondo del glifo|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;casella combinata&#47;premuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Background|`CommonControls.ComboBoxBackgroundPressed`|  
|![&#45;casella combinata&#47;premuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Bordo|`CommonControls.ComboBoxBorderPressed`|  
|![&#45;casella combinata&#47;premuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Text|`CommonControls.ComboBoxTextPressed`|  
|![&#45;casella combinata&#47;premuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Separatore|`CommonControls.ComboBoxSeparatorPressed`|  
|![&#45;casella combinata&#47;premuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Icona|`CommonControls.ComboBoxGlyphPressed`|  
|![&#45;casella combinata&#47;premuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Sfondo del glifo|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Con stato attivo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Metti&#45;giù&#47;casella combinata messa a fuoco](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Background|`CommonControls.ComboBoxBackgroundFocused`|  
|![Metti&#45;giù&#47;casella combinata messa a fuoco](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Bordo|`CommonControls.ComboBoxBorderFocused`|  
|![Metti&#45;giù&#47;casella combinata messa a fuoco](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Text|`CommonControls.ComboBoxTextFocused`|  
|![Metti&#45;giù&#47;casella combinata messa a fuoco](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Separatore|`CommonControls.ComboBoxSeparatorFocused`|  
|![Metti&#45;giù&#47;casella combinata messa a fuoco](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Icona|`CommonControls.ComboBoxGlyphFocused`|  
|![Metti&#45;giù&#47;casella combinata messa a fuoco](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Sfondo del glifo|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Selezione di input di testo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fare&#45;'input di testo della casella combinata&#47;](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Evidenziazione|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Premuto - Visualizzazione elementi elenco**  
  
|Componente|Elemento|Nome token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Background|`CommonControls.ComboBoxListBackground`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Background|`CommonControls.ComboBoxListBackgroundHover`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Background|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Background|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Bordo|`CommonControls.ComboBoxListBorder`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Bordo|`CommonControls.ComboBoxListBorderHover`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Bordo|`CommonControls.ComboBoxListBorderPressed`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Bordo|`CommonControls.ComboBoxListBorderFocused`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Testo dell'elemento|`CommonControls.ComboBoxListItemText`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Testo dell'elemento|`CommonControls.ComboBoxListItemTextHover`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Testo dell'elemento|`CommonControls.ComboBoxListItemTextPressed`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Testo dell'elemento|`CommonControls.ComboBoxListItemTextFocused`|  
|![Fare clic&#45;in basso&#47;visualizzazione elenco caselle combinate](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Ombreggiatura dello sfondo|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Controlli per dati tabulari (griglia)  
 I controlli per dati tabulari, noti anche come controlli griglia, sono controlli comuni per Visual Studio, che possono essere usati per presentare grandi quantità di dati in più colonne. I controlli per dati tabulari standard possono trovarsi in diverse posizioni all'interno di Visual Studio, ad esempio nella finestra degli strumenti Elenco errori, nei report IntelliTrace e nella visualizzazione degli heap della memoria. Usare sempre i controlli per dati tabulari standard forniti. In alcuni casi rari, si potrebbe non avere accesso ai controlli per dati tabulari standard. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri controlli per dati tabulari in Visual Studio.  
  
 ![Dati tabulari &#40;controllo griglia&#41; linea rossa](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Usare…  
 Per controlli tabulari o griglia.  
  
 Non usare...  
 Per qualsiasi interfaccia utente diversa da un controllo tabulare o griglia.  
  
##### <a name="column-headers"></a>Intestazioni di colonna  
 Le intestazioni di colonna sono costituite da uno sfondo, un bordo, il testo del titolo e un glifo facoltativo, usato in genere quando una griglia viene ordinata in base alla colonna.  
  
|State|Elemento|Nome token: Category.color|  
|-----------|-------------|--------------------------------|  
|Predefinito|Background|`Header.Default`|  
|Predefinito|Primo piano (testo)|`Environment.CommandBarTextActive`|  
|Predefinito|Primo piano (glifo)|`Header.Glyph`|  
|Predefinito|Bordo|`Header.SeparatorLine`|  
|Passaggio del mouse|Background|`Header.MouseOver`|  
|Passaggio del mouse|Primo piano (testo)|`Environment.CommandBarTextHover`|  
|Passaggio del mouse|Primo piano (glifo)|`Header.MouseOverGlyph`|  
|Passaggio del mouse|Bordo|`Header.SeparatorLine`|  
|Premuto|Background|`CommonControls.CheckBoxBackgroundPressed`|  
|Premuto|Primo piano (testo)|`CommonControls.CheckBoxBorderPressed`|  
|Premuto|Primo piano (glifo)|`CommonControls.CheckBoxTextPressed`|  
|Premuto|Bordo|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Elementi della visualizzazione elenco  
 Gli elementi della visualizzazione elenco sono costituiti da uno sfondo e da contenuto. Il contenuto può essere sotto forma di testo, icona o entrambi.  
  
|State|Elemento|Nome token: Category.color|  
|-----------|-------------|--------------------------------|  
|Predefinito|Background|Trasparente|  
|Predefinito|Primo piano (testo)|`Environment.CommandBarTextActive`|  
|Predefinito|Bordo|nessuno|  
|Selezionato (attivo)|Background|`TreeView.SelectedItemActive`|  
|Selezionato (attivo)|Primo piano (testo)|`TreeView.SelectedItemActiveText`|  
|Selezionato (attivo)|Bordo|nessuno|  
|Selezionato (inattivo)|Background|`TreeView.SelectedItemInactive`|  
|Selezionato (inattivo)|Primo piano (testo)|`TreeView.SelectedItemInactiveText`|  
|Selezionato (inattivo)|Bordo|nessuno|  
  
### <a name="manifest-designer"></a>Finestra Progettazione manifesto  
 La finestra Progettazione manifesto è stata progettata come strumento per semplificare la modifica del file manifesto in progetti Windows 8 e Windows Phone 8. Benché non sia disponibile per l'utilizzo alcun framework condiviso, potrebbe essere appropriato fare in modo che il layout di progettazione e i colori delle schede di orientamento/spostamento corrispondano alla struttura complessiva. Per altre informazioni sui dettagli del layout, vedere [Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Progettazione manifesto con linea rossa](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Usare…  
- Per le finestre di progettazione simili alla finestra Progettazione manifesto.  

- Invece di usare controlli scheda comuni nella parte superiore di un editor all'interno dell'area dei documenti.  

Non usare...  
- Se sono presenti più di sei schede.  

- Per qualsiasi interfaccia utente non strutturata come la finestra Progettazione manifesto.  
  
|State|Componente|Elemento|Nome token: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Predefinito (selezionato)|Scheda|Background|`ManifestDesigner.TabActive`|  
|Predefinito (selezionato)|Scheda|Bordo|nessuno|  
|Predefinito (selezionato)|Riquadro Descrizione|Background|`ManifestDesigner.DescriptionPane`|  
|Predefinito (selezionato)|Pagina contenuto|Background|`ManifestDesigner.Background`|  
|Predefinito (selezionato)|Pagina contenuto|Testo di supporto della finestra di dialogo|`ManifestDesigner.WatermarkText`<br /><br /> Questo nome di token non corrisponde alla sua funzione.|  
|Non selezionato|Scheda|Background|`ManifestDesigner.Tab.Inactive`|  
|Passaggio del mouse|Scheda|Background|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Assegnazione di tag  
 Visual Studio supporta l'assegnazione di tag, che permette a un utente di dichiarare parole chiave da cercare per scopi di verifica. Ad esempio, i project manager e gli sviluppatori possono usare Team Foundation Server (TFS) per assegnare tag a elementi di lavoro. La tabella seguente indica i nomi di colore per il tag stesso e il glifo dell'icona di chiusura visualizzato negli stati corrispondenti al passaggio del mouse e alla selezione.  
  
 ![Tag con linea rossa](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Usare…  
 Per un'interfaccia utente che supporta l'assegnazione di tag.  
  
 Non usare...  
 Per qualsiasi altro tipo di interfaccia utente.  
  
#### <a name="tag"></a>Tag  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Predefinito**|Background|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Predefinito**|Primo piano (testo)|`Tag.Background`|  
|![Tag al passaggio del mouse](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Passaggio del mouse**|Background|`Tag.HoverBackground`|  
|![Tag al passaggio del mouse](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Passaggio del mouse**|Primo piano (testo)|`Tag.HoverBackgroundText`|  
|![Tag scelto](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Premuto**|Background|`Tag.PressedBackground`|  
|![Tag scelto](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Premuto**|Primo piano (testo)|`Tag.PressedBackgroundText`|  
|![Tag selezionato](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selezionato**|Background|`Tag.SelectedBackground`|  
|![Tag selezionato](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selezionato**|Primo piano (testo)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glifo (icona di chiusura)  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#41;del glifo di &#40;tag](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Predefinito (impostazione predefinita del tag)**|Background|N/D|  
|![&#41;del glifo di &#40;tag](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Predefinito (impostazione predefinita del tag)**|Primo piano (glifo)|`Tag.TagHoverGlyph`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Contrassegnare &#40;&#41; glifi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Passaggio del mouse (impostazione predefinita del tag)**|Background|`Tag.TagHoverGlyphHoverBackground`|  
|![Contrassegnare &#40;&#41; glifi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Passaggio del mouse (impostazione predefinita del tag)**|Primo piano (glifo)|`Tag.TagHoverGlyphHover`|  
|![Contrassegnare &#40;&#41; glifi al passaggio del mouse](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Passaggio del mouse (impostazione predefinita del tag)**|Bordo|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![del&#41; glifo del &#40;tag premuto](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Premuto (impostazione predefinita del tag)**|Background|`Tag.TagHoverGlyphPressedBackground`|  
|![del&#41; glifo del &#40;tag premuto](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Premuto (impostazione predefinita del tag)**|Primo piano (glifo)|`Tag.TagHoverGlyphPressed`|  
|![del&#41; glifo del &#40;tag premuto](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Premuto (impostazione predefinita del tag)**|Bordo|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Tag selezionato/impostazione predefinita del glifo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag selezionato](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Predefinito (tag selezionato)**|Background|N/D|  
|![Tag selezionato](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Predefinito (tag selezionato)**|Primo piano (glifo)|`Tag.TagSelectedGlyph`|  
  
 **Tag selezionato/passaggio del mouse sul glifo**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag selezionato al passaggio del mouse](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Passaggio del mouse (tag selezionato)**|Background|`Tag.TagSelectedGlyphHoverBackground`|  
|![Tag selezionato al passaggio del mouse](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Passaggio del mouse (tag selezionato)**|Primo piano (glifo)|`Tag.TagSelectedGlyphHover`|  
|![Tag selezionato al passaggio del mouse](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Passaggio del mouse (tag selezionato)**|Bordo|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Tag selezionato/glifo premuto**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag selezionato scelto](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Premuto (tag selezionato)**|Background|`Tag.TagSelectedGlyphPressedBackground`|  
|![Tag selezionato scelto](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Premuto (tag selezionato)**|Primo piano (glifo)|`Tag.TagSelectedGlyphPressed`|  
|![Tag selezionato scelto](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Premuto (tag selezionato)**|Bordo|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Shell  
  
#### <a name="background"></a>Background  
 Lo sfondo dell'ambiente è costituito da due livelli. Il livello inferiore è un colore a tinta unita che ricopre l'intero IDE. Il livello superiore si trova sotto lo scaffale dei comandi tra i canali Nascondi automaticamente della finestra degli strumenti, nei bordi destro e sinistro dell'IDE. A partire da Visual Studio 2013, i livelli superiore e inferiore dello sfondo sono impostati sullo stesso colore dei temi Chiaro e Scuro.  
  
 ![Sfondo della shell con linea rossa](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Usare…  
 Per i punti che devono corrispondere allo sfondo dell'ambiente di Visual Studio.  
  
Non usare...  
- Come riempimento per i punti che non sono superfici di sfondo.  

- Come sfondo su cui si vuole posizionare elementi in primo piano.  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|Livello inferiore|Background|`Environment.EnvironmentBackground`|  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|Livello superiore|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Livello superiore|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Livello superiore|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Livello superiore|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Scaffale dei comandi  
 Due set di nomi di token vengono usati per gli sfondi dello scaffale dei comandi, uno per il punto in cui si trova la barra dei menu e l'altro per il punto in cui si trova la barra dei comandi. Un singolo gruppo della barra dei comandi ha valori di colore di sfondo propri, che vengono descritti in modo più dettagliato nella sezione "Barra dei comandi". Il testo della barra dei menu e della barra dei comandi viene descritto nelle rispettive sezioni.  
  
 ![Scaffale dei comandi con linea rossa](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Usare…  
- Per le aree in cui si posizionano menu o barre degli strumenti.  

- con la combinazione corretta nome token di sfondo/primo piano.  
  
  Non usare...  
  Per aree che non sono simili a uno scaffale dei comandi.  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|Barra dei menu|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Barra dei menu|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Barra dei menu|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Barra dei comandi|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Barra dei comandi|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Barra dei comandi|Background<br /><br /> *Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Casella degli strumenti  
 La casella degli strumenti è una delle finestre degli strumenti comuni usata più di frequente in Visual Studio. Si tratta essenzialmente di un controllo albero con un tema e stili speciali applicati.  
  
 ![Casella degli strumenti con linea rossa](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Usare…  
 Quando si progetta una finestra degli strumenti che deve essere sempre coerente con la casella degli strumenti della shell.  
  
 Non usare...  
 Per qualsiasi altro elemento diverso dall'interfaccia utente della casella degli strumenti oppure se si teme il verificarsi di problemi nell'interfaccia utente in caso di modifica dei colori della casella degli strumenti della shell.  
  
 **Predefinito**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nodo padre della casella degli strumenti](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo padre**|Background|`Environment.ToolboxContent`<br /><br /> Intestazioni<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Singoli elementi o intera finestra se non è disponibile alcun controllo|  
|![Nodo figlio della casella degli strumenti](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo figlio**|Background|`Environment.ToolboxContent`<br /><br /> Intestazioni<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Singoli elementi o intera finestra se non è disponibile alcun controllo|  
|![Nodo padre della casella degli strumenti](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo padre**|Bordo|nessuno|  
|![Nodo figlio della casella degli strumenti](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo figlio**|Bordo|nessuno|  
|![Nodo padre della casella degli strumenti](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo padre**|Primo piano (glifo)|`Environment.ToolboxContent`|  
|![Nodo figlio della casella degli strumenti](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo figlio**|Primo piano (glifo)|`Environment.ToolboxContent`|  
|![Nodo padre della casella degli strumenti](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo padre**|Primo piano (testo)|`Environment.ToolboxContent`|  
|![Nodo figlio della casella degli strumenti](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo figlio**|Primo piano (testo)|`Environment.ToolboxContent`|  
  
 **Passaggio del mouse**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nodo figlio della casella degli strumenti al passaggio del mouse](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Passaggio del mouse sulla casella degli strumenti nel nodo figlio**|Background|`Environment.ToolboxContentMouseOver`<br /><br /> Solo singoli elementi|  
|![Nodo figlio della casella degli strumenti al passaggio del mouse](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Passaggio del mouse sulla casella degli strumenti nel nodo figlio**|Bordo|nessuno|  
|![Nodo figlio della casella degli strumenti al passaggio del mouse](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Passaggio del mouse sulla casella degli strumenti nel nodo figlio**|Primo piano (testo)|`Environment.ToolboxContentMouseOver`<br /><br /> Solo singoli elementi|  
  
 **Selezionato**  
  
|Componente|Elemento|Nome token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nodo padre della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo padre con stato attivo**|Background|`TreeView.SelectedItemActive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo figlio della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo figlio con stato attivo**|Background|`TreeView.SelectedItemActive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo padre della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo padre con stato attivo**|Bordo|`TreeView.FocusVisualBorder`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo figlio della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo figlio con stato attivo**|Bordo|`TreeView.FocusVisualBorder`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo padre della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo padre con stato attivo**|Primo piano (glifo)|`TreeView.SelectedItemActive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo figlio della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo figlio con stato attivo**|Primo piano (glifo)|`TreeView.SelectedItemActive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo padre della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo padre con stato attivo**|Primo piano (testo)|`TreeView.SelectedItemActive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo figlio della casella degli strumenti con stato attivo](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo figlio con stato attivo**|Primo piano (testo)|`TreeView.SelectedItemActive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo padre della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo padre con stato non attivo**|Background|`TreeView.SelectedItemInactive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo figlio della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo figlio con stato non attivo**|Background|`TreeView.SelectedItemInactive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo padre della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo padre con stato non attivo**|Bordo|nessuno|  
|![Nodo figlio della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo figlio con stato non attivo**|Bordo|nessuno|  
|![Nodo padre della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo padre con stato non attivo**|Primo piano (glifo)|`TreeView.SelectedItemInactive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo figlio della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo figlio con stato non attivo**|Primo piano (glifo)|`TreeView.SelectedItemInactive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo padre della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo padre con stato non attivo**|Primo piano (testo)|`TreeView.SelectedItemInactive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo figlio della casella degli strumenti con stato non attivo](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo figlio con stato non attivo**|Primo piano (testo)|`TreeView.SelectedItemInactive`<br /><br /> Dalla categoria [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Riferimento del valore di colore  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Componente|Parte|Elemento|State|Light|Dark (Scuro)|Blu|Contrasto elevato|  
|Linee di divisione|||Predefinito|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Glifo espansore||Primo piano|Predefinito|||||  
|Glifo espansore||Primo piano|Passaggio del mouse|||||  
|Glifo espansore||Background|Predefinito|||||  
|Glifo espansore||Background|Passaggio del mouse|||||  
|Glifo espansore||Bordo|Predefinito|||||  
|Glifo espansore||Bordo|Passaggio del mouse|||||