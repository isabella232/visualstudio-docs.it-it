---
title: 'Procedura: aprire Editor Project-Specific | Microsoft Docs'
description: Viene illustrato come implementare il Metodo OpenItem con un editor specifico del progetto, in modo che un progetto possa aprire un file associato a un editor per il progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 719460b36f926df19e76db1aab4e90b4d959fdc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850494"
---
# <a name="how-to-open-project-specific-editors"></a>Procedura: aprire editor specifici del progetto
Se un file di elemento aperto da un progetto viene associato intrinsecamente all'editor specifico per il progetto, il progetto deve aprire il file utilizzando un editor specifico del progetto. Non è possibile delegare il file al meccanismo dell'IDE per la selezione di un editor. Ad esempio, invece di usare un editor di bitmap standard, è possibile usare questa opzione dell'editor specifico del progetto per specificare un editor di bitmap specifico che riconosca le informazioni nel file che sono univoche per il progetto.

 L'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo quando determina che un file deve essere aperto da un progetto specifico. Per altre informazioni, vedere [visualizzare i file tramite il comando Apri file](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Usare le linee guida seguenti per implementare il `OpenItem` metodo in modo che il progetto apra un file usando un editor specifico del progetto.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Per implementare il Metodo OpenItem con un editor specifico del progetto

1. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Metodo ( `RDT_EditLock` ) per determinare se il file (oggetto dati del documento) è già aperto.

    > [!NOTE]
    > Per ulteriori informazioni sui dati del documento e sugli oggetti visualizzazione documento, vedere Document [data and Document view in editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Se il file è già aperto, riesporre il file chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo e specificando il valore IDO_ActivateIfOpen per il `grfIDO` parametro.

     Se il file è aperto e il documento è di proprietà di un progetto diverso dal progetto chiamante, viene visualizzato un avviso all'utente che l'Editor aperto appartiene a un altro progetto. La finestra del file viene quindi rilevata.

3. Se il buffer di testo (oggetto dati del documento) è già aperto e si desidera associarvi un'altra visualizzazione, l'utente è responsabile dell'associazione di tale visualizzazione. L'approccio consigliato per creare un'istanza di una vista (oggetto visualizzazione documento) dal progetto è il seguente:

    1. Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> servizio per ottenere un puntatore all' <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfaccia.

    2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodo per creare un'istanza della classe di visualizzazione del documento.

4. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metodo, specificando l'oggetto visualizzazione del documento.

     Questo metodo consente di siti l'oggetto visualizzazione documento in una finestra del documento.

5. Eseguire le chiamate appropriate ai <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metodi o.

     A questo punto, la vista deve essere completamente inizializzata e pronta per l'apertura.

6. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo per visualizzare e aprire la visualizzazione.

## <a name="see-also"></a>Vedi anche
- [Apri e Salva elementi progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: aprire gli editor standard](../extensibility/how-to-open-standard-editors.md)
- [Procedura: aprire Editor per documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)
