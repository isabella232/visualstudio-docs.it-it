---
title: Opzioni utente della soluzione (. Suo) File | Microsoft Docs
description: Informazioni sul file delle opzioni utente della soluzione (con estensione suo), che contiene le opzioni della soluzione per utente in un file di archiviazione strutturata archiviato in formato binario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a38eb865cf003f7a2f9bafde7b6e527ce24f2bd
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899615"
---
# <a name="solution-user-options-suo-file"></a>File delle opzioni utente della soluzione (con estensione suo)
Il file delle opzioni utente della soluzione (con estensione suo) contiene le opzioni della soluzione per utente. Questo file non deve essere archiviato nel controllo del codice sorgente.

 Il file delle opzioni utente della soluzione (con estensione suo) è un file di archiviazione strutturata, o composto, archiviato in formato binario. Le informazioni utente vengono salvate in flussi con il nome del flusso che corrisponde alla chiave che verrà usata per identificare le informazioni nel file con estensione suo. Il file delle opzioni utente della soluzione viene usato per archiviare le impostazioni delle preferenze utente e viene creato automaticamente Visual Studio salva una soluzione.

 Quando l'ambiente apre un file con estensione suo, enumera tutti i pacchetti VSPackage attualmente caricati. Se un VSPackage implementa l'interfaccia , l'ambiente chiama il metodo sul pacchetto VSPackage per chiedere di caricare tutti i dati <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> dal file con estensione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> suo.

 È responsabilità del VSPackage conoscere i flussi che potrebbe aver scritto nel file con estensione suo. Per ogni flusso scritto, il pacchetto VSPackage richiama l'ambiente tramite per caricare un flusso specifico identificato dalla chiave, ovvero il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> nome del flusso. L'ambiente chiama quindi il vspackage per leggere il flusso specifico passando il nome del flusso e un `IStream` puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metodo .

 A questo punto, viene effettuata un'altra chiamata a per verificare se è presente un'altra sezione del file con estensione `LoadUserOptions` suo che deve essere letta. Questo processo continua fino a quando tutti i flussi di dati nel file con estensione suo non sono stati letti ed elaborati dall'ambiente.

 Quando la soluzione viene salvata o chiusa, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metodo con un puntatore al metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> . Un oggetto contenente le informazioni binarie da salvare viene passato al metodo , che quindi scrive le informazioni nel file con estensione suo e chiama di nuovo il metodo per verificare se esiste un altro flusso di informazioni da scrivere nel file con estensione `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> `SaveUserOptions` suo.

 Questi due metodi, e , vengono chiamati in modo ricorsivo per ogni flusso di informazioni da salvare nel file con estensione suo, passando il `SaveUserOptions` `WriteUserOptions` puntatore a `IVsSolutionPersistence` . Vengono chiamati in modo ricorsivo per consentire la scrittura di più flussi nel file con estensione suo. In questo modo, le informazioni utente vengono mantenute con la soluzione ed è garantito che saranno presenti alla successiva apertura della soluzione.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluzioni](../../extensibility/internals/solutions-overview.md)
