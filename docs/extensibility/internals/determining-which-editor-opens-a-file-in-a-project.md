---
title: Determinare quale Editor viene aperto un File in un progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61aa726a7088d08db6d759a9835816dcaf826a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941060"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determinare quale editor viene aperto un file in un progetto
Quando un utente apre un file in un progetto, l'ambiente passa attraverso un processo di polling, alla fine apertura dell'editor appropriato o una finestra di progettazione per il file. La procedura iniziale impiegata dall'ambiente è lo stesso per gli editor standard e personalizzati. L'ambiente Usa una serie di criteri quando l'editor da utilizzare per aprire un file di polling e il pacchetto VSPackage deve coordinare con l'ambiente durante questo processo.  
  
 Ad esempio, quando un utente seleziona il **aperto** dal **File** dal menu e poi sceglie *filename.rtf* (o qualsiasi altro file con un *RTF*estensione), l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementazione per ogni progetto, alla fine ed esegue il ciclo attraverso tutte le istanze del progetto nella soluzione. Progetti di restituiscono un set di flag che specificano le attestazioni in un documento in base alla priorità. Usa la priorità più alta, l'ambiente chiama l'oggetto appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> (metodo). Per altre informazioni sul processo di polling, vedere [aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Il progetto file esterni attestazioni tutti i file che non sono richiesti da altri progetti. In questo modo, editor personalizzati possono aprire i documenti prima di aprirli editor standard. Se un file di attestazioni di un progetto di file esterni, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per aprire il file con un editor standard. L'ambiente controlla l'elenco interno degli editor registrati per uno che gestisce *RTF* file. Questo elenco si trova nel Registro di sistema la chiave seguente:  
  
 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<versione > \Editors\\\<guid della factory dell'editor > \Extensions**
  
 L'ambiente controlla anche gli identificatori di classe **HKEY_CLASSES_ROOT\CLSID** chiave per gli oggetti che hanno una sottochiave **DocObject**. Se viene trovato l'estensione di file, una versione incorporata dell'applicazione, ad esempio Microsoft Word, viene creata sul posto in Visual Studio. Questi oggetti documento devono essere file compositi che implementano il <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaccia oppure l'oggetto deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaccia.  
  
 Se è presente alcuna factory dell'editor per *RTF* i file nel Registro di sistema, quindi l'ambiente è simile **HKEY_CLASSES_ROOT\\RTF** della chiave e apre l'editor specificato non esiste. Se l'estensione di file non viene trovato nel **HKEY_CLASSES_ROOT**, quindi l'ambiente Usa l'editor di testo principale di Visual Studio per aprire il file, se si tratta di un file di testo.  
  
 Se l'editor di testo principale ha esito negativo, che si verifica che se il file non è un file di testo, l'ambiente utilizza relativo editor binario per il file.  
  
 Se l'ambiente di trovare un editor per il *RTF* estensione nel relativo Registro di sistema, carica il pacchetto VSPackage che implementa la factory dell'editor. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> (metodo) nel nuovo pacchetto VSPackage. Le chiamate di VSPackage `QueryService` per `SID_SVsRegistorEditor`, usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodo per registrare la factory dell'editor con l'ambiente.  
  
 L'ambiente esegue il controllo a questo punto l'elenco interno degli editor registrati per la factory dell'editor appena registrato per trovare *RTF* file. L'ambiente chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo, passando il tipo di nome e la visualizzazione di file da creare.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>