---
title: Richiamo del Debugger per Windows Workflow Foundation (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 82532fc2864bcb4c19b0cf122e60fd9a64b2dbf9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113066"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)
In questo argomento viene descritto come usare il Debugger di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per eseguire il debug di applicazioni [!INCLUDE[wf](../includes/wf-md.md)] in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Il debug dei flussi di lavoro legacy viene in genere eseguito nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio. È possibile avviare il debugger di [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per Windows Workflow Foundation nei modi seguenti:

- Selezionare **Connetti a processo** nel **Debug** menu per selezionare un'istanza del flusso di lavoro in esecuzione dai processi disponibili.

- Premere **F5** per avviare l'esecuzione di un'istanza del flusso di lavoro o per continuare a eseguire dopo aver raggiunto un punto di interruzione.

## <a name="stepping-through-code"></a>Avanzamento tramite codice
 Il debugger supporta una delle procedure di debug più comuni, l’avanzamento, che consiste nell'esecuzione di una riga di codice alla volta. Esistono tre comandi di avanzamento tramite codice:

- **Passaggio**: È possibile avanzare in un'attività usando **F11**. Il debugger avanza in qualsiasi gestore definito. Se nessun gestore è definito, viene eseguita l'istruzione/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione. L'esecuzione di istruzioni in gestori del codice dalla finestra di progettazione non è supportato per le attività seguenti: **Attività IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**, o il **ReplicatorActivity**. Per eseguire il debug dei gestori associati a queste attività è necessario inserire punti di interruzione espliciti nel codice.

- **Esci da istruzione**: È possibile uscire un'attività usando **MAIUSC+F11**. Uscendo da un'istruzione/routine di un'attività, l'attività corrente e tutte le relative attività di pari livello vengono eseguite fino al completamento. Il debugger reimposta quindi il padre dell'attività corrente. Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.

- **Esegui istruzione/routine**: È possibile passare a un'attività usando **F10**. Quando si passa a un'altra attività composta. Il debugger reimposta il primo figlio eseguibile dell'attività composta. Scavalcando un' non composte, ad esempio un **CodeActivity** attività, il debugger esegue l'attività e gestori ad essa associati e le interruzioni di attività successiva. Se l'attività eseguita è l'ultima attività figlio di un'attività composta, dopo l'esecuzione il debugger reimposterà l'attività padre.

## <a name="attaching-to-a-process"></a>Connessione a un processo
 Per eseguire il debug di un flusso di lavoro mediante il collegamento di un processo, selezionare il processo disponibile dal **processi disponibili** casella di riepilogo il **Connetti a processo** nella finestra di dialogo. Se **automatico: Codice del flusso di lavoro** non viene visualizzato nei **collegare a** testo casella, quindi fare clic su **selezionare**. Nel **Seleziona tipo di codice** finestra di dialogo, fare clic su **eseguire il Debug di questi tipi di codice** e selezionare **flusso di lavoro**. Quindi fare clic su **OK** e fare clic su **Attach**.

## <a name="debugging-with-f5"></a>Debug con F5
 Se un'applicazione host del flusso di lavoro e flusso di lavoro DLL si trovano in diversi progetti di Visual Studio, ad esempio, quando si usa una libreria di attività del flusso di lavoro, è necessario impostare il progetto DLL del flusso di lavoro come progetto di avvio di soluzione Visual Studio per eseguire il debug del flusso di lavoro usando **F5**. È anche necessario impostare il percorso all'applicazione host del progetto di DLL del flusso di lavoro **Avvia programma esterno** proprietà.

 Per impostare un progetto di avvio in Esplora soluzioni, fare clic sul nome del progetto e scegliere **imposta come progetto di avvio**. Per impostare il percorso nell'host nel **Avvia programma esterno** proprietà, fare doppio clic il flusso di lavoro **delle proprietà** nodo in Esplora soluzioni e selezionare il **Debug** scheda. Sotto **azione di avvio**, selezionare **Avvia programma esterno** e immettere il percorso del file .exe che ospita il flusso di lavoro che si desidera eseguire il debug.

 Se l'applicazione host è impostata come progetto di avvio, solo il debugger di Visual Studio viene richiamato per l'esecuzione del debug. Il debugger di [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per Windows Workflow Foundation non viene richiamato. Se viene usato il debugger di Visual Studio, vengono eseguiti solo i punti di interruzione del codice C# o di Visual Basic, mentre i punti di interruzione impostati nella finestra di progettazione del flusso di lavoro non vengono eseguiti. Ad esempio, un punto di interruzione impostato su un'attività <xref:System.Workflow.Activities.ParallelActivity> nella finestra di progettazione verrà eseguito se viene usato il debugger di [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per Windows Workflow Foundation, ma non quando si usa il debugger di Visual Studio.

## <a name="see-also"></a>Vedere anche
 [Procedura: Impostare punti di interruzione nei flussi di lavoro (Legacy)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [debug dei flussi di lavoro Legacy](../workflow-designer/debugging-legacy-workflows.md)