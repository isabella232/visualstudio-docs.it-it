---
title: Dettagli di configurazione del controllo del codice | Microsoft Docs
description: Informazioni sull'implementazione del controllo del codice sorgente per un tipo di progetto in Visual Studio, che prevede la configurazione del sistema di progetto o dell'editor per richiedere le autorizzazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 22b4cccf05fb3f18b809d3d76cade14c57ea0188
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102349"
---
# <a name="source-control-configuration-details"></a>Dettagli di configurazione del controllo del codice sorgente
Per implementare il controllo del codice sorgente, è necessario configurare correttamente il sistema di progetto o l'editor per eseguire le operazioni seguenti:

- Richiedere l'autorizzazione per la transizione allo stato modificato

- Richiedere l'autorizzazione per salvare un file

- Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare file nel progetto

## <a name="request-permission-to-transition-to-changed-state"></a>Richiedere l'autorizzazione per la transizione allo stato modificato
 Un progetto o un editor deve richiedere l'autorizzazione per passare allo stato modificato (dirty) chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Ogni editor che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> deve chiamare e ricevere <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> l'approvazione per modificare il documento dall'ambiente prima di restituire `True` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Un progetto è essenzialmente un editor per un file di progetto e, di conseguenza, ha la stessa responsabilità di implementare il rilevamento dello stato modificato per il file di progetto come fa un editor di testo per i relativi file. L'ambiente gestisce lo stato modificato della soluzione, ma è necessario gestire lo stato modificato di qualsiasi oggetto a cui fa riferimento la soluzione, ma non archivia, ad esempio un file di progetto o i relativi elementi. In generale, se il progetto o l'editor è responsabile della gestione della persistenza per un elemento, è responsabile dell'implementazione del rilevamento dello stato modificato.

 In risposta alla `IVsQueryEditQuerySave2::QueryEditFiles` chiamata, l'ambiente può eseguire le operazioni seguenti:

- Rifiutare la chiamata di modifica, nel qual caso l'editor o il progetto deve rimanere nello stato non modificato (pulito).

- Indicare che i dati del documento devono essere ricaricati. Per un progetto, l'ambiente ricarica i dati per il progetto. Un editor deve ricaricare i dati dal disco tramite la relativa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementazione. In entrambi i casi, il contesto nel progetto o nell'editor può cambiare quando i dati vengono ricaricati.

  È un'attività complessa e difficile modificare le chiamate appropriate `IVsQueryEditQuerySave2::QueryEditFiles` in una codebase esistente. Di conseguenza, queste chiamate devono essere integrate durante la creazione del progetto o dell'editor.

## <a name="request-permission-to-save-a-file"></a>Richiedere l'autorizzazione per salvare un file
 Prima che un progetto o un editor salvi un file, deve chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . Per i file di progetto, queste chiamate vengono completate automaticamente dalla soluzione, che sa quando salvare un file di progetto. Gli editor sono responsabili dell'esecuzione di queste chiamate a meno che l'implementazione dell'editor `IVsPersistDocData2` di non usi la funzione helper <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Se l'editor `IVsPersistDocData2` implementa in questo modo, la chiamata a `IVsQueryEditQuerySave2::QuerySaveFile` o viene effettuata per `IVsQueryEditQuerySave2::QuerySaveFiles` l'utente.

> [!NOTE]
> Eseguire sempre queste chiamate in modo preventivo, ovvero in un momento in cui l'editor è in grado di ricevere un annullamento.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Richiedere l'autorizzazione per aggiungere, rimuovere o rinominare file nel Project
 Prima che un progetto possa aggiungere, rinominare o rimuovere un file o una directory, deve chiamare il metodo appropriato per `IVsTrackProjectDocuments2::OnQuery*` richiedere l'autorizzazione dall'ambiente. Se viene concessa l'autorizzazione , il progetto deve completare l'operazione e quindi chiamare il metodo appropriato per notificare all'ambiente `IVsTrackProjectDocuments2::OnAfter*` che l'operazione è stata completata. Il progetto deve chiamare i metodi dell'interfaccia per tutti i file (ad esempio, i file speciali) e <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> non solo per i file padre. Le chiamate di file sono obbligatorie, ma le chiamate di directory sono facoltative. Se il progetto contiene informazioni sulla directory, deve chiamare i metodi appropriati, ma se non contiene queste informazioni, l'ambiente dedurrà le informazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> della directory.

 Il progetto non deve chiamare i metodi di `IVsTrackProjectDocuments2` all'apertura o alla chiusura del progetto. I listener che desiderano queste informazioni all'avvio possono attendere l'evento e scorrere la soluzione per <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> trovare le informazioni necessarie. All'arresto, queste informazioni non sono necessarie. `IVsTrackProjectDocuments2` viene fornito da <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Per ogni azione di aggiunta, ridenominazione e rimozione sono disponibili un `OnQuery*` metodo e un metodo `OnAfter*` . Chiamare il `OnQuery*` metodo per chiedere l'autorizzazione per aggiungere, rinominare o rimuovere il file o la directory. Chiamare il metodo dopo che il file o la directory è stata aggiunta, rinominata o rimossa e lo stato `OnAfter*` del progetto riflette il nuovo stato.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
