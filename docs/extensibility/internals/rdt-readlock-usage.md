---
title: Utilizzo RDT_ReadLock | Microsoft Docs
description: Informazioni sul _VSRDTFLAGS. RDT_ReadLock flag, che fornisce la logica per il blocco di un documento nella tabella documenti in esecuzione.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2c946d69cf1aded072d27e7c6ccbdf28f1122571
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875388"
---
# <a name="rdt_readlock-usage"></a>Uso di RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) è un flag che fornisce la logica per il blocco di un documento nella tabella documenti in esecuzione (RDT), che è l'elenco di tutti i documenti attualmente aperti nell'IDE di Visual Studio. Questo flag determina quando i documenti vengono aperti e se un documento è visibile nell'interfaccia utente o viene mantenuto in memoria.

In genere si usa [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) quando si verifica una delle condizioni seguenti:

- Si vuole aprire un documento in modo invisibile e di sola lettura, ma non è ancora stato stabilito che <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dovrebbe essere il proprietario.

- Si desidera che all'utente venga richiesto di salvare un documento che è stato aperto in modo invisibile prima che l'utente lo visualizzasse nell'interfaccia utente e quindi tentasse di chiuderlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Come gestire documenti visibili e invisibili

Quando un utente apre un documento nell'interfaccia utente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> deve essere stabilito un proprietario per il documento e un [_VSRDTFLAGS. ](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) È necessario impostare RDT_EditLock flag. Se non <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> è possibile stabilire alcun proprietario, il documento non verrà salvato quando l'utente fa clic su **Salva tutto** o chiude l'IDE. Ciò significa che se un documento è aperto in modo invisibile quando viene modificato in memoria e all'utente viene richiesto di salvare il documento in caso di arresto o di salvataggio se si sceglie **Salva tutto** , `RDT_ReadLock` non sarà possibile utilizzare un oggetto. Al contrario, è necessario usare un `RDT_EditLock` e registrare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> quando un [__VSREGDOCLOCKHOLDER. Flag RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) .

## <a name="rdt_editlock-and-document-modification"></a>Modifica di RDT_EditLock e documenti

Il flag precedente indicato indica che l'apertura invisibile del documento verrà restituita `RDT_EditLock` quando il documento viene aperto dall'utente in un **DocumentWindow** visibile. Quando si verifica questo problema, all'utente viene visualizzata una richiesta di **salvataggio** quando il **DocumentWindow** visibile viene chiuso. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` le implementazioni che utilizzano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> servizio funzionano inizialmente quando viene eseguito solo un oggetto `RDT_ReadLock` , ad esempio quando il documento viene aperto in modo invisibile per analizzare le informazioni. In seguito, se il documento deve essere modificato, il blocco viene aggiornato a un **RDT_EditLock** vulnerabile. Se l'utente apre il documento in un **DocumentWindow** visibile, `CodeModel` viene rilasciato l'oggetto vulnerabile `RDT_EditLock` .

Se l'utente chiude il **DocumentWindow** e sceglie **No** quando viene richiesto di salvare il documento aperto, l' `CodeModel` implementazione Elimina tutte le informazioni nel documento e riapre il documento dal disco in modo invisibile alla successiva richiesta di ulteriori informazioni per il documento. La sottigliezza di questo comportamento è un'istanza in cui l'utente apre il **DocumentWindow** del documento invisibile aperto, lo modifica, lo chiude e quindi sceglie **No** quando viene richiesto di salvare il documento. In questo caso, se il documento dispone di un `RDT_ReadLock` , il documento non verrà effettivamente chiuso e il documento modificato rimarrà aperto in modo invisibile in memoria, anche se l'utente ha scelto di non salvare il documento.

Se l'apertura invisibile del documento utilizza un oggetto debole `RDT_EditLock` , viene restituito il blocco quando l'utente apre il documento in modo visibile e non vengono mantenuti altri blocchi. Quando l'utente chiude il **DocumentWindow** e sceglie **No** quando viene richiesto di salvare il documento, il documento deve essere chiuso dalla memoria. Ciò significa che il client invisibile deve restare in ascolto degli eventi di RDT per tenere traccia dell'occorrenza. La volta successiva che il documento è necessario, il documento deve essere riaperto.
