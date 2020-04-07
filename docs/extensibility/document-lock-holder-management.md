---
title: Gestione del supporto per il blocco dei documenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712133"
---
# <a name="document-lock-holder-management"></a>Gestione dei titolari dei blocchi di documenti

La tabella documenti in esecuzione (RDT) mantiene un conteggio dei documenti aperti e di tutti i blocchi di modifica di cui dispongono. È possibile inserire un blocco di modifica su un documento in RDT quando viene modificato a livello di codice in background senza che l'utente visualizzi un documento aperto in una finestra del documento. Questa funzionalità viene spesso utilizzata dalle finestre di progettazione che modificano più file tramite un'interfaccia utente grafica.

## <a name="document-lock-holder-scenarios"></a>Scenari di supporto del blocco documento

### <a name="file-a-has-a-dependence-on-file-b"></a>Il file "a" ha una dipendenza dal file "b"

Si consideri una situazione in cui si implementa un editor standard "A" per il tipo di file "a" e ogni file di tipo "a" ha un riferimento a (o dipendenza da) un file di tipo "b". Esiste un editor standard "B" per i file di tipo "b". Quando l'editor "A" apre il file "a" recupera il riferimento al file corrispondente "b". Il file "b" non viene visualizzato, ma l'editor "A" può modificarlo. Editor "A" ottiene un riferimento ai dati del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> documento del file "b" dal metodo e mantiene anche un blocco di modifica sul file "b". Dopo che l'editor "A" ha finito di modificare il file "b" <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> è possibile diminuire il conteggio dei blocchi di modifica sul file "b" chiamando il metodo. È possibile omettere questo passaggio <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> se il `dwRDTLockType` metodo è stato chiamato con il parametro impostato su [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Il file "b" viene aperto da un editor diverso

Nel caso in cui il file "b" sia già aperto dall'editor "B" quando l'editor "A" tenta di aprirlo, esistono due scenari separati da gestire:

- Se il file "b" è aperto in un editor compatibile, è necessario che l'editor "A" registri un blocco di modifica del documento sul file "b" utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodo. Dopo che l'editor "A" ha finito di modificare il file <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> "b", annullare la registrazione del blocco di modifica del documento utilizzando il metodo .

- Se il file "b" è aperto in modo incompatibile, è possibile lasciare che il tentativo di apertura del file "b" dall'editor "A" non riesca, oppure è possibile lasciare che la visualizzazione associata all'editor "A" venga parzialmente aperta e visualizzi un messaggio di errore appropriato. Il messaggio di errore dovrebbe indicare all'utente di chiudere il file "b" nell'editor incompatibile e quindi riaprire il file "a" utilizzando l'editor "A". È inoltre possibile [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> implementare il metodo per richiedere all'utente di chiudere il file "b" aperto nell'editor incompatibile. Se l'utente chiude il file "b", l'apertura del file "a" nell'editor "A" continua normalmente.

## <a name="additional-document-edit-lock-considerations"></a>Considerazioni aggiuntive sul blocco della modifica dei documenti

Si ottiene un comportamento diverso se l'editor "A" è l'unico editor che ha un blocco di modifica del documento sul file "b" rispetto a quanto si farebbe se l'editor "B" contiene anche un blocco di modifica del documento sul file "b". In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Progettazione classi** è un esempio di finestra di progettazione visiva che non contiene un blocco di modifica sul file di codice associato. Ovvero, se l'utente dispone di un diagramma classi aperto in visualizzazione progettazione e il file di codice associato aperto contemporaneamente e se l'utente modifica il file di codice ma non salva le modifiche, le modifiche vengono perse anche nel file del diagramma classi (con estensione cd). Se **Progettazione classi** dispone dell'unico blocco di modifica del documento nel file di codice, all'utente non viene chiesto di salvare le modifiche alla chiusura del file di codice. L'IDE chiede all'utente di salvare le modifiche solo dopo che l'utente chiude La finestra di **progettazione**di classi . Le modifiche salvate si riflettono in entrambi i file. Se sia **Progettazione** classi che l'editor di file di codice hanno mantenuto blocchi di modifica del documento nel file di codice, all'utente viene richiesto di salvare alla chiusura del file di codice o del form. A questo punto le modifiche salvate vengono riflesse sia nel modulo che nel file di codice. Per ulteriori informazioni sui diagrammi classi, vedere [Utilizzare i diagrammi classi (Progettazione classi)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Si noti che se è necessario inserire un blocco di modifica <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> su un documento per un non editor, è necessario implementare l'interfaccia.

Spesso una finestra di progettazione dell'interfaccia utente che modifica i file di codice a livello di codice apporta modifiche a più di un file. In questi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> casi il metodo gestisce il salvataggio di uno o più documenti tramite la finestra di dialogo **Salvare le modifiche apportate agli elementi seguenti?** .

## <a name="see-also"></a>Vedere anche

- [Tabella documenti in esecuzione](../extensibility/internals/running-document-table.md)
- [Persistenza e tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
