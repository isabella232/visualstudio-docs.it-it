---
title: 'CA1307: Specificare StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 292e174feeb123c640306bc8ef3ffedd7e8847f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966798"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Specificare StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione deve essere un numero limitato di utenti locale e pertanto non verrà localizzata.

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md) [CA1309: Utilizza StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)
