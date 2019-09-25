---
title: 'CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4f02938aed7456762f1ef51da716b6b96bdf437
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232154"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Metodo trasparente:

- gestisce un tipo di eccezione di sicurezza critico per la sicurezza

- dispone di un parametro contrassegnato come tipo critico di sicurezza

- dispone di un parametro generico con vincoli critical per la sicurezza

- dispone di una variabile locale di un tipo critico per la sicurezza

- fa riferimento a un tipo contrassegnato come critico per la sicurezza

- chiama un metodo contrassegnato come critico per la sicurezza

- fa riferimento a un campo contrassegnato come critico per la sicurezza

- Restituisce un tipo contrassegnato come critico per la sicurezza

## <a name="rule-description"></a>Descrizione della regola

Un elemento di codice contrassegnato con l'attributo <xref:System.Security.SecurityCriticalAttribute> è critico per la sicurezza. Un metodo trasparente non può usare un elemento critico per la sicurezza. Se un tipo trasparente tenta di utilizzare un tipo critico per la <xref:System.TypeAccessException>sicurezza <xref:System.MethodAccessException> , viene <xref:System.FieldAccessException> generato un oggetto, o.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, effettuare una delle operazioni seguenti:

- Contrassegnare l'elemento di codice che utilizza il codice critico per <xref:System.Security.SecurityCriticalAttribute> la sicurezza con l'attributo

     \- oppure -

- Rimuovere l' <xref:System.Security.SecurityCriticalAttribute> attributo dagli elementi di codice contrassegnati come SecurityCritical e contrassegnarli invece con l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo o <xref:System.Security.SecurityTransparentAttribute> .

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Negli esempi seguenti un metodo trasparente tenta di fare riferimento a una raccolta generica di sicurezza critica, un campo critico per la sicurezza e un metodo critico per la sicurezza.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>