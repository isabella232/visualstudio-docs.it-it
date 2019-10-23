---
title: Uso della macchina a stati legacy Progettazione flussi di lavoro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2b1ce1f1b2c6a16b5576880904feadf37a3e7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606763"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Utilizzo della finestra di progettazione flusso di lavoro di una macchina a stati (legacy)
Quando si crea un nuovo progetto flusso di lavoro della macchina a stati in [!INCLUDE[vs2010](../includes/vs2010-md.md)] destinato al [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o al [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], è possibile scegliere di usare l' **applicazione console del flusso** di lavoro della macchina a Stati o la **libreria del flusso di lavoro della macchina a stati** legacy modello di progetto. Se si sceglie uno di questi modelli di progetto della macchina a stati, la finestra di progettazione della macchina a stati viene presentata come interfaccia utente della finestra di progettazione del flusso di lavoro legacy. Per informazioni sui modelli di progetto della macchina a stati legacy, vedere [How: Creazione di applicazioni console flusso di lavoro macchina a stati (legacy) ](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) e [How a: Creare una libreria flusso di lavoro macchina a stati (legacy) ](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Il flusso di lavoro di una macchina a stati è costituito da un set di stati. Uno stato è indicato come stato iniziale. Ogni stato può ricevere un determinato set di eventi. In base a un evento, può essere fatta una transizione a un altro stato. Il flusso di lavoro di una macchina a stati può avere uno stato finale. Quando viene effettuata una transizione allo stato finale, l'esecuzione del flusso di lavoro è completata.

## <a name="state-machine-designer-views"></a>Visualizzazioni della finestra di progettazione della macchina a stati
 La finestra di progettazione della macchina a stati è una finestra di progettazione con figura a mano libera, ciò vuol dire che le attività possono essere spostate liberamente sull'area di progettazione. Progettazione macchina a stati dispone di due visualizzazioni: visualizzazione *stato* e visualizzazione *basata su eventi* .

 La visualizzazione di stato mostra le attività di stato e le attività basate sugli eventi che possono essere contenute all'interno di un'attività di stato. In questa visualizzazione, le transizioni da uno stato a un altro vengono rappresentate da righe che si estendono dall'attività basata sugli eventi in uno stato a un altro stato. È anche possibile creare transizioni tracciando una linea. Per tracciare la transizione, selezionare l'attività basata sugli eventi e quindi selezionare uno degli handle sull'attività e trascinarlo. Questa azione consente di tracciare una riga. Questa riga viene quindi allegata allo stato di destinazione, indicando una transizione tra stati.

 Per accedere alla visualizzazione basata sugli eventi, fare doppio clic su un'attività basata sugli eventi. La finestra di progettazione che verrà visualizzata è molto simile alla finestra di progettazione del flusso di lavoro sequenziale. All'inizio della finestra di progettazione, una barra di navigazione illustra la gerarchia delle attività fino all'attività basata sugli eventi visualizzata. È possibile tornare alla visualizzazione di stato facendo clic su qualsiasi elemento nella gerarchia visualizzata. Se è stata tracciata una transizione da uno stato all’altro nella visualizzazione di stato e se si sta visualizzando la visualizzazione basata sugli eventi di quell'attività, un'attività di stato fissa verrà aggiunta all'attività basata sugli eventi. Se si modificano le proprietà dell'attività di stato fissa, questa modifica è riflessa nella visualizzazione di stato.

## <a name="state-machine-workflow-activities"></a>Attività del flusso di lavoro di una macchina a stati
 Nella tabella seguente sono descritte le attività principali usate nella finestra di progettazione del flusso di lavoro della macchina a stati.

|Nome della casella degli strumenti|Attività|Descrizione|
|------------------|--------------|-----------------|
|**Stato**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in una macchina a Stati. può contenere altre attività **StateActivity** . Per ulteriori informazioni, vedere [utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato. Per ulteriori informazioni, vedere [utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Viene eseguita quando viene immesso uno stato; può contenere altre attività. Per ulteriori informazioni, vedere [utilizzo dell'attività StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Esegue le attività contenute quando si esce da un'attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) . Per ulteriori informazioni, vedere [utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Viene usata per stati che si basano su un evento esterno per avviare l’esecuzione. L'attività **EventDrivenActivity** deve avere un'attività che implementa l'interfaccia [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) come prima attività figlio. Per ulteriori informazioni, vedere [utilizzo dell'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|

 Il componente principale del flusso di lavoro di una macchina a Stati è l'attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) . Dato che gli eventi vengono acquisiti nei vari punti del flusso di lavoro della macchina a stati, vengono immessi stati diversi per gestire le attività associate agli eventi. Nel corso della durata del flusso di lavoro, il flusso di lavoro può uscire da e accedere a molti stati diversi. Questi Stati si connettono tra loro tramite l'attività [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) .

 Quando si trascina una nuova **StateActivity** sull'area di progettazione del flusso di lavoro, è possibile aggiungere attività [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)o **StateActivity** aggiuntive come attività figlio.

> [!CAUTION]
> Quando si utilizza Progettazione flussi di lavoro macchina a stati per creare flussi di lavoro, è necessario monitorare la struttura del flusso di lavoro che si sta progettando con la finestra visualizzazione **struttura documento** . La visualizzazione della struttura del flusso di lavoro della macchina a stati nella finestra visualizzazione **struttura documento** rispecchia il layout logico delle attività nel file di markup del flusso di lavoro. Il layout fisico delle attività del flusso di lavoro, così come vengono visualizzate nell'area di progettazione, potrebbe non rispecchiare il layout logico delle attività nel file di markup del flusso di lavoro.
>
> Per aprire la finestra **struttura documento** , scegliere **altre finestre**dal menu **Visualizza** , quindi selezionare **struttura documento**.

## <a name="see-also"></a>Vedere anche
 [Procedura: Creazione di applicazioni console flusso di lavoro macchina a stati (legacy) ](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [How a: Creare una libreria flusso di lavoro macchina a stati (legacy) ](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) i [flussi di lavoro della macchina a stati](http://go.microsoft.com/fwlink?LinkID=65016) [usando](http://go.microsoft.com/fwlink?LinkID=65083) l'attività StateActivity [usando l'attività StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006) [usando l'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008) [ Uso dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082) [usando l'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)