---
title: Panoramica delle soluzioni
description: Informazioni sugli elementi interni di una soluzione, per gli sviluppatori di estensioni che vogliono usare le soluzioni nelle estensioni di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 914f1744accc10eb55cfb0b321a04560c27bca05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069374"
---
# <a name="solutions-overview"></a>Panoramica delle soluzioni

Una soluzione è un raggruppamento di uno o più progetti che interagiscono tra loro per creare un'applicazione. Le informazioni sul progetto e sullo stato relative alla soluzione vengono archiviate in due diversi file di soluzione. Il [file della soluzione (. sln)](solution-dot-sln-file.md) è basato su testo e può essere inserito nel controllo del codice sorgente e condiviso tra gli utenti. Il [file delle opzioni utente della soluzione (. suo)](solution-user-options-dot-suo-file.md) è binario. Di conseguenza, il file con estensione suo non può essere inserito nel controllo del codice sorgente e contiene informazioni specifiche dell'utente.

Qualsiasi pacchetto VSPackage può scrivere in entrambi i tipi di file di soluzione. A causa della natura dei file, esistono due interfacce diverse implementate per la scrittura. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaccia scrive le informazioni di testo nel file con estensione sln e l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaccia scrive i flussi binari nel file con estensione suo.

> [!NOTE]
> Un progetto non deve scrivere in modo esplicito una voce per se stesso nel file di soluzione. l'ambiente gestisce quello per il progetto. Pertanto, a meno che non si desideri aggiungere contenuti aggiuntivi in modo specifico al file della soluzione, non è necessario registrare il pacchetto VSPackage in questo modo.

Ogni VSPackage che supporta la persistenza della soluzione USA tre interfacce, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaccia, che viene implementata dall'ambiente e chiamata dal pacchetto VSPackage, e `IVsPersistSolutionProps` e `IVsPersistSolutionOpts` , che sono entrambi implementati dal pacchetto VSPackage. L' `IVsPersistSolutionOpts` interfaccia deve essere implementata solo se le informazioni private devono essere scritte dal pacchetto VSPackage nel file con estensione suo.

Quando si apre una soluzione, si verifica il processo seguente.

1. La soluzione viene letta dall'ambiente.

2. Se l'ambiente rileva un oggetto `CLSID` , carica il pacchetto VSPackage corrispondente.

3. Se viene caricato un pacchetto VSPackage, l'ambiente chiama l' `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfaccia per l'interfaccia richiesta dal pacchetto VSPackage.

   - Quando si esegue la lettura da un file con estensione sln, l'ambiente chiama `QueryInterface` `IVsPersistSolutionProps` .

   - Quando si esegue la lettura da un file con estensione suo, l'ambiente chiama `QueryInterface` `IVsPersistSolutionOpts` .

   Informazioni specifiche relative all'utilizzo di questi file sono disponibili nella [soluzione (. Sln)](../../extensibility/internals/solution-dot-sln-file.md) [Opzioni utente file e soluzione (. Suo) file](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Se si vuole creare una nuova configurazione di soluzione costituita da due configurazioni di progetti ed escludendo un terzo dalla compilazione, è necessario usare l'interfaccia utente delle pagine delle proprietà o l'automazione. Non è possibile modificare direttamente le configurazioni del gestore di compilazione della soluzione e le relative proprietà, ma è possibile modificare il gestore di compilazione della soluzione usando la `SolutionBuild` classe da DTE nel modello di automazione. Per altre informazioni sulla configurazione delle soluzioni, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
