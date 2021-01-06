---
title: Salvataggio di un documento personalizzato | Microsoft Docs
description: Informazioni sul processo che si verifica per un documento personalizzato per un tipo di progetto aggiunto all'IDE di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2d2aa249d6944e33ab9556000c483efdec78f20
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875679"
---
# <a name="saving-a-custom-document"></a>Salvataggio di un documento personalizzato
L'ambiente gestisce i comandi **Salva**, **Salva con nome** e **Salva tutti** . Quando un utente fa clic su **Salva**, **Salva con nome** **o Salva tutto** dal menu **file** o chiude la soluzione, generando un salvataggio, si verifica il processo seguente.

 ![Salvataggio dell'editor del cliente](../../extensibility/internals/media/private.gif "Privato") Salva, Salva con nome e Salva tutte le operazioni di gestione dei comandi per un editor personalizzato

 Questo processo è descritto in dettaglio nei passaggi seguenti:

1. Per i comandi **Salva** e **Salva con nome** , l'ambiente USA il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio per determinare la finestra del documento attiva e quindi gli elementi che devono essere salvati. Quando la finestra del documento attivo è nota, l'ambiente trova il puntatore della gerarchia e l'identificatore dell'elemento (itemID) per il documento nella tabella documenti in esecuzione. Per ulteriori informazioni, vedere [esecuzione della tabella documenti](../../extensibility/internals/running-document-table.md).

     Per il comando Salva tutto, l'ambiente USA le informazioni nella tabella documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione riceve una <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiamata, scorre il set di elementi selezionati, ovvero le selezioni multiple esposte dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio.

3. Per ogni elemento della selezione, la soluzione USA il puntatore della gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodo per determinare se il comando di menu Salva deve essere abilitato. Se uno o più elementi sono Dirty, il comando Salva è abilitato. Se la gerarchia usa un editor standard, la gerarchia delega la query per lo stato dirty all'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metodo.

4. Per ogni elemento selezionato Dirty, la soluzione USA il puntatore della gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Metodo sulle gerarchie appropriate.

     Nel caso di un editor personalizzato, la comunicazione tra l'oggetto dati del documento e il progetto è privata. Quindi, eventuali problemi di persistenza speciali vengono gestiti tra questi due oggetti.

    > [!NOTE]
    > Se si implementa la propria persistenza, assicurarsi di chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodo per risparmiare tempo. Questo metodo verifica che sia possibile salvare il file in modo sicuro (ad esempio, il file non è di sola lettura).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
