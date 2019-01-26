---
title: 'Procedura: Creare un elemento di lavoro per un difetto del codice gestito'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1cb63612194148b5f3ea1f90d7c57e59fb84edbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941827"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Procedura: Creare un elemento di lavoro per un difetto del codice gestito

È possibile usare la funzionalità di rilevamento elemento di lavoro all'elemento di lavoro di log dall'interno di Visual Studio. Per usare questa funzionalità, il progetto deve far parte di un progetto Azure DevOps in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Per creare un elemento di lavoro per difetto del codice gestito

1. Nel **analisi del codice** finestra, selezionare l'avviso.

2. Scegli **azioni**, quindi scegliere **Crea elemento di lavoro** e scegliere il tipo di elemento di lavoro da creare.

     È possibile specificare le informazioni di difetto viene creato un nuovo elemento di lavoro.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Per creare un elemento di lavoro per più difetti del codice gestito

1. Nel **elenco errori**, selezionare più avvisi e quindi fare doppio clic su avvisi.

2. Puntare **Crea elemento di lavoro** e fare clic sul tipo di elemento di lavoro da creare.

     Viene creato un singolo elemento di lavoro per tutti gli avvisi selezionati è possibile specificare le informazioni sull'errore.