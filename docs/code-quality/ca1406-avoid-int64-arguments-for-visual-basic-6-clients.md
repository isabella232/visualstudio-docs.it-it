---
title: 'CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f1c8e50acf2aa4d061461ad934dbd61ba9be9644
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546453"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contrassegnato specificatamente come visibile al modello COM (Component Object) dichiara un membro che accetta un <xref:System.Int64?displayProperty=fullName> argomento.

## <a name="rule-description"></a>Descrizione della regola
 I client COM Visual Basic 6 non è possibile accedere a numeri interi a 64 bit.

 Per impostazione predefinita, sono visibili a COM seguente: assembly, i tipi pubblici, i membri di istanza pubblici nei tipi pubblici e tutti i membri dei tipi di valore pubblico. Tuttavia, per ridurre i falsi positivi, questa regola richiede che la visibilità COM per essere dichiarata in modo esplicito; il tipo l'assembly che contiene deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostata su `false` e il tipo deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola per un parametro il cui valore può sempre essere espresso come integrale a 32 bit, modificare il tipo di parametro in <xref:System.Int32?displayProperty=fullName>. Se il valore del parametro può essere maggiore di quanto può essere espresso come un integrale a 32 bit, modificare il tipo di parametro in <xref:System.Decimal?displayProperty=fullName>. Si noti che entrambe <xref:System.Single?displayProperty=fullName> e <xref:System.Double?displayProperty=fullName> perderebbe la precisione a gamme del <xref:System.Int64> tipo di dati. Se il membro non deve essere visibile a COM, contrassegnarla con il <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `false`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se si è certi che i client COM Visual Basic 6 non accederanno al tipo.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche

- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
- [Tipo di dati Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)