---
title: 'CA1057: gli overload URI di stringa chiamano gli overload System. Uri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bcdb4d8333b0a4d2d06580d882cf736d4527eca4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539529"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo dichiara gli overload del metodo che differiscono solo per la sostituzione di un parametro di stringa con un <xref:System.Uri?displayProperty=fullName> parametro e l'overload che accetta il parametro di stringa non chiama l'overload che accetta il <xref:System.Uri> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Poiché gli overload differiscono solo per la stringa o il <xref:System.Uri> parametro, si presuppone che la stringa rappresenti un URI (Uniform Resource Identifier). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La <xref:System.Uri> classe fornisce questi servizi in modo sicuro e protetto. Per sfruttare i vantaggi della <xref:System.Uri> classe, l'overload di stringa deve chiamare l' <xref:System.Uri> Overload usando l'argomento di stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Implementare nuovamente il metodo che utilizza la rappresentazione di stringa dell'URI in modo da creare un'istanza della <xref:System.Uri> classe utilizzando l'argomento stringa, quindi passa l' <xref:System.Uri> oggetto all'overload con il <xref:System.Uri> parametro.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro di stringa non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un overload di stringa implementato correttamente.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
