---
title: RDT_ReadLock utilizzo | Microsoft Docs
description: Informazioni sul _VSRDTFLAGS. RDT_ReadLock flag , che fornisce la logica per bloccare un documento nella tabella dei documenti in esecuzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 957e67e852baac541cfe62955fa7220ac2e170cdff75c60c82cc58a357396c00
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414441"
---
# <a name="rdt_readlock-usage"></a>Uso di RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) è un flag che fornisce la logica per bloccare un documento nella tabella di documenti in esecuzione, ovvero l'elenco di tutti i documenti attualmente aperti nell'IDE di Visual Studio. Questo flag determina quando vengono aperti i documenti e se un documento è visibile nell'interfaccia utente o mantenuto invisibile in memoria.

In genere, si usa [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) quando si verifica una delle condizioni seguenti:

- Si vuole aprire un documento in modo invisibile e di sola lettura, ma non è ancora stato stabilito quale <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dovrebbe essere il proprietario.

- Si vuole che all'utente venga richiesto di salvare un documento aperto in modo invisibile prima che l'utente lo visualizza nell'interfaccia utente e quindi teda di chiuderlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Come gestire documenti visibili e invisibili

Quando un utente apre un documento nell'interfaccia utente, è necessario stabilire un proprietario per il documento e un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) flag deve essere impostato. Se non è possibile stabilire alcun proprietario, il documento non verrà salvato quando l'utente fa clic su Salva tutto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o chiude  l'IDE. Ciò significa che se un documento viene aperto in modo invisibile in cui viene modificato in  memoria e all'utente viene richiesto di salvare il documento all'arresto o salvato se si sceglie Salva tutto, non è possibile usare `RDT_ReadLock` un oggetto . È invece necessario usare e `RDT_EditLock` registrare un oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> quando un [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) flag.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock e modifica del documento

Il flag precedente indicato indica che l'apertura invisibile del documento restituisce quando il documento viene aperto dall'utente `RDT_EditLock` in **un oggetto DocumentWindow visibile.** In questo caso, all'utente viene visualizzata una richiesta **di** salvataggio quando **l'oggetto DocumentWindow visibile** viene chiuso. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` Le implementazioni che usano inizialmente il servizio funzionano quando viene assunto solo un oggetto , ad esempio quando il documento viene aperto in modo invisibile per <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> analizzare le `RDT_ReadLock` informazioni. In un secondo momento, se il documento deve essere modificato, il blocco viene aggiornato a un RDT_EditLock **.** Se l'utente apre quindi il documento in **un oggetto DocumentWindow visibile,** viene `CodeModel` rilasciato l'elemento debole di `RDT_EditLock` .

Se l'utente chiude **DocumentWindow** e sceglie **No** quando viene richiesto di salvare il documento aperto, l'implementazione elimina tutte le informazioni nel documento e riapre il documento dal disco in modo invisibile alla successiva richiesta di altre informazioni per `CodeModel` il documento. La sottigliezza di questo comportamento è un'istanza in cui l'utente apre **DocumentWindow** del documento aperto invisibile, lo modifica, lo chiude e quindi sceglie **No** quando viene richiesto di salvare il documento. In questo caso, se il documento ha un , il documento non verrà effettivamente chiuso e il documento modificato rimarrà aperto in modo invisibile in memoria, anche se l'utente ha scelto di non salvare il `RDT_ReadLock` documento.

Se l'apertura invisibile del documento usa un oggetto debole, il blocco viene generato quando l'utente apre il documento in modo visibile e non vengono mantenuti `RDT_EditLock` altri blocchi. Quando l'utente chiude **DocumentWindow** e sceglie **No** quando viene richiesto di salvare il documento, il documento deve essere chiuso dalla memoria. Ciò significa che il client invisibile deve restare in ascolto degli eventi RDT per tenere traccia di questa occorrenza. Alla successiva richiesta del documento, il documento deve essere riaperto.
