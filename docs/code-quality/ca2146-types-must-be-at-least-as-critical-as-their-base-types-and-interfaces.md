---
title: 'CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a70e999505bd900a7b3d89693ef4f6a1cef9de7d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920417"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un tipo trasparente viene derivato da <xref:System.Security.SecuritySafeCriticalAttribute> un tipo contrassegnato con <xref:System.Security.SecurityCriticalAttribute>o oppure un tipo <xref:System.Security.SecuritySafeCriticalAttribute> contrassegnato con l'attributo viene derivato da un tipo contrassegnato con l' <xref:System.Security.SecurityCriticalAttribute> attributo di.

## <a name="rule-description"></a>Descrizione della regola
Questa regola viene attivata quando un tipo derivato dispone di un attributo di trasparenza di sicurezza che non è critico come il tipo di base o l'interfaccia implementata. Solo i tipi critici possono derivare da tipi di base critici o implementare interfacce critiche e solo tipi critici o critici per la sicurezza possono derivare da tipi di base critici per la sicurezza o implementare interfacce critiche per la sicurezza. Le violazioni di questa regola nella trasparenza di livello 2 generano <xref:System.TypeLoadException> un oggetto per il tipo derivato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere questa violazione, contrassegnare il tipo derivato o di implementazione con un attributo di trasparenza che è almeno critico come il tipo o l'interfaccia di base.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
[!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]