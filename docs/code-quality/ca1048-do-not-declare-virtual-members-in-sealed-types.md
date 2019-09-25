---
title: 'CA1048: Non dichiarare membri virtuali nei tipi sealed'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be0e1b4865b19930f8ddf7163a36b71123bb3a55
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235703"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Non dichiarare membri virtuali nei tipi sealed

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo pubblico è sealed e dichiara un metodo che è sia `virtual` (`Overridable` in Visual Basic) che non finale. Questa regola non segnala violazioni per i tipi delegati, che devono seguire questo modello.

## <a name="rule-description"></a>Descrizione della regola
I tipi dichiarano metodi come virtuali in modo che l'ereditarietà di tipi possa eseguire l'override dell'implementazione del metodo virtuale. Per definizione, non è possibile ereditare da un tipo sealed, rendendo un metodo virtuale su un tipo sealed non significativo.

Il Visual Basic e C# i compilatori non consentono ai tipi di violare questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rendere il metodo non virtuale o rendere il tipo ereditabile.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola. Lasciare il tipo nello stato corrente può causare problemi di manutenzione e non fornisce alcun vantaggio.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola questa regola.

[!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]