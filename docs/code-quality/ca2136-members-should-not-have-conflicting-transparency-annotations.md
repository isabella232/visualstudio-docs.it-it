---
title: 'CA2136: I membri non devono avere annotazioni di trasparenza in conflitto'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90970ca6be894719ea53ff6af725118626a52f20
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903660"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: I membri non devono avere annotazioni di trasparenza in conflitto

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola viene attivata quando un membro del tipo è contrassegnato con un <xref:System.Security> attributo di sicurezza che dispone di una trasparenza diversa rispetto all'attributo di sicurezza di un contenitore del membro.

## <a name="rule-description"></a>Descrizione della regola
 Gli attributi di trasparenza vengono applicati da elementi di codice con un ambito più ampio a elementi con ambito più ridotto. Gli attributi di trasparenza di elementi di codice che presentano un ambito più ampio hanno la precedenza su quelli contenuti nel primo elemento. Ad esempio, una classe contrassegnata con il <xref:System.Security.SecurityCriticalAttribute> attributo non può contenere un metodo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere questa violazione, rimuovere l'attributo di sicurezza dall'elemento di codice che ha un ambito più basso o modificare il relativo attributo per corrispondere all'elemento di codice che lo contiene.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non eliminare gli avvisi da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, un metodo è contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo ed è un membro di una classe contrassegnata con il <xref:System.Security.SecurityCriticalAttribute> attributo. L'attributo di protezione sicura deve essere rimosso.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]