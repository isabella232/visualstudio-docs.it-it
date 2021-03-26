---
title: IDE-Defined comandi per estendere i sistemi di progetto | Microsoft Docs
description: Informazioni sui comandi e sui gruppi di comandi definiti in Visual Studio Integrated Development Environment (IDE) usati per estendere i sistemi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fedca7081c531fef257e20e64426f8b35e88e87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086001"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandi definiti dall'IDE per l'estensione dei sistemi di progetto
Quando si desidera estendere i sistemi del progetto, è possibile utilizzare i comandi e i gruppi di comandi forniti dall' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Le sezioni seguenti elencano gli elementi del comando particolarmente utili per l'estensione dei sistemi di progetto.

## <a name="command-menus"></a>Menu di comando
 La tabella seguente illustra i menu di comando che sono posizioni utili per l'inserimento di comandi di alto livello che richiamano un'estensione di progetto.

|Menu di comando|Descrizione|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Menu di primo livello del **progetto** .|
|IDM_VS_TOOL_PROJWIN|Barra degli strumenti **Esplora soluzioni** .|

## <a name="shortcut-menus"></a>Menu di scelta rapida
 Nella tabella seguente vengono illustrati i menu di scelta rapida che si applicano quando si seleziona un singolo nodo nel **Esplora soluzioni** o quando sono presenti più selezioni omogenee nell' **Esplora soluzioni**, ovvero quando tutti i nodi selezionati sono dello stesso tipo.

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Si applica quando viene selezionato il nodo del progetto.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Si applica quando viene selezionato un file.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Si applica quando si seleziona una cartella.|
|IDM_VS_CTXT_WEBREFFOLDER|Si applica quando viene selezionata la cartella dei riferimenti Web.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Si applica quando viene selezionato il nodo radice dei riferimenti denominato "References".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Si applica quando sono selezionati i nodi di riferimento; sono inclusi solo i riferimenti a assembly, COM e progetto. Non include i riferimenti Web.|

 Nella tabella seguente vengono illustrati i menu di scelta rapida che si applicano quando la selezione nel **Esplora soluzioni** si estende su più gerarchie.

|Menu di scelta rapida|Descrizione|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Si applica quando la selezione corrente contiene i nodi del nodo della soluzione e del progetto radice.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Si applica quando la selezione corrente contiene il nodo della soluzione e gli elementi del progetto.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Si applica quando la selezione corrente è costituita solo da più nodi di progetto radice.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Si applica quando la selezione corrente contiene una combinazione di nodi di progetto radice ed elementi di progetto. La selezione può inoltre contenere il nodo della soluzione.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Si applica quando la selezione corrente contiene elementi di progetto di più progetti nella soluzione oppure quando nello stesso progetto vengono selezionati elementi di tipi diversi.|

## <a name="command-groups"></a>Gruppi di comandi
 La tabella seguente illustra i gruppi di comandi che è possibile usare quando si estendono i progetti e a cui è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu di scelta rapida.

|Gruppo di comandi|Descrizione|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Comandi per la compilazione, la ricompilazione e la distribuzione del progetto.|
|IDG_VS_CTXT_COMPILELINK|Comandi per la compilazione e il collegamento del progetto.|
|IDG_VS_CTXT_PROJECT_CONFIG|Comandi che impostano la configurazione e l'ordine di compilazione del progetto.|
|IDG_VS_CTXT_PROJECT_ADD|Comandi che aggiungono elementi al progetto.|
|IDG_VS_CTXT_PROJECT_START|Comandi che impostano il progetto di avvio associato al tasto F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Comandi per il salvataggio degli elementi del progetto.|
|IDG_VS_CTXT_PROJECT_DEBUG|Comandi per il debug.|
|IDG_VS_CTXT_PROJECT_SCC|Comandi per il controllo del codice sorgente.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandi per operazioni Taglia, copia e incolla.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Comandi che consentono di accedere alla finestra di dialogo delle **proprietà del progetto** .|

## <a name="see-also"></a>Vedi anche

- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md)
