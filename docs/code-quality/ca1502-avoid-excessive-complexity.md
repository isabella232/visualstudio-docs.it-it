---
title: 'CA1502: Evitare complessità eccessiva'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f26faf16cc8a9a8235596aef68e5af5c3b4401e
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253295"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Evitare complessità eccessiva

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Category|Microsoft.Maintainability|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un metodo ha una complessità ciclomatica eccessiva.

## <a name="rule-description"></a>Descrizione della regola

La *complessità ciclomatica* misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità dei rami condizionali. Una complessità ciclomatica bassa indica in genere un metodo facile da comprendere, testare e gestire. La complessità ciclomatica viene calcolata da un grafico del flusso di controllo del metodo e viene fornita come indicato di seguito:

complessità ciclomatica = numero di bordi: numero di nodi + 1

Un *nodo* rappresenta un punto del ramo della logica e un *bordo* rappresenta una linea tra i nodi.

La regola segnala una violazione quando la complessità ciclomatica è maggiore di 25.

È possibile ottenere altre informazioni sulle metriche del codice in base alla [complessità della misura del codice gestito](../code-quality/code-metrics-values.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, effettuare il refactoring del metodo per ridurre la complessità del ciclomatica.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se la complessità non può essere facilmente ridotta e il metodo è facile da comprendere, testare e gestire. In particolare, un metodo che contiene un'istruzione `switch` Large`Select` ( [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in) è un candidato per l'esclusione. Il rischio di destabilizzare la codebase in ritardo nel ciclo di sviluppo o di introdurre una modifica imprevista del comportamento in fase di esecuzione nel codice fornito in precedenza potrebbe superare i vantaggi della gestibilità del refactoring del codice.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Modalità di calcolo della complessità ciclomatica

La complessità ciclomatica viene calcolata aggiungendo 1 ai seguenti elementi:

- Numero di rami (ad esempio `if`, `while`e `do`)

- Numero di `case` istruzioni in un oggetto`switch`

## <a name="example"></a>Esempio

Negli esempi seguenti vengono illustrati i metodi con complessità ciclomatica variabili.

**Complessità ciclomatica di 1**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>Esempio

**Complessità ciclomatica di 2**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>Esempio

**Complessità ciclomatica 3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>Esempio

**Complessità ciclomatica di 8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>Regole correlate

[CA1501: Evitare un'ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Vedere anche

- [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/code-metrics-values.md)