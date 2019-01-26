---
title: "CA2131: I tipi SecurityCritical possono non partecipare all'equivalenza del tipo"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d42b7f0104f00f346146de882c903c2ebd0ececc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993159"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: I tipi SecurityCritical possono non partecipare all'equivalenza del tipo

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo partecipa all'equivalenza del tipo e il tipo stesso o un membro o un campo del tipo, è contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata su qualsiasi tipo critico o a tipi che contengono metodi o campi critici che partecipano all'equivalenza del tipo. Quando CLR rileva tale tipo, non è possibile caricarlo con un <xref:System.TypeLoadException> in fase di esecuzione. In genere, questa regola funziona solo quando gli utenti implementano l'equivalenza del tipo manualmente piuttosto che basarsi su tlbimp e i compilatori per fare l'equivalenza del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Gli esempi seguenti illustrano un'interfaccia, un metodo e un campo che causa la regola da attivare.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Codice SecurityTransparent, livello 2](/dotnet/framework/misc/security-transparent-code-level-2)