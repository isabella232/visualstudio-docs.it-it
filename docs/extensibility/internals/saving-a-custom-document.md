---
title: Salvataggio di un documento personalizzato | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724082"
---
# <a name="saving-a-custom-document"></a>Salvataggio di un documento personalizzato
L'ambiente gestisce i comandi **Salva**, **Salva con nome**e **Salva tutti** . Quando un utente fa clic su **Salva**, **Salva con nome** **o Salva tutto** dal menu **file** o chiude la soluzione, generando un salvataggio, si verifica il processo seguente.

 ![Salvataggio dell'editor del cliente](../../extensibility/internals/media/private.gif "Private") Salva, Salva con nome e Salva tutte le operazioni di gestione dei comandi per un editor personalizzato

 Questo processo è descritto in dettaglio nei passaggi seguenti:

1. Per i comandi **Salva** e **Salva con nome** , l'ambiente USA il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> per determinare la finestra del documento attiva e quindi gli elementi da salvare. Quando la finestra del documento attivo è nota, l'ambiente trova il puntatore della gerarchia e l'identificatore dell'elemento (itemID) per il documento nella tabella documenti in esecuzione. Per ulteriori informazioni, vedere [esecuzione della tabella documenti](../../extensibility/internals/running-document-table.md).

     Per il comando Salva tutto, l'ambiente USA le informazioni nella tabella documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione riceve una chiamata di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, scorre il set di elementi selezionati, ovvero le selezioni multiple esposte dal servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.

3. Per ogni elemento della selezione, la soluzione USA il puntatore della gerarchia per chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> per determinare se il comando di menu Salva deve essere abilitato. Se uno o più elementi sono Dirty, il comando Salva è abilitato. Se la gerarchia usa un editor standard, la gerarchia delega la query per lo stato dirty all'editor chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Per ogni elemento selezionato Dirty, la soluzione USA il puntatore della gerarchia per chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> sulle gerarchie appropriate.

     Nel caso di un editor personalizzato, la comunicazione tra l'oggetto dati del documento e il progetto è privata. Quindi, eventuali problemi di persistenza speciali vengono gestiti tra questi due oggetti.

    > [!NOTE]
    > Se si implementa la propria persistenza, assicurarsi di chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> per risparmiare tempo. Questo metodo verifica che sia possibile salvare il file in modo sicuro (ad esempio, il file non è di sola lettura).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)