---
title: Determinazione dell'editor che consente di aprire un file in un progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708651"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determinare quale editor apre un file in un progetto
Quando un utente apre un file in un progetto, l'ambiente passa attraverso un processo di polling, aprendo infine l'editor o la finestra di progettazione appropriata per tale file. La procedura iniziale utilizzata dall'ambiente è la stessa sia per gli editor standard che per quelli personalizzati. L'ambiente utilizza una varietà di criteri durante il polling dell'editor da utilizzare per aprire un file e il pacchetto VSPackage deve coordinarsi con l'ambiente durante questo processo.

 Ad esempio, quando un utente seleziona il comando **Apri** dal menu **File** e quindi sceglie *filename.rtf* (o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> qualsiasi altro file con estensione *rtf),* l'ambiente chiama l'implementazione per ogni progetto, scorrendo infine tutte le istanze del progetto nella soluzione. I progetti restituiscono un set di flag che identificano le attestazioni in base alla priorità. Utilizzando la priorità più alta, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> l'ambiente chiama il metodo appropriato. Per ulteriori informazioni sul processo di polling, consultate Aggiungere modelli di [progetto e di elemento](../../extensibility/internals/adding-project-and-project-item-templates.md)di progetto .

 Il progetto File vari rivendica tutti i file che non sono rivendicati da altri progetti. In questo modo, gli editor personalizzati possono aprire i documenti prima che gli editor standard li aprano. Se un progetto File esterni richiede un file, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per aprire il file con un editor standard. L'ambiente controlla l'elenco interno degli editor registrati per uno che gestisce i file *rtf.* Questo elenco si trova nel Registro di sistema nella seguente chiave:

 **HKEY_LOCAL_MACHINE Software , Microsoft\\\<VisualStudio versione\\\<>, Editor editor factory guid>>**

 L'ambiente controlla inoltre gli identificatori di classe nella chiave **HKEY_CLASSES_ROOT-CLSID** per tutti gli oggetti che dispongono di una sottochiave **DocObject**. Se l'estensione del file viene trovata, viene creata sul posto una versione incorporata dell'applicazione, ad esempio Microsoft Word, sul posto in Visual Studio. Questi oggetti documento devono essere <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> file composti che implementano <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> l'interfaccia oppure l'oggetto deve implementare l'interfaccia.

 Se nel Registro di sistema non è presente alcuna factory dell'editor per i file *RTF,* l'ambiente cerca nella chiave **HKEY_CLASSES_ROOT\\RTF** e apre l'editor specificato. Se l'estensione del file non viene trovata in **HKEY_CLASSES_ROOT**, l'ambiente utilizza l'editor di testo principale di Visual Studio per aprire il file, se si tratta di un file di testo.

 Se l'editor di testo principale ha esito negativo, che si verifica se il file non è un file di testo, quindi l'ambiente utilizza il suo editor binario per il file.

 Se l'ambiente trova un editor per l'estensione *RTF* nel registro di sistema, carica il pacchetto VSPackage che implementa questa factory dell'editor. L'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> chiama il metodo sul nuovo VSPackage. Il pacchetto `QueryService` VSPackage chiama per `SID_SVsRegistorEditor`, utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodo per registrare la factory dell'editor con l'ambiente.

 L'ambiente ora ricontrolla l'elenco interno degli editor registrati per trovare la fabbrica di editor appena registrata per i file *.rtf.* L'ambiente chiama l'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> del metodo, passando il nome del file e il tipo di visualizzazione da creare.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
