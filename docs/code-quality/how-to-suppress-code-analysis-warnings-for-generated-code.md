---
title: Non visualizzare le violazioni di analisi del codice per il codice generato
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a7990f5e9fa1893d8813b1307ab6a0a7fee46be
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613561"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: Non visualizzare gli avvisi relativi all'analisi del codice generato

Codice generato include il codice che viene aggiunto al progetto da codice gestito compilatori o dagli strumenti di terze parti. Si potrebbe voler visualizzare le violazioni delle regole di analisi del codice consente di individuare il codice generato. Tuttavia, poiché non è possibile visualizzare e gestire il codice che contiene le violazioni, si potrebbe non desidera visualizzarli.

Il **non visualizzare i risultati dal codice generato** casella di controllo nella pagina delle proprietà di analisi codice di un progetto consente di scegliere se visualizzare gli avvisi di analisi del codice generato da uno strumento di terze parti di codice.

> [!NOTE]
> Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Per non visualizzare avvisi per il codice generato in un progetto

1. Fare clic sul progetto in **Esplora soluzioni** e quindi fare clic su **proprietà**.

2. Scegliere il **analisi del codice** scheda.

3. Selezionare il **non visualizzare i risultati dal codice generato** casella di controllo.

> [!NOTE]
> È possibile eliminare solo gli avvisi generati dall'analisi statica del codice. Attualmente, non è possibile sopprimere gli avvisi dell'analisi codice dal [analizzatori](roslyn-analyzers-overview.md).