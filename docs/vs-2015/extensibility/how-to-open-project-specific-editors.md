---
title: 'Procedura: aprire gli editor specifici del progetto | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 255d95d92aae3f73e4c5f77a6f7a5a4219d73d19
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198146"
---
# <a name="how-to-open-project-specific-editors"></a>Procedura: aprire gli editor specifici del progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se un file di elemento che viene aperto da un progetto è intrinsecamente associato all'editor specifico per il progetto, il progetto deve aprire il file usando un editor specifico del progetto. Il file non può essere delegato al meccanismo dell'IDE per la selezione di un editor. Ad esempio, invece di usare un editor di bitmap standard, è possibile utilizzare questa opzione dell'editor specifiche del progetto per specificare un editor di bitmap specifico che riconosce le informazioni nel file univoco per il progetto.  
  
 Le chiamate dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo quando determina che un file deve essere aperto da un progetto specifico. Per altre informazioni, vedere [i file di visualizzazione utilizzando il comando File Apri](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Usare le linee guida seguenti per implementare il `OpenItem` metodo per il progetto aperto un file usando un editor specifico del progetto.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Per implementare il metodo OpenItem con un editor specifico del progetto  
  
1.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo (RDT_EditLock) per determinare se il file (oggetto dati del documento) è già aperto.  
  
    > [!NOTE]
    >  Per altre informazioni sui dati del documento e oggetti di visualizzazione di documenti, vedere [i dati del documento e visualizzazione documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Se il file è già aperto, il file resurface chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo e specificando il valore di IDO_ActivateIfOpen per il `grfIDO` parametro.  
  
     Se il file è aperto e il documento è di proprietà da un progetto diverso dal progetto chiama, verrà visualizzato un avviso all'utente che l'editor viene aperto da un altro progetto. Finestra di dialogo file viene quindi esposto.  
  
3.  Se il buffer di testo (oggetto dati del documento) è già aperto e si desidera associarvi un'altra visualizzazione, si è responsabili agganciarmi a tale visualizzazione. L'approccio consigliato per creare un'istanza di una vista (oggetto visualizzazione del documento) dal progetto, è come segue:  
  
    1.  Chiamare `QueryService` nella <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> servizio per ottenere un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfaccia.  
  
    2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodo per creare un'istanza della classe di visualizzazione documento.  
  
4.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metodo, specificando l'oggetto visualizzazione del documento.  
  
     Questo metodo siti oggetto visualizzazione del documento in una finestra del documento.  
  
5.  Eseguire le chiamate appropriate a entrambi i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> o il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metodi.  
  
     A questo punto, la visualizzazione deve essere completamente inizializzato e pronto per essere aperto.  
  
6.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo per visualizzare e aprire la visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: aprire gli editor Standard](../extensibility/how-to-open-standard-editors.md)   
 [Procedura: Aprire gli editor per i documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)

