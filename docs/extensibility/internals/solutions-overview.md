---
title: Panoramica delle soluzioni
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705304"
---
# <a name="solutions-overview"></a>Panoramica delle soluzioni

Una soluzione è un raggruppamento di uno o più progetti che lavorano insieme per creare un'applicazione. Le informazioni sul progetto e sullo stato relative alla soluzione vengono archiviate in due file di soluzione diversi. Il file di [soluzione (sln)](solution-dot-sln-file.md) è basato su testo e può essere inserito nel controllo del codice sorgente e condiviso tra gli utenti. Il file dell'opzione utente della [soluzione (con estensione suo)](solution-user-options-dot-suo-file.md) è binario. Di conseguenza, il file con estensione suo non può essere inserito nel controllo del codice sorgente e contiene informazioni specifiche dell'utente.

Qualsiasi VSPackage può scrivere in entrambi i tipi di file di soluzione. A causa della natura dei file, ci sono due diverse interfacce implementate per scrivere su di loro. L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> scrive informazioni di testo nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> file sln e l'interfaccia scrive flussi binari nel file con estensione suo.

> [!NOTE]
> Un progetto non deve scrivere in modo esplicito una voce per se stesso nel file di soluzione; l'ambiente gestisce che per il progetto. Pertanto, a meno che non si desidera aggiungere contenuto aggiuntivo in modo specifico al file di soluzione, non è necessario registrare il pacchetto VSPackage in questo modo.

Ogni VSPackage che supporta la persistenza della soluzione utilizza tre interfacce, l'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> che viene implementata dall'ambiente e chiamata dal pacchetto VSPackage e `IVsPersistSolutionProps` e `IVsPersistSolutionOpts`, che sono entrambi implementati dal pacchetto VSPackage. L'interfaccia `IVsPersistSolutionOpts` deve essere implementata solo se le informazioni private devono essere scritte dal pacchetto VSPackage nel file con estensione suo.

Quando viene aperta una soluzione, viene eseguito il processo seguente.

1. L'ambiente legge la soluzione.

2. Se l'ambiente `CLSID`trova un , carica il pacchetto VSPackage corrispondente.

3. Se viene caricato un pacchetto `QueryInterface` VSPackage, l'ambiente chiama l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> per l'interfaccia necessaria per il pacchetto VSPackage.

   - Durante la lettura da un file sln, l'ambiente richiede `QueryInterface` `IVsPersistSolutionProps`.

   - Durante la lettura da un file `QueryInterface` `IVsPersistSolutionOpts`con estensione suo, l'ambiente richiede .

   Informazioni specifiche relative all'uso di questi file sono disponibili in [Soluzione (. Sln) Opzioni](../../extensibility/internals/solution-dot-sln-file.md) utente file e [soluzione (. Suo) File](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Se si vuole creare una nuova configurazione di soluzione costituita da configurazioni di due progetti ed escluderne un terzo dalla compilazione, è necessario usare l'interfaccia utente o l'automazione delle pagine delle proprietà. Non è possibile modificare direttamente le configurazioni del gestore di compilazione `SolutionBuild` della soluzione e le relative proprietà, ma è possibile modificare il gestore di compilazione della soluzione usando la classe da DTE nel modello di automazione. Per ulteriori informazioni sulla configurazione delle soluzioni, vedere [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
