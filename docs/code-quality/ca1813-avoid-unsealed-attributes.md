---
title: 'CA1813: Evitare attributi unsealed'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 63b69b95dc676213c39c4cf10c212472218a0c24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838924"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitare attributi unsealed

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft.Performance|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo pubblico eredita da <xref:System.Attribute?displayProperty=fullName>, non è astratta e non è bloccato (`NotInheritable` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola

La libreria di classi .NET Framework fornisce metodi per recuperare gli attributi personalizzati. Per impostazione predefinita, questi metodi eseguono ricerche nella gerarchia di ereditarietà dell'attributo. Ad esempio, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> Cerca il tipo di attributo specificato o qualsiasi tipo di attributo che estende il tipo di attributo specificato. Utilizzo di attributi sealed Elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rendere sealed il tipo di attributo o renderla astratta.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola. Escludere solo se si sta definendo una gerarchia dell'attributo e non è possibile bloccare l'attributo o renderla astratta.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un attributo personalizzato che soddisfa questa regola.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Vedere anche

- [Attributi](/dotnet/standard/design-guidelines/attributes)