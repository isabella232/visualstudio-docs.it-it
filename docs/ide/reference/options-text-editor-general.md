---
title: Opzioni, Editor di testo, Generale
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4405e50a2bc264c88c073980da77fafbedf49cbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830665"
---
# <a name="options-text-editor-general"></a>Opzioni, Editor di testo, Generale

Questa finestra di dialogo consente di modificare le impostazioni globali di Visual Studio Code e dell'editor di testo. Per visualizzare questa finestra di dialogo, selezionare **Opzioni** nel menu **Strumenti**, espandere la cartella **Editor di testo** e quindi selezionare **Generale**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="settings"></a>Impostazioni

### <a name="drag-and-drop-text-editing"></a>Trascina la selezione

Quando questa opzione è selezionata, è possibile spostare il testo selezionandolo e trascinandolo con il mouse in un'altra posizione all'interno del documento corrente o in un altro documento aperto.

### <a name="automatic-delimiter-highlighting"></a>Evidenzia delimitatore automatico

Quando questa opzione è selezionata, i caratteri di delimitazione che separano i parametri o le coppie elemento-valore, così come le parentesi graffe corrispondenti, vengono evidenziati.

### <a name="track-changes"></a>Revisioni

Quando questa opzione è selezionata, nel margine di selezione viene visualizzata una linea gialla per contrassegnare il codice modificato dall'ultimo salvataggio del file. Quando si salvano le modifiche, le linee verticali diventano verdi.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Rileva automaticamente codifica UTF-8 senza firma

Per impostazione predefinita, l'editor rileva la codifica cercando indicatori dell'ordine dei byte o tag del set di caratteri. Se nel documento corrente non vengono trovati indicatori o tag di questo tipo, l'editor di codice tenterà di rilevare automaticamente la codifica UTF-8 analizzando le sequenze di byte. Per disabilitare il rilevamento automatico della codifica, deselezionare questa opzione.

## <a name="display"></a>Display

### <a name="selection-margin"></a>Margine selezione

Quando questa opzione è selezionata, viene visualizzato un margine verticale lungo il bordo sinistro dell'area di testo dell'editor. È possibile fare clic nel margine per selezionare un'intera riga di testo oppure fare clic e trascinare per selezionare righe di testo consecutive.

|Margine di selezione attivato|Margine di selezione disattivato|
| - | - |
|![Schermata HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Schermata HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margine indicatore

Quando questa opzione è selezionata, viene visualizzato un margine verticale all'esterno del bordo sinistro dell'area di testo dell'editor. Quando si fa clic su questo margine vengono visualizzate un'icona e un tooltip relativi al testo. Ad esempio, nel margine indicatore vengono visualizzati punti di interruzione o collegamenti dell'Elenco attività. Le informazioni del margine indicatore non vengono stampate.

### <a name="vertical-scroll-bar"></a>Barra di scorrimento verticale

Quando questa opzione è selezionata, viene visualizzata una barra di scorrimento verticale che consente di scorrere verso l'alto e verso il basso per visualizzare gli elementi al di fuori dell'area di visualizzazione dell'editor. Se non sono disponibili barre di scorrimento verticali, per scorrere è possibile usare i tasti PGSU e PGGIÙ e i tasti di direzione.

### <a name="horizontal-scroll-bar"></a>Barra di scorrimento orizzontale

Quando questa opzione è selezionata, viene visualizzata una barra di scorrimento orizzontale che consente di scorrere da un lato all'altro per visualizzare gli elementi al di fuori dell'area di visualizzazione dell'editor. Se non sono disponibili barre di scorrimento orizzontali, per scorrere è possibile utilizzare i tasti di direzione.

### <a name="highlight-current-line"></a>Evidenzia riga corrente

Quando questa opzione è selezionata, viene visualizzata una casella grigia intorno alla riga di codice in cui si trova il cursore.

## <a name="see-also"></a>Vedere anche

- [Opzioni, Editor di testo, Tutti i linguaggi](../../ide/reference/options-text-editor-all-languages.md)
- [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opzioni, Editor di testo, Estensione file](../../ide/reference/options-text-editor-file-extension.md)
- [Identificazione e personalizzazione dei tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Personalizzazione dell'editor](../../ide/customizing-the-editor.md)
- [Utilizzo di IntelliSense](../../ide/using-intellisense.md)