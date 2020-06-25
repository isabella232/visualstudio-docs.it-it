---
title: Come eseguire manualmente l'analisi codice per il codice gestito
ms.date: 11/04/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 584ddc9953b6f1522d12722fdd9a24d71e4e1538
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371833"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Procedura: eseguire manualmente l'analisi codice per il codice gestito (richiede Visual Studio 2019 versione 16,5 o successiva)
Per impostazione predefinita, gli analizzatori di codice .NET Compiler Platform ("Roslyn") analizzano il codice C# o Visual Basic durante la digitazione eseguendo l'analisi in tempo reale e durante la compilazione. Di conseguenza, in genere non è necessario attivare manualmente l'analisi del codice. Tuttavia, esistono alcuni scenari in cui potrebbe essere necessario attivare manualmente l'analisi del codice:

- Per impostazione predefinita, l'analisi del codice in tempo reale esegue gli analizzatori solo per i file aperti in Visual Studio. Tuttavia, potrebbe essere interessante visualizzare gli avvisi di analisi del codice per tutti i file in un progetto o in una soluzione specifica. In tal caso, è necessario attivare l'analisi del codice una volta in un progetto o in una soluzione. In alternativa, è possibile abilitare l'analisi del codice Live continua per l'esecuzione in un'intera soluzione. Per altre informazioni, vedere [procedura: configurare l'ambito di analisi del codice in tempo reale per il codice gestito](./configure-live-code-analysis-scope-managed-code.md).
- Potrebbe essere preferibile un flusso di lavoro di esecuzione dell'analisi del codice su richiesta su un'analisi dinamica continua o sull'analisi in tempo reale. In tal caso, è possibile disabilitare l'esecuzione dell'analizzatore durante l'analisi in tempo reale e/o la compilazione. Per informazioni sulla disabilitazione dell'analisi, vedere [come disabilitare l'analisi del codice sorgente](disable-code-analysis.md). Sarà quindi necessario attivare manualmente l'analisi del codice una volta in un progetto o in una soluzione. 

### <a name="run-code-analysis-manually"></a>Eseguire manualmente l'analisi del codice

1. In **Esplora soluzioni**fare clic sul progetto.

2. Nel menu **analizza** fare clic su **Esegui analisi del codice sul** *nome del progetto*.

L'analisi del codice inizierà a essere eseguita in background. Verrà visualizzato il messaggio **esecuzione dell'analisi del codice per \<project> ..** . nella barra di stato di Visual Studio verso l'angolo inferiore sinistro. Al termine dell'analisi del codice, il messaggio di stato viene modificato in **analisi codice \<project> completato per **. L'elenco errori verrà aggiornato a breve con tutta la diagnostica dell'analisi del codice.
