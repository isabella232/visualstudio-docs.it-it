---
title: Dettagli di configurazione del controllo del codice sorgente - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705286"
---
# <a name="source-control-configuration-details"></a>Dettagli di configurazione del controllo del codice sorgente
Per implementare il controllo del codice sorgente, è necessario configurare correttamente il sistema di progetto o l'editor per eseguire le operazioni seguenti:In order to implement source control, you need to properly configure your project system or editor to do the following:

- Richiedere l'autorizzazione per la transizione allo stato modificatoRequest permission to transition to changed state

- Richiedere l'autorizzazione per salvare un file

- Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare file nel progetto

## <a name="request-permission-to-transition-to-changed-state"></a>Richiedere l'autorizzazione per passare allo stato modificatoRequest Permission to Transition to Changed State
 Un progetto o un editor deve richiedere l'autorizzazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>per la transizione allo stato modificato (dirty) chiamando . Ogni editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> che <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> implementa deve chiamare e ricevere l'approvazione per modificare il documento dall'ambiente prima di tornare `True` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Un progetto è essenzialmente un editor per un file di progetto e, di conseguenza, ha la stessa responsabilità per l'implementazione del rilevamento dello stato modificato per il file di progetto come un editor di testo fa per i file. L'ambiente gestisce lo stato modificato della soluzione, ma è necessario gestire lo stato modificato di qualsiasi oggetto a cui la soluzione fa riferimento ma non archivia, ad esempio un file di progetto o i relativi elementi. In generale, se il progetto o l'editor è responsabile della gestione della persistenza per un elemento, è responsabile dell'implementazione del rilevamento dello stato modificato.

 In risposta `IVsQueryEditQuerySave2::QueryEditFiles` alla chiamata, l'ambiente può eseguire le operazioni seguenti:In response to the call, the environment can do the following:

- Rifiutare la chiamata a change, nel qual caso l'editor o il progetto deve rimanere nello stato invariato (pulito).

- Indicare che i dati del documento devono essere ricaricati. Per un progetto, l'ambiente ricarica i dati per il progetto. Un editor deve ricaricare i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> dati dal disco tramite la relativa implementazione. In entrambi i casi, il contesto nel progetto o nell'editor può cambiare quando i dati vengono ricaricati.

  È un compito complesso e `IVsQueryEditQuerySave2::QueryEditFiles` difficile riadattare le chiamate appropriate su una base di codice esistente. Di conseguenza, queste chiamate devono essere integrate durante la creazione del progetto o dell'editor.

## <a name="request-permission-to-save-a-file"></a>Richiedere l'autorizzazione per salvare un file
 Prima che un progetto o un editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>salvi un file, deve chiamare o . Per i file di progetto, queste chiamate vengono completate automaticamente dalla soluzione, che sa quando salvare un file di progetto. Gli editor sono responsabili dell'esecuzione di `IVsPersistDocData2` queste chiamate, a meno che l'implementazione dell'editor di non utilizzi la funzione <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>di supporto . Se l'editor implementa `IVsPersistDocData2` in questo `IVsQueryEditQuerySave2::QuerySaveFile` modo, la chiamata a o `IVsQueryEditQuerySave2::QuerySaveFiles` viene effettuata per l'utente.

> [!NOTE]
> Effettuare sempre queste chiamate in modo preemptive, ovvero in un momento in cui l'editor è in grado di ricevere un annullamento.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Richiedere l'autorizzazione ad aggiungere, rimuovere o rinominare i file nel progetto
 Prima che un progetto possa aggiungere, rinominare o rimuovere `IVsTrackProjectDocuments2::OnQuery*` un file o una directory, deve chiamare il metodo appropriato per richiedere l'autorizzazione dall'ambiente. Se viene concessa l'autorizzazione, il progetto deve `IVsTrackProjectDocuments2::OnAfter*` completare l'operazione e quindi chiamare il metodo appropriato per notificare all'ambiente che l'operazione è stata completata. Il progetto deve chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> i metodi dell'interfaccia per tutti i file (ad esempio, i file speciali) e non solo i file padre. Le chiamate ai file sono obbligatorie, ma le chiamate alla directory sono facoltative. Se il progetto dispone di informazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> directory, quindi deve chiamare i metodi appropriati, ma se non dispone di queste informazioni, quindi l'ambiente dedurrà le informazioni della directory.

 Il progetto non deve `IVsTrackProjectDocuments2` chiamare i metodi di all'apertura o alla chiusura del progetto. I listener che desiderano queste informazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> all'avvio possono attendere l'evento e scorrere la soluzione per trovare le informazioni necessarie. All'arresto, queste informazioni non sono necessarie. `IVsTrackProjectDocuments2`è fornito <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>dal file .

 Per ogni azione di aggiunta, ridenominazione e rimozione, è disponibile un `OnQuery*` metodo e un `OnAfter*` metodo. Chiamare `OnQuery*` il metodo per chiedere l'autorizzazione per aggiungere, rinominare o rimuovere il file o la directory. Chiamare `OnAfter*` il metodo dopo che il file o la directory è stata aggiunta, rinominata o rimossa e lo stato del progetto riflette il nuovo stato.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
