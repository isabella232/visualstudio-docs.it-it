---
title: GUID e ID dei menu di Visual Studio | Microsoft Docs
description: Visualizzare un elenco di valori GUID e ID per i menu e i gruppi nella barra dei menu di Visual Studio inclusa nell'IDE di Visual Studio Integrated Development Environment.
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9f5066c5ae5c9fa57517406b8eca388747979c4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082088"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e ID dei menu di Visual Studio
Questo articolo enumera i valori GUID e ID dei menu e dei gruppi sulla barra dei menu di Visual Studio. Questi valori sono definiti nei file con *estensione vsct* installati come parte di Visual Studio SDK. Per altre informazioni, vedere [comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Per altre informazioni su come usare gli oggetti Integrated Development Environment (IDE) definiti nei file *vsct* , vedere [estendere i menu e i comandi](../../extensibility/extending-menus-and-commands.md).

 I menu e i gruppi sulla barra dei menu di Visual Studio usano il GUID `guidSHLMainMenu` . La barra dei menu ha un ID `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppi sulla barra dei menu di Visual Studio
 Per aggiungere un menu alla barra dei menu, impostare uno di questi gruppi come padre.

|Group|ID|
|-----------|--------|
|File/modifica/visualizzazione|IDG_VS_MM_FILEEDITVIEW|
|Refactoring|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Compilazione|IDG_VS_MM_BUILDDEBUGRUN|
|Formato/strumenti|IDG_VS_MM_TOOLSADDINS|
|Finestra/Guida/community|IDG_VS_MM_WINDOWHELP|
|Add-in|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu sulla barra dei menu di Visual Studio
 Per aggiungere un gruppo a un menu di Visual Studio esistente, impostare uno dei seguenti menu come padre. I sottomenu non sono inclusi in questo elenco.

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

## <a name="groups-on-visual-studio-menus"></a>Gruppi nei menu di Visual Studio
 Gli elenchi seguenti illustrano i gruppi che scendono direttamente dai menu della barra dei menu di Visual Studio. Il modo più rapido per aggiungere un comando a un menu di Visual Studio consiste nell'impostare uno di questi gruppi come padre. I gruppi che discendono dai sottomenu non vengono visualizzati in questa sezione.

### <a name="file-menu-groups"></a>Gruppi di menu file

|Group|ID|
|-----------|--------|
|Nuovo/Apri|IDG_VS_FILE_FILE|
|Add|IDG_VS_FILE_ADD|
|Soluzione|IDG_VS_FILE_SOLUTION|
|Varie|IDG_VS_FILE_MISC|
|Salva|IDG_VS_FILE_SAVE|
|Rinominare|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Stampa|IDG_VS_FILE_PRINT|
|Usati più di recente|IDG_VS_FILE_MRU|
|Sposta|IDG_VS_FILE_MOVE|
|Esci|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Modifica gruppi di menu

|Group|ID|
|-----------|--------|
|Annullamento/ripristino|IDG_VS_EDIT_UNDOREDO|
|Taglia/copia/incolla|IDG_VS_EDIT_CUTCOPY|
|Select|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|Oggetti|IDG_VS_EDIT_OBJECTS|
|Verbi OLE|IDG_VS_EDIT_OLEVERBS|
|Ben comando|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Gruppi di menu di refactoring

|Group|ID|
|-----------|--------|
|Comuni|IDG_REFACTORING_COMMON|
|Avanzato|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Visualizza gruppi di menu

|Group|ID|
|-----------|--------|
|Codice modulo|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definire le viste|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Finestre Architect|IDG_VS_VIEW_ARCH_WINDOWS|
|Finestre dell'organizzazione|IDG_VS_VIEW_ORG_WINDOWS|
|Browser del codice|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Finestre di sviluppo|IDG_VS_VIEW_DEV_WINDOWS|
|Barre degli strumenti|IDG_VS_VIEW_TOOLBARS|
|Simboli|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Esplorare|IDG_VS_VIEW_NAVIGATE|
|Esplorazione piccola|IDG_VS_VIEW_SMALLNAVIGATE|
|Visualizzatore oggetti|IDG_VS_VIEW_OBJBRWSR|
|Ben comando|IDG_VS_VIEW_COMMANDWELL|
|Pagine delle proprietà|IDG_VS_VIEW_PROPPAGES|
|Aggiorna|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Gruppi di menu progetto

|Group|ID|
|-----------|--------|
|Aggiunta di varie|IDG_VS_PROJ_MISCADD|
|Add|IDG_VS_PROJ_ADD|
|Cartella|IDG_VS_PROJ_FOLDER|
|Scarica/ricarica|IDG_VS_PROJ_UNLOADRELOAD|
|Riferimento|IDG_VS_PROJ_REFERENCE|
|Opzioni|IDG_VS_PROJ_OPTIONS|
|Impostazioni|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Gruppi di menu Compila

|Group|ID|
|-----------|--------|
|Soluzione|IDG_VS_BUILD_SOLUTION|
|Selezione|IDG_VS_BUILD_SELECTION|
|Ottimizzazione GPO|IDG_VS_PGO_SELECTION|
|Varie|IDG_VS_BUILD_MISC|
|Annulla|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Gruppi di menu strumenti

|Group|ID|
|-----------|--------|
|Riga di comando|IDG_VS_TOOLS_CMDLINE|
|Frammenti di codice|IDG_VS_TOOLS_SNIPPETS|
|Subset di oggetti|IDG_VS_TOOLS_OBJSUBSET|
|Opzioni|IDG_VS_TOOLS_OPTIONS|
|Altro 2|IDG_VS_TOOLS_OTHER2|
|Strumenti esterni|IDG_VS_TOOLS_EXT_TOOLS|
|Personalizzazioni esterne|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Gruppi di menu finestra

|Group|ID|
|-----------|--------|
|Nuova|IDG_VS_WINDOW_NEW|
|Ancoraggio/chiusura|IDG_VS_DOCKCLOSE|
|Ancoraggio/Nascondi|IDG_VS_DOCKHIDE|
|Disponi|IDG_VS_WINDOW_ARRANGE|
|Spostamento|IDG_VS_WINDOW_NAVIGATION|
|Elenco|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Gruppi di menu della Guida

|Group|ID|
|-----------|--------|
|Esempi|IDG_VS_HELP_SAMPLES|
|Supporto|IDG_VS_HELP_SUPPORT|
|Informazioni|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Sottomenu dei menu di Visual Studio
 La gerarchia seguente mostra i sottomenu associati ai menu sulla barra dei menu di Visual Studio. Poiché solo un gruppo può avere un menu come padre, ogni sottomenu deve scendere da un gruppo in un menu, anziché direttamente dal menu. Per ulteriori informazioni sulla relazione tra menu, gruppi e sottomenu, vedere [aggiungere un sottomenu a un menu](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> I nomi dei menu sulla barra dei menu di Visual Studio non vengono visualizzati separatamente in questa gerarchia perché possono essere dedotti dalla convenzione di denominazione per i gruppi nell'IDE, come indicato di seguito: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

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
- [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
