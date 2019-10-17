---
title: avvisi di manutenibilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e9e24e7769cf4c632faab7795fe2f67844fe7d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445675"
---
# <a name="maintainability-warnings"></a>Avvisi di manutenibilità

Gli avvisi di gestibilità supportano la libreria e la manutenzione dell'applicazione.

## <a name="in-this-section"></a>In questa sezione

| Regola | Descrizione |
|-----------|-----------------------------------|
| [CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante, che genera errori. |
| [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md) | Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. |
| [CA1502: Evitare complessità eccessiva](../code-quality/ca1502-avoid-excessive-complexity.md) | Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali. |
| [CA1504: Controllare i nomi dei campi fuorvianti](../code-quality/ca1504-review-misleading-field-names.md) | Il nome di un campo di istanza inizia con "s_" o il nome di un campo statico (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) inizia con "m_". |
| [CA1505: evitare codice non gestibile](../code-quality/ca1505-avoid-unmaintainable-code.md) | Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione. |
| [CA1506: Evitare un numero eccessivo di accoppiamenti di classi](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo. |
| [Ca1507: usare NameOf al posto della stringa](../code-quality/ca1507.md) | Un valore letterale stringa viene usato come argomento in cui è possibile usare un'espressione `nameof`. |

## <a name="see-also"></a>Vedere anche

- [Misurazione della complessità e della gestibilità del codice gestito](../code-quality/code-metrics-values.md)
