---
title: 'Procedura: richiamare il debugger del flusso di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292891"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Procedura: richiamare il debugger del flusso di lavoro.
Generalmente si esegue il debug dei flussi di lavoro nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio. È possibile avviare il debugger del flusso di lavoro nei modi seguenti:

- Scegliere **Connetti a processo** dal menu **debug** per selezionare il processo host in esecuzione per l'istanza del flusso di lavoro. La procedura è identica a quella di collegamento a un processo host nel codice gestito.

- Premere **F5** per avviare l'esecuzione di un'istanza del flusso di lavoro o per continuare l'esecuzione dopo che è stato raggiunto un punto di interruzione.

- Usare debug remoto. Per informazioni sull'uso del debug remoto, vedere [procedura: abilitare il debug remoto](https://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Se l'applicazione del flusso di lavoro è destinata all'architettura x86 ed è ospitata in un computer che esegue un sistema operativo a 64 bit, il debug remoto non funzionerà a meno che [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] non sia installato nel computer remoto o la destinazione dell'applicazione del flusso di lavoro venga modificata in **qualsiasi CPU**.

### <a name="stepping-through-code"></a>Esecuzione di codice istruzione per istruzione

- **Esegui istruzione**: è possibile eseguire un'istruzione in un'attività con **F11**. Il debugger avanza in qualsiasi gestore definito. Se nessun gestore è definito, viene eseguita l'istruzione/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione.

- Esci **da istruzione/uscita:** È possibile uscire da un'attività usando **Shift-F11**. Uscendo da un'istruzione/routine di un'attività, l'attività corrente e tutte le relative attività di pari livello vengono eseguite fino al completamento. Il debugger reimposta quindi il padre dell'attività corrente. Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.

- **Esegui istruzione/** routine: è possibile eseguire un'istruzione/routine di un'attività usando **F10**. Quando viene eseguita l'istruzione/routine di un oggetto CompositeActivity, il debugger reimposta il primo figlio eseguibile del CompositeActivity. Quando viene eseguita l'istruzione/routine di un attività diversa da CompositeActivity, ad esempio <xref:System.Activities.Statements.Assign>, il debugger esegue l'attività e i gestori ad essa associati e reimposta l’attività successiva. Se l'attività eseguita è l'ultima attività figlio di un oggetto CompositeActivity, dopo l'esecuzione il debugger reimposterà l'attività padre.

### <a name="debugging-with-f5"></a>Debug con F5

- Se si compila un progetto di applicazione console del flusso di lavoro, è sufficiente premere **F5** per avviare il debug nell'applicazione e nel flusso di lavoro. Se si compila una libreria attività autonomamente, è necessario usare come progetto di avvio un'applicazione host eseguibile. Per impostare un progetto di avvio in **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nome del progetto dell'host e selezionare **Imposta come progetto di avvio**.

## <a name="see-also"></a>Vedere anche
 [Procedura: impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [debug dei flussi di lavoro con il progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)