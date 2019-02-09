---
title: 'CA1307: Specificare StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3aabd73a3c234be61cecdf68fbc92fc7e52883e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927685"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Specificare StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un'operazione di confronto di stringhe viene utilizzato un overload del metodo che non viene impostato un <xref:System.StringComparison> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Molte operazioni stringa, soprattutto il <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A> metodi, fornire un overload che accetta un <xref:System.StringComparison> come parametro un valore di enumerazione.

 Ogni volta che è presente un overload che accetta un <xref:System.StringComparison> parametro deve essere usato invece di un overload che non accetta questo parametro. Impostando questo parametro in modo esplicito, il codice è spesso diventa più chiaro e semplice da gestire.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare metodi di confronto di stringhe per gli overload che accettano il <xref:System.StringComparison> enumerazione come parametro. Ad esempio: cambiare `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione deve essere un numero limitato di utenti locale e pertanto non verrà localizzata.

## <a name="see-also"></a>Vedere anche

- [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)
- [CA1309: Utilizza StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)