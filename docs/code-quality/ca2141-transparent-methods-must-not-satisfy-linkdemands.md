---
title: CA2141:I metodi Transparent non devono soddisfare i LinkDemand
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24723559988974c51798c3e099ff8c1d86a15db9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920512"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:I metodi Transparent non devono soddisfare i LinkDemand

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un metodo trasparente per la sicurezza chiama un metodo in un assembly che non è contrassegnato <xref:System.Security.AllowPartiallyTrustedCallersAttribute> con l'attributo (APTCA) oppure un metodo trasparente per la sicurezza <xref:System.Security.Permissions.SecurityAction> soddisfa un oggetto `.LinkDemand` per un tipo o un metodo.

## <a name="rule-description"></a>Descrizione della regola
La soddisfazione di un LinkDemand è un'operazione sensibile alla sicurezza che può causare un'elevazione non intenzionale dei privilegi. Il codice trasparente per la sicurezza non deve soddisfare I LinkDemand, perché non è soggetto agli stessi requisiti di controllo di sicurezza del codice critico per la sicurezza. I metodi Transparent negli assembly di livello 1 del set di regole di sicurezza provocheranno la conversione di tutti i I LinkDemand che soddisfano per essere completati in fase di esecuzione, che può causare problemi di prestazioni. Negli assembly di livello 2 del set di regole di sicurezza, i metodi Transparent non vengono compilati nel compilatore JIT (just-in-Time) se tentano di soddisfare un LinkDemand.

Negli assembly che utilizzano la sicurezza di livello 2, i tentativi eseguiti da un metodo trasparente per la sicurezza per soddisfare un LinkDemand o chiamare un metodo in un <xref:System.MethodAccessException>assembly non APTCA generano; in assembly di livello 1, LinkDemand diventa una richiesta completa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, contrassegnare il metodo di accesso con <xref:System.Security.SecurityCriticalAttribute> l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo o oppure rimuovere LinkDemand dal metodo a cui si accede.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
In questo esempio, un metodo trasparente tenta di chiamare un metodo con un LinkDemand. Questa regola verrà attivata su questo codice.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]