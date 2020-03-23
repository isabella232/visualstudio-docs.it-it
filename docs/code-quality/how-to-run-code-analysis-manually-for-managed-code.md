---
title: "Procedura: eseguire manualmente l'analisi del codice per il codice gestitoHow to: Run code analysis manually for managed code"
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431384"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Procedura: Eseguire manualmente l'analisi del codice per il codice gestito (richiede Visual Studio 2019 versione 16.5 o successiva)How to: Run code analysis manually for managed code (requires Visual Studio 2019 version 16.5 or later)
Per impostazione predefinita, gli analizzatori di codice della piattaforma del compilatore .NET ("Roslyn") analizzano il codice Di Visual Basic durante la digitazione eseguendo l'analisi in tempo reale, nonché durante la compilazione. Di conseguenza, in genere non è necessario attivare manualmente l'analisi del codice. Tuttavia, esistono alcuni scenari in cui è possibile attivare manualmente l'analisi del codice:However, there are some scenarios where you may want to manually trigger code analysis:

- Per impostazione predefinita, l'analisi del codice attivo esegue analizzatori solo per i file aperti in Visual Studio.By default, live code analysis executes analyzers only for open files in Visual Studio. Tuttavia, potrebbe essere interessato a visualizzare gli avvisi dell'analisi del codice per tutti i file in un progetto o soluzione specifica. In tal caso, si desidera attivare l'analisi del codice una volta in un progetto o una soluzione. In alternativa, è possibile abilitare l'analisi continua del codice in tempo reale per l'esecuzione su tutta la soluzione. Per ulteriori informazioni, vedere [Procedura: configurare l'ambito di analisi del codice in tempo reale per il codice gestito.](./configure-live-code-analysis-scope-managed-code.md)
- È possibile preferire il flusso di lavoro di esecuzione dell'analisi del codice su richiesta rispetto all'analisi in tempo reale continua o all'analisi in fase di compilazione. In tal caso, è possibile disabilitare l'esecuzione dell'analizzatore durante l'analisi in tempo reale e/o la compilazione. Per informazioni sulla disabilitazione dell'analisi, vedere [Come disabilitare l'analisi](disable-code-analysis.md)del codice sorgente. Quindi si desidera attivare manualmente l'analisi del codice una volta su un progetto o una soluzione. 

### <a name="run-code-analysis-manually"></a>Eseguire manualmente l'analisi del codice

1. In **Esplora soluzioni**fare clic sul progetto.

2. Scegliere **Esegui** analisi **codice in** *Nome progetto*dal menu Analizza .

L'analisi del codice inizierà l'esecuzione in background. Verrà visualizzato il messaggio **Esecuzione \<dell'analisi del codice per** i> del progetto... nella barra di stato di Visual Studio verso l'angolo inferiore sinistro. Al termine dell'analisi del codice, il messaggio di stato verrà modificato in **Analisi del codice completata per \< **il progetto>. L'elenco degli errori verrà presto aggiornato con tutta la diagnostica dell'analisi del codice.
