---
title: 'CA1502: Evitare complessità eccessiva'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 35fa770c9a7f1d2e0a5d1a5634edf21caae26cfc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006134"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Evitare complessità eccessiva

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Category|Microsoft.Maintainability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un metodo presenta una complessità ciclomatica eccessivo.

## <a name="rule-description"></a>Descrizione della regola

*Complessità ciclomatica* misura il numero di percorsi linearmente indipendenti tramite il metodo, che è determinato dal numero e dalla complessità di rami condizionale. Una complessità ciclomatica basso indica in genere un metodo che è facile da comprendere, testare e gestire. La complessità ciclomatica viene calcolata da un grafico del flusso di controllo del metodo e come indicato di seguito:

complessità ciclomatica = numero di vertici - 1 + il numero di nodi

in cui un nodo rappresenta un punto di branch per la logica e una rete perimetrale rappresenta una linea tra i nodi.

La regola genera una violazione quando la complessità ciclomatica è più di 25.

Altre informazioni sulla metrica del codice in [misurazione della complessità e manutenibilità del codice gestito](../code-quality/code-metrics-values.md),

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, eseguire il refactoring del metodo per ridurre la complessità ciclomatica.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se non è possibile ridurre facilmente la complessità e il metodo è facile da comprendere, testare e gestire. In particolare, un metodo che contiene una grande `switch` (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) istruzione sia un candidato per l'esclusione. Il rischio di destabilizzare il ritardo del ciclo di sviluppo o di introdurre modifiche impreviste del comportamento di runtime nel codice fornito in precedenza potrebbe superare i vantaggi di manutenibilità di refactoring del codice base di codice.

## <a name="how-cyclomatic-complexity-is-calculated"></a>La modalità di calcolo complessità ciclomatica

La complessità ciclomatica viene calcolata aggiungendo 1 al seguente:

- Numero di rami (ad esempio `if`, `while`, e `do`)

- Numero di `case` le istruzioni in un `switch`

## <a name="example"></a>Esempio

Gli esempi seguenti illustrano i metodi che hanno complessità ciclomatica diversi.

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

**Complessità ciclomatica di 3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>Esempio

**Complessità ciclomatica di 8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>Regole correlate

[CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Vedere anche

- [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/code-metrics-values.md)