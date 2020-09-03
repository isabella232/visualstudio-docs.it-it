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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcb1165ea00d407f5b4840358cc270eb299ba198
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586223"
---
# <a name="maintainability-warnings"></a>Avvisi di manutenibilità

Gli avvisi di gestibilità supportano la libreria e la manutenzione dell'applicazione.

## <a name="in-this-section"></a>Contenuto della sezione

| Regola | Descrizione |
|-----------|-----------------------------------|
| [CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi](../code-quality/ca1500.md) | Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante, che genera errori. |
| [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501.md) | Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. |
| [CA1502: Evitare complessità eccessiva](../code-quality/ca1502.md) | Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali. |
| [CA1504: Controllare i nomi dei campi fuorvianti](../code-quality/ca1504.md) | Il nome di un campo di istanza inizia con "s_" o il nome di un campo statico (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) inizia con "m_". |
| [CA1505: Evitare codice non gestibile](../code-quality/ca1505.md) | Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione. |
| [CA1506: Evitare un numero eccessivo di accoppiamenti tra classi](../code-quality/ca1506.md) | Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo. |
| [CA1507: Usare nameof invece della stringa](../code-quality/ca1507.md) | Un valore letterale stringa viene usato come argomento in cui è `nameof` possibile usare un'espressione. |
| [CA1508: Evitare codice di condizione non utilizzato](../code-quality/ca1508.md) | Un metodo ha codice condizionale che restituisce sempre `true` o `false` in fase di esecuzione. In questo modo viene creato codice non attivo nel `false` ramo della condizione. |
| [CA1509: Voce non valida nel file di configurazione della metrica del codice](../code-quality/ca1509.md) | Le regole della metrica del codice, ad esempio [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) e [CA1506](ca1506.md), hanno fornito un file di configurazione denominato `CodeMetricsConfig.txt` con una voce non valida. |

## <a name="see-also"></a>Vedere anche

- [Misurazione della complessità e della gestibilità del codice gestito](../code-quality/code-metrics-values.md)
