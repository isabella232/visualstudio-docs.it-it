---
title: Opzioni, Editor di testo, Generale
ms.date: 01/18/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69c74548340e8b8f642fa1e373bdd424c3c81a69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989744"
---
# <a name="options-text-editor-general"></a>Opzioni, Editor di testo, Generale

Questa finestra di dialogo consente di modificare le impostazioni globali di Visual Studio Code e dell'editor di testo. Per visualizzare questa finestra di dialogo, selezionare **Opzioni** nel menu **Strumenti**, espandere la cartella **Editor di testo** e quindi selezionare **Generale**.

## <a name="settings"></a>Impostazioni

### <a name="drag-and-drop-text-editing"></a>Trascina la selezione

Quando questa opzione è selezionata, è possibile spostare il testo selezionandolo e trascinandolo con il mouse in un'altra posizione all'interno del documento corrente o in un altro documento aperto.

### <a name="automatic-delimiter-highlighting"></a>Evidenzia delimitatore automatico

Quando questa opzione è selezionata, i caratteri di delimitazione che separano i parametri o le coppie elemento-valore, così come le parentesi graffe corrispondenti, vengono evidenziati.

### <a name="track-changes"></a>Revisioni

Quando questa opzione è selezionata, nel margine di selezione viene visualizzata una linea gialla per contrassegnare il codice modificato dall'ultimo salvataggio del file. Quando si salvano le modifiche, le linee verticali diventano verdi.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Rileva automaticamente codifica UTF-8 senza firma

Per impostazione predefinita, l'editor rileva la codifica cercando indicatori dell'ordine dei byte o tag del set di caratteri. Se nel documento corrente non vengono trovati indicatori o tag di questo tipo, l'editor del codice tenta di rilevare automaticamente la codifica UTF-8 analizzando le sequenze di byte. Per disabilitare il rilevamento automatico della codifica, deselezionare questa opzione.

### <a name="follow-project-coding-conventions"></a>Segui convenzioni di scrittura codice del progetto

Se selezionata, le convenzioni di scrittura del codice specificate del progetto sostituiscono le eventuali convenzioni di scrittura del codice usate per i progetti personali.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Abilita clic del mouse per eseguire Vai a definizione

Se selezionata, è possibile premere **CTRL** e passare il mouse su un elemento mentre si fa clic del mouse. In questo modo si passa alla definizione dell'elemento selezionato. È anche possibile scegliere **ALT** oppure **CTRL** + **ALT** nell'elenco a discesa **Usa tasto di modifica**.

Selezionare la casella di controllo **Apri definizione in visualizzazione rapida** per visualizzare la definizione dell'elemento selezionato in una finestra senza spostarsi dalla posizione corrente nell'editor del codice.

## <a name="display"></a>Visualizzazione

### <a name="selection-margin"></a>Margine selezione

Quando questa opzione è selezionata, viene visualizzato un margine verticale lungo il bordo sinistro dell'area di testo dell'editor. È possibile fare clic nel margine per selezionare un'intera riga di testo oppure fare clic e trascinare per selezionare righe di testo consecutive.

|Margine di selezione attivato|Margine di selezione disattivato|
| - | - |
|![Schermata HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Schermata HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margine indicatore

Quando questa opzione è selezionata, viene visualizzato un margine verticale all'esterno del bordo sinistro dell'area di testo dell'editor. Quando si fa clic su questo margine vengono visualizzate un'icona e un tooltip relativi al testo. Ad esempio, nel margine indicatore vengono visualizzati punti di interruzione o collegamenti dell'Elenco attività. Le informazioni del margine indicatore non vengono stampate.

### <a name="highlight-current-line"></a>Evidenzia riga corrente

Quando questa opzione è selezionata, viene visualizzata una casella grigia intorno alla riga di codice in cui si trova il cursore.

### <a name="show-structure-guide-lines"></a>Mostra guide per strutture

Se selezionata, nell'editor vengono visualizzate linee verticali allineate ai blocchi di codice strutturato, che consentono di identificare facilmente i singoli blocchi di codice.

## <a name="see-also"></a>Vedere anche

- [Opzioni, Editor di testo, Tutti i linguaggi](../../ide/reference/options-text-editor-all-languages.md)
- [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opzioni, Editor di testo, Estensione file](../../ide/reference/options-text-editor-file-extension.md)
- [Identificazione e personalizzazione dei tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Personalizzazione dell'editor](../../ide/customizing-the-editor.md)
- [Utilizzo di IntelliSense](../../ide/using-intellisense.md)