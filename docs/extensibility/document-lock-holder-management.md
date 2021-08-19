---
title: Gestione del titolare del blocco dei documenti | Microsoft Docs
description: Informazioni su come inserire un blocco di modifica su un documento nella tabella del documento in esecuzione senza che l'utente veda un documento aperto in una finestra del documento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: caed437da38206b351634e8f59d04463a221e267
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152510"
---
# <a name="document-lock-holder-management"></a>Gestione del titolare del blocco dei documenti

La tabella di documenti in esecuzione (RDT) mantiene un conteggio di documenti aperti ed eventuali blocchi di modifica di cui dispongono. È possibile inserire un blocco di modifica su un documento in RDT quando viene modificato a livello di codice in background senza che l'utente veda un documento aperto in una finestra del documento. Questa funzionalità viene spesso usata dalle finestre di progettazione che modificano più file tramite un'interfaccia utente grafica.

## <a name="document-lock-holder-scenarios"></a>Scenari del titolare del blocco dei documenti

### <a name="file-a-has-a-dependence-on-file-b"></a>Il file "a" ha una dipendenza dal file "b"

Si consideri una situazione in cui si implementa un editor standard "A" per il tipo di file "a" e ogni file di tipo "a" ha un riferimento a (o dipendenza da) un file di tipo "b". Esiste un editor standard "B" per i file di tipo "b". Quando l'editor "A" apre il file "a", recupera il riferimento al file corrispondente "b". Il file "b" non viene visualizzato, ma l'editor "A" può modificarlo. L'editor "A" ottiene un riferimento ai dati del documento del file "b" dal metodo e mantiene anche un blocco di modifica sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> file "b". Al termine della modifica del file "b" dell'editor "A" è possibile diminuire il numero di blocchi di modifica sul file "b" chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodo . È possibile omettere questo passaggio se è stato chiamato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo con il parametro impostato su `dwRDTLockType` [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Il file "b" viene aperto da un editor diverso

Nel caso in cui il file "b" sia già aperto dall'editor "B" quando l'editor "A" tenta di aprirlo, esistono due scenari distinti da gestire:

- Se il file "b" è aperto in un editor compatibile, è necessario che l'editor "A" registri un blocco di modifica del documento sul file "b" usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodo . Dopo che l'editor "A" ha modificato il file "b", annullare la registrazione del blocco di modifica del documento usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metodo .

- Se il file "b" è aperto in modo incompatibile, è possibile lasciare che il tentativo di apertura del file "b" dall'editor "A" non riesca oppure è possibile consentire la visualizzazione associata all'editor "A" parzialmente aperta e visualizzare un messaggio di errore appropriato. Il messaggio di errore deve indicare all'utente di chiudere il file "b" nell'editor incompatibile e quindi ria aprire il file "a" usando l'editor "A". È anche possibile implementare il metodo per richiedere all'utente di chiudere il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> file "b" aperto nell'editor incompatibile. Se l'utente chiude il file "b", l'apertura del file "a" nell'editor "A" continua normalmente.

## <a name="additional-document-edit-lock-considerations"></a>Considerazioni aggiuntive sul blocco delle modifiche ai documenti

Si ottiene un comportamento diverso se l'editor "A" è l'unico editor con un blocco di modifica del documento sul file "b" rispetto a quello che si farebbe se l'editor "B" contiene anche un blocco di modifica del documento sul file "b". In , Progettazione classi è un esempio di finestra di progettazione visiva che non contiene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un blocco di modifica sul file di codice associato.  Ovvero, se l'utente ha un diagramma classi aperto nella visualizzazione Progettazione e il file di codice associato viene aperto contemporaneamente e se l'utente modifica il file di codice ma non salva le modifiche, le modifiche andranno perse anche nel file del diagramma classi (cd). Se il **Progettazione classi** ha l'unico blocco di modifica del documento sul file di codice, all'utente non viene richiesto di salvare le modifiche alla chiusura del file di codice. L'IDE chiede all'utente di salvare le modifiche solo dopo che l'utente ha chiuso il **Progettazione classi**. Le modifiche salvate vengono riflesse in entrambi i file. Se sia il **Progettazione classi** che l'editor del file di codice hanno mantenuto blocchi di modifica del documento sul file di codice, all'utente viene richiesto di salvare quando si chiude il file di codice o il modulo. A questo punto le modifiche salvate vengono riflesse sia nel form che nel file di codice. Per altre informazioni sui diagrammi classi, vedere [Usare i diagrammi classi (Progettazione classi)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Si noti che se è necessario inserire un blocco di modifica su un documento per un non editor, è necessario implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> l'interfaccia .

Molte volte una finestra di progettazione dell'interfaccia utente che modifica i file di codice a livello di codice apporta modifiche a più file. In questi casi il metodo gestisce il salvataggio di uno o più documenti tramite la finestra di dialogo Salvare le modifiche apportate <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> **agli elementi** seguenti.

## <a name="see-also"></a>Vedi anche

- [Esecuzione della tabella del documento](../extensibility/internals/running-document-table.md)
- [Persistenza e tabella del documento in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
