---
title: Determinare quale Editor viene aperto un File in un progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196763"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Scelta dell'editor da usare per aprire un file in un progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando un utente apre un file in un progetto, l'ambiente passa attraverso un processo di polling, alla fine apertura dell'editor appropriato o una finestra di progettazione per il file. La procedura iniziale impiegata dall'ambiente è lo stesso per gli editor standard e personalizzati. L'ambiente Usa una serie di criteri quando l'editor da utilizzare per aprire un file di polling e il pacchetto VSPackage deve coordinare con l'ambiente durante questo processo.  
  
 Ad esempio, quando un utente seleziona il **Open** dal **File** dal menu e poi sceglie `filename`RTF (o qualsiasi altro file con estensione. RTF), l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementazione per ogni progetto, alla fine ed esegue il ciclo attraverso tutte le istanze del progetto nella soluzione. Progetti di restituiscono un set di flag che specificano le attestazioni in un documento in base alla priorità. Usa la priorità più alta, l'ambiente chiama l'oggetto appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> (metodo). Per ulteriori informazioni sul processo di polling, [aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Il progetto file esterni attestazioni tutti i file che non sono richiesti da altri progetti. In questo modo, editor personalizzati possono aprire i documenti prima di aprirli editor standard. Se un file di attestazioni di un progetto di file esterni, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per aprire il file con un editor standard. L'ambiente controlla l'elenco interno degli editor registrati per uno che gestisce i file RTF. Questo elenco si trova nel Registro di sistema la chiave seguente:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 L'ambiente controlla anche gli identificatori di classe nella chiave del HKEY_CLASSES_ROOT\CLSID per tutti gli oggetti che hanno la sottochiave DocObject. Se viene trovato l'estensione di file, una versione incorporata dell'applicazione, ad esempio Microsoft Word, viene creata sul posto in Visual Studio. Questi oggetti documento devono essere file compositi che implementano il <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaccia oppure l'oggetto deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaccia.  
  
 Se nessun factory di editor per i file RTF nel Registro di sistema, quindi l'ambiente è simile in HKEY_CLASSES_ROOT della \\chiave RTF e verrà aperto l'editor specificato non esiste. Se l'estensione di file non viene trovato in HKEY_CLASSES_ROOT, l'ambiente Usa l'editor di testo principale di Visual Studio aprire il file se si tratta di un file di testo.  
  
 Se l'editor di testo principale ha esito negativo, che si verifica che se il file non è un file di testo, l'ambiente utilizza relativo editor binario per il file.  
  
 Se l'ambiente di trovare un editor per l'estensione. RTF nel relativo Registro di sistema, carica il pacchetto VSPackage che implementa la factory dell'editor. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> (metodo) nel nuovo pacchetto VSPackage. Le chiamate di VSPackage `QueryService` per `SID_SVsRegistorEditor`, usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodo per registrare la factory dell'editor con l'ambiente.  
  
 A questo punto l'ambiente controlla nuovamente l'elenco interno degli editor registrati per trovare la factory dell'editor appena registrato per i file RTF. L'ambiente chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo, passando il tipo di nome e la visualizzazione di file da creare.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
