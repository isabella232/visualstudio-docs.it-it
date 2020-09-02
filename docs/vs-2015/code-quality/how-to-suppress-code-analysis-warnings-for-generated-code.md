---
title: 'Procedura: non visualizzare gli avvisi di analisi codice per il codice generato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646268"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: non visualizzare gli avvisi relativi all'analisi del codice generato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I compilatori di codice gestito spesso generano codice aggiunto a un progetto per semplificare lo sviluppo rapido di codice. Inoltre, gli sviluppatori spesso utilizzano strumenti di terze parti per facilitare lo sviluppo rapido delle applicazioni. Questi strumenti generano anche codice aggiunto al progetto.

 È possibile che si desideri visualizzare le violazioni della regola individuate dall'analisi del codice nel codice generato. Tuttavia, è possibile che non si desideri visualizzarli se non è possibile visualizzare e gestire il codice che contiene la violazione.

 La casella di controllo non **visualizzare i risultati del codice generato** nella pagina delle proprietà analisi codice di un progetto consente di scegliere se visualizzare gli avvisi di analisi codice dal codice generato da uno strumento di terze parti.

> [!NOTE]
> Questa opzione non consente di escludere gli errori e gli avvisi di analisi codice dal codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Per non visualizzare gli avvisi per il codice generato in un progetto

1. Fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, quindi scegliere **Proprietà**.

2. Fare clic su **Analisi codice**.

3. Selezionare la casella di controllo non **visualizzare i risultati del codice generato** .
