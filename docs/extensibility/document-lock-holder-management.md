---
title: Gestione dei contenitori di blocco del documento | Microsoft Docs
description: Informazioni su come inserire un blocco di modifica su un documento nella tabella documenti in esecuzione senza che l'utente visualizzi un documento aperto in una finestra del documento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88e66ed3b0a5434f4d875bf941e3eeffb8adc092
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091188"
---
# <a name="document-lock-holder-management"></a>Gestione dei contenitori di blocco del documento

La tabella documenti in esecuzione (RDT) mantiene un conteggio dei documenti aperti ed eventuali blocchi di modifica. È possibile inserire un blocco di modifica su un documento in RDT quando viene modificato a livello di codice in background senza che l'utente visualizzi un documento aperto in una finestra del documento. Questa funzionalità viene spesso utilizzata da finestre di progettazione che modificano più file tramite un'interfaccia utente grafica.

## <a name="document-lock-holder-scenarios"></a>Scenari di supporto di blocco del documento

### <a name="file-a-has-a-dependence-on-file-b"></a>Il file "a" ha una dipendenza dal file "b"

Si consideri una situazione in cui si implementa un editor standard "A" per il tipo di file "a" e ogni file di tipo "a" ha un riferimento (o dipendenza) a un file di tipo "b". Un editor standard "B" esiste per i file di tipo "b". Quando l'editor "A" apre il file "a", recupera il riferimento al file corrispondente "b". Il file "b" non è visualizzato, ma l'editor "A" può modificarlo. L'editor "A" ottiene un riferimento ai dati del documento del file "b" dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo e mantiene anche un blocco di modifica sul file "b". Dopo che l'editor "A" ha completato la modifica del file "b", è possibile decrementare il numero di blocchi di modifica sul file "b" chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodo. È possibile omettere questo passaggio se è stato chiamato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo con il parametro `dwRDTLockType` impostato su [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Il file "b" è aperto da un altro editor

Nel caso in cui il file "b" sia già aperto dall'editor "B" quando l'editor "A" tenta di aprirlo, è possibile gestire due scenari distinti:

- Se il file "b" è aperto in un editor compatibile, è necessario avere l'editor "A" registrare un blocco di modifica del documento nel file "b" utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodo. Al termine della modifica del file "b", l'editor "A" Annulla la registrazione del blocco di modifica del documento usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metodo.

- Se il file "b" è aperto in modo incompatibile, è possibile lasciare che il tentativo di apertura del file "b" dall'editor "A" abbia esito negativo. in alternativa, è possibile lasciare che la visualizzazione associata all'editor "A" sia parzialmente aperta e visualizzare un messaggio di errore appropriato. Il messaggio di errore deve indicare all'utente di chiudere il file "b" nell'editor non compatibile e quindi riaprire il file "a" utilizzando l'editor "A". È anche possibile implementare il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> per chiedere all'utente di chiudere il file "b" aperto nell'editor non compatibile. Se l'utente chiude il file "b", l'apertura del file "a" nell'editor "A" continuerà normalmente.

## <a name="additional-document-edit-lock-considerations"></a>Considerazioni aggiuntive sui blocchi per la modifica di documenti

Si ottiene un comportamento diverso se l'editor "A" è l'unico editor in cui è presente un blocco di modifica del documento sul file "b" rispetto a quando l'editor "B" contiene anche un blocco di modifica del documento nel file "b". In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Progettazione classi** è un esempio di finestra di progettazione visiva che non tiene un blocco di modifica sul file di codice associato. Ovvero, se l'utente dispone di un diagramma classi aperto in visualizzazione progettazione e il file di codice associato viene aperto simultaneamente e se l'utente modifica il file di codice ma non salva le modifiche, le modifiche andranno perse anche nel file del diagramma classi (con estensione CD). Se il **Progettazione classi** dispone dell'unico blocco di modifica del documento per il file di codice, all'utente non viene richiesto di salvare le modifiche alla chiusura del file di codice. L'IDE chiede all'utente di salvare le modifiche solo dopo che l'utente ha chiuso la **Progettazione classi**. Le modifiche salvate vengono riflesse in entrambi i file. Se il **Progettazione classi** e l'editor del file di codice hanno mantenuto i blocchi di modifica del documento nel file di codice, all'utente viene richiesto di salvare la chiusura del file di codice o del modulo. A questo punto le modifiche salvate vengono riflesse sia nel form che nel file di codice. Per ulteriori informazioni sui diagrammi classi, vedere [utilizzo dei diagrammi classi (Progettazione classi)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Si noti che se è necessario inserire un blocco di modifica su un documento per un non editor, è necessario implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia.

Molte volte una finestra di progettazione dell'interfaccia utente che modifica i file di codice apporta modifiche a livello di codice a più di un file. In questi casi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> metodo gestisce il salvataggio di uno o più documenti per mezzo della finestra di dialogo **Salva le modifiche apportate agli elementi seguenti** .

## <a name="see-also"></a>Vedi anche

- [Tabella documenti in esecuzione](../extensibility/internals/running-document-table.md)
- [Persistenza e tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
