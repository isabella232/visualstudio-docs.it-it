---
title: "Procedura: non visualizzare gli avvisi relativi all'analisi del codice generato"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac2c5d4a7aca3f77feabc0aaba75d7f56a751821
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919454"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: non visualizzare gli avvisi relativi all'analisi del codice generato
I compilatori di codice gestito spesso generano codice che viene aggiunto a un progetto per facilitare lo sviluppo rapido di codice. Inoltre, gli sviluppatori spesso utilizzano gli strumenti di terze parti per sviluppare rapidamente applicazioni. Questi strumenti generano anche il codice che viene aggiunto al progetto.

 Si potrebbe voler visualizzare le violazioni delle regole individuate dall'analisi nel codice generato. Tuttavia, si potrebbe non si desidera visualizzarli se non è possibile visualizzare e gestire il codice che contiene la violazione.

 Il **Elimina i risultati dal codice generato** casella di controllo nella pagina delle proprietà di un progetto di analisi del codice consente di selezionare se si desidera visualizzare gli avvisi di analisi del codice dal codice generato da uno strumento di terze parti.

> [!NOTE]
>  Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e avvisi vengono visualizzati nel form e i modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Esclusione di avvisi per il codice generato in un progetto

1.  Fare clic sul progetto in Esplora soluzioni e quindi fare clic su **proprietà**.

2.  Fare clic su **l'analisi del codice**.

3.  Selezionare il **Elimina i risultati dal codice generato** casella di controllo.