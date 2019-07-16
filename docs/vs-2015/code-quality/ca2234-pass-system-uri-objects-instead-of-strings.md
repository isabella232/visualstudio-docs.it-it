---
title: 'CA2234: Passare oggetti System. Uri invece di stringhe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ce0ed8a2600d52d3a8f6649a528b6c809895f3fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142407"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Passare oggetti System.Uri invece di stringhe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Viene eseguita una chiamata a un metodo che ha un parametro di stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url"; e il tipo dichiarante del metodo contiene un overload del metodo corrispondente che ha un <xref:System.Uri?displayProperty=fullName> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Un nome di parametro è suddiviso in token in base alla convenzione camel, e quindi ogni token viene controllato per verificare se è uguale a "uri", "Uri", "urn", "Urn", "url" o "Url". Se non esiste una corrispondenza, si presuppone che il parametro rappresenti un uniform resource identifier (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. Il <xref:System.Uri> classe fornisce questi servizi in modo sicuro e affidabile. Quando è possibile scegliere tra due overload che differiscono solo per quanto riguarda la rappresentazione di un URI, l'utente deve scegliere l'overload che accetta un <xref:System.Uri> argomento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare l'overload che accetta il <xref:System.Uri> argomento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro della stringa non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `ErrorProne`, che viola la regola e un metodo `SaferWay`, che chiama correttamente la <xref:System.Uri> rapporto di overload.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1057: Stringa chiamano gli overload System. Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI restituiscono valori non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
