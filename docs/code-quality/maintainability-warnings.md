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
ms.openlocfilehash: fd7fe79665ac8de665116a6832d5ef9327fb356c
ms.sourcegitcommit: dab57cebd484228e6f0cf7ab1b9685c575410c06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/25/2020
ms.locfileid: "82152984"
---
# <a name="maintainability-warnings"></a>Avvisi di manutenibilità

Gli avvisi di gestibilità supportano la libreria e la manutenzione dell'applicazione.

## <a name="in-this-section"></a>Contenuto della sezione

| Regola | Descrizione |
|-----------|-----------------------------------|
| [CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi](../code-quality/ca1500.md) | Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante, che genera errori. |
| [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501.md) | Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. |
| [CA1502: Evitare complessità eccessiva](../code-quality/ca1502.md) | Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali. |
| [CA1504: Controllare i nomi dei campi fuorvianti](../code-quality/ca1504.md) | Il nome di un campo di istanza inizia con "s_" o il nome di un campo statico (Shared [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in) inizia con "m_". |
| [CA1505: Evitare codice non gestibile](../code-quality/ca1505.md) | Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione. |
| [CA1506: Evitare un numero eccessivo di accoppiamenti tra classi](../code-quality/ca1506.md) | Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo. |
| [CA1507: Usare nameof invece della stringa](../code-quality/ca1507.md) | Un valore letterale stringa viene usato come argomento in `nameof` cui è possibile usare un'espressione. |
| [Ca1508: evitare codice condizionale non attivo](../code-quality/ca1508.md) | Un metodo ha codice condizionale che restituisce sempre `true` o `false` in fase di esecuzione. In questo modo viene creato codice non `false` attivo nel ramo della condizione. |

## <a name="see-also"></a>Vedi anche

- [Misurazione della complessità e della gestibilità del codice gestito](../code-quality/code-metrics-values.md)
