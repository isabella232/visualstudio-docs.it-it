---
title: Debug dei flussi di lavoro mediante Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7432e02a4c8e133d7d758909a7ea851f90b88841
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650566"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Eseguire il debug dei flussi di lavoro con il Progettazione flussi di lavoro

Il **Progettazione flussi di lavoro** fornisce la possibilità di eseguire il debug di flussi di lavoro e attività personalizzate. Il processo e il comportamento sono simili a quelli del debugger predefinito di Visual Studio.

## <a name="invoke-the-workflow-debugger"></a>Richiamare il debugger del flusso di lavoro

Generalmente si esegue il debug dei flussi di lavoro nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio. È possibile avviare il debugger del flusso di lavoro nei modi seguenti:

- Scegliere **Connetti a processo** dal menu **debug** per selezionare il processo host in esecuzione per l'istanza del flusso di lavoro. La procedura è identica a quella di collegamento a un processo host nel codice gestito.

- Premere **F5** per avviare l'esecuzione di un'istanza del flusso di lavoro o per continuare l'esecuzione dopo che è stato raggiunto un punto di interruzione.

- Usare debug remoto. Per informazioni sull'uso del debug remoto, vedere [procedura: abilitare il debug remoto](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Se l'applicazione flusso di lavoro è destinata all'architettura x86 ed è ospitata in un computer che esegue un sistema operativo a 64 bit, il debug remoto non funzionerà a meno che Visual Studio non sia installato nel computer remoto o la destinazione dell'applicazione del flusso di lavoro venga modificata in  **Qualsiasi CPU**.

## <a name="step-through-code"></a>Esecuzione del codice un'istruzione alla volta

- **Esegui istruzione**: eseguire un'istruzione in un'attività premendo **F11**. Il debugger avanza in qualsiasi gestore definito. Se nessun gestore è definito, viene eseguita l'istruzione/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione.

- Esci **da istruzione/uscita:** Uscire da un'attività premendo **maiusc** +**F11**. Uscendo da un'istruzione/routine di un'attività, l'attività corrente e tutte le relative attività di pari livello vengono eseguite fino al completamento. Il debugger reimposta quindi il padre dell'attività corrente. Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.

- **Esegui istruzione/** routine: Esegui istruzione/routine di un'attività premendo **F10**. Quando viene eseguita l'istruzione/routine di un oggetto CompositeActivity, il debugger reimposta il primo figlio eseguibile del CompositeActivity. Quando viene eseguita l'istruzione/routine di un attività diversa da CompositeActivity, ad esempio <xref:System.Activities.Statements.Assign>, il debugger esegue l'attività e i gestori ad essa associati e reimposta l’attività successiva. Se l'attività eseguita è l'ultima attività figlio di un oggetto CompositeActivity, dopo l'esecuzione il debugger reimposterà l'attività padre.

## <a name="debug-with-f5"></a>Debug con F5

Se si sta compilando un'app console del flusso di lavoro, è sufficiente premere **F5** per avviare il debug nell'applicazione e nel flusso di lavoro. Se si compila una libreria attività in modo autonomo, è necessario specificare un'applicazione host eseguibile come progetto di avvio. Per impostare un progetto di avvio in **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nome del progetto dell'host e selezionare **Imposta come progetto di avvio**.