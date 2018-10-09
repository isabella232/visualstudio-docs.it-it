---
title: Uso di Rdt_readlock | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87f92f525d94ac81231272658c26f7484d93bef8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531127"
---
# <a name="rdtreadlock-usage"></a>Uso di RDT_ReadLock
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [uso di Rdt_readlock](https://docs.microsoft.com/visualstudio/extensibility/internals/rdt-readlock-usage).  
  
<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> è un flag che fornisce la logica per il blocco di un documento in esecuzione nella tabella (documenti), ovvero l'elenco di tutti i documenti attualmente aperti nell'IDE di Visual Studio. Questo flag determina quando vengono aperti i documenti e indica se un documento è visibile nell'interfaccia utente o mantenuto in modo invisibile in memoria.  
  
 In genere, si utilizzerebbe <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> quando una delle operazioni seguenti è vera:  
  
-   Quando si desidera aprire un documento in modo invisibile e sola lettura, ma non è ancora stato stabilito che <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> deve esserne il proprietario.  
  
-   Quando si desidera che l'utente verrà chiesto di salvare un documento che è stato aperto in modo invisibile prima che l'utente viene visualizzato nell'interfaccia utente e quindi ha tentato di chiuderlo.  
  
## <a name="how-to-manage-visible-and-invisible-documents"></a>Come gestire documenti visibili sia invisibili  
 Quando un utente apre un documento nell'interfaccia utente, un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proprietario per il documento deve essere stabilita e un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> flag deve essere impostato. Se nessun <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proprietario può essere stabilito, quindi il documento non verrà salvato quando l'utente sceglie **Salva tutto** o chiude l'IDE. Ciò significa che se un documento viene aperto in modo invisibile in cui viene modificato in memoria e l'utente viene richiesto di salvare il documento in fase di arresto o salvato se **Salva tutto** scelto, un' `RDT_ReadLock` non può essere utilizzato. In alternativa, è necessario usare un `RDT_EditLock` e registrare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> quando un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> flag.  
  
## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock e modifica dei documenti  
<<<<<<< Testa il flag precedente menzionato indica che l'apertura del documento invisibile produrrà relativi `RDT_EditLock` quando il documento viene aperto dall'utente in un oggetto visibile **DocumentWindow**. In questo caso, viene visualizzato con un **salvare** richiedere quando il visibile **DocumentWindow** viene chiuso. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` le implementazioni che usano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> servizio funziona inizialmente quando solo un `RDT_ReadLock` (ad esempio, quando il documento viene aperto in modo invisibile per analizzare le informazioni), viene acquisito. In un secondo momento, se il documento deve essere modificato, quindi il blocco viene aggiornato a un "Weak" **RDT_EditLock**. Se l'utente apre quindi il documento in un oggetto visibile **DocumentWindow**, il `CodeModel`del debole `RDT_EditLock` viene rilasciato.  
=== Il flag precedente menzionato indica che l'apertura del documento invisibile produrrà relativi `RDT_EditLock` quando il documento viene aperto dall'utente in un oggetto visibile **DocumentWindow**. In questo caso, viene visualizzato con un **salvare** richiedere quando il visibile **DocumentWindow** viene chiuso. Implementazioni Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel che usano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> servizio funziona inizialmente quando solo un `RDT_ReadLock` (ad esempio, quando il documento viene aperto in modo invisibile per analizzare le informazioni), viene acquisito. In un secondo momento, se il documento deve essere modificato, quindi il blocco viene aggiornato a un "Weak" **RDT_EditLock**. Se l'utente apre quindi il documento in un oggetto visibile **DocumentWindow**, il `CodeModel`del debole `RDT_EditLock` viene rilasciato.  
>>>>>>> 9c8493a8dd... Provare un nuovo intervallo di moniker per supportare le versioni di combinazione
  
 Se l'utente chiude quindi la **DocumentWindow** e sceglie **No** quando viene richiesto di salvare il documento aperto, il `CodeModel` implementazione Elimina tutte le informazioni nel documento e riapre la documento da disco in modo invisibile al successivo che ulteriori informazioni sono necessarie per il documento. L'importante sottolineare che questo comportamento è un'istanza in cui l'utente apre la **DocumentWindow** del documento aperto invisibile, modificato, lo chiude e poi sceglie **No** quando viene richiesto di salvare il documento. In questo caso, se il documento ha un `RDT_ReadLock`, quindi il documento non verrà effettivamente chiusa e il documento modificato resterà aperto in modo invisibile in memoria, anche se l'utente sceglie di non salvare il documento.  
  
 Se l'apertura del documento invisibile viene utilizzato un "Weak" `RDT_EditLock`, quindi restituisce il blocco quando l'utente apre il documento in modo visibile e non altre i blocchi vengono mantenuti. Quando l'utente chiude il **DocumentWindow** e sceglie **No** quando viene richiesto di salvare il documento, il documento deve essere chiuso dalla memoria. Ciò significa che il client invisibile deve essere in ascolto per gli eventi RDT rilevare questo evento. La volta successiva che il documento è obbligatorio, il documento deve essere riaperta.
