---
title: Riferimento di set di regole di analisi di codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a1f91b352da5a41ec2ef81fb6067976073c787ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576754"
---
# <a name="code-analysis-rule-set-reference"></a>Tabella di riferimento del set di regole di analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si configurano analisi codice per progetti di codice in gestito [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], o [!INCLUDE[vsPro](../includes/vspro-md.md)]viene visualizzato un elenco incorporati *set di regole*. È possibile utilizzare uno dei set di regole standard o personalizzare un set di regole per soddisfare i requisiti del progetto.  
  
## <a name="available-rule-sets"></a>Set di regole disponibili  
 Nella tabella seguente sono elencati i set di regole predefiniti:  
  
|||  
|-|-|  
|[Set di regole Tutte le regole](../code-quality/all-rules-rule-set.md)|Questo set di regole contiene tutte le regole. Esecuzione di questo set di regole può comportare un numero elevato di avvisi da segnalare. Usare questo set di regole per ottenere un quadro completo di tutti i problemi nel codice. Ciò consente di decidere quale la regola più mirata set sono più appropriato da eseguire per i progetti.|  
|[Set di regole base di correttezza per codice gestito](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Queste regole sono orientate in presenza di errori logici ed errori comuni di utilizzo dell'API del framework. Includere questo set di regole per espandere l'elenco degli avvisi segnalati dalle regole minime consigliate.|  
|[Set di regole Regole base delle linee guida di progettazione per codice gestito](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Queste regole sono orientate alla applicando le procedure consigliate per rendere il codice facile da comprendere e usare. Includere questo set di regole se il progetto contiene codice di libreria o se si desidera applicare le procedure consigliate per codice di facile.|  
|[Set di regole estese di correttezza per codice gestito](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Queste regole espandono le regole di base di correttezza per ottimizzare gli errori di utilizzo per la logica e framework che vengono segnalati. Viene posta particolare attenzione su scenari specifici, ad esempio applicazioni per dispositivi mobili e interoperabilità COM. È consigliabile includere questo set di regole se uno di questi scenari si applica al progetto o per individuare ulteriori problemi nel progetto.|  
|[Set di regole Regole estese delle linee guida di progettazione per codice gestito](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Queste regole espandono le regole di progettazione di base delle linee guida per ottimizzare i problemi di usabilità e facilità di gestione che vengono segnalati. Extra attenzione è rivolta alle linee guida sulla denominazione. È consigliabile includere questo set di regole se il progetto contiene codice di libreria o se si desidera applicare gli standard ottimali per la scrittura di codice facile da gestire.|  
|[Set di regole delle Regole di globalizzazione per codice gestito](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Queste regole orientate ai problemi che impediscono di dati nell'applicazione vengano visualizzate correttamente quando utilizzata in, le impostazioni locali, lingue e culture diverse. Includere questo set di regole se l'applicazione è localizzata o globalizzata.|  
|[Set di regole minime gestite per codice gestito](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Queste regole orientate ai problemi più critici del codice per il quale è il più accurato l'analisi del codice.  Queste regole sono in numero limitate e sono progettati per l'esecuzione nelle edizioni di Visual Studio limitate.  Utilizzare Minimumrecommendedrules con altre edizioni di Visual Studio.|  
|[Set di regole consigliate gestite per codice gestito](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Queste regole sono orientate ai problemi più critici del codice, incluse potenziali lacune nella protezione, arresti anomali delle applicazioni e altri errori importanti per la logica e progettazione. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti.|  
|[Set di regole minime miste](../code-quality/mixed-minimum-rules-rule-set.md)|Queste regole orientate ai problemi più critici nei progetti C++ che supportano Common Language Runtime, incluse potenziali lacune nella protezione e arresti anomali delle applicazioni. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti C++ che supportano Common Language Runtime.|  
|[Set di regole consigliate miste](../code-quality/mixed-recommended-rules-rule-set.md)|Queste regole orientate ai problemi più critici e comuni nei progetti C++ che supportano Common Language Runtime, incluse potenziali lacune nella protezione, arresti anomali delle applicazioni e altri errori importanti per la logica e progettazione. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti C++ che supportano Common Language Runtime.  Questo set di regole è progettato per essere configurato con l'edizione di Visual Studio Professional e versioni successive.|  
|[Set di regole minime native](../code-quality/native-minimum-rules-rule-set.md)|Queste regole orientate ai problemi più critici del codice nativo, incluse potenziali lacune nella protezione e arresti anomali delle applicazioni. È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.|  
|[Set di regole consigliate native](../code-quality/native-recommended-rules-rule-set.md)|Queste regole orientate ai problemi più critici e comuni nel codice nativo, incluse potenziali lacune nella protezione e arresti anomali delle applicazioni.  È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.  Questo set di regole è progettato per funzionare con l'edizione di Visual Studio Professional e versioni successive.|  
|[Set di regole di sicurezza per codice gestito](../code-quality/security-rules-rule-set-for-managed-code.md)|Questo set di regole contiene tutte le regole di sicurezza di Microsoft. Includere questo set di regole per ottimizzare il numero di potenziali problemi di sicurezza che vengono segnalati.|
