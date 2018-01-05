---
title: Riferimento del set di regole di analisi di codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f396bb289e7e4288dbb80c6e08990960861e970c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-rule-set-reference"></a>Tabella di riferimento del set di regole di analisi del codice
Quando si configura l'analisi del codice gestito in progetti di codice [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]viene visualizzata con un elenco di incorporato *set di regole*. È possibile utilizzare uno dei set di regole standard oppure è possibile personalizzare una set di regole per soddisfare i requisiti del progetto.  
  
## <a name="available-rule-sets"></a>Set di regole disponibili  
 Nella tabella seguente sono elencati i set di regole predefiniti:  
  
|||  
|-|-|  
|[Set di regole Tutte le regole](../code-quality/all-rules-rule-set.md)|Il set di regole contiene tutte le regole. Esegue il set di regole potrebbe un numero elevato di avvisi da segnalare. Usare questo set di regole per ottenere un quadro completo di tutti i problemi nel codice. Ciò consente di decidere quale di regole specifico set sono più appropriato per i progetti.|  
|[Set di regole base di correttezza per codice gestito](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Queste regole sono orientate errori di logica e gli errori più comuni di utilizzo delle API del framework. Includere questo set di regole per espandere l'elenco degli avvisi segnalati dalle regole minime consigliate.|  
|[Set di regole Regole base delle linee guida di progettazione per codice gestito](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Queste regole sono orientate all'applicazione delle procedure consigliate per rendere più facile comprendere e usare il codice. Includere questo set di regole se il progetto contiene codice di libreria o se si desidera applicare le procedure consigliate per il codice di facile manutenzione.|  
|[Set di regole estese di correttezza per codice gestito](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Queste regole espandono le regole di base di correttezza per aumentare il logica e i framework utilizzo sono segnalati errori. Attenzione è rivolta a scenari specifici, ad esempio applicazioni per dispositivi mobili e interoperabilità COM. È consigliabile includere questo set di regole se uno di questi scenari si applica al progetto o per individuare ulteriori problemi nel progetto.|  
|[Set di regole Regole estese delle linee guida di progettazione per codice gestito](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Queste regole espandono le regole di progettazione di base delle linee guida per ottimizzare i problemi di usabilità e manutenibilità segnalati. Aggiuntivo attenzione è rivolta alle convenzioni di denominazione. È consigliabile includere questo set di regole se il progetto contiene codice di libreria o se si desidera applicare gli standard ottimali per la scrittura di codice di facile manutenibilità.|  
|[Set di regole delle Regole di globalizzazione per codice gestito](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Queste regole sono orientate alla segnalazione dei problemi dei dati nell'applicazione vengano visualizzate correttamente quando utilizzato in lingue diverse impostazioni cultura e le impostazioni locali. Includere questo set di regole se l'applicazione è localizzata o globalizzata.|  
|[Gestito minimo set di regole per il codice gestito](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Queste regole sono orientate ai problemi più critici del codice per il quale è il più accurato l'analisi del codice.  Queste regole sono un numero limitate e destinati solo per l'esecuzione nelle edizioni di Visual Studio limitate.  Utilizzare Minimumrecommendedrules con altre edizioni di Visual Studio.|  
|[Set di regole consigliate gestite per codice gestito](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Queste regole sono orientate ai problemi più critici del codice, inclusi i potenziali problemi di sicurezza, arresti anomali delle applicazioni e altri errori di logica e di progettazione rilevanti. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti.|  
|[Set di regole minime miste](../code-quality/mixed-minimum-rules-rule-set.md)|Queste regole sono orientate ai problemi più critici dei progetti C++ che supportano Common Language Runtime, inclusi potenziali problemi di sicurezza e arresti anomali delle applicazioni. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti C++ che supportano Common Language Runtime.|  
|[Set di regole consigliate miste](../code-quality/mixed-recommended-rules-rule-set.md)|Queste regole sono orientate ai problemi più critici e comuni nei progetti C++ che supportano Common Language Runtime, inclusi potenziali problemi di sicurezza, arresti anomali delle applicazioni e altri errori di logica e di progettazione rilevanti. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti C++ che supportano Common Language Runtime.  Questo set di regole è progettato per essere configurato con l'edizione di Visual Studio Professional e versioni successive.|  
|[Set di regole minime native](../code-quality/native-minimum-rules-rule-set.md)|Queste regole sono orientate ai problemi più critici del codice nativo, inclusi potenziali problemi di sicurezza e arresti anomali delle applicazioni. È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.|  
|[Set di regole consigliate native](../code-quality/native-recommended-rules-rule-set.md)|Queste regole sono orientate ai problemi più critici e comuni nel codice nativo, inclusi potenziali problemi di sicurezza e arresti anomali delle applicazioni.  È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.  Questo set di regole è progettato per funzionare con l'edizione di Visual Studio Professional e versioni successive.|  
|[Set di regole di sicurezza per codice gestito](../code-quality/security-rules-rule-set-for-managed-code.md)|Il set di regole contiene tutte le regole di sicurezza di Microsoft. Includere questo set di regole per aumentare del numero di potenziali problemi di sicurezza che vengono segnalati.|
