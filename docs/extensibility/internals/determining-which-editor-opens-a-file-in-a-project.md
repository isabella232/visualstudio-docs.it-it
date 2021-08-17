---
title: Determinazione dell'editor che apre un file in un Project | Microsoft Docs
description: Informazioni sulle chiavi del Registro di sistema Visual Studio metodi SDK usati da Visual Studio determinare quale editor apre un file in un progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 197b310c37ba3c9395cd5120d4e0e8fb4d066e0669b3e409b06af0b10475137d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376235"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determinare quale editor apre un file in un progetto
Quando un utente apre un file in un progetto, l'ambiente esegue un processo di polling, aprendo infine l'editor o la finestra di progettazione appropriata per tale file. La procedura iniziale utilizzata dall'ambiente è la stessa per gli editor standard e personalizzati. L'ambiente usa una varietà di criteri quando si esegue il polling dell'editor da usare per aprire un file e il pacchetto VSPackage deve coordinarsi con l'ambiente durante questo processo.

 Ad esempio, quando un  utente seleziona il comando Apri dal menu **File** e quindi sceglie *filename.rtf* (o qualsiasi altro file con estensione *RTF),* l'ambiente chiama l'implementazione per ogni progetto, infine esplorando tutte le istanze del progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> nella soluzione. I progetti restituiscono un set di flag che identificano le attestazioni in un documento in base alla priorità. Usando la priorità più alta, l'ambiente chiama il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> appropriato. Per altre informazioni sul processo di polling, vedere [Aggiungere modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Il progetto File esterni rivendica tutti i file non rivendicati da altri progetti. In questo modo, gli editor personalizzati possono aprire i documenti prima che gli editor standard li a aperti. Se un progetto File esterni richiede un file, l'ambiente chiama il metodo per aprire il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> file con un editor standard. L'ambiente controlla l'elenco interno degli editor registrati per verificarne uno che gestisce i file CON ESTENSIONE *RTF.* Questo elenco si trova nel Registro di sistema nella chiave seguente:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ \<version> \Editors \\ \<editor factory guid> \Extensions**

 L'ambiente controlla anche gli identificatori di classe nella **chiaveHKEY_CLASSES_ROOT\CLSID** per tutti gli oggetti che dispongono di una sottochiave **DocObject**. Se viene trovata l'estensione di file, viene creata sul posto una versione incorporata dell'applicazione, ad esempio Microsoft Word, nel Visual Studio. Questi oggetti documento devono essere file composti che implementano l'interfaccia oppure <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> l'oggetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> l'interfaccia .

 Se nel Registro di sistema non è presente alcuna factory dell'editor per i file *RTF,* l'ambiente cerca nella chiave **HKEY_CLASSES_ROOT \\ .rtf** e apre l'editor specificato. Se l'estensione di file non viene trovata in **HKEY_CLASSES_ROOT**, l'ambiente usa l'editor di testo principale di Visual Studio per aprire il file, se si tratta di un file di testo.

 Se l'editor di testo principale ha esito negativo, che si verifica se il file non è un file di testo, l'ambiente usa il relativo editor binario per il file.

 Se l'ambiente trova un editor per l'estensione *RTF* nel registro, carica il pacchetto VSPackage che implementa questa factory dell'editor. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> il metodo sul nuovo VSPackage. Il pacchetto VSPackage `QueryService` chiama per , usando il metodo per `SID_SVsRegistorEditor` <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> registrare la factory dell'editor con l'ambiente.

 L'ambiente ora verifica nuovamente l'elenco interno degli editor registrati per trovare la factory dell'editor appena registrata per *i file CON* ESTENSIONE RTF. L'ambiente chiama l'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> del metodo , passando il nome file e il tipo di vista da creare.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
