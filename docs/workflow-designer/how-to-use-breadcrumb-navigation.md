---
title: "Progettazione flussi di lavoro - Procedura: Usare l'esplorazione tramite navigazione"
description: Informazioni su come usare la navigazione tramite navigazione per accedere a un'attività figlio, passare a un'attività predecessore o espandere o comprimere le attività sul posto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b0daeebb7db8ca87ebd225f683b171b56e28822d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067974"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procedura: utilizzare l'esplorazione tramite la barra di navigazione

Esistono tre modi principali per modificare il set di attività visualizzate in Progettazione flussi di lavoro:

1. Facendo doppio clic per analizzare un'attività figlio.

2. Facendo clic su un pulsante nella barra di navigazione per passare a un'attività predecessore.

3. Espandendo o comprimendo le attività sul posto.

## <a name="using-breadcrumb-navigation"></a>Usando l'esplorazione tramite la barra di navigazione

1. Fare doppio clic su un'attività Progettazione flussi di lavoro per modificare l'attività radice con l'attività selezionata. L'attività selezionata viene quindi espansa completamente nella radice e i relativi predecessori vengono visualizzati nella barra di navigazione. Questa operazione viene talvolta definita analisi o annullamento dell'analisi di un'attività.

2. Per passare a un predecessore dell'attività radice corrente, fare clic sull'attività nella barra di navigazione.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Espansione o compressione di un'attività sul posto

1. Fare clic sulle virgolette in un'attività per espanderla o comprimerla sul posto.

2. Quando lo stato di espansione viene modificato facendo clic sul pulsante, il nuovo stato di espansione viene salvato in XAML.

    > [!WARNING]
    > Non tutte le attività possono essere espanse sul posto. Esistono due casi in cui un'attività non può essere espansa sul posto, ovvero quando il padre dell'attività non consente l'espansione sul posto dei relativi figli (le attività di un diagramma di flusso non possono ad esempio essere espanse sul posto) o quando non è consentita l'espansione automatica dell'ActivityDesigner sul posto. Anche se nessuno degli ActivityDesigner inclusi Progettazione flussi di lavoro il secondo comportamento, alcune attività personalizzate possono presentare questo comportamento.

## <a name="expanding-all-or-collapsing-all-activities"></a>Espansione o compressione di tutte le attività

1. Usare i **pulsanti Espandi tutto** e **Comprimi** tutto nell'interfaccia utente per espandere o comprimere tutte le attività nella radice di navigazione corrente. Si noti che Espandi tutto e Comprimi tutto sono stati globali. Ciò significa che quando si modifica l'attività radice usando la navigazione tramite navigazione, lo stato espandi tutto o comprimi tutto rimane fino a quando non si fa clic su **Ripristina**.

2. Dopo aver applicato uno stato espandi tutto o  comprimi tutto, è possibile fare clic sul pulsante Ripristina visualizzato per tornare allo stato applicato in precedenza a ogni attività.

    > [!WARNING]
    > Se un'attività, ad esempio , ha scelto esplicitamente di disattivare l'espansione sul posto, la funzionalità associata ai pulsanti Espandi tutto e Comprimi tutto è disabilitata nella finestra <xref:System.Activities.Statements.Flowchart> di progettazione del diagramma **di** flusso.   Per altre informazioni sulla finestra **di progettazione diagramma** di flusso, vedere l'argomento Diagramma [di](../workflow-designer/flowchart-activity-designer.md) flusso.

    > [!WARNING]
    > Espandi tutto ha anche un effetto speciale negli **ActivityDesigner Switch** e **TryCatch.** Quando si fa **clic su Espandi tutto**, vengono visualizzati tutti i case delle opzioni e tutti i blocchi try/catch/finally. Facendo **clic su** Ripristina o **Comprimi** tutto, queste finestre di progettazione vengono ripristinate allo stato predefinito, da cui è possibile fare clic su un singolo case/blocco per visualizzarne il contenuto.
