---
title: GUID e ID delle barre degli Visual Studio di | Microsoft Docs
description: Visualizzare un elenco di valori GUID e ID per le barre degli strumenti e i gruppi che contengono, inclusi nell'ambiente di sviluppo integrato (IDE) di Visual Studio di sviluppo integrato (IDE) di .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d2ba6c92a2913ec63a59751a4181454aa67fa67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898110"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUID e ID delle barre Visual Studio barre degli strumenti
In questo argomento vengono enumerati i valori GUID e ID delle barre degli strumenti incluse nell'ambiente di sviluppo integrato (IDE) di Visual Studio e dei gruppi che contengono. Questi valori sono definiti in file con estensione *vsct* installati come parte di Visual Studio SDK. Per altre informazioni, vedere Comandi, menu e gruppi definiti [dall'IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

> [!NOTE]
> Molte delle barre degli strumenti disponibili Visual Studio non sono definite da Visual Studio e i relativi valori GUID e ID non sono pubblici. Questo argomento elenca solo le barre degli strumenti definite nei file Visual Studio SDK *con estensione vsct.*

 Per altre informazioni su come usare gli oggetti IDE definiti nei file con estensione *vsct,* vedere [Estendere menu e comandi.](../../extensibility/extending-menus-and-commands.md)

 Le barre degli strumenti predefinite fornite dall'IDE Visual Studio usano il GUID , tranne quando diversamente `guidSHLMainMenu` specificato tramite la `GUID:ID` sintassi .

## <a name="ide-toolbars"></a>Barre degli strumenti dell'IDE
 Le barre degli strumenti seguenti vengono fornite dall'IDE Visual Studio. Le barre degli strumenti possono essere visualizzate selezionandole **nel** sottomenu Barre degli strumenti **del** menu Strumenti. Le barre degli strumenti nelle finestre degli strumenti non sono incluse in questa sezione.

 Solo i gruppi possono discendere direttamente dalle barre degli strumenti. Per aggiungere un gruppo, impostarne il padre sul GUID e sull'ID della barra degli strumenti. Per aggiungere un pulsante a una barra degli strumenti, impostarne il padre su un gruppo sulla barra degli strumenti.

|Barra degli strumenti|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Compilazione|IDM_VS_TOOL_BUILD|
|Editor di testo|IDM_VS_TOOL_TEXTEDITOR|
|Debug|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Percorso di debug|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Barre degli strumenti speciali
 Queste barre degli strumenti sono definite dall'IDE Visual Studio, ma servono funzioni specializzate e non ospitano gruppi di comandi.

|Barra degli strumenti|ID|
|-------------|--------|
|Comando Add|IDM_VS_TOOL_ADDCOMMAND|
|Non definito|IDM_VS_TOOL_UNDEFINED|
|XML Schema|IDM_VS_TOOL_SCHEMA|
|Dati XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Gruppi sulle barre degli strumenti dell'IDE
 Per aggiungere un pulsante a una barra degli strumenti standard, impostare uno dei gruppi seguenti come padre. I gruppi sono ordinati in base alla barra degli strumenti padre.

### <a name="standard-toolbar-groups"></a>Gruppi di barre degli strumenti standard

|Nome|ID|
|----------|--------|
|Salva/Apri|IDG_VS_TOOLSB_SAVEOPEN|
|Taglia/Copia|IDG_VS_TOOLSB_CUTCOPY|
|Annullamento/ripristino|IDG_VS_TOOLSB_UNDOREDO|
|Esecuzione/compilazione|IDG_VS_TOOLSB_RUNBUILD|
|Ricerca|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nuove finestre|IDG_VS_TOOLSB_NEWWINDOWS|
|Carica/Salva|IDG_VS_WINDOWUI_LOADSAVE|
|Misuratore|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Creare gruppi di barre degli strumenti

|Nome|ID|
|----------|--------|
|Barra di compilazione|IDG_VS_BUILDBAR|
|Annulla|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Gruppi di barre degli strumenti dell'editor di testo

|Nome|ID|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Impostare un rientro|IDG_VS_EDITTOOLBAR_INDENT|
|Commento|IDG_VS_EDITTOOLBAR_COMMENT|
|Segnalibri|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Gruppi di barre degli strumenti di debug

|Nome|ID|
|----------|--------|
|Esecuzione|IDM_DEBUG_TOOLBAR|
|Esecuzione di istruzioni|IDG_DEBUG_TOOLBAR_STEPPING|
|Video|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Gruppi di barre degli strumenti percorso di debug

|Nome|ID|
|----------|--------|
|Percorso di debug|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Barre degli strumenti della finestra degli strumenti
 Le barre degli strumenti possono essere visualizzate direttamente nell'IDE o nelle finestre degli strumenti, ad esempio **Esplora soluzioni**. Poiché le finestre degli strumenti non sono definite nei file *con estensione vsct,* le barre degli strumenti delle finestre degli strumenti non hanno elementi padre definiti. Vengono invece inseriti nel codice. La tabella seguente illustra le barre degli strumenti visualizzate nelle finestre degli strumenti nell'IDE e i gruppi di comandi che contengono.

> [!NOTE]
> Le barre degli strumenti e i gruppi usano il GUID , tranne se diversamente `guidSHLMainMenu` specificato tramite la sintassi GUID:ID. Se viene specificato un GUID per una barra degli strumenti, si applica anche ai gruppi che discendono da tale barra degli strumenti.

|Finestra degli strumenti|Barra degli strumenti|Gruppi|
|-----------------|-------------|------------|
|Esplora soluzioni|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. 5|
|Esplora server|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Proprietà|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Visualizzazione classi|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Visualizzazione classi|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Visualizzatore oggetti|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Visualizzatore oggetti|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Output|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Trova e sostituisci|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Risultati della ricerca 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Risultati di ricerca 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Frammento di codice|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Segnalibri|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Elenco attività|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Attività definite dall'utente|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Elenco errori|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Visualizzatore chiamate|IDM_VS_TOOL_CALLBROWSER1.. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Punti di interruzione|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Disassembly|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Memoria 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1.. 4<br /><br /> IDG_MEMORY_COLUMNS1.. 4|
|Processi|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Vedere anche
- [Aggiungere un controller di menu a una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Aggiungere una barra degli strumenti a una finestra degli strumenti](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [GUID e ID di Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
