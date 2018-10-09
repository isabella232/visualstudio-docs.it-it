---
title: 'Procedura: Configurare la riduzione del rumore nelle visualizzazioni dei rapporti | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee848f506a81b156309fa7e0d86891418251d0e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541048"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Procedura: Configurare la riduzione del rumore nelle visualizzazioni report
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: configurare la riduzione del rumore nelle visualizzazioni Report](https://docs.microsoft.com/visualstudio/profiling/how-to-configure-noise-reduction-in-report-views).  
  
I rapporti di prestazioni possono essere configurati per la riduzione del rumore limitando la quantità di dati presentati nelle visualizzazioni Albero delle chiamate e Allocazioni. Con la riduzione del rumore, i problemi di prestazioni sono più evidenti. In questo modo è più semplice analizzare i rapporti di prestazioni.  
  
 Le opzioni di configurazione della riduzione del rumore includono le impostazioni seguenti:  
  
-   **Trimming**: quando un rapporto viene analizzato, la visualizzazione ometterà le funzioni che rientrano all'interno delle impostazioni di valore e soglia che sono state configurate, come descritto nella procedura di trimming riportata di seguito. Il trimming è abilitato per impostazione predefinita.  
  
-   **Riduzione**: se si abilita la riduzione, le funzioni consecutive su un percorso che soddisfano le impostazioni configurate verranno unite, come descritto nella procedura di riduzione riportata di seguito. La riduzione è abilitata per impostazione predefinita.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Per configurare il trimming per un rapporto di prestazioni  
  
1.  Quando viene visualizzata una visualizzazione Albero delle chiamate o Allocazioni nel rapporto generato, dal menu **Sviluppatore** scegliere **Profiler** e quindi fare clic su **Opzioni riduzione rumore**.  
  
     Verrà visualizzata la finestra di dialogo **Riduzione rumore** .  
  
2.  Per abilitare il trimming, attenersi alla procedura seguente:  
  
    1.  Selezionare **Abilita trimming**. Questa è l'impostazione predefinita.  
  
        > [!NOTE]
        >  Se è abilitata la riduzione del rumore, nel rapporto verrà visualizzata una barra informazioni. Per altre informazioni, vedere [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configurare l'impostazione del valore usando l'elenco a discesa **Valore** e scegliendo l'impostazione applicabile.  
  
    3.  Configurare l'impostazione di soglia desiderata digitando un valore percentuale nella casella di testo **Soglia**.  
  
    4.  Per abilitare l'avviso di riduzione del rumore nel rapporto generato, selezionare **Visualizza un avviso nel rapporto generato quando è abilitata Riduzione rumore**. Questa è l'impostazione predefinita.  
  
3.  Per disabilitare il trimming, deselezionare **Abilita trimming**.  
  
4.  Fare clic su **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Per configurare la riduzione per un rapporto di prestazioni  
  
1.  Dal menu **Sviluppatore** scegliere **Profiler** e quindi fare clic su **Opzioni riduzione rumore**.  
  
     Verrà visualizzata la finestra di dialogo **Riduzione rumore** .  
  
2.  Per abilitare la riduzione, attenersi alla procedura seguente:  
  
    1.  Selezionare **Abilita riduzione**. Questa è l'impostazione predefinita.  
  
        > [!NOTE]
        >  Se è abilitata la riduzione del rumore, nel rapporto verrà visualizzata una barra informazioni. Per altre informazioni, vedere [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configurare l'impostazione del valore usando l'elenco a discesa **Valore** e selezionando l'impostazione applicabile.  
  
    3.  Configurare l'impostazione di soglia desiderata digitando un valore percentuale nella casella di testo **Soglia**.  
  
    4.  Per abilitare l'avviso di riduzione del rumore nel rapporto generato, selezionare **Visualizza un avviso nel rapporto generato quando è abilitata Riduzione rumore**. Questa è l'impostazione predefinita.  
  
3.  Per disabilitare la riduzione, deselezionare **Abilita riduzione**.  
  
4.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle visualizzazioni dei rapporti degli strumenti per le prestazioni](../profiling/customizing-performance-tools-report-views.md)   
 [Procedura: Escludere o includere funzioni brevi nella strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md)   
 [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md)


