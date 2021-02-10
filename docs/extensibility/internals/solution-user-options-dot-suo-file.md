---
title: Opzioni utente soluzione (. Suo) file | Microsoft Docs
description: Informazioni sul file delle opzioni utente della soluzione (. suo), che contiene le opzioni della soluzione per ogni utente in un file di archiviazione strutturato archiviato in un formato binario.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a978986ed6ef32dbad3ad06eafcba11d7f4782ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962912"
---
# <a name="solution-user-options-suo-file"></a>File delle opzioni utente della soluzione (con estensione suo)
Il file delle opzioni utente della soluzione (. suo) contiene le opzioni per la soluzione per utente. Questo file non deve essere archiviato nel controllo del codice sorgente.

 Il file delle opzioni utente della soluzione (. suo) è un file di archiviazione strutturata, o composto, archiviato in un formato binario. Salvare le informazioni utente in flussi con il nome del flusso che è la chiave che verrà usata per identificare le informazioni nel file con estensione suo. Il file delle opzioni utente della soluzione viene usato per archiviare le impostazioni delle preferenze utente e viene creato automaticamente quando Visual Studio salva una soluzione.

 Quando l'ambiente apre un file con estensione suo, enumera tutti i pacchetti VSPackage attualmente caricati. Se un pacchetto VSPackage implementa l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaccia, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metodo sul pacchetto VSPackage chiedendogli di caricare tutti i dati dal file con estensione suo.

 È responsabilità del VSPackage conoscere i flussi che potrebbero essere stati scritti nel file con estensione suo. Per ogni flusso scritto, il pacchetto VSPackage richiama l'ambiente tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> per caricare un flusso specifico identificato dalla chiave, che è il nome del flusso. L'ambiente richiama quindi il pacchetto VSPackage per leggere il flusso specifico che passa il nome del flusso e un `IStream` puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metodo.

 A questo punto, viene eseguita un'altra chiamata a `LoadUserOptions` per verificare se è presente un'altra sezione del file con estensione suo che deve essere letta. Questo processo continua fino a quando tutti i flussi di dati nel file con estensione suo non sono stati letti ed elaborati dall'ambiente.

 Quando la soluzione viene salvata o chiusa, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metodo con un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metodo. Un oggetto `IStream` contenente le informazioni binarie da salvare viene passato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metodo, che quindi scrive le informazioni nel file con estensione suo e chiama `SaveUserOptions` di nuovo il metodo per verificare se è presente un altro flusso di informazioni da scrivere nel file con estensione suo.

 Questi due metodi, `SaveUserOptions` e `WriteUserOptions` , vengono chiamati in modo ricorsivo per ogni flusso di informazioni da salvare nel file con estensione suo, passando il puntatore a `IVsSolutionPersistence` . Vengono chiamati in modo ricorsivo per consentire la scrittura di più flussi nel file con estensione suo. In questo modo, le informazioni utente vengono rese permanente con la soluzione e si garantisce che sia presente alla successiva apertura della soluzione.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluzioni](../../extensibility/internals/solutions-overview.md)
