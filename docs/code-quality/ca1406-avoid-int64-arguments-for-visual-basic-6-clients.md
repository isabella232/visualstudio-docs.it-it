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
ms.openlocfilehash: 82a8b1ea389c37dc63a9fe7366208a2a3028efb8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234804"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft. interoperabilità|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo contrassegnato in modo specifico come visibile a Component Object Model (com) dichiara un membro che accetta un <xref:System.Int64?displayProperty=fullName> argomento.

## <a name="rule-description"></a>Descrizione della regola
I client COM Visual Basic 6 non è possibile accedere a numeri interi a 64 bit.

Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanze pubbliche nei tipi pubblici e tutti i membri dei tipi di valore pubblici. Tuttavia, per ridurre i falsi positivi, questa regola richiede che la visibilità COM del tipo venga dichiarata in modo esplicito; l'assembly contenitore deve <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> essere contrassegnato con impostato su `false` e il tipo <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve essere contrassegnato con impostato su `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola per un parametro il cui valore può essere sempre espresso come integrale a 32 bit, modificare il tipo di parametro <xref:System.Int32?displayProperty=fullName>in. Se il valore del parametro potrebbe essere maggiore di quello che può essere espresso come integrale a 32 bit, modificare il tipo di parametro <xref:System.Decimal?displayProperty=fullName>in. Si noti che <xref:System.Single?displayProperty=fullName> e <xref:System.Double?displayProperty=fullName> perdono <xref:System.Int64> la precisione in corrispondenza degli intervalli superiori del tipo di dati. Se il membro non è destinato a essere visibile a com, contrassegnarlo con <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su. `false`

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se è certo che Visual Basic 6 client COM non accederanno al tipo.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola la regola.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Regole correlate
[CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017 Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche

- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
- [Tipo di dati Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)