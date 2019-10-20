---
title: Riferimento al set di regole di analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c0b347f186c5adee6cf86a0e1720ebfa80f253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670107"
---
# <a name="code-analysis-rule-set-reference"></a>Tabella di riferimento del set di regole di analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si configura l'analisi del codice per i progetti di codice gestito in [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] o [!INCLUDE[vsPro](../includes/vspro-md.md)]you viene visualizzato un elenco di *set di regole*predefiniti. È possibile utilizzare uno dei set di regole standard o personalizzare un set di regole per soddisfare i requisiti del progetto.

## <a name="available-rule-sets"></a>Set di regole disponibili
 Nella tabella seguente sono elencati i set di regole predefiniti:

|||
|-|-|
|[Set di regole Tutte le regole](../code-quality/all-rules-rule-set.md)|Questo set di regole contiene tutte le regole. L'esecuzione di questo set di regole può causare la segnalazione di un numero elevato di avvisi. Utilizzare questo set di regole per ottenere una panoramica completa di tutti i problemi del codice. Ciò può essere utile per decidere quale dei set di regole più mirati sono più appropriati per l'esecuzione per i progetti.|
|[Set di regole base di correttezza per codice gestito](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Queste regole sono incentrate sugli errori logici e sugli errori comuni effettuati nell'utilizzo delle API del Framework. Includere questo set di regole per espandersi nell'elenco di avvisi segnalato dalle regole minime consigliate.|
|[Set di regole Regole base delle linee guida di progettazione per codice gestito](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Queste regole sono incentrate sull'applicazione delle procedure consigliate per semplificare la comprensione e l'utilizzo del codice. Includere questo set di regole se il progetto include il codice della libreria o se si desidera applicare procedure consigliate per il codice facilmente gestibile.|
|[Set di regole estese di correttezza per codice gestito](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Queste regole si espandono sulle regole di correttezza di base per ottimizzare la logica e gli errori di utilizzo del framework segnalati. L'enfasi aggiuntiva è posizionata su scenari specifici come l'interoperabilità COM e le applicazioni per dispositivi mobili. Si consiglia di includere questo set di regole se uno di questi scenari si applica al progetto o si riscontrano altri problemi nel progetto.|
|[Set di regole Regole estese delle linee guida di progettazione per codice gestito](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Queste regole si espandono sulle regole delle linee guida di progettazione di base per massimizzare i problemi di usabilità e gestibilità segnalati. Le linee guida per la denominazione hanno un'enfasi aggiuntiva. Si consiglia di includere questo set di regole se il progetto include codice della libreria o se si desidera applicare gli standard più elevati per la scrittura di codice gestibile.|
|[Set di regole delle Regole di globalizzazione per codice gestito](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Queste regole sono incentrate sui problemi che impediscono la visualizzazione corretta dei dati dell'applicazione quando vengono usati in lingue, impostazioni locali e impostazioni cultura diverse. Includere questo set di regole se l'applicazione è localizzata o globalizzata.|
|[Set di regole minime gestite per codice gestito](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Queste regole sono incentrate sui problemi più critici del codice per cui l'analisi del codice è la più accurata.  Queste regole sono di numero ridotto e sono progettate solo per l'esecuzione in versioni di Visual Studio limitate.  Usare MinimumRecommendedRules. RuleSet con altre edizioni di Visual Studio.|
|[Set di regole consigliate gestite per codice gestito](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Queste regole sono incentrate sui problemi più critici del codice, inclusi i potenziali problemi di sicurezza, gli arresti anomali dell'applicazione e altri importanti errori di logica e progettazione. È necessario includere questo set di regole in tutti i set di regole personalizzati creati per i progetti.|
|[Set di regole minime miste](../code-quality/mixed-minimum-rules-rule-set.md)|Queste regole sono incentrate sui problemi più critici C++ nei progetti che supportano Common Language Runtime, inclusi potenziali problemi di sicurezza e arresti anomali dell'applicazione. È necessario includere questo set di regole in qualsiasi set di regole personalizzato creato per C++ i progetti che supportano Common Language Runtime.|
|[Set di regole consigliate miste](../code-quality/mixed-recommended-rules-rule-set.md)|Queste regole sono incentrate sui problemi più comuni e critici C++ nei progetti che supportano Common Language Runtime, inclusi potenziali problemi di sicurezza, arresti anomali dell'applicazione e altri errori di logica e progettazione importanti. È necessario includere questo set di regole in qualsiasi set di regole personalizzato creato per C++ i progetti che supportano Common Language Runtime.  Questo set di regole è progettato per essere configurato con la Visual Studio Professional Edition e versioni successive.|
|[Set di regole minime native](../code-quality/native-minimum-rules-rule-set.md)|Queste regole sono incentrate sui problemi più critici del codice nativo, inclusi i potenziali problemi di sicurezza e gli arresti anomali dell'applicazione. È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.|
|[Set di regole consigliate native](../code-quality/native-recommended-rules-rule-set.md)|Queste regole sono incentrate sui problemi più critici e comuni del codice nativo, inclusi i potenziali problemi di sicurezza e gli arresti anomali dell'applicazione.  È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.  Questo set di regole è progettato per funzionare con Visual Studio Professional Edition e versioni successive.|
|[Set di regole di sicurezza per codice gestito](../code-quality/security-rules-rule-set-for-managed-code.md)|Questo set di regole contiene tutte le regole di sicurezza Microsoft. Includere questo set di regole per ottimizzare il numero di potenziali problemi di sicurezza segnalati.|
