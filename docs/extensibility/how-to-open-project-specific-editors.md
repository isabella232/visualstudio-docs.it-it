---
title: 'Procedura: Aprire Project-Specific Editor | Microsoft Docs'
description: Informazioni su come implementare il metodo OpenItem con un editor specifico del progetto in modo che un progetto possa aprire un file associato a un editor per tale progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7f28ce796b38c0d0ce51c67b7c5a36a573dae771
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050312"
---
# <a name="how-to-open-project-specific-editors"></a>Procedura: Aprire editor specifici del progetto
Se un file di elemento aperto da un progetto è intrinsecamente associato all'editor specifico per tale progetto, il progetto deve aprire il file usando un editor specifico del progetto. Il file non può essere delegato al meccanismo dell'IDE per la selezione di un editor. Ad esempio, invece di usare un editor bitmap standard, è possibile usare questa opzione dell'editor specifica del progetto per specificare un editor di bitmap specifico che riconosce le informazioni nel file univoche per il progetto.

 L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> chiama il metodo quando determina che un file deve essere aperto da un progetto specifico. Per altre informazioni, vedere [Visualizzare i file usando il comando Apri file](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Usare le linee guida seguenti per implementare il metodo per fare in modo che il progetto a open `OpenItem` un file usando un editor specifico del progetto.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Per implementare il metodo OpenItem con un editor specifico del progetto

1. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo ( ) per `RDT_EditLock` determinare se il file (oggetto dati documento) è già aperto.

    > [!NOTE]
    > Per altre informazioni sui dati del documento e sugli oggetti visualizzazione documento, vedere Dati del documento e [visualizzazione documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Se il file è già aperto, riemerre il file chiamando il metodo e specificando il valore IDO_ActivateIfOpen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> per il `grfIDO` parametro .

     Se il file è aperto e il documento è di proprietà di un progetto diverso dal progetto chiamante, all'utente verrà visualizzato un avviso che indica che l'editor aperto appartiene a un altro progetto. Viene quindi visualizzata la finestra del file.

3. Se il buffer di testo (oggetto dati documento) è già aperto e si vuole associare un'altra visualizzazione, si è responsabili dell'associazione di tale visualizzazione. L'approccio consigliato per creare un'istanza di una vista (oggetto visualizzazione documento) dal progetto è il seguente:

    1. Chiamare `QueryService` sul servizio per ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> puntatore all'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> .

    2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodo per creare un'istanza della classe di visualizzazione del documento.

4. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metodo , specificando l'oggetto visualizzazione documento.

     Questo metodo consente di visualizzare l'oggetto documento in una finestra del documento.

5. Eseguire le chiamate appropriate ai <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> metodi o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> .

     A questo punto, la vista deve essere completamente inizializzata e pronta per l'apertura.

6. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo per visualizzare e aprire la visualizzazione.

## <a name="see-also"></a>Vedi anche
- [Aprire e salvare elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: Aprire editor standard](../extensibility/how-to-open-standard-editors.md)
- [Procedura: Aprire editor per documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)
