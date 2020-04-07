---
title: GUID e gli ED dei menu di Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a656d5cb9a126a9dc3988d70a290fceb3e56439e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708234"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e GLI URL dei menu di Visual Studio
In questo articolo vengono enumerati i valori GUID e ID dei menu e gruppi sulla barra dei menu di Visual Studio. Questi valori sono definiti nei file *vsct* installati come parte di Visual Studio SDK. Per ulteriori informazioni, vedere [Comandi, menu e gruppi definiti dall'IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Per ulteriori informazioni sull'utilizzo degli oggetti DELL'ambiente di sviluppo integrato (IDE) definiti nei file *vsct,* vedere [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md).

 I menu e i gruppi sulla barra `guidSHLMainMenu`dei menu di Visual Studio utilizzano il GUID . La barra dei menu `IDM_VS_TOOL_MAINMENU`stessa ha un ID di .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppi sulla barra dei menu di Visual Studio
 Per aggiungere un menu alla barra dei menu, impostare uno di questi gruppi come padre.

|Gruppo|ID|
|-----------|--------|
|File/Modifica/Visualizza|IDG_VS_MM_FILEEDITVIEW|
|Refactoring|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Compilazione|IDG_VS_MM_BUILDDEBUGRUN|
|Formato/Strumenti|IDG_VS_MM_TOOLSADDINS|
|Finestra/Guida/Comunità|IDG_VS_MM_WINDOWHELP|
|Add-in|IDG_VS_MM_MACROS|
|Controllo FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu sulla barra dei menu di Visual Studio
 Per aggiungere un gruppo a un menu di Visual Studio esistente, impostare uno dei menu seguenti come padre. I sottomenu non sono inclusi in questo elenco.

|Menu|ID|
|----------|--------|
|File|IDM_VS_MENU_FILE|
|Modifica|IDM_VS_MENU_EDIT|
|Visualizza|IDM_VS_MENU_VIEW|
|Refactoring|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Compilazione|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|Strumenti|IDM_VS_MENU_TOOLS|
|Estensioni|IDM_VS_MENU_EXTENSIONS|
|Finestra|IDM_VS_MENU_WINDOW|
|Add-in|IDM_VS_MENU_ADDINS|
|Community|IDM_VS_MENU_COMMUNITY|
|Guida|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Gruppi nei menu di Visual StudioGroups on Visual Studio menus
 Negli elenchi seguenti vengono illustrati i gruppi discendenti direttamente dai menu della barra dei menu di Visual Studio.The following lists show the groups that descend directly from menus on the Visual Studio menu bar. Il modo più rapido per aggiungere un comando a un menu di Visual Studio consiste nell'impostare uno di questi gruppi come padre. I gruppi discendenti dai sottomenu non vengono visualizzati in questa sezione.

### <a name="file-menu-groups"></a>Gruppi di menu file

|Gruppo|ID|
|-----------|--------|
|Nuovo/Aperto|IDG_VS_FILE_FILE|
|Add|IDG_VS_FILE_ADD|
|Soluzione|IDG_VS_FILE_SOLUTION|
|Varie|IDG_VS_FILE_MISC|
|Salvare|IDG_VS_FILE_SAVE|
|Rinomina|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Print|IDG_VS_FILE_PRINT|
|Usati più di recente|IDG_VS_FILE_MRU|
|Spostamento|IDG_VS_FILE_MOVE|
|Esci|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Modificare i gruppi di menu

|Gruppo|ID|
|-----------|--------|
|Annullamento/ripristino|IDG_VS_EDIT_UNDOREDO|
|Taglia/Copia/Incolla|IDG_VS_EDIT_CUTCOPY|
|Select|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|Oggetti|IDG_VS_EDIT_OBJECTS|
|Verbi OLE|IDG_VS_EDIT_OLEVERBS|
|Pozzo di comando|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Gruppi di menu di refactoringRefactor menu groups

|Gruppo|ID|
|-----------|--------|
|Comuni|IDG_REFACTORING_COMMON|
|Avanzate|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Visualizzare i gruppi di menu

|Gruppo|ID|
|-----------|--------|
|Codice modulo|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definire le viste|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architette Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Windows dell'organizzazione|IDG_VS_VIEW_ORG_WINDOWS|
|Browser del codice|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Finestre di sviluppo|IDG_VS_VIEW_DEV_WINDOWS|
|Barre degli strumenti|IDG_VS_VIEW_TOOLBARS|
|Symbols|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Esplorare|IDG_VS_VIEW_NAVIGATE|
|Navigazione piccola|IDG_VS_VIEW_SMALLNAVIGATE|
|Visualizzatore oggetti|IDG_VS_VIEW_OBJBRWSR|
|Pozzo di comando|IDG_VS_VIEW_COMMANDWELL|
|Pagine delle proprietà|IDG_VS_VIEW_PROPPAGES|
|Aggiorna|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Gruppi di menu progetto

|Gruppo|ID|
|-----------|--------|
|Aggiunta varie|IDG_VS_PROJ_MISCADD|
|Add|IDG_VS_PROJ_ADD|
|Cartella|IDG_VS_PROJ_FOLDER|
|Scarica/Ricarica|IDG_VS_PROJ_UNLOADRELOAD|
|Informazioni di riferimento|IDG_VS_PROJ_REFERENCE|
|Opzioni|IDG_VS_PROJ_OPTIONS|
|Impostazioni|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Creare gruppi di menu

|Gruppo|ID|
|-----------|--------|
|Soluzione|IDG_VS_BUILD_SOLUTION|
|Selezione|IDG_VS_BUILD_SELECTION|
|Ottimizzazione GPO|IDG_VS_PGO_SELECTION|
|Varie|IDG_VS_BUILD_MISC|
|Annulla|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Gruppi di menu Strumenti

|Gruppo|ID|
|-----------|--------|
|Riga di comando|IDG_VS_TOOLS_CMDLINE|
|Frammenti di codice|IDG_VS_TOOLS_SNIPPETS|
|Sottoinsieme di oggetti|IDG_VS_TOOLS_OBJSUBSET|
|Opzioni|IDG_VS_TOOLS_OPTIONS|
|Altri 2|IDG_VS_TOOLS_OTHER2|
|Strumenti esterni|IDG_VS_TOOLS_EXT_TOOLS|
|Personalizzazioni esterne|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Gruppi di menu della finestra

|Gruppo|ID|
|-----------|--------|
|Nuovo|IDG_VS_WINDOW_NEW|
|Ancoraggio/Chiusura|IDG_VS_DOCKCLOSE|
|Ancora/Nascondi|IDG_VS_DOCKHIDE|
|Disponi|IDG_VS_WINDOW_ARRANGE|
|Navigazione|IDG_VS_WINDOW_NAVIGATION|
|Elenco|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Gruppi di menu della Guida

|Gruppo|ID|
|-----------|--------|
|Esempi|IDG_VS_HELP_SAMPLES|
|Supporto|IDG_VS_HELP_SUPPORT|
|Informazioni|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Sottomenu dei menu di Visual Studio
 Nella gerarchia seguente vengono illustrati i sottomenu associati ai menu nella barra dei menu di Visual Studio. Poiché solo un gruppo può avere un menu come padre, ogni sottomenu deve scendere da un gruppo in un menu, anziché direttamente dal menu. Per ulteriori informazioni sulla relazione tra menu, gruppi e sottomenu, consultate [Aggiungere un sottomenu a un menu.](../../extensibility/adding-a-submenu-to-a-menu.md)

> [!NOTE]
> I nomi dei menu sulla barra dei menu di Visual Studio non vengono visualizzati separatamente in questa gerarchia perché possono essere dedotti dalla convenzione di denominazione per i gruppi nell'IDE, come indicato di seguito: *IDG_VS_\<Nome menu\>_\<Nome\>gruppo*.

|Gruppo padre|Sottomenu|Gruppi figlio|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1... 6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>Vedere anche
- [GUID e GUID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUID e GLI URL dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
