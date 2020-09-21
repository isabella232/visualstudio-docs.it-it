---
title: Regole di gestibilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 751cec177e066da1210997ef0f6f8d869ba7d0dc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808584"
---
# <a name="maintainability-rules"></a>Regole di gestibilità

Le regole di manutenzione supportano la libreria e la manutenzione dell'applicazione.

## <a name="in-this-section"></a>Contenuto della sezione

| Regola | Descrizione |
|-----------|-----------------------------------|
| [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501.md) | Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. |
| [CA1502: Evitare complessità eccessiva](../code-quality/ca1502.md) | Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali. |
| [CA1505: Evitare codice non gestibile](../code-quality/ca1505.md) | Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione. |
| [CA1506: Evitare un numero eccessivo di accoppiamenti tra classi](../code-quality/ca1506.md) | Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo. |
| [CA1507: Usare nameof invece della stringa](../code-quality/ca1507.md) | Un valore letterale stringa viene usato come argomento in cui è `nameof` possibile usare un'espressione. |
| [CA1508: Evitare codice di condizione non utilizzato](../code-quality/ca1508.md) | Un metodo ha codice condizionale che restituisce sempre `true` o `false` in fase di esecuzione. In questo modo viene creato codice non attivo nel `false` ramo della condizione. |
| [CA1509: Voce non valida nel file di configurazione della metrica del codice](../code-quality/ca1509.md) | Le regole della metrica del codice, ad esempio [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) e [CA1506](ca1506.md), hanno fornito un file di configurazione denominato `CodeMetricsConfig.txt` con una voce non valida. |

## <a name="see-also"></a>Vedere anche

- [Misurazione della complessità e della gestibilità del codice gestito](../code-quality/code-metrics-values.md)
