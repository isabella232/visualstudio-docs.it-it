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
ms.openlocfilehash: e3b3d979910883f6be9f542ec581ecbda0f91deb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444367"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Specificare StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft. globalizzazione|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un'operazione di confronto tra stringhe usa un overload del metodo che non imposta un parametro <xref:System.StringComparison>.

## <a name="rule-description"></a>Descrizione della regola
Molte operazioni di stringa, più importanti i metodi <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A>, forniscono un overload che accetta un valore di enumerazione <xref:System.StringComparison> come parametro.

Quando esiste un overload che accetta un parametro <xref:System.StringComparison>, deve essere usato al posto di un overload che non accetta questo parametro. Impostando in modo esplicito questo parametro, il codice viene spesso reso più chiaro e facile da gestire.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare i metodi di confronto tra stringhe in overload che accettano l'enumerazione <xref:System.StringComparison> come parametro. Ad esempio: sostituire `String.Compare(str1, str2)` con `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un gruppo di destinatari locale limitato e pertanto non verrà localizzata.

## <a name="see-also"></a>Vedere anche

- [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)
- [CA1309: Usare StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)
