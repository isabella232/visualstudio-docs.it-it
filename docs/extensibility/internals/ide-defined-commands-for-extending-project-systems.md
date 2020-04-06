---
title: Comandi definiti dall'IDE per l'estensione dei sistemi di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707729"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandi definiti dall'IDE per l'estensione dei sistemi di progetto
Quando si desidera estendere i sistemi di progetto, è [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possibile utilizzare i comandi e i gruppi di comandi forniti dall'IDE.

 Nelle sezioni seguenti sono elencati gli elementi di comando che sono particolarmente utili per estendere i sistemi di progetto.

## <a name="command-menus"></a>Menu dei comandi
 Nella tabella seguente vengono illustrati i menu dei comandi che sono percorsi utili per inserire comandi di alto livello che richiamano un'estensione del progetto.

|Menu dei comandi|Descrizione|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Menu di primo livello **progetto.**|
|IDM_VS_TOOL_PROJWIN|Barra degli strumenti **di Esplora soluzioni.**|

## <a name="shortcut-menus"></a>Menu di scelta rapida
 Nella tabella seguente vengono illustrati i menu di scelta rapida che si applicano quando viene selezionato un singolo nodo in **Esplora soluzioni**o quando sono presenti più selezioni omogenee in **Esplora soluzioni**, ovvero quando tutti i nodi selezionati sono dello stesso tipo.

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Si applica quando viene selezionato il nodo del progetto.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Si applica quando viene selezionato un file.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Si applica quando viene selezionata una cartella.|
|IDM_VS_CTXT_WEBREFFOLDER|Si applica quando è selezionata la cartella Riferimento Web.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Si applica quando viene selezionato il nodo radice dei riferimenti denominato "References".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Si applica quando i nodi di riferimento sono selezionati; questi includono solo riferimenti ad assembly, COM e progetti. Non include riferimenti Web.|

 Nella tabella seguente vengono illustrati i menu di scelta rapida che si applicano quando la selezione in **Esplora soluzioni** si estende su più gerarchie,

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Si applica quando la selezione corrente contiene il nodo della soluzione e i nodi del progetto radice.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Si applica quando la selezione corrente contiene il nodo della soluzione e gli elementi del progetto.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Si applica quando la selezione corrente è costituita solo da più nodi di progetto radice.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Si applica quando la selezione corrente contiene una combinazione di nodi di progetto radice ed elementi di progetto. Inoltre, la selezione può contenere il nodo della soluzione.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Si applica quando la selezione corrente contiene elementi di progetto da più progetti nella soluzione o quando elementi di tipi diversi vengono selezionati nello stesso progetto.|

## <a name="command-groups"></a>Gruppi di comandi
 Nella tabella seguente vengono illustrati i gruppi di comandi che è possibile <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> utilizzare quando si estendono i progetti e a cui è possibile accedere tramite il menu di scelta rapida.

|Gruppo di comandi|Descrizione|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Comandi per la compilazione, la ricompilazione e la distribuzione del progetto.|
|IDG_VS_CTXT_COMPILELINK|Comandi per la compilazione e il collegamento del progetto.|
|IDG_VS_CTXT_PROJECT_CONFIG|Comandi che impostano la configurazione e l'ordine di compilazione del progetto.|
|IDG_VS_CTXT_PROJECT_ADD|Comandi che aggiungono elementi al progetto.|
|IDG_VS_CTXT_PROJECT_START|Comandi che impostano il progetto di avvio associato al tasto F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Comandi per il salvataggio degli elementi di progetto.|
|IDG_VS_CTXT_PROJECT_DEBUG|Comandi per il debug.|
|IDG_VS_CTXT_PROJECT_SCC|Comandi per il controllo del codice sorgente.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandi per le operazioni di taglia, copia e incolla.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Comandi che consentono di accedere alla finestra di dialogo **Proprietà progetto.**|

## <a name="see-also"></a>Vedere anche

- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md)
