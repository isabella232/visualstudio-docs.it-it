---
title: Opzioni utente soluzione (. Suo) File Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705309"
---
# <a name="solution-user-options-suo-file"></a>File delle opzioni utente della soluzione (con estensione suo)
Il file delle opzioni utente della soluzione (con estensione suo) contiene le opzioni della soluzione per utente. Questo file non deve essere archiviato nel controllo del codice sorgente.

 Il file delle opzioni utente della soluzione (con estensione suo) è un file di archiviazione strutturata, o composto, archiviato in un formato binario. Le informazioni utente vengono salvate in flussi con il nome del flusso come chiave che verrà utilizzata per identificare le informazioni nel file con estensione suo. Il file delle opzioni utente della soluzione viene utilizzato per archiviare le impostazioni delle preferenze utente e viene creato automaticamente quando Visual Studio salva una soluzione.

 Quando l'ambiente apre un file con estensione suo, enumera tutti i package VS attualmente caricati. Se un pacchetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> VSPackage implementa l'interfaccia, quindi l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metodo sul pacchetto VSPackage chiedendo di caricare tutti i dati dal file con estensione suo.

 È responsabilità del pacchetto VSPackage sapere quali flussi potrebbe essere scritto nel file con estensione suo. Per ogni flusso che ha scritto, il pacchetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> VSPackage richiama all'ambiente tramite per caricare un flusso specifico identificato dalla chiave, ovvero il nome del flusso. L'ambiente richiama quindi al pacchetto VSPackage per leggere quel particolare `IStream` flusso <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> passando il nome del flusso e un puntatore al metodo.

 A questo punto, viene `LoadUserOptions` effettuata un'altra chiamata per vedere se c'è un'altra sezione del file .suo che deve essere letto. Questo processo continua fino a quando tutti i flussi di dati nel file con estensione suo sono stati letti ed elaborati dall'ambiente.

 Quando la soluzione viene salvata o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> chiusa, l'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> chiama il metodo con un puntatore al metodo . Un `IStream` contenente le informazioni binarie da <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> salvare viene passato al metodo , che `SaveUserOptions` quindi scrive le informazioni nel file con estensione suo e chiama nuovamente il metodo per verificare se è presente un altro flusso di informazioni da scrivere nel file con estensione suo.

 Questi due `SaveUserOptions` metodi, e `WriteUserOptions`, vengono chiamati in modo ricorsivo per ogni flusso di informazioni `IVsSolutionPersistence`da salvare nel file con estensione suo, passando il puntatore a . Vengono chiamati in modo ricorsivo per consentire la scrittura di più flussi nel file con estensione suo. In questo modo, le informazioni utente vengono mantenute con la soluzione e sarà garantito che sia presente alla successiva apertura della soluzione.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluzioni](../../extensibility/internals/solutions-overview.md)
