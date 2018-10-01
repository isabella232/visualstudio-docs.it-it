---
title: "Procedura: modificare l'opzione l'esecuzione di istruzioni di Debug (Legacy) | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1fbe4ef5feeff7201a5c8772c1e754402db9ffd5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528142"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procedura: modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)
In questo argomento viene descritto come modificare l'opzione di avanzamento nell'esecuzione del debug per le applicazioni [!INCLUDE[wf](../includes/wf-md.md)] in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy aventi azioni simultanee. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Quando si esegue il debug legacy attività ad esecuzione contemporanea, ad esempio **ParallelActivity** oppure **ConditionedActivityGroup**, è possibile usare una delle due opzioni per esaminare il codice.  
  
 Seguire questi passaggi per modificare l'opzione di avanzamento nell’esecuzione del debug nel progetto del flusso di lavoro legacy.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-change-the-debug-stepping-option"></a>Per modificare l'opzione di avanzamento nell'esecuzione del debug  
  
1.  Avviare Visual Studio.  
  
2.  Aprire un progetto flusso di lavoro legacy esistente o creare un nuovo progetto che usa attività simultanee e che viene destinato a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
3.  Nel **flusso di lavoro** dal menu legacy [!INCLUDE[wfd2](../includes/wfd2-md.md)], scegliere **Debug**e quindi scegliere **opzioni di avanzamento**.  
  
4.  Selezionare uno **istanza** oppure **ramo**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei flussi di lavoro Legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Opzioni di avanzamento nell’esecuzione del debug (legacy)](../workflow-designer/debug-stepping-options-legacy.md)