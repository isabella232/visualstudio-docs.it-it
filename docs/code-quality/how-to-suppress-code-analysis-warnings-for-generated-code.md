---
title: Non visualizzare le violazioni dell'analisi codice per il codice generato
ms.date: 05/13/2019
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 175df8bb4dded4f66508ef405e031178606fd531
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371807"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: non visualizzare gli avvisi di analisi codice per il codice generato

Il codice generato include codice aggiunto al progetto da compilatori di codice gestito o strumenti di terze parti. È possibile che si desideri visualizzare le violazioni della regola individuate dall'analisi del codice nel codice generato. Tuttavia, poiché non è possibile visualizzare e gestire il codice che contiene le violazioni, è possibile che non si desideri visualizzarle.

La casella di controllo non **visualizzare i risultati del codice generato** nella pagina delle proprietà analisi codice di un progetto consente di scegliere se visualizzare gli avvisi di analisi codice dal codice generato da uno strumento di terze parti.

> [!NOTE]
> Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Per non visualizzare gli avvisi per il codice generato in un progetto

1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** , quindi scegliere **Proprietà**.

2. Scegliere la scheda **analisi codice** .

3. Selezionare la casella di controllo non **visualizzare i risultati del codice generato** .

> [!IMPORTANT]
> È possibile escludere solo gli avvisi dall'analisi legacy. La pagina delle proprietà con l'impostazione è stata deprecata e verrà rimossa in una versione futura del prodotto. Attualmente, non è possibile escludere gli avvisi di analisi del codice dagli [analizzatori](roslyn-analyzers-overview.md).
