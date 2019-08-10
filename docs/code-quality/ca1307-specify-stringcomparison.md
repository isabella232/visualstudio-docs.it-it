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
ms.openlocfilehash: ce2da2c1ff5b2f74d8b4d6341050c1895b68955a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922300"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Specificare StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
Un'operazione di confronto tra stringhe usa un overload del metodo che non <xref:System.StringComparison> imposta un parametro.

## <a name="rule-description"></a>Descrizione della regola
Molte operazioni di stringa, più importanti <xref:System.String.Compare%2A> dei <xref:System.String.Equals%2A> metodi e, forniscono un overload che accetta <xref:System.StringComparison> un valore di enumerazione come parametro.

Ogni volta che è presente un overload <xref:System.StringComparison> che accetta un parametro, deve essere usato anziché un overload che non accetta questo parametro. Impostando in modo esplicito questo parametro, il codice viene spesso reso più chiaro e facile da gestire.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare i metodi di confronto tra stringhe in overload che accettano <xref:System.StringComparison> l'enumerazione come parametro. Ad esempio: modificare `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un gruppo di destinatari locale limitato e pertanto non verrà localizzata.

## <a name="see-also"></a>Vedere anche

- [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)
- [CA1309: USA StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)