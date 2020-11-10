---
title: Tabella di riferimento del set di regole di analisi del codice
ms.date: 04/04/2018
description: Informazioni sui set di regole predefiniti nell'analisi del codice legacy di Visual Studio. Vedere risorse nei set di regole. Informazioni su come usare questi set in set di regole personalizzati.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce5b7f2ecdc854269288c61eaeee6d46b4a74d91
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436979"
---
# <a name="code-analysis-rule-set-reference"></a>Tabella di riferimento del set di regole di analisi del codice

Quando si configura l'analisi legacy per i progetti di codice gestito in Visual Studio, è possibile scegliere da un elenco di *set di regole* predefiniti. Alcune regole sono incluse in più di uno dei set di regole predefiniti, ad esempio il set di regole di base di correttezza include regole incluse nel set di regole consigliate gestite.

> [!NOTE]
> I set di regole in questa sezione riguardano l'analisi legacy. Per informazioni sui set di regole disponibili per i pacchetti dell'analizzatore di codice, vedere [usare i set di regole con gli analizzatori di codice](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

È possibile usare uno di questi set di regole predefiniti oppure [personalizzare un set di regole](../code-quality/how-to-create-a-custom-rule-set.md) per soddisfare i requisiti del progetto. Se si includono più set di regole che contengono la stessa regola in un set di regole personalizzato, tale regola viene visualizzata una sola volta nel set di regole personalizzate.

Negli argomenti di questa sezione vengono descritti i set di regole predefiniti e le regole o gli avvisi in essi contenuti.

| Set di regole | Regole incluse |
| - | - |
| [Tutte le regole](all-rules-rule-set.md) | Contiene tutte le regole gestite e C++ disponibili |
| [Regole di correttezza di base](basic-correctness-rules-rule-set-for-managed-code.md) | Include le regole consigliate gestite più le regole per gli errori logici e l'utilizzo del Framework |
| [Regole di correttezza estese](extended-correctness-rules-rule-set-for-managed-code.md) | Include regole di correttezza di base (incluse le regole consigliate gestite) più regole per gli errori logici e l'utilizzo del Framework |
| [Regole delle linee guida di progettazione di base](basic-design-guideline-rules-rule-set-for-managed-code.md) | Include regole consigliate gestite e regole per garantire che il codice sia facile da leggere, comprendere e gestire |
| [Regole delle linee guida di progettazione estese](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Include le regole delle linee guida di progettazione di base (incluse le regole consigliate gestite) più altre regole di gestibilità che si concentrano sulla denominazione |
| [Regole di globalizzazione](globalization-rules-rule-set-for-managed-code.md) | Include regole per i problemi di globalizzazione |
| [Regole minime gestite](managed-minimum-rules-rule-set-for-managed-code.md) | Include quattro regole per i problemi critici del codice gestito |
| [Regole consigliate gestite](managed-recommended-rules-rule-set-for-managed-code.md) | Include le regole minime gestite e altre regole per i problemi critici del codice gestito |
| [Regole minime miste](mixed-minimum-rules-rule-set.md) | Include regole per problemi critici nel codice C++ per CLR |
| [Regole consigliate miste](mixed-recommended-rules-rule-set.md) | Include regole minime miste più regole per problemi critici nel codice C++ per CLR |
| [Regole minime native](native-minimum-rules-rule-set.md) | Include regole per problemi critici nel codice nativo |
| [Regole consigliate native](native-recommended-rules-rule-set.md) | Include le regole minime native più altre regole per i problemi critici nel codice nativo |
| [Regole di sicurezza](security-rules-rule-set-for-managed-code.md) | Include le regole per individuare le vulnerabilità della sicurezza |