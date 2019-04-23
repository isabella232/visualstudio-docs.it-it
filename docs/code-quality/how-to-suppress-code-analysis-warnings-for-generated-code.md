---
title: "Procedura: Non visualizzare gli avvisi relativi all'analisi del codice generato"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2d58ea5d23ed8b302b6ec2a0352f23b0eeeff66
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066520"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: Non visualizzare gli avvisi relativi all'analisi del codice generato
I compilatori di codice gestito è spesso generano codice che viene aggiunto a un progetto per facilitare lo sviluppo rapido di codice. Inoltre, gli sviluppatori usano spesso gli strumenti di terze parti per consentono di sviluppare rapidamente applicazioni. Questi strumenti generano anche codice che viene aggiunto al progetto.

 Si potrebbe voler visualizzare le violazioni delle regole di analisi del codice consente di individuare il codice generato. Tuttavia, si potrebbe non si desidera visualizzarli se non è possibile visualizzare e gestire il codice che contiene la violazione.

 Il **non visualizzare i risultati dal codice generato** casella di controllo nella pagina delle proprietà di analisi del codice di un progetto consente di specificare se si vuole visualizzare gli avvisi di analisi del codice del codice generato da uno strumento di terze parti.

> [!NOTE]
>  Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e avvisi vengono visualizzati nei form e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Per non visualizzare avvisi per il codice generato in un progetto

1. Fare clic sul progetto in Esplora soluzioni e quindi fare clic su **proprietà**.

2. Fare clic su **analisi del codice**.

3. Selezionare il **non visualizzare i risultati dal codice generato** casella di controllo.