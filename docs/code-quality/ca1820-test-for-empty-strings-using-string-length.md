---
title: 'CA1820: Testare le stringhe vuote usando la lunghezza di stringa'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233426"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testare le stringhe vuote usando la lunghezza di stringa

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Category|Microsoft.Performance|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Una stringa viene confrontata con la stringa <xref:System.Object.Equals%2A?displayProperty=nameWithType>vuota utilizzando.

## <a name="rule-description"></a>Descrizione della regola

Il confronto tra stringhe <xref:System.String.Length%2A?displayProperty=nameWithType> tramite la proprietà <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> o il metodo è più <xref:System.Object.Equals%2A>veloce rispetto all'uso di. Questo perché <xref:System.Object.Equals%2A> esegue in modo significativo più istruzioni MSIL <xref:System.String.IsNullOrEmpty%2A> rispetto a o al numero di istruzioni eseguite per recuperare il <xref:System.String.Length%2A> valore della proprietà e confrontarlo con zero.

Per <xref:System.Object.Equals%2A> le stringhe null e `<string>.Length == 0` si comportano in modo diverso. Se si tenta di ottenere il valore della <xref:System.String.Length%2A> proprietà in una stringa null, il Common Language Runtime genera un' <xref:System.NullReferenceException?displayProperty=fullName>eccezione. Se si esegue un confronto tra una stringa null e una stringa vuota, il Common Language Runtime non genera un'eccezione e restituisce `false`. Il testing di null non influisce in modo significativo sulle prestazioni relative di questi due approcci. Quando la destinazione è .NET Framework 2,0 o versione successiva, <xref:System.String.IsNullOrEmpty%2A> usare il metodo. In caso contrario, <xref:System.String.Length%2A> utilizzare il confronto = = 0 quando possibile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il confronto in modo da <xref:System.String.IsNullOrEmpty%2A> usare il metodo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se le prestazioni non sono un problema.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrate le diverse tecniche utilizzate per cercare una stringa vuota.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]