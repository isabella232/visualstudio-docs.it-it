---
title: 'Procedura: Creare un elemento di lavoro per un errore del codice gestito'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: fcbb7716d8ba0496d267f3c8757bb8425884cfb0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Procedura: Creare un elemento di lavoro per un errore del codice gestito

È possibile utilizzare la funzionalità di rilevamento di elementi di lavoro per registrare un elemento di lavoro all'interno di Visual Studio. Per utilizzare questa funzionalità, il progetto deve far parte del progetto Team in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Per creare un elemento di lavoro per un errore del codice gestito

1. Nel **analisi del codice** finestra, selezionare l'avviso.

2. Scegliere **azioni**, quindi scegliere **Crea elemento di lavoro** e scegliere il tipo di elemento di lavoro da creare.

     È possibile specificare le informazioni di errore, viene creato un nuovo elemento di lavoro.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Per creare un elemento di lavoro per più difetti del codice gestito

1. Nel **elenco errori**, selezionare più avvisi e quindi fare doppio clic sugli avvisi.

2. Scegliere **Crea elemento di lavoro** e fare clic sul tipo di elemento di lavoro da creare.

     Per tutti gli avvisi selezionati è possibile specificare le informazioni sull'errore, viene creato un singolo elemento di lavoro.