---
title: "Finestra di progettazione del flusso di lavoro - procedura: modificare l'opzione di esecuzione di istruzioni Debug (Legacy)"
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971983"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procedura: modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)

In questo argomento viene descritto come modificare l'opzione per le applicazioni di Windows Workflow Foundation (WF) in Progettazione flussi di lavoro Windows legacy aventi azioni simultanee l'esecuzione di istruzioni di debug. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando è necessario avere come destinazione .NET Framework versione 3.5 o la WinFX.

Quando si esegue il debug di attività legacy esecuzione simultanea, ad esempio **ParallelActivity** o **ConditionedActivityGroup**, è possibile utilizzare una delle due opzioni per esaminare il codice.

Seguire questi passaggi per modificare l'opzione di avanzamento nell’esecuzione del debug nel progetto del flusso di lavoro legacy.

## <a name="procedures"></a>Procedure

### <a name="to-change-the-debug-stepping-option"></a>Per modificare l'opzione di avanzamento nell'esecuzione del debug

1.  Avviare Visual Studio.

2.  Aprire un progetto flusso di lavoro legacy esistente o creare un nuovo progetto che Usa attività simultanee e che fa riferimento a .NET Framework versione 3.5 o la WinFX.

3.  Nel **flusso di lavoro** menu nella finestra di progettazione legacy del flusso di lavoro, scegliere **Debug**e quindi scegliere **opzioni di esecuzione di istruzioni**.

4.  Selezionare l'opzione **istanza** o **ramo**.

## <a name="see-also"></a>Vedere anche

- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)
- [Opzioni di avanzamento nell’esecuzione del debug (legacy)](../workflow-designer/debug-stepping-options-legacy.md)