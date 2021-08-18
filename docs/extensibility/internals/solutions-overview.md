---
title: Panoramica delle soluzioni
description: Informazioni sui componenti interni di una soluzione, per gli sviluppatori di estensioni che vogliono usare soluzioni in Visual Studio specifiche.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6ea779481103042241821086d04e874d10d2ced2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028722"
---
# <a name="solutions-overview"></a>Panoramica delle soluzioni

Una soluzione è un raggruppamento di uno o più progetti che lavorano insieme per creare un'applicazione. Le informazioni sul progetto e sullo stato relative alla soluzione vengono archiviate in due file di soluzione diversi. Il [file di soluzione (sln)](solution-dot-sln-file.md) è basato su testo e può essere inserito nel controllo del codice sorgente e condiviso tra gli utenti. Il [file dell'opzione utente della soluzione (con estensione suo)](solution-user-options-dot-suo-file.md) è binario. Di conseguenza, il file con estensione suo non può essere inserito nel controllo del codice sorgente e contiene informazioni specifiche dell'utente.

Qualsiasi VSPackage può scrivere in qualsiasi tipo di file di soluzione. A causa della natura dei file, esistono due interfacce diverse implementate per scrivervi. L'interfaccia scrive informazioni di testo nel file sln e l'interfaccia scrive flussi binari <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> nel file con estensione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> suo.

> [!NOTE]
> Un progetto non deve scrivere in modo esplicito una voce nel file della soluzione. l'ambiente lo gestisce per il progetto. Pertanto, a meno che non si voglia aggiungere contenuto aggiuntivo in modo specifico al file di soluzione, non è necessario registrare il pacchetto VSPackage in questo modo.

Ogni persistenza della soluzione di supporto di VSPackage usa tre interfacce, l'interfaccia , implementata dall'ambiente e chiamata dal pacchetto VSPackage, e , entrambe implementate dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> `IVsPersistSolutionProps` pacchetto `IVsPersistSolutionOpts` VSPackage. L'interfaccia deve essere implementata solo se le informazioni private devono essere scritte dal `IVsPersistSolutionOpts` pacchetto VSPackage nel file con estensione suo.

Quando viene aperta una soluzione, viene generato il processo seguente.

1. L'ambiente legge la soluzione.

2. Se l'ambiente trova `CLSID` , carica il pacchetto VSPackage corrispondente.

3. Se viene caricato un VSPackage, l'ambiente chiama l'interfaccia `QueryInterface` per l'interfaccia richiesta dal pacchetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> VSPackage.

   - Durante la lettura da un file sln, l'ambiente chiama `QueryInterface` `IVsPersistSolutionProps` per .

   - Durante la lettura da un file con estensione suo, l'ambiente chiama `QueryInterface` `IVsPersistSolutionOpts` per .

   Informazioni specifiche relative all'uso di questi file sono disponibili in [Soluzione (. Sln) Opzioni utente](../../extensibility/internals/solution-dot-sln-file.md) per file [e soluzioni (. Suo) File](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Se si vuole creare una nuova configurazione della soluzione costituita da configurazioni di due progetti ed escluderne un terzo dalla compilazione, è necessario usare l'interfaccia utente o l'automazione di Pagine delle proprietà. Non è possibile modificare direttamente le configurazioni di gestione della compilazione della soluzione e le relative proprietà, ma è possibile modificare il gestore di compilazione della soluzione usando la classe da DTE nel `SolutionBuild` modello di automazione. Per altre informazioni sulla configurazione delle soluzioni, vedere [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
