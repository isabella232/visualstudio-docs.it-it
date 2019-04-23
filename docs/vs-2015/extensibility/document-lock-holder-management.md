---
title: Gestione dei detentori di blocchi del documento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73c6151b5c02cb81a10c2725091c16457db70e33
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056822"
---
# <a name="document-lock-holder-management"></a>Gestione dei detentori di blocchi dei documenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tabella documenti in esecuzione (RDT) mantiene un conteggio di documenti aperti e dispongono di eventuali blocchi di modifica. Quando viene modificata a livello di codice in background senza visualizzare un documento aperto in una finestra del documento, è possibile inserire un blocco di modifica in un documento nella RDT. Questa funzionalità viene spesso usata dagli strumenti di progettazione che modificano più file tramite un'interfaccia utente grafica.  
  
## <a name="document-lock-holder-scenarios"></a>Scenari titolare di blocco del documento  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>File "a" non ha una dipendenza dalla File "b"  
 Si consideri una situazione in cui viene implementata un editor standard "A" per il tipo di file "a" e ogni file di tipo "a" contiene un riferimento a (o la dipendenza dalla) un file di tipo "b". Per i file di tipo "b" è presente un editor standard di "B". Quando viene aperto l'editor "A" file "a" it recupera il riferimento al file corrispondente "b". File "b" non è visualizzato, ma editor "A" può essere modificato. Editor "A" Ottiene un riferimento ai dati del documento del file "b" dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo e gestisce anche un blocco di modifica nel file "b". Al termine dell'editor "A" modifica di file "b" è possibile diminuire il blocco di modifica figure professionali annovera file "b" chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> (metodo). È possibile omettere questo passaggio se si chiamasse il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo con il parametro `dwRDTLockType` impostato su <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>File "b" viene aperto da un altro Editor  
 Nel caso in cui il file "b" è già aperto per "B" editor quando si tenta di aprire editor "A", esistono due scenari distinti per gestire:  
  
- Se il file "b" è aperto in un editor compatibile, è necessario disporre dell'editor "A" Registra un blocco di modifica del documento sull'uso di file "b" il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> (metodo). Dopo che l'editor "A" avviene la modifica dei file "b", annullare la registrazione del documento Modifica blocco usando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> (metodo).  
  
- Se il file "b" è aperto in modo non compatibile, è possibile consentire l'apertura del file "b" effettuata è fallita dall'editor "A" hanno esito negativo oppure è possibile consentire la visualizzazione associata all'editor "A" parzialmente apre e visualizza un messaggio di errore appropriato. Il messaggio di errore dovrebbe indicare all'utente per chiudere il file "b" nell'editor non compatibile e quindi aprire nuovamente file "a" tramite editor "A". È anche possibile implementare il [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> per richiedere all'utente di chiudere il file "b" che viene aperto nell'editor non compatibile. Se l'utente chiude il file "b", l'apertura del file "a" nell'editor "A" continua normalmente.  
  
## <a name="additional-document-edit-lock-considerations"></a>Considerazioni sul blocco di modifica del documento aggiuntivo  
 Si verifica un comportamento diverso se editor "A" è l'unico editor che ha un documento di modifica blocco sul file "b", quello che si avrebbe se editor "B" contiene anche un documento di modifica blocco sul file "b". Nelle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **Progettazione classi** è riportato un esempio di una finestra di progettazione visiva che non viene mantenuto un blocco di modifica il file di codice associato. Vale a dire, se l'utente ha un diagramma classi aperto in visualizzazione progettazione e contemporaneamente aprire il file di codice associato, e se l'utente modifica il file di codice, ma non salvare le modifiche, le modifiche sono inoltre perse al file di diagramma (. CD) della classe. Se il **Progettazione classi** ha il solo documento Modifica blocco sul file di codice, all'utente non è richiesto per salvare le modifiche quando si chiude il file di codice. L'IDE chiede all'utente di salvare le modifiche solo dopo che l'utente chiude il **Progettazione classi**. Le modifiche salvate vengono riflesse in entrambi i file. Se entrambi i **Progettazione classi** l'editor di file di codice mantenuti attivi i blocchi di modifica del documento nel file di codice, quindi l'utente viene richiesto di salvare durante la chiusura del file di codice o del form. A questo punto le modifiche salvate vengono riflesse in forma e il file di codice. Per altre informazioni sui diagrammi classi, vedere [utilizzo dei diagrammi classi (Progettazione classi)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Si noti che se è necessario inserire un blocco di modifica in un documento per un editor diverso, è necessario implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia.  
  
 Numero di volte una progettazione interfaccia utente che modifica i file di codice a livello di codice apporta modifiche a più di un file. In questi casi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> metodo gestisce il salvataggio di uno o più documenti tramite il **si desidera salvare le modifiche apportate agli elementi seguenti?** nella finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella documenti in esecuzione](../extensibility/internals/running-document-table.md)   
 [Salvataggio permanente e tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
