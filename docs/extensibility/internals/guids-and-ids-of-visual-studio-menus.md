---
title: GUID e ID dei Visual Studio menu | Microsoft Docs
description: Visualizzare un elenco di valori GUID e ID per i menu e i gruppi nella barra dei menu Visual Studio inclusa nell'ambiente Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a35af9a88d42bcc413c5c926d74f34b840d4ea59
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634555"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e ID di Visual Studio menu
Questo articolo enumera i valori GUID e ID dei menu e dei gruppi Visual Studio barra dei menu. Questi valori sono definiti nei *file con estensione vsct* installati come parte di Visual Studio SDK. Per altre informazioni, vedere Comandi, menu e gruppi definiti [dall'IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Per altre informazioni su come usare gli oggetti dell'ambiente di sviluppo integrato (IDE) definiti nei file con estensione *vsct,* vedere [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md).

 I menu e i gruppi nella barra Visual Studio di menu usano il GUID `guidSHLMainMenu` . La barra dei menu stessa ha un ID `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppi sulla barra Visual Studio menu
 Per aggiungere un menu alla barra dei menu, impostare uno di questi gruppi come padre.

|Group|ID|
|-----------|--------|
|File/Modifica/Visualizzazione|IDG_VS_MM_FILEEDITVIEW|
|Refactoring|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Compilazione|IDG_VS_MM_BUILDDEBUGRUN|
|Formato/Strumenti|IDG_VS_MM_TOOLSADDINS|
|Finestra/Guida/Community|IDG_VS_MM_WINDOWHELP|
|Add-in|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu sulla barra Visual Studio menu
 Per aggiungere un gruppo a un menu Visual Studio esistente, impostare uno dei menu seguenti come padre. I sottomenu non sono inclusi in questo elenco.

|Menu|ID|
|----------|--------|
|File|IDM_VS_MENU_FILE|
|Modifica|IDM_VS_MENU_EDIT|
|Visualizzazione|IDM_VS_MENU_VIEW|
|Refactoring|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Compilazione|IDM_VS_MENU_BUILD|
|Formato|IDM_VS_MENU_FORMAT|
|Strumenti|IDM_VS_MENU_TOOLS|
|Estensioni|IDM_VS_MENU_EXTENSIONS|
|Finestra|IDM_VS_MENU_WINDOW|
|Add-in|IDM_VS_MENU_ADDINS|
|Community|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Gruppi nei menu Visual Studio di lavoro
 Gli elenchi seguenti mostrano i gruppi che discendono direttamente dai menu nella barra Visual Studio menu. Il modo più rapido per aggiungere un comando a un menu Visual Studio è impostare uno di questi gruppi come padre. I gruppi che discendono dai sottomenu non vengono visualizzati in questa sezione.

### <a name="file-menu-groups"></a>Gruppi di menu file

|Group|ID|
|-----------|--------|
|Nuovo/Aperto|IDG_VS_FILE_FILE|
|Add|IDG_VS_FILE_ADD|
|Soluzione|IDG_VS_FILE_SOLUTION|
|Varie|IDG_VS_FILE_MISC|
|Salva|IDG_VS_FILE_SAVE|
|Rinominare|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Stampa|IDG_VS_FILE_PRINT|
|Usato più di recente|IDG_VS_FILE_MRU|
|Spostamento|IDG_VS_FILE_MOVE|
|Esci|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Modificare i gruppi di menu

|Group|ID|
|-----------|--------|
|Annullamento/ripristino|IDG_VS_EDIT_UNDOREDO|
|Taglia/Copia/Incolla|IDG_VS_EDIT_CUTCOPY|
|Select|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|Oggetti|IDG_VS_EDIT_OBJECTS|
|Verbi OLE|IDG_VS_EDIT_OLEVERBS|
|Well di comando|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Eseguire il refactoring dei gruppi di menu

|Group|ID|
|-----------|--------|
|Comuni|IDG_REFACTORING_COMMON|
|Avanzato|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Visualizzare i gruppi di menu

|Group|ID|
|-----------|--------|
|Codice modulo|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definire le visualizzazioni|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Progettista Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Organizzazione Windows|IDG_VS_VIEW_ORG_WINDOWS|
|Browser del codice|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Sviluppo Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Barre degli strumenti|IDG_VS_VIEW_TOOLBARS|
|Simboli|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Esplorare|IDG_VS_VIEW_NAVIGATE|
|Esplorazione di piccole dimensioni|IDG_VS_VIEW_SMALLNAVIGATE|
|Visualizzatore oggetti|IDG_VS_VIEW_OBJBRWSR|
|Well di comando|IDG_VS_VIEW_COMMANDWELL|
|Pagine delle proprietà|IDG_VS_VIEW_PROPPAGES|
|Aggiorna|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Project di menu

|Group|ID|
|-----------|--------|
|Aggiunta varie|IDG_VS_PROJ_MISCADD|
|Add|IDG_VS_PROJ_ADD|
|Cartella|IDG_VS_PROJ_FOLDER|
|Scarica/Ricarica|IDG_VS_PROJ_UNLOADRELOAD|
|Riferimento|IDG_VS_PROJ_REFERENCE|
|Opzioni|IDG_VS_PROJ_OPTIONS|
|Impostazioni|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Creare gruppi di menu

|Group|ID|
|-----------|--------|
|Soluzione|IDG_VS_BUILD_SOLUTION|
|Selezione|IDG_VS_BUILD_SELECTION|
|Ottimizzazione GPO|IDG_VS_PGO_SELECTION|
|Varie|IDG_VS_BUILD_MISC|
|Annulla|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Gruppi di menu degli strumenti

|Group|ID|
|-----------|--------|
|Riga di comando|IDG_VS_TOOLS_CMDLINE|
|Frammenti di codice|IDG_VS_TOOLS_SNIPPETS|
|Subset di oggetti|IDG_VS_TOOLS_OBJSUBSET|
|Opzioni|IDG_VS_TOOLS_OPTIONS|
|Altri 2|IDG_VS_TOOLS_OTHER2|
|Strumenti esterni|IDG_VS_TOOLS_EXT_TOOLS|
|Personalizzazioni esterne|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Gruppi di menu delle finestre

|Group|ID|
|-----------|--------|
|Nuova|IDG_VS_WINDOW_NEW|
|Ancora/Chiudi|IDG_VS_DOCKCLOSE|
|Ancora/Nascondi|IDG_VS_DOCKHIDE|
|Disponi|IDG_VS_WINDOW_ARRANGE|
|Spostamento|IDG_VS_WINDOW_NAVIGATION|
|Elenco|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Gruppi di menu della Guida

|Group|ID|
|-----------|--------|
|Esempi|IDG_VS_HELP_SAMPLES|
|Supporto|IDG_VS_HELP_SUPPORT|
|Informazioni|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Sottomenu di Visual Studio menu
 La gerarchia seguente mostra i sottomenu associati ai menu nella barra Visual Studio menu. Poiché solo un gruppo può avere un menu come padre, ogni sottomenu deve derivare da un gruppo in un menu, anziché direttamente dal menu. Per altre informazioni sulla relazione tra menu, gruppi e sottomenu, vedere [Aggiungere un sottomenu a un menu.](../../extensibility/adding-a-submenu-to-a-menu.md)

> [!NOTE]
> I nomi dei menu nella barra dei menu Visual Studio non vengono visualizzati separatamente in questa gerarchia perché possono essere dedominati dalla convenzione di denominazione per i gruppi nell'IDE, come *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

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

## <a name="see-also"></a>Vedi anche
- [GUID e ID delle barre Visual Studio strumenti](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUID e ID di Visual Studio comandi](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
