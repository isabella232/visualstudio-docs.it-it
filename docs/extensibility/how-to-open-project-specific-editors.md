---
title: 'Procedura: aprire gli editor specifici del progetto Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710837"
---
# <a name="how-to-open-project-specific-editors"></a>Procedura: aprire editor specifici del progettoHow to: Open project-specific editors
Se un file di elemento aperto da un progetto è intrinsecamente associato all'editor specifico per tale progetto, il progetto deve aprire il file utilizzando un editor specifico del progetto. Il file non può essere delegato al meccanismo dell'IDE per la selezione di un editor. Ad esempio, anziché utilizzare un editor di bitmap standard, è possibile utilizzare questa opzione dell'editor specifico del progetto per specificare un editor di bitmap specifico che riconosce le informazioni nel file univoco per il progetto.

 L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> chiama il metodo quando determina che un file deve essere aperto da un progetto specifico. Per ulteriori informazioni, consultate [Visualizzare i file utilizzando il comando Apri file.](../extensibility/internals/displaying-files-by-using-the-open-file-command.md) Utilizzare le linee guida `OpenItem` seguenti per implementare il metodo per fare in modo che il progetto apra un file utilizzando un editor specifico del progetto.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Per implementare il metodo OpenItem con un editor specifico del progettoTo implement the OpenItem method with a project-specific editor

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> il`RDT_EditLock`metodo ( ) per determinare se il file (oggetto dati del documento) è già aperto.

    > [!NOTE]
    > Per ulteriori informazioni sui dati del documento e sugli oggetti visualizzazione documento, consultate [Dati del documento e visualizzazione del documento negli editor personalizzati.](../extensibility/document-data-and-document-view-in-custom-editors.md)

2. Se il file è già aperto, riaffiorarlo chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo `grfIDO` e specificando un valore di IDO_ActivateIfOpen per il parametro.

     Se il file è aperto e il documento è di proprietà di un progetto diverso dal progetto chiamante, verrà visualizzato un avviso per l'utente che l'editor viene aperto da un altro progetto. La finestra del file viene quindi visualizzata.

3. Se il buffer di testo (oggetto dati del documento) è già aperto e si desidera associarvi un'altra visualizzazione, si è responsabili dell'associazione di tale visualizzazione. L'approccio consigliato per creare un'istanza di una vista (oggetto visualizzazione documento) dal progetto, è il seguente:The recommended approach to instantiating a view (document view object) from the project, is as follows:

    1. Chiamare `QueryService` il <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> servizio per ottenere <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> un puntatore all'interfaccia.

    2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> il metodo per creare un'istanza della classe di visualizzazione del documento.

4. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> il metodo , specificando l'oggetto visualizzazione del documento.

     Questo metodo siti l'oggetto visualizzazione documento in una finestra del documento.

5. Eseguire le chiamate appropriate <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> ai metodi o . <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>

     A questo punto, la vista deve essere completamente inizializzata e pronta per essere aperta.

6. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> il metodo per visualizzare e aprire la visualizzazione.

## <a name="see-also"></a>Vedere anche
- [Aprire e salvare elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: aprire gli editor standardHow to: Open standard editors](../extensibility/how-to-open-standard-editors.md)
- [Procedura: aprire gli editor per i documenti apertiHow to: Open editors for open documents](../extensibility/how-to-open-editors-for-open-documents.md)
