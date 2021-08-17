---
title: Salvataggio di un documento personalizzato | Microsoft Docs
description: Informazioni sul processo che si verifica per un documento personalizzato per un tipo di progetto aggiunto all'IDE Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ae3e4fd732b4a0a296701b137fa158eb5926162b11f1cdaf8988c2f4ed3a10bb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401239"
---
# <a name="saving-a-custom-document"></a>Salvataggio di un documento personalizzato
L'ambiente gestisce **i comandi Salva**, Salva **con** nome **e Salva** tutto . Quando un utente fa clic  su Salva **,** Salva con nome o Salva tutto dal menu **File** o chiude la soluzione, determinando un'operazione Salva tutto, si verifica il processo seguente.

 ![Salvataggio dell'editor del cliente](../../extensibility/internals/media/private.gif "Privato") Gestione dei comandi Salva, Salva con nome e Salva tutto per un editor personalizzato

 Questo processo è descritto in dettaglio nei passaggi seguenti:

1. Per i **comandi Salva** e Salva **con nome,** l'ambiente usa il servizio per determinare la finestra del documento attivo e quindi gli <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> elementi da salvare. Una volta nota la finestra del documento attivo, l'ambiente trova il puntatore della gerarchia e l'identificatore dell'elemento (itemID) per il documento nella tabella del documento in esecuzione. Per altre informazioni, vedere [Running Document Table](../../extensibility/internals/running-document-table.md).

     Per il comando Salva tutto, l'ambiente usa le informazioni nella tabella del documento in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione riceve una chiamata, scorre il set di elementi selezionati, ovvero le selezioni multiple esposte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio.

3. Per ogni elemento nella selezione, la soluzione usa il puntatore della gerarchia per chiamare il metodo per determinare se il comando di menu Salva <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> deve essere abilitato. Se uno o più elementi sono dirty, il comando Salva è abilitato. Se la gerarchia usa un editor standard, la gerarchia delega l'esecuzione di query per lo stato dirty all'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metodo .

4. Per ogni elemento selezionato modificato, la soluzione usa il puntatore della gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodo sulle gerarchie appropriate.

     Nel caso di un editor personalizzato, la comunicazione tra l'oggetto dati del documento e il progetto è privata. Pertanto, eventuali problemi di persistenza speciali vengono gestiti tra questi due oggetti.

    > [!NOTE]
    > Se si implementa la persistenza personalizzata, assicurarsi di chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodo per risparmiare tempo. Questo metodo verifica che sia possibile salvare il file in modo sicuro, ad esempio se il file non è di sola lettura.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
