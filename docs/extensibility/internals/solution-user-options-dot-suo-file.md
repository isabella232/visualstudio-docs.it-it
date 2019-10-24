---
title: Opzioni utente soluzione (. Suo) file | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723804"
---
# <a name="solution-user-options-suo-file"></a>File delle opzioni utente della soluzione (con estensione suo)
Il file delle opzioni utente della soluzione (. suo) contiene le opzioni per la soluzione per utente. Questo file non deve essere archiviato nel controllo del codice sorgente.

 Il file delle opzioni utente della soluzione (. suo) è un file di archiviazione strutturata, o composto, archiviato in un formato binario. Salvare le informazioni utente in flussi con il nome del flusso che è la chiave che verrà usata per identificare le informazioni nel file con estensione suo. Il file delle opzioni utente della soluzione viene usato per archiviare le impostazioni delle preferenze utente e viene creato automaticamente quando Visual Studio salva una soluzione.

 Quando l'ambiente apre un file con estensione suo, enumera tutti i pacchetti VSPackage attualmente caricati. Se un pacchetto VSPackage implementa l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>, l'ambiente chiama il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> sul pacchetto VSPackage chiedendogli di caricare tutti i dati dal file con estensione suo.

 È responsabilità del VSPackage conoscere i flussi che potrebbero essere stati scritti nel file con estensione suo. Per ogni flusso scritto, il pacchetto VSPackage richiama l'ambiente tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> per caricare un flusso specifico identificato dalla chiave, che è il nome del flusso. L'ambiente richiama quindi il pacchetto VSPackage per leggere il flusso specifico che passa il nome del flusso e un puntatore `IStream` al metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>.

 A questo punto, viene eseguita un'altra chiamata a `LoadUserOptions` per verificare se è presente un'altra sezione del file con estensione suo da leggere. Questo processo continua fino a quando tutti i flussi di dati nel file con estensione suo non sono stati letti ed elaborati dall'ambiente.

 Quando la soluzione viene salvata o chiusa, l'ambiente chiama il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> con un puntatore al metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>. Un `IStream` contenente le informazioni binarie da salvare viene passato al metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>, che quindi scrive le informazioni nel file con estensione suo e chiama di nuovo il metodo `SaveUserOptions` per verificare se è presente un altro flusso di informazioni da scrivere nel file con estensione suo.

 Questi due metodi, `SaveUserOptions` e `WriteUserOptions`, vengono chiamati in modo ricorsivo per ogni flusso di informazioni da salvare nel file con estensione suo, passando il puntatore a `IVsSolutionPersistence`. Vengono chiamati in modo ricorsivo per consentire la scrittura di più flussi nel file con estensione suo. In questo modo, le informazioni utente vengono rese permanente con la soluzione e si garantisce che sia presente alla successiva apertura della soluzione.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluzioni](../../extensibility/internals/solutions-overview.md)