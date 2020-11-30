---
title: Determinare quale editor apre un file in un progetto | Microsoft Docs
description: Informazioni sulle chiavi del registro di sistema e sui metodi di Visual Studio SDK utilizzati da Visual Studio per determinare quale editor apre un file in un progetto.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f9574a3319d3c43c17d7351e462b6956ae899d84
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328405"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determinare quale editor apre un file in un progetto
Quando un utente apre un file in un progetto, l'ambiente viene sottoposto a un processo di polling, aprendo infine l'editor o la finestra di progettazione appropriata per tale file. La procedura iniziale utilizzata dall'ambiente è la stessa per gli editor standard e personalizzati. L'ambiente USA diversi criteri durante il polling dell'editor da usare per aprire un file e il pacchetto VSPackage deve coordinarsi con l'ambiente durante questo processo.

 Ad esempio, quando un utente seleziona il comando **Apri** dal menu **file** e quindi sceglie *filename. RTF* (o qualsiasi altro file con estensione *RTF* ), l'ambiente chiama l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementazione per ogni progetto, infine scorre in ciclo tutte le istanze del progetto nella soluzione. I progetti restituiscono un set di flag che identificano le attestazioni in un documento per priorità. Con la priorità più alta, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo appropriato. Per altre informazioni sul processo di polling, vedere [aggiungere modelli di progetti e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Il progetto di file esterni attesta tutti i file non richiesti da altri progetti. In questo modo, gli editor personalizzati possono aprire i documenti prima che vengano aperti dagli editor standard. Se un progetto di file esterni attesta un file, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per aprire il file con un editor standard. L'ambiente controlla l'elenco interno di editor registrati per uno che gestisce i file con *estensione RTF* . Questo elenco si trova nel registro di sistema in corrispondenza della chiave seguente:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ \<version> \Editors \\ \<editor factory guid> \Extensions**

 L'ambiente controlla anche gli identificatori di classe nella chiave **HKEY_CLASSES_ROOT\CLSID** per tutti gli oggetti che hanno una sottochiave **DocObject**. Se l'estensione del file viene trovata, viene creata sul posto una versione incorporata dell'applicazione, ad esempio Microsoft Word, in Visual Studio. Questi oggetti documento devono essere file composti che implementano l' <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaccia oppure l'oggetto deve implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaccia.

 Se non è presente alcuna factory dell'editor per i file con *estensione RTF* nel registro di sistema, l'ambiente Cerca nella chiave **HKEY_CLASSES_ROOT \\ . RTF** e apre l'editor specificato. Se l'estensione di file non viene trovata in **HKEY_CLASSES_ROOT**, l'ambiente USA l'editor di testo principale di Visual Studio per aprire il file, se si tratta di un file di testo.

 Se l'editor di testo principale ha esito negativo, che si verifica se il file non è un file di testo, l'ambiente USA il relativo editor binario per il file.

 Se l'ambiente trova un editor per l'estensione *RTF* nel registro di sistema, carica il pacchetto VSPackage che implementa la factory dell'editor. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo sul nuovo pacchetto VSPackage. Il pacchetto VSPackage chiama `QueryService` per `SID_SVsRegistorEditor` , usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodo per registrare la factory dell'editor con l'ambiente.

 L'ambiente ora Ricontrolla l'elenco interno di editor registrati per trovare la factory dell'editor appena registrata per i file con *estensione RTF* . L'ambiente chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo, passando il nome del file e il tipo di visualizzazione da creare.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
