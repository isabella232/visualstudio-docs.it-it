---
title: Richiamo del debugger per Windows Workflow Foundation (legacy) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658984"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)
In questo argomento viene descritto come usare il Debugger di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per eseguire il debug di applicazioni [!INCLUDE[wf](../includes/wf-md.md)] in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Il debug dei flussi di lavoro legacy viene in genere eseguito nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio. È possibile avviare il debugger di [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per Windows Workflow Foundation nei modi seguenti:

- Scegliere **Connetti a processo** dal menu **debug** per selezionare un'istanza del flusso di lavoro in esecuzione dai processi disponibili.

- Premere **F5** per avviare l'esecuzione di un'istanza del flusso di lavoro o per continuare l'esecuzione dopo che è stato raggiunto un punto di interruzione.

## <a name="stepping-through-code"></a>Avanzamento tramite codice
 Il debugger supporta una delle procedure di debug più comuni, l’avanzamento, che consiste nell'esecuzione di una riga di codice alla volta. Esistono tre comandi di avanzamento tramite codice:

- **Esegui istruzione**: è possibile eseguire un'istruzione in un'attività con **F11**. Il debugger avanza in qualsiasi gestore definito. Se nessun gestore è definito, viene eseguita l'istruzione/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione. L'esecuzione di un'istruzione nei gestori del codice dalla finestra di progettazione non è supportata per le attività seguenti: **IfElseActivity**, **dell'WhileActivity**, **ConditionedActivityGroup**o **ReplicatorActivity**. Per eseguire il debug dei gestori associati a queste attività è necessario inserire punti di interruzione espliciti nel codice.

- Esci da **istruzione/uscita**: è possibile uscire da un'attività usando **Shift-F11**. Uscendo da un'istruzione/routine di un'attività, l'attività corrente e tutte le relative attività di pari livello vengono eseguite fino al completamento. Il debugger reimposta quindi il padre dell'attività corrente. Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.

- **Esegui istruzione/** routine: è possibile eseguire un'istruzione/routine di un'attività usando **F10**. Quando si passa a un'altra attività composta. Il debugger reimposta il primo figlio eseguibile dell'attività composta. Quando si esegue l'istruzione/routine di un oggetto non composito, ad esempio un'attività **CodeActivity** , il debugger esegue l'attività e i gestori associati e si interrompe nell'attività successiva. Se l'attività eseguita è l'ultima attività figlio di un'attività composta, dopo l'esecuzione il debugger reimposterà l'attività padre.

## <a name="attaching-to-a-process"></a>Connessione a un processo
 Per eseguire il debug di un flusso di lavoro mediante la connessione a un processo, selezionare il processo disponibile nella casella di riepilogo **processi disponibili** della finestra di dialogo **Connetti a processo** . Se **automatico: il codice del flusso di lavoro** non viene visualizzato nella casella **di testo Connetti a** , quindi fare clic su **Seleziona**. Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare flusso di **lavoro**. Fare quindi clic su **OK** e quindi su **Connetti**.

## <a name="debugging-with-f5"></a>Debug con F5
 Se un'applicazione host del flusso di lavoro e una DLL del flusso di lavoro si trovano in progetti di Visual Studio diversi, ad esempio quando si usa una libreria di attività del flusso di lavoro, è necessario impostare il progetto di DLL del flusso **F5**di lavoro come progetto di avvio della soluzione di Visual Studio per eseguire il debug del flusso di lavoro È inoltre necessario impostare il percorso dell'applicazione host nella proprietà **Avvia programma esterno** del progetto di dll del flusso di lavoro.

 Per impostare un progetto di avvio in Esplora soluzioni, fare clic con il pulsante destro del mouse sul nome del progetto e scegliere **Imposta come progetto di avvio**. Per impostare il percorso dell'host nella proprietà **Avvia programma esterno** , fare doppio clic sul nodo **Proprietà** del progetto flusso di lavoro in Esplora soluzioni e selezionare la scheda **debug** . In **azione di avvio**selezionare **Avvia programma esterno** e immettere il percorso del file con estensione exe che ospita il flusso di lavoro di cui si vuole eseguire il debug.

 Se l'applicazione host è impostata come progetto di avvio, solo il debugger di Visual Studio viene richiamato per l'esecuzione del debug. Il debugger di [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per Windows Workflow Foundation non viene richiamato. Se viene usato il debugger di Visual Studio, vengono eseguiti solo i punti di interruzione del codice C# o di Visual Basic, mentre i punti di interruzione impostati nella finestra di progettazione del flusso di lavoro non vengono eseguiti. Ad esempio, un punto di interruzione impostato su un'attività <xref:System.Workflow.Activities.ParallelActivity> nella finestra di progettazione verrà eseguito se viene usato il debugger di [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per Windows Workflow Foundation, ma non quando si usa il debugger di Visual Studio.

## <a name="see-also"></a>Vedere anche
 [Procedura: impostare punti di interruzione nei flussi di lavoro legacy di debug (legacy)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [Debugging Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)