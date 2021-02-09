---
title: Dettagli di configurazione del controllo del codice sorgente | Microsoft Docs
description: Informazioni sull'implementazione del controllo del codice sorgente per un tipo di progetto in Visual Studio, che prevede la configurazione del sistema di progetto o dell'editor per richiedere le autorizzazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9a3a2f33fcbb94d1e863daf69b8561f7bad4f2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846504"
---
# <a name="source-control-configuration-details"></a>Dettagli di configurazione del controllo del codice sorgente
Per implementare il controllo del codice sorgente, è necessario configurare correttamente il sistema di progetto o l'editor per eseguire le operazioni seguenti:

- Richiedi autorizzazione per la transizione allo stato modificato

- Richiedi l'autorizzazione per il salvataggio di un file

- Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare i file nel progetto

## <a name="request-permission-to-transition-to-changed-state"></a>Richiedi autorizzazione per la transizione allo stato modificato
 Un progetto o un editor deve richiedere l'autorizzazione per la transizione allo stato modificato (Dirty) chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Ogni editor che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> deve chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e ricevere l'approvazione per modificare il documento dall'ambiente prima di restituire `True` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Un progetto è essenzialmente un editor per un file di progetto e, di conseguenza, ha la stessa responsabilità di implementare il rilevamento dello stato modificato per il file di progetto come un editor di testo per i relativi file. L'ambiente gestisce lo stato modificato della soluzione, ma è necessario gestire lo stato modificato di qualsiasi oggetto che fa riferimento alla soluzione, ma non archivia, ad esempio un file di progetto o i relativi elementi. In generale, se il progetto o l'editor è responsabile della gestione della persistenza per un elemento, è responsabile dell'implementazione del rilevamento dello stato modificato.

 In risposta alla `IVsQueryEditQuerySave2::QueryEditFiles` chiamata, l'ambiente può eseguire le operazioni seguenti:

- Rifiutare la chiamata a Change, nel qual caso l'editor o il progetto deve rimanere nello stato non modificato (pulito).

- Indica che i dati del documento devono essere ricaricati. Per un progetto, l'ambiente caricherà nuovamente i dati per il progetto. Un editor deve ricaricare i dati dal disco tramite la relativa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementazione. In entrambi i casi, il contesto nel progetto o nell'editor può cambiare quando i dati vengono ricaricati.

  Si tratta di un'attività complessa e difficile per il retrofit delle `IVsQueryEditQuerySave2::QueryEditFiles` chiamate appropriate su una codebase esistente. Di conseguenza, queste chiamate devono essere integrate durante la creazione del progetto o dell'editor.

## <a name="request-permission-to-save-a-file"></a>Richiedi l'autorizzazione per il salvataggio di un file
 Prima che un progetto o un editor salvi un file, deve chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . Per i file di progetto, queste chiamate vengono completate automaticamente dalla soluzione, che sa quando salvare un file di progetto. Gli editor sono responsabili di effettuare queste chiamate a meno che l'implementazione dell'editor di non `IVsPersistDocData2` usi la funzione di supporto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Se l'editor implementa `IVsPersistDocData2` in questo modo, viene eseguita la chiamata a `IVsQueryEditQuerySave2::QuerySaveFile` o `IVsQueryEditQuerySave2::QuerySaveFiles` .

> [!NOTE]
> Effettuare sempre queste chiamate in modo preemptive, ovvero in un momento in cui l'editor è in grado di ricevere un annullamento.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare i file nel progetto
 Prima che un progetto possa aggiungere, rinominare o rimuovere un file o una directory, deve chiamare il `IVsTrackProjectDocuments2::OnQuery*` metodo appropriato per richiedere l'autorizzazione all'ambiente. Se l'autorizzazione viene concessa, il progetto deve completare l'operazione e quindi chiamare il `IVsTrackProjectDocuments2::OnAfter*` metodo appropriato per notificare all'ambiente che l'operazione è stata completata. Il progetto deve chiamare i metodi dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaccia per tutti i file (ad esempio, file speciali) e non solo i file padre. Le chiamate di file sono obbligatorie, ma le chiamate alle directory sono facoltative. Se il progetto contiene informazioni sulla directory, deve chiamare i metodi appropriati <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> , ma se non dispone di queste informazioni, l'ambiente dedurrà le informazioni sulla directory.

 Il progetto non deve chiamare i metodi di `IVsTrackProjectDocuments2` all'apertura o alla chiusura del progetto. I listener che desiderano queste informazioni all'avvio possono attendere l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> evento e scorrere la soluzione per trovare le informazioni necessarie. All'arresto, queste informazioni non sono necessarie. `IVsTrackProjectDocuments2` viene fornito da <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Per ogni azione di aggiunta, ridenominazione e rimozione sono disponibili un `OnQuery*` metodo e un `OnAfter*` metodo. Chiamare il `OnQuery*` metodo per richiedere l'autorizzazione per aggiungere, rinominare o rimuovere il file o la directory. Chiamare il `OnAfter*` metodo dopo che il file o la directory è stata aggiunta, rinominata o rimossa e lo stato del progetto riflette il nuovo stato.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
