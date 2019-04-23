---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Usare la barra di navigazione'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de1004dd7a62fe4163147db4928783dd9a0dca98
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049570"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procedura: Usare la barra di navigazione

Esistono tre modi principali per modificare il set di attività che vengono visualizzati nella finestra di progettazione del flusso di lavoro:

1. Facendo doppio clic per analizzare un'attività figlio.

2. Facendo clic su un pulsante nella barra di navigazione per passare a un'attività predecessore.

3. Espandendo o comprimendo le attività sul posto.

## <a name="using-breadcrumb-navigation"></a>Usando l'esplorazione tramite la barra di navigazione

1. Fare doppio clic su un'attività di progettazione del flusso di lavoro per modificare l'attività radice per l'attività selezionata. L'attività selezionata viene quindi espansa completamente alla radice e relativi predecessori vengono mostrati nella barra di navigazione. Questa operazione viene talvolta definita analisi o annullamento dell'analisi di un'attività.

2. Per passare a un predecessore dell'attività radice corrente, fare clic sull'attività nella barra di navigazione.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Espansione o compressione di un'attività sul posto

1. Fare clic sulle virgolette in un'attività per espanderla o comprimerla sul posto.

2. Quando lo stato di espansione viene modificato facendo clic sul pulsante, il nuovo stato di espansione viene salvato in XAML.

    > [!WARNING]
    > Non tutte le attività possono essere espanse sul posto. Esistono due casi in cui un'attività non può essere espansa sul posto, ovvero quando il padre dell'attività non consente l'espansione sul posto dei relativi figli (le attività di un diagramma di flusso non possono ad esempio essere espanse sul posto) o quando non è consentita l'espansione automatica dell'ActivityDesigner sul posto. Anche se nessuno degli ActivityDesigner inclusi nella finestra di progettazione del flusso di lavoro hanno il comportamento di quest'ultimo, alcune attività personalizzate lo espongano.

## <a name="expanding-all-or-collapsing-all-activities"></a>Espansione o compressione di tutte le attività

1. Usare la **Espandi tutto** e **Comprimi tutto** pulsanti nell'interfaccia utente per espandere o comprimere tutte le attività sotto la radice di navigazione corrente. Si noti che Espandi tutto e Comprimi tutto sono stati globali. Ciò significa che quando si modifica l'attività radice usando la struttura di spostamento, espandere tutte o comprimere tutti gli stati persiste fino a quando non si fa clic su **ripristinare**.

2. Quando è stato applicato un Espandi tutto o Comprimi tutti gli stati, è possibile scegliere il **ripristinare** pulsante visualizzato per tornare alla visualizzazione dello stato in precedenza applicato a ogni attività.

    > [!WARNING]
    > Se un'attività, ad esempio <xref:System.Activities.Statements.Flowchart>, ha acconsentito esplicitamente espansione sul posto, la funzionalità associata il **Espandi tutto** e **Comprimi tutto** pulsanti sono disabilitato nel **diagramma di flusso**  finestra di progettazione. Per altre informazioni sul **diagramma di flusso** della finestra di progettazione, vedere il [Flowchart](../workflow-designer/flowchart-activity-designer.md) argomento.

    > [!WARNING]
    > Espandi tutto ha anche un effetto speciale **commutatore** e **TryCatch** ActivityDesigner. Quando fa clic su **Espandi tutto**, vengono visualizzati tutti i case switch e tutti i blocchi try/catch/finally. Facendo clic **ripristinare** oppure **Comprimi tutto** restituisce queste finestre di progettazione al relativo stato predefinito, in cui è possibile scegliere un case/blocco singolo per visualizzarne il contenuto.