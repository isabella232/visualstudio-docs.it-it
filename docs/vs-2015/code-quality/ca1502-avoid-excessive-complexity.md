---
title: 'CA1502: evitare una complessità eccessiva | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5da2e2bf26bb1894987caa8b748181d952bd7c18
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547836"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Evitare complessità eccessiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Category|Microsoft. gestibilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo ha una complessità ciclomatica eccessiva.

## <a name="rule-description"></a>Descrizione della regola
 La *complessità ciclomatica* misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità dei rami condizionali. Una complessità ciclomatica bassa indica in genere un metodo facile da comprendere, testare e gestire. La complessità ciclomatica viene calcolata da un grafico del flusso di controllo del metodo e viene fornita come indicato di seguito:

 complessità ciclomatica = numero di bordi: numero di nodi + 1

 dove un nodo rappresenta un punto di ramo della logica e un bordo rappresenta una linea tra i nodi.

 La regola segnala una violazione quando la complessità ciclomatica è maggiore di 25.

 Per altre informazioni sulle metriche del codice, vedere la pagina relativa alla [misurazione della complessità e della gestibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, effettuare il refactoring del metodo per ridurre la complessità del ciclomatica.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la complessità non può essere facilmente ridotta e il metodo è facile da comprendere, testare e gestire. In particolare, un metodo che contiene un' `switch` istruzione Large ( `Select` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) è un candidato per l'esclusione. Il rischio di destabilizzare la base di codice in ritardo nel ciclo di sviluppo o di introdurre una modifica imprevista del comportamento in fase di esecuzione nel codice fornito in precedenza potrebbe superare i vantaggi della gestibilità del refactoring del codice.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Modalità di calcolo della complessità ciclomatica
 La complessità ciclomatica viene calcolata aggiungendo 1 ai seguenti elementi:

- Numero di rami (ad esempio `if` , `while` e `do` )

- Numero di `case` istruzioni in un oggetto`switch`

  Negli esempi seguenti vengono illustrati i metodi con complessità ciclomatica variabili.

## <a name="example"></a>Esempio
 **Complessità ciclomatica di 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Esempio
 **Complessità ciclomatica di 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Esempio
 **Complessità ciclomatica 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Esempio
 **Complessità ciclomatica di 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Regole correlate
 [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Vedere anche
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
