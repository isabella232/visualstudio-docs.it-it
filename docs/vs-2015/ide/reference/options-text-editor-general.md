---
title: Opzioni, Editor di testo, Generale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
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
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662255"
---
# <a name="options-text-editor-general"></a>Opzioni, Editor di testo, Generale
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare le impostazioni globali di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Code e dell'editor di testo. Per visualizzare questa finestra di dialogo, fare clic su **Opzioni** nel menu **Strumenti**, espandere la cartella **Editor di testo** e quindi fare clic su **Generale**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Impostazioni
 Trascinamento della selezione del testo quando selezionato consente di spostare il testo selezionandolo e trascinandolo con il mouse in un'altra posizione all'interno del documento corrente o di qualsiasi altro documento aperto.

 Evidenziazione automatica dei delimitatori quando selezionati, i caratteri delimitatori che separano i parametri o le coppie elemento-valore, nonché le parentesi graffe corrispondenti, vengono evidenziati.

 Tenere traccia delle modifiche quando l'editor di codice è selezionato, viene visualizzata una riga gialla verticale nel margine di selezione per contrassegnare il codice che è stato modificato dopo l'ultimo salvataggio del file. Quando si salvano le modifiche, le linee verticali diventano verdi.

 Rileva automaticamente la codifica UTF-8 senza firma per impostazione predefinita, l'Editor rileva la codifica cercando gli indicatori per l'ordine dei byte o i tag del set di caratteri. Se nel documento corrente non vengono trovati indicatori o tag di questo tipo, l'editor di codice tenterà di rilevare automaticamente la codifica UTF-8 analizzando le sequenze di byte. Per disabilitare il rilevamento automatico della codifica, deselezionare questa opzione.

## <a name="display"></a>Visualizzazione
 Margine di selezione, se selezionato, Visualizza un margine verticale lungo il bordo sinistro dell'area di testo dell'editor. È possibile fare clic nel margine per selezionare un'intera riga di testo oppure fare clic e trascinare per selezionare righe di testo consecutive.

|Margine di selezione attivato|Margine di selezione disattivato|
|-------------------------|--------------------------|
|![Screenshot HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif "|::ref1::|")|![Screenshot HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "|::ref2::|")|

 Indicatore margin quando selezionato, Visualizza un margine verticale all'esterno del bordo sinistro dell'area di testo dell'editor. Quando si fa clic su questo margine vengono visualizzate un'icona e un tooltip relativi al testo. Ad esempio, nel margine indicatore vengono visualizzati punti di interruzione o collegamenti dell'Elenco attività. Le informazioni del margine indicatore non vengono stampate.

 Barra di scorrimento verticale quando selezionata, Visualizza una barra di scorrimento verticale che consente di scorrere verso l'alto e verso il basso per visualizzare gli elementi che non rientrano nell'area di visualizzazione dell'editor. Se non sono disponibili barre di scorrimento verticali, per scorrere è possibile usare i tasti PGSU e PGGIÙ e i tasti di direzione.

 Barra di scorrimento orizzontale quando selezionata, Visualizza una barra di scorrimento orizzontale che consente di scorrere da un lato all'altro per visualizzare gli elementi che non rientrano nell'area di visualizzazione dell'editor. Se non sono disponibili barre di scorrimento orizzontali, per scorrere è possibile utilizzare i tasti di direzione.

 Evidenzia riga corrente quando è selezionata, Visualizza una casella grigia intorno alla riga di codice in cui si trova il cursore.

## <a name="see-also"></a>Vedere anche
 Opzioni [, editor di testo, opzioni tutti i linguaggi](../../ide/reference/options-text-editor-all-languages.md) [, editor di testo, tutti i linguaggi, opzioni tabulazioni](../../ide/reference/options-text-editor-all-languages-tabs.md) [, editor di testo, estensione di file](../../ide/reference/options-text-editor-file-extension.md) [identificazione e personalizzazione dei tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [personalizzazione dell'editor](../../ide/customizing-the-editor.md) [con IntelliSense](../../ide/using-intellisense.md)
