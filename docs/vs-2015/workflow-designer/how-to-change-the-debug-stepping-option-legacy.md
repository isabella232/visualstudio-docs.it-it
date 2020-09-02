---
title: "Procedura: modificare l'opzione di esecuzione del debug (legacy) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663443"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procedura: modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)
In questo argomento viene descritto come modificare l'opzione di avanzamento nell'esecuzione del debug per le applicazioni [!INCLUDE[wf](../includes/wf-md.md)] in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy aventi azioni simultanee. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Quando si esegue il debug di attività legacy con esecuzione simultanea, ad esempio **ParallelActivity** o **ConditionedActivityGroup**, è possibile usare una delle due opzioni per eseguire il codice un'istruzione alla volta.

 Seguire questi passaggi per modificare l'opzione di avanzamento nell’esecuzione del debug nel progetto del flusso di lavoro legacy.

## <a name="procedures"></a>Procedure

#### <a name="to-change-the-debug-stepping-option"></a>Per modificare l'opzione di avanzamento nell'esecuzione del debug

1. Avviare Visual Studio.

2. Aprire un progetto flusso di lavoro legacy esistente o creare un nuovo progetto che usa attività simultanee e che viene destinato a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

3. Nel menu **flusso di lavoro** del legacy [!INCLUDE[wfd2](../includes/wfd2-md.md)] , scegliere **debug**, quindi scegliere **Opzioni di esecuzione**.

4. Selezionare **istanza** o **ramo**.

## <a name="see-also"></a>Vedere anche
 Debug delle opzioni di esecuzione del debug di [flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md) [(legacy)](../workflow-designer/debug-stepping-options-legacy.md)