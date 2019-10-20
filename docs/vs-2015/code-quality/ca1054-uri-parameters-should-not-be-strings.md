---
title: 'CA1054: i parametri URI non devono essere stringhe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2062c7518545300074a0377b7a9cca7ddf1a8aa5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603372"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: I parametri URI non devono essere stringhe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo dichiara un metodo con un parametro di stringa il cui nome contiene "URI", "URI", "urn", "urn", "URL" o "URL" e il tipo non dichiara un overload corrispondente che accetta un parametro <xref:System.Uri?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola suddivide il nome del parametro in token in base alla convenzione dell'involucro Camel e controlla se ogni token è uguale a "URI", "URI", "urn", "urn", "URL" o "URL". Se esiste una corrispondenza, la regola presuppone che il parametro rappresenti un URI (Uniform Resource Identifier). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. Se un metodo accetta una rappresentazione di stringa di un URI, è necessario fornire un overload corrispondente che accetta un'istanza della classe <xref:System.Uri>, che fornisce questi servizi in modo sicuro e sicuro.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare il parametro su un tipo <xref:System.Uri>; si tratta di una modifica di rilievo. In alternativa, fornire un overload del metodo che accetta un parametro di <xref:System.Uri>; si tratta di una modifica senza interruzioni.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ErrorProne`, che viola questa regola e un tipo, `SaferWay`, che soddisfa la regola.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
