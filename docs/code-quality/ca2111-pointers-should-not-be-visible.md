---
title: 'CA2111: I puntatori non devono essere visibili'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1427cc61d540599b04118e6efff020f62a58bd1b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839742"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: I puntatori non devono essere visibili

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un oggetto pubblico o protetto <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo non è in sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.IntPtr> e <xref:System.UIntPtr> sono tipi di puntatore vengono utilizzati per accedere alla memoria non gestita. Se un puntatore non è privato, interno o di sola lettura, codice dannoso può modificare il valore del puntatore, potenzialmente consentire l'accesso a percorsi arbitrari nella memoria o causando errori di sistema o dell'applicazione.

 Se si prevede di proteggere l'accesso al tipo che contiene il campo del puntatore, vedere [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Proteggere il puntatore del mouse, rendendo di sola lettura, interni o privati.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola se non si fa affidamento sul valore dell'indicatore di misura.

## <a name="example"></a>Esempio
 Il codice seguente illustra i puntatori che violano ed soddisfano la regola. Si noti che i puntatori non privati anche violano la regola [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>