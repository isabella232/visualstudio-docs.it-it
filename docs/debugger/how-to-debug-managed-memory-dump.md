---
title: Eseguire il debug managed memory dump di diagnostica con gli analizzatori di diagnostica .NET | Microsoft Docs
description: Informazioni su come usare gli analizzatori di diagnostica .NET di Visual Studio per analizzare un dump managed memory
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: a0931f6f8aba8dfbef705542cad889edc1441a327945d5640459e7cac4d0a2d5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379334"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>Come eseguire il debug di un dump managed memory con gli analizzatori di diagnostica .NET



In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Apertura di un dump della memoria
> * Selezionare ed eseguire gli analizzatori rispetto al dump
> * Esaminare i risultati degli analizzatori
> * Passaggio al codice problematico


Nell'esempio descritto in questo articolo, il problema è che l'app non risponde alle richieste in modo corretto. 


## <a name="opening-a-memory-dump-in-visual-studio"></a>Apertura di un dump della memoria in Visual Studio

1. Aprire il dump della memoria Visual Studio file usando il comando di menu > Apri > **file** e selezionare il dump della memoria.

1. Si noti che nella pagina Riepilogo dump memoria è presente una **nuova azione** denominata Esegui **analisi diagnostica**.

   ![Azione - Analisi diagnostica](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. Selezionare questa azione per avviare il debugger e aprire la nuova pagina **Analisi** diagnostica con un elenco delle opzioni dell'analizzatore disponibili, organizzate in base al sintomo sottostante.


## <a name="select-and-execute-analyzers-against-the-dump"></a>Selezionare ed eseguire gli analizzatori rispetto al dump

Per analizzare questi sintomi, le opzioni migliori sono disponibili in **Velocità di** risposta del processo perché corrisponde meglio al problema in questo esempio.

   ![Selezionare gli analizzatori di diagnostica](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. Fare clic **sul pulsante** Analizza per avviare il processo di indagine 

1. L'analizzatore presenterà i risultati in base alla combinazione di informazioni sul processo e dati CLR acquisiti nel dump della memoria.
 
## <a name="review-the-results-of-the-analyzers"></a>Esaminare i risultati degli analizzatori

1. In questo caso, l'analizzatore ha rilevato due errori. Selezionare il risultato dell'analizzatore per visualizzare **il riepilogo dell'analisi** e **la correzione suggerita.**

   ![Risultati degli analizzatori di diagnostica](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. Il **riepilogo dell'analisi** ha dichiarato che il "pool di thread CLR sta riscontrando un'carezza". Queste informazioni suggeriscono che CLR ha attualmente usato tutti i thread del pool di thread disponibili, il che significa che il servizio non può rispondere ad alcuna nuova richiesta fino a quando non viene rilasciato un thread.

    > [!NOTE] 
    > La **correzione** in questo caso è "Non attendere in modo sincrono monitoraggi, eventi, attività o qualsiasi altro oggetto che potrebbe bloccare il thread. Verificare se è possibile aggiornare il metodo in modo che sia asincrono".

## <a name="navigating-to-the-problematic-code"></a>Passaggio al codice problematico

Il mio compito successivo è trovare il codice problematico.

1. Facendo clic sul **collegamento Mostra stack** di chiamate Visual Studio si passa immediatamente ai thread che presentano questo comportamento.

1. La **finestra Stack di** chiamate mostrerà i metodi che potrebbero potenzialmente distinguere rapidamente tra il codice (SyncOverAsyncExmple. ) dal codice del framework *(sistema).*

   ![Collegamento degli analizzatori di diagnostica a uno stack di chiamate](../debugger/media/diagnostic-analyzer-call-stack.png)

1. Ogni stack frame corrisponde a un metodo e facendo doppio clic sugli stack frame Visual Studio si passa al codice che ha portato direttamente a questo scenario in questo thread.

1. In questo esempio non sono presenti simboli o  codice, tuttavia, nella pagina Simboli non caricati è possibile selezionare l'opzione **[Decompila codice sorgente.](../debugger/decompilation.md)**

   ![Decompilazione](../debugger/media/diagnostic-analyzer-decompilation.png)

1. Nell'origine decompilata seguente è evidente che un'attività asincrona (ConsumeThreadPoolThread) chiama una funzione di blocco sincrona.

    > [!NOTE]  
    > Metodo "DoSomething()" che contiene un metodo WaitHandle.WaitOne, che blocca il thread del pool di thread corrente fino a quando non riceve un segnale.

   Per migliorare la velocità di risposta delle app, è importante rimuovere il blocco del codice sincrono da tutti i contesti asincroni.

   ![Analizzare il codice decompilato](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>Vedi anche

* [Usare i file di dump nel debugger](../debugger/using-dump-files.md)
* [Generare codice sorgente da assembly .NET durante il debug](../debugger/decompilation.md)
* [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
