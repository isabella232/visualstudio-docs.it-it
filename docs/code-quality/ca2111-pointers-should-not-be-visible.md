---
title: 'CA2111: I puntatori non devono essere visibili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a93f776ac6e133b0ebf79d1dfa56f802ff66e5f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232776"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: I puntatori non devono essere visibili

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un campo public o <xref:System.IntPtr?displayProperty=fullName> protected o <xref:System.UIntPtr?displayProperty=fullName> non è di sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.IntPtr>e <xref:System.UIntPtr> sono tipi di puntatore usati per accedere alla memoria non gestita. Se un puntatore non è privato, interno o di sola lettura, il codice dannoso può modificare il valore del puntatore, consentendo potenzialmente l'accesso a percorsi arbitrari nella memoria o causando errori dell'applicazione o del sistema.

Se si intende proteggere l'accesso al tipo che contiene il campo puntatore, vedere [CA2112: I tipi protetti non devono esporre](../code-quality/ca2112-secured-types-should-not-expose-fields.md)i campi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Proteggere il puntatore rendendolo di sola lettura, interno o privato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola se non si fa affidamento sul valore del puntatore.

## <a name="example"></a>Esempio
Il codice seguente mostra i puntatori che violano e soddisfano la regola. Si noti che i puntatori non privati violano anche la regola [CA1051: Non dichiarare campi](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)di istanza visibili.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA2112 I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>