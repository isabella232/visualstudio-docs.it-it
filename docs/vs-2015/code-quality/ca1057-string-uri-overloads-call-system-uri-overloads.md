---
title: 'CA1057: Stringa chiamano gli overload System. Uri | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4cf50ca225544b06409415320c73e7824a10843a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966813"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo dichiara overload del metodo che differiscono solo per la sostituzione di un parametro di stringa con un <xref:System.Uri?displayProperty=fullName> parametro e l'overload che accetta il parametro della stringa non chiama l'overload che accetta il <xref:System.Uri> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Perché gli overload diversi solo la stringa /<xref:System.Uri> parametro, la stringa viene considerata come rappresenti un uniform resource identifier (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. Il <xref:System.Uri> classe fornisce questi servizi in modo sicuro e affidabile. Per sfruttare i vantaggi del <xref:System.Uri> (classe), che deve chiamare l'overload dei valori di <xref:System.Uri> overload usando l'argomento di stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Implementare nuovamente il metodo che usa la rappresentazione di stringa dell'URI in modo che crei un'istanza del <xref:System.Uri> classe usando l'argomento di stringa e quindi passa il <xref:System.Uri> oggetto all'overload che dispone di <xref:System.Uri> parametro.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro della stringa non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un overload di stringa implementato in modo corretto.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2234: Passare oggetti System. Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI restituiscono valori non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
