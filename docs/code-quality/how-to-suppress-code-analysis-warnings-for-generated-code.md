---
title: Eliminare Code Analysis violazioni per il codice generato
ms.date: 05/13/2019
description: Informazioni su come eliminare gli avvisi di analisi del codice per il codice generato. Informazioni su come impedire Visual Studio di visualizzare avvisi di analisi legacy sul codice generato.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 214c7ca6bd7dcf648060383462fa2dfef24a3618
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631926"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: Eliminare gli avvisi di analisi del codice per il codice generato

Il codice generato include il codice aggiunto al progetto da compilatori di codice gestito o strumenti di terze parti. È possibile visualizzare le violazioni delle regole individuate dall'analisi del codice nel codice generato. Tuttavia, poiché non è possibile visualizzare e gestire il codice che contiene le violazioni, potrebbe non essere necessario visualizzarle.

La **casella di controllo** Elimina risultati dal codice generato nella pagina delle proprietà Analisi codice di un progetto consente di scegliere se visualizzare gli avvisi di analisi del codice dal codice generato da uno strumento di terze parti.

> [!NOTE]
> Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Per eliminare gli avvisi per il codice generato in un progetto

1. Fare clic con il pulsante destro del mouse **sul Esplora soluzioni** e quindi scegliere **Proprietà**.

2. Scegliere la **Code Analysis** impostazioni.

3. Selezionare la **casella di controllo Elimina risultati dal** codice generato.

> [!IMPORTANT]
> È possibile eliminare solo gli avvisi dall'analisi legacy. La pagina delle proprietà con l'impostazione è stata deprecata e verrà rimossa in una versione futura del prodotto. Attualmente non è possibile eliminare gli avvisi di analisi del codice [dagli analizzatori](roslyn-analyzers-overview.md).
