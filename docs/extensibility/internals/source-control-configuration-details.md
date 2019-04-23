---
title: I dettagli di configurazione di controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9a8abb2b1013a7d11a4013d602e33592beff70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070095"
---
# <a name="source-control-configuration-details"></a>Dettagli di configurazione del controllo del codice sorgente
Per implementare il controllo del codice sorgente, è necessario configurare correttamente il sistema di progetto o l'editor per eseguire le operazioni seguenti:

- Richiedere l'autorizzazione per eseguire la transizione allo stato modificato

- Richiedere l'autorizzazione per salvare un file

- Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare i file nel progetto

## <a name="request-permission-to-transition-to-changed-state"></a>Richiedere l'autorizzazione per eseguire la transizione allo stato modificato
 Un editor o il progetto deve richiedere l'autorizzazione per eseguire la transizione allo stato (dirty) modificato chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Ogni editor che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> chiamino <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e aver ricevuto l'approvazione per modificare il documento dall'ambiente prima della restituzione `True` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Un progetto è essenzialmente un editor per un file di progetto e di conseguenza, ha la responsabilità stesso per l'implementazione del rilevamento dello stato modificato per il file di progetto come un editor di testo per i file. L'ambiente gestisce la modifica dello stato della soluzione, ma è necessario gestire la modifica dello stato di qualsiasi oggetto della soluzione fa riferimento a ma non memorizzi, ad esempio un file di progetto o i relativi elementi. In generale, se il progetto o l'editor è responsabile della gestione della persistenza per un elemento, quindi è responsabile dell'implementazione di rilevamento dello stato modificato.

 In risposta al `IVsQueryEditQuerySave2::QueryEditFiles` chiamare, l'ambiente può eseguire le operazioni seguenti:

- Rifiuta la chiamata per la modifica, nel qual caso l'editor o un progetto deve rimanere nello stato unchanged (pulito).

- Indica che i dati del documento devono essere ricaricati. Per un progetto, l'ambiente ricarica i dati per il progetto. Un editor deve ricaricare i dati dal disco tramite relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementazione. In entrambi i casi, è possibile modificare il contesto del progetto o l'editor quando vengano caricato di nuovo i dati.

  È un'attività complessa e difficile adattare appropriato `IVsQueryEditQuerySave2::QueryEditFiles` chiamate in una codebase esistente. Di conseguenza, queste chiamate devono essere integrate durante la creazione del progetto o dell'editor.

## <a name="request-permission-to-save-a-file"></a>Richiedere l'autorizzazione per salvare un File
 Prima di un progetto o un editor Salva un file, è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Per i file di progetto, queste chiamate vengono completate automaticamente per la soluzione, che conosce il momento di salvare un file di progetto. Gli editor sono responsabili per le chiamate a meno che l'implementazione dell'editor di `IVsPersistDocData2` viene utilizzata la funzione helper <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Se l'editor implementa `IVsPersistDocData2` in questo modo, quindi la chiamata a `IVsQueryEditQuerySave2::QuerySaveFile` o `IVsQueryEditQuerySave2::QuerySaveFiles` viene eseguita automaticamente.

> [!NOTE]
>  Sempre effettuare queste chiamate preventivamente, vale a dire alla volta quando l'editor è in grado di ricevere un annullamento.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare i file nel progetto
 Prima di un progetto può aggiungere, rinominare o rimuovere un file o directory, è necessario chiamare appropriato `IVsTrackProjectDocuments2::OnQuery*` metodo per richiedere l'autorizzazione dall'ambiente. Se l'autorizzazione viene concessa, quindi il progetto deve completare l'operazione e quindi chiamare appropriato `IVsTrackProjectDocuments2::OnAfter*` metodo per notificare l'ambiente che l'operazione è stata completata. Il progetto deve chiamare i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaccia per tutti i file (ad esempio, i file speciali) e non solo i file padre. Le chiamate di file sono obbligatori, ma le chiamate di directory sono facoltative. Se il progetto contiene le informazioni della directory, quindi è opportuno chiamare appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metodi, ma se non dispone di questa informazioni, l'ambiente verrà dedotto le informazioni della directory.

 Il progetto non deve chiamare i metodi di `IVsTrackProjectDocuments2` al progetto aprire o chiudere. I listener che vuole che queste informazioni all'avvio possono attendere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> eventi ed eseguire l'iterazione attraverso la soluzione per trovare le informazioni necessarie. Al momento della chiusura, queste informazioni non sono necessarie. `IVsTrackProjectDocuments2` viene fornito dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Per ogni componente, ridenominazione e azione di rimozione, è disponibile un' `OnQuery*` metodo e un `OnAfter*` (metodo). Chiamare il `OnQuery*` metodo per richiedere l'autorizzazione per aggiungere, rinominare o rimuovere file o directory. Chiamare il `OnAfter*` metodo dopo che il file o la directory è stato aggiunto, rinominati o rimosso e lo stato del progetto riflette il nuovo stato.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)