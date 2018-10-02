---
title: 'CA1055: URI restituiscono valori non devono essere stringhe | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fccccdef16d29e1dcc890c7799a8cb8a4486288
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589766"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: I valori restituiti URI non devono essere stringhe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1055: URI restituiscono valori non devono essere stringhe](https://docs.microsoft.com/visualstudio/code-quality/ca1055-uri-return-values-should-not-be-strings).

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un metodo contiene "uri", "Uri", "urn", "Urn", "url" o "Url" e il metodo restituisce una stringa.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola il nome del metodo si divide in token in base alla convenzione Pascal e verifica se ogni token uguale a "uri", "Uri", "urn", "Urn", "url" o "Url". Se non esiste una corrispondenza, la regola presuppone che il metodo restituisce un identificatore di risorsa uniforme (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. Il <xref:System.Uri?displayProperty=fullName> classe fornisce questi servizi in modo sicuro e affidabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare il tipo restituito su una <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il valore restituito non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ErrorProne`, che viola la regola e un tipo, `SaferWay`, che soddisfa la regola.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)



