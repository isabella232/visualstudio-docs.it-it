---
title: GUID e ID delle barre degli strumenti di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7bc5c4957bb9db072bf5c55d9b3b11edfbae96f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969798"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Barre degli strumenti GUID e ID di Visual Studio
In questo argomento elenca i valori GUID e ID delle barre degli strumenti che sono inclusi nell'ambiente di sviluppo integrato (IDE) di Visual Studio e dei gruppi che contengono. Questi valori sono definiti nella *vsct* i file che vengono installati come parte di Visual Studio SDK. Per altre informazioni, vedere [definiti dall'IDE comandi, menu e gruppi](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Molte delle barre degli strumenti disponibili per Visual Studio non sono definite da Visual Studio e i rispettivi GUID e valori di ID non sono pubblici. Questo argomento vengono elencate solo le barre degli strumenti che sono definiti in Visual Studio SDK *vsct* file.  
  
 Per altre informazioni su come lavorare con gli oggetti definiti in IDE *vsct* i file, vedere [estendono i menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Le barre degli strumenti predefinita fornite dall'IDE di Visual Studio utilizzare il GUID `guidSHLMainMenu`, salvo diversa indicazione tramite `GUID:ID` sintassi.  
  
## <a name="ide-toolbars"></a>Barre degli strumenti dell'IDE  
 Le barre degli strumenti seguenti vengono forniti tramite l'IDE di Visual Studio. Le barre degli strumenti possono essere visualizzati selezionandole nel **barre degli strumenti** sottomenu delle **strumenti** menu. Le barre degli strumenti nelle finestre degli strumenti non sono inclusi in questa sezione.  
  
 Solo i gruppi possono discendono direttamente dalle barre degli strumenti. Per aggiungere un gruppo, impostare il relativo elemento padre sul GUID e ID della barra degli strumenti. Per aggiungere un pulsante a una barra degli strumenti, impostare il relativo elemento padre a un gruppo sulla barra degli strumenti.  
  
|ToolBar|Id|  
|-------------|--------|  
|Standard|IDM_VS_TOOL_STANDARD|  
|Compilazione|IDM_VS_TOOL_BUILD|  
|Editor di testo|IDM_VS_TOOL_TEXTEDITOR|  
|Debug|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Posizione di debug|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Barre degli strumenti speciali  
 Queste barre degli strumenti sono definiti dall'IDE di Visual Studio, ma che svolgono funzioni specializzate e non ospitano gruppi di comandi.  
  
|ToolBar|Id|  
|-------------|--------|  
|Comando Add|IDM_VS_TOOL_ADDCOMMAND|  
|Undefined|IDM_VS_TOOL_UNDEFINED|  
|Schema XML|IDM_VS_TOOL_SCHEMA|  
|XML (dati)|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Gruppi in barre degli strumenti dell'IDE  
 Per aggiungere un pulsante a una barra degli strumenti standard, impostare uno dei seguenti gruppi come elemento padre. I gruppi vengono ordinati in base della barra degli strumenti padre.  
  
### <a name="standard-toolbar-groups"></a>Gruppi della barra degli strumenti standard  
  
|nome|Id|  
|----------|--------|  
|Salva/Apri|IDG_VS_TOOLSB_SAVEOPEN|  
|Taglia/Copia|IDG_VS_TOOLSB_CUTCOPY|  
|Annullamento/ripristino|IDG_VS_TOOLSB_UNDOREDO|  
|Esecuzione/Build|IDG_VS_TOOLSB_RUNBUILD|  
|Cerca|IDG_VS_TOOLSB_SEARCH|  
|WINDOWS|IDG_VS_TOOLSB_WINDOWS|  
|Nuove finestre|IDG_VS_TOOLSB_NEWWINDOWS|  
|Caricamento/salvataggio|IDG_VS_WINDOWUI_LOADSAVE|  
|Misuratore|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>I gruppi della barra degli strumenti di compilazione  
  
|nome|Id|  
|----------|--------|  
|Barra di compilazione|IDG_VS_BUILDBAR|  
|Annulla|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Gruppi della barra degli strumenti editor di testo  
  
|nome|Id|  
|----------|--------|  
|Completamento|IDM_VS_TOOL_TEXTEDITOR|  
|Indent|IDG_VS_EDITTOOLBAR_INDENT|  
|Commento|IDG_VS_EDITTOOLBAR_COMMENT|  
|Segnalibri|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>I gruppi della barra degli strumenti di debug  
  
|nome|Id|  
|----------|--------|  
|Esecuzione|IDM_DEBUG_TOOLBAR|  
|Esecuzione di istruzioni|IDG_DEBUG_TOOLBAR_STEPPING|  
|Espressioni di controllo|IDG_DEBUG_TOOLBAR_WATCH|  
|WINDOWS|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>I gruppi della barra degli strumenti posizione di debug  
  
|nome|Id|  
|----------|--------|  
|Posizione di debug|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Barre degli strumenti della finestra degli strumenti  
 Le barre degli strumenti possono essere visualizzati direttamente nell'IDE o nelle finestre degli strumenti, ad esempio **Esplora soluzioni**. Perché non sono definite finestre degli strumenti nel *vsct* file, barre degli strumenti finestra degli strumenti non è definito gli elementi padre. Al contrario, vengono inseriti nel codice. La tabella seguente illustra le barre degli strumenti visualizzati nelle finestre degli strumenti nell'IDE e dei gruppi di comandi che contengono.  
  
> [!NOTE]
>  Barre degli strumenti e i gruppi di utilizzano il GUID `guidSHLMainMenu`, salvo dove diversamente specificato usando la sintassi di coppia GUID: ID. Per una barra degli strumenti viene specificato un GUID, si applica anche ai gruppi che derivano da tale barra degli strumenti.  
  
|Finestra degli strumenti|ToolBar|Gruppi|  
|-----------------|-------------|------------|  
|Esplora soluzioni|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1..5|  
|Esplora server|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Proprietà|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Visualizzazione classi|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Visualizzazione classi|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Visualizzatore oggetti|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Visualizzatore oggetti|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Output|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Trova e sostituisci|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Risultati ricerca 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Risultati ricerca 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Frammento di codice|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Segnalibri|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Elenco attività|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Attività definite dall'utente|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Elenco errori|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Visualizzatore chiamate|IDM_VS_TOOL_CALLBROWSER1..16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Punti di interruzione|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Disassembly|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Memoria 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1...4|IDG_MEMORY_EXPRESSION1..4<br /><br /> IDG_MEMORY_COLUMNS1..4|  
|Processi|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere un controller di menu per una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Aggiungere una barra degli strumenti a una finestra degli strumenti](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Menu GUID e ID di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)