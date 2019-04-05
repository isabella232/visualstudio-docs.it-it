---
title: "Procedura: Imporre codice di facile manutenibilità con criteri di controllo dell'analisi codice | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5676bfaabb20ebf6dabea7bae66527d17891b362
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954383"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: Applicare codice di facile manutenibilità con i criteri di archiviazione per l'analisi codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli sviluppatori possono usare lo strumento di metrica codice per misurare la complessità e della manutenibilità del codice, ma non possono richiamare la metrica del codice come parte di un criterio di controllo. Tuttavia, un team può abilitare le regole di analisi del codice che verificano la conformità del codice con gli standard della metrica del codice e applicano le regole tramite i criteri di archiviazione. Per altre informazioni sulla metrica del codice, vedere la [valori della metrica del codice](../code-quality/code-metrics-values.md).  
  
 Gli sviluppatori possono abilitare la profondità dell'ereditarietà, accoppiamento di classe, indice di manutenibilità e le regole di complessità applicare il codice gestibile tramite criteri di archiviazione dell'analisi del codice. Tutti e quattro queste regole si trovano sotto la categoria "Regole di manutenibilità" nell'editor dei criteri analisi codice.  
  
 Gli amministratori della versione di controllo per [!INCLUDE[esprfound](../includes/esprfound-md.md)] possono aggiungere le regole di manutenibilità di analisi codice per i requisiti dei criteri di archiviazione. Questi check-in criteri richiedono agli sviluppatori di eseguire l'analisi del codice basato su queste modifiche alle regole prima dell'avvio di un'archiviazione.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'Editor criteri di analisi codice  
  
1.  Nelle **Team Explorer**, fare clic sul progetto team, fare clic su **le impostazioni del progetto Team**, quindi fare clic su **controllo del codice sorgente**.  
  
     Il **controllo del codice sorgente** verrà visualizzata la finestra di dialogo.  
  
2.  Nel **dei criteri di archiviazione** scheda e fare clic su **Add**.  
  
     Il **aggiungere i criteri di archiviazione** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **dei criteri di archiviazione** elenco, selezionare la **analisi del codice** casella di controllo e quindi fare clic su **OK**.  
  
     Il **Editor dei criteri analisi codice** verrà visualizzata la finestra di dialogo.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di manutenibilità analisi codice  
  
1.  Nel **Editor criteri di analisi di codice** nella finestra di dialogo **le impostazioni delle regole**, espandere il **regole di manutenibilità** nodo.  
  
2.  Selezionare le caselle di controllo per le regole seguenti:  
  
    -   Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** -soglia: Più di 5 livelli di avviso  
  
    -   Complessità: **CA1502 AvoidExcessiveComplexity** -soglia: Avviso in più di 25  
  
    -   Indice di manutenibilità: **CA1505 AvoidUnmaintainableCode** -soglia: Avviso per meno di 20  
  
    -   Accoppiamento di classe: **CA1506 AvoidExcessiveClassCoupling** -soglia: Avviso più di 80 per una classe e più di 30 per un metodo  
  
    -   Inoltre, se si desidera che una violazione delle regole per impedire una compilazione, selezionare la **trattare avvisi come errori** casella di controllo accanto alla descrizione della regola.  
  
3.  Fare clic su **OK**. Il nuovo criterio si applica ora a archiviazioni future.  
  
## <a name="see-also"></a>Vedere anche  
 [Valori della metrica del codice](../code-quality/code-metrics-values.md)   
 [Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
