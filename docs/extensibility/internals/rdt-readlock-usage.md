---
title: Utilizzo di RDT_ReadLock Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705921"
---
# <a name="rdt_readlock-usage"></a>Uso di RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) è un flag che fornisce la logica per il blocco di un documento nella tabella documenti in esecuzione (RDT), ovvero l'elenco di tutti i documenti attualmente aperti nell'IDE di Visual Studio. Questo flag determina quando i documenti vengono aperti e se un documento è visibile nell'interfaccia utente o mantenuto invisibile in memoria.

In genere, si utilizza [no di _VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) in caso di una delle seguenti condizioni:

- Si desidera aprire un documento in modo invisibile e di sola <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> lettura, ma non è ancora stabilito che dovrebbe essere il proprietario.

- Si desidera che all'utente venga richiesto di salvare un documento che è stato aperto in modo invisibilmente prima che l'utente lo visualizzasse nell'interfaccia utente e quindi tentasse di chiuderlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Come gestire i documenti visibili e invisibili

Quando un utente apre un documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nell'interfaccia utente, è necessario stabilire un proprietario per il documento e [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) flag deve essere impostato. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> non è possibile stabilire alcun proprietario, il documento non verrà salvato quando l'utente fa clic su **Salva tutto** o chiude l'IDE. Ciò significa che se un documento è aperto in modo invisibilmente dove viene modificato in memoria e all'utente viene richiesto di salvare il documento all'arresto o al salvataggio se si seleziona **Salva tutto,** non è possibile utilizzare un `RDT_ReadLock` file. Al contrario, `RDT_EditLock` è necessario <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> utilizzare un e registrare un quando un [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) bandiera.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock e modifica del documento

Il flag precedente menzionato indica che l'apertura `RDT_EditLock` invisibile del documento produrrà la sua quando il documento viene aperto dall'utente in un **visibile DocumentWindow**. In questo caso, all'utente viene visualizzato un prompt **di salvataggio** quando il visibile **DocumentWindow** viene chiuso. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`le implementazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> che utilizzano il `RDT_ReadLock` servizio funzionano inizialmente quando viene eseguito solo un oggetto (ad esempio, quando il documento viene aperto in modo invisibile per analizzare le informazioni). Successivamente, se il documento deve essere modificato, il blocco viene aggiornato a un **RDT_EditLock**debole . Se l'utente apre quindi il documento `CodeModel`in un `RDT_EditLock` oggetto **visibile DocumentWindow**, viene rilasciato il debole 's weak.

Se l'utente chiude quindi **il DocumentWindow** e sceglie **No** quando viene `CodeModel` richiesto di salvare il documento aperto, l'implementazione elimina tutte le informazioni nel documento e riapre il documento dal disco in modo invisibilmente la volta successiva che sono necessarie ulteriori informazioni per il documento. La sottigliezza di questo comportamento è un'istanza in cui l'utente apre il **DocumentWindow** del documento aperto invisibile, lo modifica, lo chiude e quindi sceglie **No** quando viene richiesto di salvare il documento. In questo caso, se `RDT_ReadLock`il documento ha un oggetto , il documento non verrà effettivamente chiuso e il documento modificato rimarrà aperto in modo invitante in memoria, anche se l'utente ha scelto di non salvare il documento.

Se l'apertura invisibile del `RDT_EditLock`documento utilizza un debole , quindi restituisce il suo blocco quando l'utente apre il documento visibilmente e non vengono mantenuti altri blocchi. Quando l'utente chiude il **DocumentWindow** e sceglie **No** quando viene richiesto di salvare il documento, quindi il documento deve essere chiuso dalla memoria. Ciò significa che il client invisibile deve restare in ascolto degli eventi RDT per tenere traccia di questa occorrenza. La volta successiva che il documento è necessario, il documento deve essere riaperto.
