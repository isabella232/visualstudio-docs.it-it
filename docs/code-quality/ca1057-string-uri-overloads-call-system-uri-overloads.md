---
title: 'CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e6bd77a49690979ea7ab3c4619fdd578a80bb77c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235514"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo dichiara gli overload del metodo che differiscono solo per la sostituzione di un parametro di stringa con <xref:System.Uri?displayProperty=fullName> un parametro e l'overload che accetta il parametro di stringa non chiama l'overload che accetta il <xref:System.Uri> parametro.

## <a name="rule-description"></a>Descrizione della regola
Poiché gli overload differiscono solo per la stringa o <xref:System.Uri> il parametro, si presuppone che la stringa rappresenti un URI (Uniform Resource Identifier). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La <xref:System.Uri> classe fornisce questi servizi in modo sicuro e protetto. Per sfruttare i vantaggi della <xref:System.Uri> classe, l'overload di stringa deve chiamare l' <xref:System.Uri> Overload usando l'argomento di stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Reimplementare il metodo che utilizza la rappresentazione di stringa dell'URI in modo che crei un'istanza della <xref:System.Uri> classe utilizzando l'argomento di stringa, quindi passa l' <xref:System.Uri> oggetto all'overload con il <xref:System.Uri> parametro.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se il parametro di stringa non rappresenta un URI.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un overload di stringa implementato correttamente.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Regole correlate
[CA2234: Passare oggetti System. URI anziché stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)