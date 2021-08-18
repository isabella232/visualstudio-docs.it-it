---
title: Configurare la riduzione del rumore nelle visualizzazioni report | Microsoft Docs
description: Usare il trimming e la riduzione, entrambi abilitati per impostazione predefinita, per ridurre il rumore e rendere più evidenti i problemi di prestazioni nei report.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 015ea700cca87912013b5b12c3d9e2ead78a0c54
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038851"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Procedura: Configurare la riduzione del rumore nelle visualizzazioni dei report
I rapporti di prestazioni possono essere configurati per la riduzione del rumore limitando la quantità di dati presentati nelle visualizzazioni Albero delle chiamate e Allocazioni. Con la riduzione del rumore, i problemi di prestazioni sono più evidenti. In questo modo è più semplice analizzare i rapporti di prestazioni.

 Le opzioni di configurazione della riduzione del rumore includono le impostazioni seguenti:

- **Trimming**: quando un rapporto viene analizzato, la visualizzazione ometterà le funzioni che rientrano all'interno delle impostazioni di valore e soglia che sono state configurate, come descritto nella procedura di trimming riportata di seguito. Il trimming è abilitato per impostazione predefinita.

- **Riduzione**: se si abilita la riduzione, le funzioni consecutive su un percorso che soddisfano le impostazioni configurate verranno unite, come descritto nella procedura di riduzione riportata di seguito. La riduzione è abilitata per impostazione predefinita.

### <a name="to-configure-trimming-for-a-performance-report"></a>Per configurare il trimming per un rapporto di prestazioni

1. Quando viene visualizzata una visualizzazione Albero delle chiamate o Allocazioni nel rapporto generato, dal menu **Sviluppatore** scegliere **Profiler** e quindi fare clic su **Opzioni riduzione rumore**.

     Verrà visualizzata la finestra di dialogo **Riduzione rumore** .

2. Per abilitare il trimming, attenersi alla procedura seguente:

    1. Selezionare **Abilita trimming**. Si tratta dell'impostazione predefinita.

        > [!NOTE]
        > Se è abilitata la riduzione del rumore, nel rapporto verrà visualizzata una barra informazioni. Per altre informazioni, vedere [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).

    2. Configurare l'impostazione del valore usando l'elenco a discesa **Valore** e scegliendo l'impostazione applicabile.

    3. Configurare l'impostazione di soglia desiderata digitando un valore percentuale nella casella di testo **Soglia**.

    4. Per abilitare l'avviso di riduzione del rumore nel rapporto generato, selezionare **Visualizza un avviso nel rapporto generato quando è abilitata Riduzione rumore**. Si tratta dell'impostazione predefinita.

3. Per disabilitare il trimming, deselezionare **Abilita trimming**.

4. Fare clic su **OK**.

### <a name="to-configure-folding-for-a-performance-report"></a>Per configurare la riduzione per un rapporto di prestazioni

1. Dal menu **Sviluppatore** scegliere **Profiler** e quindi fare clic su **Opzioni riduzione rumore**.

     Verrà visualizzata la finestra di dialogo **Riduzione rumore** .

2. Per abilitare la riduzione, attenersi alla procedura seguente:

    1. Selezionare **Abilita riduzione**. Si tratta dell'impostazione predefinita.

        > [!NOTE]
        > Se è abilitata la riduzione del rumore, nel rapporto verrà visualizzata una barra informazioni. Per altre informazioni, vedere [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).

    2. Configurare l'impostazione del valore usando l'elenco a discesa **Valore** e selezionando l'impostazione applicabile.

    3. Configurare l'impostazione di soglia desiderata digitando un valore percentuale nella casella di testo **Soglia**.

    4. Per abilitare l'avviso di riduzione del rumore nel rapporto generato, selezionare **Visualizza un avviso nel rapporto generato quando è abilitata Riduzione rumore**. Si tratta dell'impostazione predefinita.

3. Per disabilitare la riduzione, deselezionare **Abilita riduzione**.

4. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche
- [Personalizzare le visualizzazioni dei report degli strumenti per le prestazioni](../profiling/customizing-performance-tools-report-views.md)
- [Procedura: Escludere o includere funzioni brevi nella strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md)
- [Visualizzazione allocazioni](../profiling/dotnet-memory-allocations-view.md)
