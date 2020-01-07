---
title: Tabella di riferimento del set di regole di analisi del codice
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d380346b7e049a6ffc4e8d03a5be27983de10249
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587238"
---
# <a name="code-analysis-rule-set-reference"></a>Tabella di riferimento del set di regole di analisi del codice

Quando si configura l'analisi legacy per i progetti di codice gestito in Visual Studio, è possibile scegliere da un elenco di *set di regole*predefiniti. Alcune regole sono incluse in più di uno dei set di regole predefiniti, ad esempio il set di regole di base di correttezza include regole incluse nel set di regole consigliate gestite.

> [!NOTE]
> I set di regole in questa sezione riguardano l'analisi legacy. Per informazioni sui set di regole disponibili per i pacchetti dell'analizzatore di codice, vedere [usare i set di regole con gli analizzatori di codice](analyzer-rule-sets.md).

È possibile usare uno di questi set di regole incorporate oppure è possibile [personalizzare un set di regole](../code-quality/how-to-create-a-custom-rule-set.md) in base alle esigenze di progetto. Se si includono più set di regole che contengono la stessa regola in un set di regole personalizzato, tale regola viene visualizzata una sola volta nel set di regole personalizzate.

In questa sezione vengono illustrate le regole incorporate set e le regole (o gli avvisi) che contengono.

| Set di regole | Regole incluse |
| - | - |
| [Tutte le regole](all-rules-rule-set.md) | Contiene tutte le regole e C++ gestite disponibili |
| [Regole di correttezza di base](basic-correctness-rules-rule-set-for-managed-code.md) | Include le regole consigliate gestite più le regole per gli errori logici e l'utilizzo del Framework |
| [Regole estese di correttezza](extended-correctness-rules-rule-set-for-managed-code.md) | Include regole di correttezza di base (incluse le regole consigliate gestite) più regole per gli errori logici e l'utilizzo del Framework |
| [Regole delle linee guida di progettazione di base](basic-design-guideline-rules-rule-set-for-managed-code.md) | Include regole consigliate gestite e regole per garantire che il codice sia facile da leggere, comprendere e gestire |
| [Regole delle linee guida di progettazione estese](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Include le regole delle linee guida di progettazione di base (incluse le regole consigliate gestite) più altre regole di gestibilità che si concentrano sulla denominazione |
| [Regole di globalizzazione](globalization-rules-rule-set-for-managed-code.md) | Include regole per i problemi di globalizzazione |
| [Regole minime gestite](managed-minimum-rules-rule-set-for-managed-code.md) | Include quattro regole per i problemi critici del codice gestito |
| [Regole consigliate gestite](managed-recommended-rules-rule-set-for-managed-code.md) | Include le regole minime gestite e altre regole per i problemi critici del codice gestito |
| [Regole minime miste](mixed-minimum-rules-rule-set.md) | Include regole per problemi critici nel C++ codice per CLR |
| [Regole consigliate miste](mixed-recommended-rules-rule-set.md) | Include regole minime miste più regole per problemi critici C++ nel codice per CLR |
| [Regole minime Native](native-minimum-rules-rule-set.md) | Include regole per problemi critici nel codice nativo |
| [Regole consigliate Native](native-recommended-rules-rule-set.md) | Include le regole minime native più altre regole per i problemi critici nel codice nativo |
| [Regole di sicurezza](security-rules-rule-set-for-managed-code.md) | Include le regole per individuare le vulnerabilità della sicurezza |
