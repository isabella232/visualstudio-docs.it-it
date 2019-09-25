---
title: 'CA2136: I membri non devono avere annotazioni di trasparenza in conflitto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f9455e83d7cb128a34696ae5e849fd0901f1891
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232211"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: I membri non devono avere annotazioni di trasparenza in conflitto

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Questa regola viene attivata quando un membro di un tipo è <xref:System.Security> contrassegnato con un attributo di sicurezza con una trasparenza diversa rispetto all'attributo di sicurezza di un contenitore del membro.

## <a name="rule-description"></a>Descrizione della regola
Gli attributi di trasparenza vengono applicati da elementi di codice con un ambito più ampio a elementi con ambito più ridotto. Gli attributi di trasparenza di elementi di codice che presentano un ambito più ampio hanno la precedenza su quelli contenuti nel primo elemento. Una classe contrassegnata con l' <xref:System.Security.SecurityCriticalAttribute> attributo, ad esempio, non può contenere un metodo contrassegnato con l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere questa violazione, rimuovere l'attributo di sicurezza dall'elemento di codice con ambito inferiore oppure modificare l'attributo in modo che corrisponda all'elemento di codice contenitore.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non eliminare gli avvisi da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente un metodo è contrassegnato con l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo ed è un membro di una classe contrassegnata con l' <xref:System.Security.SecurityCriticalAttribute> attributo. È necessario rimuovere l'attributo security safe.

[!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]