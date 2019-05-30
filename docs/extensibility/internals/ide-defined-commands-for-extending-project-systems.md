---
title: Comandi definiti dall'IDE per l'estensione di sistemi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49a79a46fdcc6c969a489efb12eefb6bbc674126
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311887"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandi definiti dall'IDE per l'estensione dei sistemi di progetto
Quando si desidera estendere sistemi di progetto, è possibile usare i comandi e comando forniti da gruppi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Le sezioni seguenti elencano gli elementi di comando che risultano particolarmente utili per estendere i sistemi di progetto.

## <a name="command-menus"></a>Menu dei comandi
 La tabella seguente mostra i menu dei comandi che sono percorsi utili per poter immettere comandi di alto livello che richiamano un'estensione di progetto.

|Menu dei comandi|Descrizione|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Il **progetto** menu di primo livello.|
|IDM_VS_TOOL_PROJWIN|Il **Esplora soluzioni** sulla barra degli strumenti.|

## <a name="shortcut-menus"></a>Menu di scelta rapida
 La tabella seguente mostra i menu di scelta rapida che si applicano quando si seleziona un nodo singolo nel **Esplora soluzioni**, o quando sono presenti più selezioni omogenee nel **Esplora soluzioni**, ovvero quando tutti i nodi selezionati sono dello stesso tipo.

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Si applica quando si seleziona il nodo di progetto.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Si applica quando si seleziona un file.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Si applica quando si seleziona una cartella.|
|IDM_VS_CTXT_WEBREFFOLDER|Si applica quando si seleziona la cartella di riferimento Web.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Si applica quando si seleziona il nodo radice riferimenti denominato "Riferimenti".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Si applica quando vengono selezionati i nodi di riferimento; sono inclusi assembly, COM e solo i riferimenti al progetto. Non include riferimenti Web.|

 La tabella seguente mostra i menu di scelta rapida che si applicano quando la selezione nella **Esplora soluzioni** si estende su più gerarchie,

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Si applica quando la selezione corrente contiene il nodo della soluzione e i nodi del progetto radice.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Si applica quando la selezione corrente contiene gli elementi del progetto e del nodo della soluzione.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Si applica quando la selezione corrente è costituito da più radice progetto solo i nodi.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Si applica quando la selezione corrente contiene una combinazione di nodi del progetto radice e gli elementi del progetto. Inoltre, la selezione può contenere il nodo della soluzione.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Si applica quando la selezione corrente contiene elementi di progetto da più progetti nella soluzione, o quando sono selezionati elementi di tipi diversi nello stesso progetto.|

## <a name="command-groups"></a>Gruppi di comandi
 Nella tabella seguente mostra i gruppi di comandi che è possibile usare quando si estendono i progetti e che è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu di scelta rapida.

|Gruppo di comandi|Descrizione|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Comandi di compilazione, ricompilazione e la distribuzione del progetto.|
|IDG_VS_CTXT_COMPILELINK|Comandi per la compilazione e collegamento del progetto.|
|IDG_VS_CTXT_PROJECT_CONFIG|Comandi impostare la configurazione di progetto e ordine di compilazione.|
|IDG_VS_CTXT_PROJECT_ADD|Comandi che aggiungere elementi al progetto.|
|IDG_VS_CTXT_PROJECT_START|Comandi per l'impostazione di progetto di avvio associato con il tasto F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Comandi per il salvataggio di elementi di progetto.|
|IDG_VS_CTXT_PROJECT_DEBUG|Comandi per eseguire il debug.|
|IDG_VS_CTXT_PROJECT_SCC|Comandi di controllo del codice sorgente.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandi per le operazioni Taglia, copia e Incolla le operazioni.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|I comandi che forniscono l'accesso per il **proprietà del progetto** nella finestra di dialogo.|

## <a name="see-also"></a>Vedere anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Confronto tra oggetti MenuCommand e OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md)