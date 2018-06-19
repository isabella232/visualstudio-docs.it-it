---
title: Finestra di progettazione del flusso di lavoro - opzioni di esecuzione di istruzioni di Debug (Legacy)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969070"
---
# <a name="debug-stepping-options-legacy"></a>Opzioni di avanzamento nell’esecuzione del debug (legacy)

In questo argomento viene descritto come eseguire il debug di applicazioni di Windows Workflow Foundation (WF) che dispongono di attività simultanee in Progettazione flussi di lavoro Windows legacy. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando è necessario avere come destinazione .NET Framework versione 3.5 o la WinFX.

Quando si esegue il debug di attività legacy esecuzione simultanea, ad esempio **ParallelActivity** o **ConditionedActivityGroup**, è possibile utilizzare una delle due opzioni seguenti per esaminare il codice .

-   **Avanzamento nel ramo.** Questo metodo consente di procedere ed eseguire il debug di un particolare ramo di un'attività composta, ad esempio il **ParallelActivity** o **ConditionalActivityGroup** attività. Quando si usa quest'opzione di debug, non si noterà una modifica nel controllo dovuta all'esecuzione contemporanea di altre attività all'interno del flusso di lavoro. Il debugger avanza solo attraverso le attività del ramo attualmente selezionato mentre le altre attività del flusso di lavoro possono essere eseguite contemporaneamente. Ad esempio, per impostazione predefinita, il ramo all'estrema sinistra di un **ParallelActivity** attività e la prima attività figlio di un **ConditionedActivityGroup** attività vengono utilizzati per l'esecuzione di istruzioni. Se l’utente desidera eseguire il debug di qualsiasi altro ramo o attività figlia, un punto di interruzione esplicito deve essere posizionato su quel ramo o su quella attività figlia. Quando il punto di interruzione viene generato, l'avanzamento continua in quel ramo.

-   **Avanzamento nell'istanza.** Questa modalità di procedere consente di procedere ed eseguire il debug eseguendo contemporaneamente le attività del flusso di lavoro. Con questa opzione, si noterà che si verifica una modifica nel controllo durante l'esecuzione contemporanea di attività eseguite all'interno del flusso di lavoro.

Per impostazione predefinita, l'opzione di avanzamento nel ramo è selezionata e gli utenti possono passare tra le due opzioni durante l'esecuzione del debug di un flusso di lavoro legacy.

È necessario selezionare l'opzione di avanzamento dell’istanza in caso di esecuzione di debug di flussi di lavoro di macchine a stati legacy.

## <a name="see-also"></a>Vedere anche

- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)
- [Procedura: Modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)