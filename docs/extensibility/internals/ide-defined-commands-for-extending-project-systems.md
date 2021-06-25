---
title: IDE-Defined comandi per l'estensione dei sistemi di progetto | Microsoft Docs
description: Informazioni sui comandi e sui gruppi di comandi definiti nel Visual Studio di sviluppo integrato (IDE) usato per l'estensione dei sistemi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4525802bf308d740ea5c468fac171e74bff2b34e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901162"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandi definiti dall'IDE per l'estensione dei sistemi di progetto
Per estendere i sistemi di progetto, è possibile usare i comandi e i gruppi di comandi forniti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dall'IDE.

 Le sezioni seguenti elencano gli elementi di comando particolarmente utili per l'estensione dei sistemi di progetto.

## <a name="command-menus"></a>Menu di comando
 La tabella seguente illustra i menu di comando che sono posizioni utili per inserire comandi di alto livello che richiamano un controllo Extender di progetto.

|Menu Di comando|Descrizione|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Menu **di** primo livello progetto.|
|IDM_VS_TOOL_PROJWIN|Barra **Esplora soluzioni** barra degli strumenti.|

## <a name="shortcut-menus"></a>Menu di scelta rapida
 Nella tabella seguente vengono illustrati i menu di scelta rapida che si applicano quando viene selezionato un singolo nodo nel **Esplora soluzioni** o quando sono presenti più selezioni omogenee nel **Esplora soluzioni**, ovvero quando tutti i nodi selezionati sono dello stesso tipo.

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Si applica quando viene selezionato il nodo del progetto.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Si applica quando si seleziona un file.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Si applica quando viene selezionata una cartella.|
|IDM_VS_CTXT_WEBREFFOLDER|Si applica quando è selezionata la cartella Riferimento Web.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Si applica quando il nodo radice dei riferimenti denominato "Riferimenti" è selezionato.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Si applica quando vengono selezionati nodi di riferimento. sono inclusi solo i riferimenti ad assembly, COM e di progetto. Non include riferimenti Web.|

 Nella tabella seguente vengono illustrati i menu di scelta rapida che si applicano quando la selezione nel Esplora soluzioni **si** estende su più gerarchie.

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Si applica quando la selezione corrente contiene il nodo della soluzione e i nodi del progetto radice.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Si applica quando la selezione corrente contiene il nodo della soluzione e gli elementi del progetto.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Si applica quando la selezione corrente è costituita solo da più nodi di progetto radice.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Si applica quando la selezione corrente contiene una combinazione di nodi di progetto radice ed elementi di progetto. Inoltre, la selezione può contenere il nodo della soluzione.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Si applica quando la selezione corrente contiene elementi di progetto da più progetti nella soluzione o quando vengono selezionati elementi di tipi diversi nello stesso progetto.|

## <a name="command-groups"></a>Gruppi di comandi
 Nella tabella seguente vengono illustrati i gruppi di comandi che è possibile utilizzare quando si estendono i progetti e a cui è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu di scelta rapida.

|Gruppo di comandi|Descrizione|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Comandi per la compilazione, la ricompilazione e la distribuzione del progetto.|
|IDG_VS_CTXT_COMPILELINK|Comandi per la compilazione e il collegamento del progetto.|
|IDG_VS_CTXT_PROJECT_CONFIG|Comandi che impostano la configurazione del progetto e l'ordine di compilazione.|
|IDG_VS_CTXT_PROJECT_ADD|Comandi che aggiungono elementi al progetto.|
|IDG_VS_CTXT_PROJECT_START|Comandi che impostano il progetto di avvio associato al tasto F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Comandi per il salvataggio degli elementi di progetto.|
|IDG_VS_CTXT_PROJECT_DEBUG|Comandi per il debug.|
|IDG_VS_CTXT_PROJECT_SCC|Comandi per il controllo del codice sorgente.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandi per le operazioni taglia, copia e incolla.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Comandi che consentono di accedere alla **finestra di dialogo Proprietà** progetto .|

## <a name="see-also"></a>Vedere anche

- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md)
