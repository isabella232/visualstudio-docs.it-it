---
title: 'CA2222: Non diminuire la visibilità di membri ereditati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c737a30569ab4cd59931a3fca0e500ebe96e62de
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230986"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Non diminuire la visibilità di membri ereditati

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un metodo privato in un tipo non sealed ha una firma identica a un metodo pubblico dichiarato in un tipo di base. Il metodo privato non è finale.

## <a name="rule-description"></a>Descrizione della regola

Non modificare il modificatore di accesso per i membri ereditati. La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo. Se il membro viene reso privato e il tipo è non sealed, i tipi che ereditano possono chiamare l'ultima implementazione pubblica del metodo nella gerarchia di ereditarietà. Se è necessario modificare il modificatore di accesso, il metodo deve essere contrassegnato come Final o il tipo deve essere sealed per impedire che il metodo venga sottoposto a override.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare l'accesso in modo che non sia privato. In alternativa, se il linguaggio di programmazione lo supporta, è possibile rendere il metodo finale.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo che viola questa regola.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]