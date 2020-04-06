---
title: Salvataggio di un documento personalizzato Documenti Microsoft
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
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705620"
---
# <a name="saving-a-custom-document"></a>Salvataggio di un documento personalizzato
L'ambiente gestisce i comandi **Salva**, **Salva con nome**e Salva **tutto** . Quando un utente sceglie **Salva**, **Salva**con nome **o Salva tutto** dal menu **File** o chiude la soluzione, generando un processo Salva tutto, si verifica il processo seguente.

 ![Salvataggio dell'editor clienti](../../extensibility/internals/media/private.gif "Privato") Gestione dei comandi Salva, Salva con nome e Salva tutto per un editor personalizzato

 Questo processo è descritto nei passaggi seguenti:This process is detailed in the following steps:

1. Per i comandi **Salva** e Salva <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> con **nome,** l'ambiente utilizza il servizio per determinare la finestra del documento attivo e quindi gli elementi da salvare. Una volta nota la finestra del documento attivo, l'ambiente trova il puntatore della gerarchia e l'identificatore di elemento (itemID) per il documento nella tabella dei documenti in esecuzione. Per ulteriori informazioni, vedere [Esecuzione della tabella documenti](../../extensibility/internals/running-document-table.md).

     Per il comando Salva tutto, l'ambiente utilizza le informazioni nella tabella dei documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> riceve una chiamata, scorre il set di elementi selezionati, ovvero <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> le selezioni multiple esposte dal servizio.

3. Su ogni elemento nella selezione, la soluzione utilizza <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> il puntatore della gerarchia per chiamare il metodo per determinare se il comando di menu Salva deve essere abilitato. Se uno o più elementi sono sporchi, il comando Salva è abilitato. Se la gerarchia utilizza un editor standard, la gerarchia delega <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> l'esecuzione di query per lo stato dirty all'editor chiamando il metodo .

4. Su ogni elemento selezionato che è dirty, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> soluzione utilizza il puntatore della gerarchia per chiamare il metodo sulle gerarchie appropriate.

     Nel caso di un editor personalizzato, la comunicazione tra l'oggetto dati del documento e il progetto è privata. Pertanto, eventuali problemi di persistenza speciali vengono gestiti tra questi due oggetti.

    > [!NOTE]
    > Se si implementa la persistenza, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> assicurarsi di chiamare il metodo per risparmiare tempo. Questo metodo verifica che sia sicuro salvare il file (ad esempio, il file non è di sola lettura).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
