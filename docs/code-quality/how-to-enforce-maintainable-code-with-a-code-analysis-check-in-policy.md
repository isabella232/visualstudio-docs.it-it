---
title: "Procedura: applicare codice di facile manutenibilità con criteri di controllo dell'analisi codice | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 19d8761abea6934c59673c332ea09e8a0b4e6997
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedura: Applicare codice di facile manutenibilità con criteri di archiviazione dell'analisi del codice
Gli sviluppatori possono utilizzare lo strumento di metrica del codice per misurare la complessità e della manutenibilità del codice, ma non possono richiamare la metrica del codice come parte di un criterio di controllo. Tuttavia, un team è possibile abilitare le regole di analisi del codice che verifica la conformità del codice standard di metrica del codice e applicano le regole tramite criteri di archiviazione. Per ulteriori informazioni sulla metrica del codice, vedere il [valori della metrica del codice](../code-quality/code-metrics-values.md).  
  
 Gli sviluppatori possono abilitare la profondità dell'ereditarietà, accoppiamenti, indice di manutenibilità e le regole di complessità applicare il codice gestibile tramite criteri di archiviazione dell'analisi del codice. Le quattro di queste regole sono disponibili nella categoria "Regole di manutenibilità" nell'editor Criteri di analisi del codice.  
  
 Gli amministratori della versione di controllo per [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] possibile aggiungere le regole di manutenibilità di analisi codice per i requisiti dei criteri di archiviazione. Questi check-in criteri richiedono agli sviluppatori di eseguire l'analisi del codice in base a queste regole modificate prima dell'avvio di un controllo aggiuntivo.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Per aprire l'Editor criteri di analisi codice  
  
1.  In **Team Explorer**, fare clic sul progetto team, fare clic su **impostazioni progetto Team**, quindi fare clic su **controllo del codice sorgente**.  
  
     Il **controllo del codice sorgente** viene visualizzata la finestra di dialogo.  
  
2.  Nel **criteri di archiviazione** scheda e fare clic su **Aggiungi**.  
  
     Il **aggiungere criteri di archiviazione** viene visualizzata la finestra di dialogo.  
  
3.  Nel **criteri di archiviazione** elenco, selezionare il **analisi del codice** casella di controllo e quindi fare clic su **OK**.  
  
     Il **Editor criteri di analisi codice** viene visualizzata la finestra di dialogo.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Per abilitare le regole di manutenibilità analisi codice  
  
1.  Nel **Editor criteri di analisi codice** nella finestra di dialogo **le impostazioni delle regole**, espandere il **regole di gestibilità** nodo.  
  
2.  Selezionare le caselle di controllo per le regole seguenti:  
  
    -   Profondità dell'ereditarietà: **CA1501 AvoidExcessiveInheritance** -soglia: più di 5 livelli di avviso  
  
    -   Complessità: **CA1502 AvoidExcessiveComplexity** -soglia: avviso in più di 25.  
  
    -   Indice di manutenibilità: **CA1505 AvoidUnmaintainableCode** -soglia: avviso in meno di 20  
  
    -   Accoppiamenti di classi: **CA1506 AvoidExcessiveClassCoupling** -soglia: avviso più di 80 per una classe e più di 30 per un metodo  
  
    -   Inoltre, se si desidera una violazione delle regole per evitare una compilazione, selezionare il **considera gli avvisi come errori** casella di controllo accanto alla descrizione della regola.  
  
3.  Fare clic su **OK**. Il nuovo criterio si applica ora a future archiviazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Valori della metrica del codice](../code-quality/code-metrics-values.md)   
 [Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)