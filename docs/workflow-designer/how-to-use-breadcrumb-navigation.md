---
title: "Progettazione flussi di lavoro-procedura: usare l'esplorazione di navigazione"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 291badb04c791305f655e187ff7853fc8c5087a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584569"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procedura: utilizzare l'esplorazione tramite la barra di navigazione

Esistono tre modi principali per modificare il set di attività visualizzate in Progettazione flussi di lavoro:

1. Facendo doppio clic per analizzare un'attività figlio.

2. Facendo clic su un pulsante nella barra di navigazione per passare a un'attività predecessore.

3. Espandendo o comprimendo le attività sul posto.

## <a name="using-breadcrumb-navigation"></a>Usando l'esplorazione tramite la barra di navigazione

1. Fare doppio clic su un'attività di Progettazione flussi di lavoro per impostare l'attività radice sull'attività su cui è stato fatto clic. L'attività su cui viene fatto clic viene quindi espansa completamente alla radice e i relativi predecessori vengono visualizzati nella barra di navigazione. Questa operazione viene talvolta definita analisi o annullamento dell'analisi di un'attività.

2. Per passare a un predecessore dell'attività radice corrente, fare clic sull'attività nella barra di navigazione.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Espansione o compressione di un'attività sul posto

1. Fare clic sulle virgolette in un'attività per espanderla o comprimerla sul posto.

2. Quando lo stato di espansione viene modificato facendo clic sul pulsante, il nuovo stato di espansione viene salvato in XAML.

    > [!WARNING]
    > Non tutte le attività possono essere espanse sul posto. Esistono due casi in cui un'attività non può essere espansa sul posto, ovvero quando il padre dell'attività non consente l'espansione sul posto dei relativi figli (le attività di un diagramma di flusso non possono ad esempio essere espanse sul posto) o quando non è consentita l'espansione automatica dell'ActivityDesigner sul posto. Sebbene nessuno degli ActivityDesigner inclusi in Progettazione flussi di lavoro abbia il secondo comportamento, alcune attività personalizzate possono presentare questo comportamento.

## <a name="expanding-all-or-collapsing-all-activities"></a>Espansione o compressione di tutte le attività

1. Usare i pulsanti **Espandi tutto** e **Comprimi tutto** nell'interfaccia utente per espandere o comprimere tutte le attività sotto la radice di navigazione corrente. Si noti che Espandi tutto e Comprimi tutto sono stati globali. Ciò significa che quando si modifica l'attività radice utilizzando l'esplorazione di navigazione, lo stato Espandi tutto o Comprimi tutto viene mantenuto fino a quando non si fa clic su **Ripristina**.

2. Dopo aver applicato uno stato Espandi tutto o Comprimi tutto, è possibile fare clic sul pulsante **Ripristina** che sembra tornare a esaminare lo stato applicato in precedenza a ogni attività.

    > [!WARNING]
    > Se un'attività, ad esempio <xref:System.Activities.Statements.Flowchart>, ha rifiutato l'espansione sul posto, la funzionalità associata ai pulsanti **Espandi tutto** e **Comprimi tutto** è disabilitata nella finestra di progettazione **diagramma di flusso** . Per ulteriori informazioni sulla finestra di progettazione **diagramma di flusso** , vedere l'argomento [diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > Expand all ha un effetto speciale anche negli ActivityDesigner **Switch** e **TryCatch** . Quando si fa clic su **Espandi tutto**, vengono visualizzati tutti i case switch e tutti i blocchi try/catch/finally. Se si fa clic su **Ripristina** o **Comprimi tutto** , le finestre di progettazione vengono restituite allo stato predefinito, da cui è possibile fare clic su un singolo case/blocco per visualizzarne il contenuto.
