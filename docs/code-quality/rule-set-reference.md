---
title: Tabella di riferimento del set di regole di analisi del codice
ms.date: 04/04/2018
description: Informazioni sui set di regole predefiniti in Visual Studio'analisi del codice legacy. Vedere le risorse nei set di regole. Informazioni su come usare questi set nei set di regole personalizzati.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: c6f23dcc5646d4516f9e00e50f8bf742b94502a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113965"
---
# <a name="code-analysis-rule-set-reference"></a>Tabella di riferimento del set di regole di analisi del codice

Quando si configura l'analisi legacy per i progetti di codice gestito in Visual Studio, è possibile scegliere da un elenco di set di regole *predefiniti.* Alcune regole sono incluse in più di uno dei set di regole predefiniti, ad esempio il set di regole Regole di correttezza di base include regole incluse nel set di regole regole consigliate gestite.

> [!NOTE]
> I set di regole in questa sezione riguardano l'analisi legacy. Per informazioni sui set di regole disponibili per i pacchetti dell'analizzatore del codice, vedere [Usare set di regole con analizzatori del codice.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

È possibile usare uno di questi set di regole predefiniti oppure personalizzare un [set](../code-quality/how-to-create-a-custom-rule-set.md) di regole in base ai requisiti del progetto. Se si includono più set di regole che contengono la stessa regola in un set di regole personalizzato, tale regola viene visualizzata una sola volta nel set di regole personalizzate.

Negli argomenti di questa sezione vengono descritti i set di regole predefiniti e le regole (o gli avvisi) in essi contenuti.

| Set di regole | Regole incluse |
| - | - |
| [Tutte le regole](all-rules-rule-set.md) | Contiene tutte le regole gestite e C++ disponibili |
| [Regole di correttezza di base](basic-correctness-rules-rule-set-for-managed-code.md) | Include le regole consigliate gestite e le regole per gli errori logici e l'utilizzo del framework |
| [Regole di correttezza estese](extended-correctness-rules-rule-set-for-managed-code.md) | Include le regole di correttezza di base (incluse le regole consigliate gestite) e altre regole per gli errori logici e l'utilizzo del framework |
| [Regole delle linee guida di progettazione di base](basic-design-guideline-rules-rule-set-for-managed-code.md) | Include regole consigliate gestite e regole per garantire che il codice sia facile da leggere, comprendere e gestire |
| [Regole delle linee guida di progettazione estese](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Include le regole delle linee guida di progettazione di base (che includono le regole consigliate gestite) e altre regole di manutenibilità incentrate sulla denominazione |
| [Regole di globalizzazione](globalization-rules-rule-set-for-managed-code.md) | Include regole per i problemi di globalizzazione |
| [Regole minime gestite](managed-minimum-rules-rule-set-for-managed-code.md) | Include quattro regole per i problemi critici del codice gestito |
| [Regole consigliate gestite](managed-recommended-rules-rule-set-for-managed-code.md) | Include regole minime gestite e altre regole per i problemi critici del codice gestito |
| [Regole minime miste](mixed-minimum-rules-rule-set.md) | Include regole per i problemi critici nel codice C++ per CLR |
| [Regole consigliate miste](mixed-recommended-rules-rule-set.md) | Include regole minime miste e altre regole per i problemi critici nel codice C++ per CLR |
| [Regole minime native](native-minimum-rules-rule-set.md) | Include regole per i problemi critici nel codice nativo |
| [Regole consigliate native](native-recommended-rules-rule-set.md) | Include regole minime native più altre regole per i problemi critici nel codice nativo |
| [Regole di sicurezza](security-rules-rule-set-for-managed-code.md) | Include regole per l'individuazione delle vulnerabilità di sicurezza |