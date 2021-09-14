---
title: Come eseguire manualmente l'analisi del codice per .NET
ms.date: 09/02/2020
description: Informazioni su come eseguire manualmente l'analisi del codice in Visual Studio 2019 versione 16.5 o versioni successive. Vedere come eseguire gli analizzatori Roslyn in C# o Visual Basic codice.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 571845c313a0712a10383a1cb718fea4bc4817f2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631950"
---
# <a name="run-code-analysis-manually-for-net"></a>Eseguire manualmente l'analisi del codice per .NET
Per impostazione predefinita, .NET Compiler Platform analizzatori ("Roslyn") analizzano il codice C# o Visual Basic durante la digitazione eseguendo analisi in tempo reale, nonché durante la compilazione. Di conseguenza, in genere non è necessario attivare manualmente l'analisi del codice. Esistono tuttavia alcuni scenari in cui può essere necessario attivare manualmente l'analisi del codice:

> [!NOTE]
> L'esecuzione manuale dell'analisi del codice Visual Studio 2019 versione 16.5 o successiva

- Per impostazione predefinita, l'analisi del codice in tempo reale esegue analizzatori solo per i file aperti Visual Studio. Tuttavia, potrebbe essere necessario visualizzare gli avvisi di analisi del codice per tutti i file in un progetto o una soluzione specifica. In tal caso, è necessario attivare l'analisi del codice una sola volta in un progetto o in una soluzione. In alternativa, è possibile abilitare l'analisi continua del codice in tempo reale per l'esecuzione nell'intera soluzione. Per altre informazioni, vedere [Procedura: Configurare l'ambito di](./configure-live-code-analysis-scope-managed-code.md)analisi del codice in tempo reale per il codice gestito.
- È possibile preferire il flusso di lavoro di esecuzione dell'analisi del codice su richiesta rispetto all'analisi continua in tempo reale o all'analisi in fase di compilazione. In tal caso, è possibile disabilitare l'esecuzione dell'analizzatore durante l'analisi in tempo reale e/o la compilazione. Per informazioni sulla disabilitazione dell'analisi, vedere [Come disabilitare l'analisi del codice sorgente.](disable-code-analysis.md) È quindi necessario attivare manualmente l'analisi del codice una volta in un progetto o in una soluzione.

### <a name="run-code-analysis-manually"></a>Eseguire manualmente l'analisi del codice

1. In **Esplora soluzioni** selezionare il progetto.

2. Nel menu **Analizza** selezionare Esegui Code Analysis **in Project** *nome*.

L'analisi del codice inizierà l'esecuzione in background. Verrà visualizzato il messaggio Esecuzione dell'analisi del codice per **\<project> ...** nella barra Visual Studio di stato verso l'angolo inferiore sinistro. Al termine dell'analisi del codice, il messaggio di stato cambierà in **Analisi del codice completata per \<project>**. L'elenco degli errori verrà presto aggiornato con tutta la diagnostica dell'analisi del codice.
