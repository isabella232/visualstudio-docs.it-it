---
title: "Procedura: eliminare gli avvisi dell'analisi codice per il codice generato | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 07858183af427e2b67e1e0f63d1f8889caf72fbe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293748"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedura: non visualizzare gli avvisi relativi all'analisi del codice generato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I compilatori di codice gestito è spesso generano codice che viene aggiunto a un progetto per facilitare lo sviluppo rapido di codice. Inoltre, gli sviluppatori usano spesso gli strumenti di terze parti per consentono di sviluppare rapidamente applicazioni. Questi strumenti generano anche codice che viene aggiunto al progetto.  
  
 Si potrebbe voler visualizzare le violazioni delle regole di analisi del codice consente di individuare il codice generato. Tuttavia, si potrebbe non si desidera visualizzarli se non è possibile visualizzare e gestire il codice che contiene la violazione.  
  
 Il **non visualizzare i risultati dal codice generato** casella di controllo nella pagina delle proprietà di analisi del codice di un progetto consente di specificare se si vuole visualizzare gli avvisi di analisi del codice del codice generato da uno strumento di terze parti.  
  
> [!NOTE]
>  Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e avvisi vengono visualizzati nei form e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Per non visualizzare avvisi per il codice generato in un progetto  
  
1.  Fare clic sul progetto in Esplora soluzioni e quindi fare clic su **proprietà**.  
  
2.  Fare clic su **analisi del codice**.  
  
3.  Selezionare il **non visualizzare i risultati dal codice generato** casella di controllo.



