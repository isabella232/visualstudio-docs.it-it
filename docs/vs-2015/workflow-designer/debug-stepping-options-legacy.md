---
title: Esecuzione di istruzioni opzioni di debug (Legacy) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b7dfaa4fb659418c26d5aa0144fac4188ef4b16b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899383"
---
# <a name="debug-stepping-options-legacy"></a>Opzioni di avanzamento nell’esecuzione del debug (legacy)
In questo argomento viene descritto come eseguire il debug di applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che dispongono di attività simultanee in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Quando si esegue il debug legacy attività ad esecuzione contemporanea, ad esempio **ParallelActivity** oppure **ConditionedActivityGroup**, è possibile usare una delle due opzioni seguenti per esaminare il codice .  
  
- **Avanzamento nel ramo.** Questa modalità di procedere consente di procedere ed eseguire il debug di un particolare ramo di un'attività composta, ad esempio la **ParallelActivity** o nella **ConditionalActivityGroup** attività. Quando si usa quest'opzione di debug, non si noterà una modifica nel controllo dovuta all'esecuzione contemporanea di altre attività all'interno del flusso di lavoro. Il debugger avanza solo attraverso le attività del ramo attualmente selezionato mentre le altre attività del flusso di lavoro possono essere eseguite contemporaneamente. Ad esempio, per impostazione predefinita, il ramo all'estrema sinistra in un' **ParallelActivity** attività e la prima attività figlio di un **ConditionedActivityGroup** attività vengono usati per l'esecuzione di istruzioni. Se l’utente desidera eseguire il debug di qualsiasi altro ramo o attività figlia, un punto di interruzione esplicito deve essere posizionato su quel ramo o su quella attività figlia. Quando il punto di interruzione viene generato, l'avanzamento continua in quel ramo.  
  
- **Avanzamento nell'istanza.** Questa modalità di procedere consente di procedere ed eseguire il debug eseguendo contemporaneamente le attività del flusso di lavoro. Con questa opzione, si noterà che si verifica una modifica nel controllo durante l'esecuzione contemporanea di attività eseguite all'interno del flusso di lavoro.  
  
  Per impostazione predefinita, l'opzione di avanzamento nel ramo è selezionata e gli utenti possono passare tra le due opzioni durante l'esecuzione del debug di un flusso di lavoro legacy.  
  
  È necessario selezionare l'opzione di avanzamento dell’istanza in caso di esecuzione di debug di flussi di lavoro di macchine a stati legacy.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei flussi di lavoro Legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Procedura: Modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)