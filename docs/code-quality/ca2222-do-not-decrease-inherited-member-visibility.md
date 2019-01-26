---
title: 'CA2222: Non diminuire la visibilità di membri ereditati'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: bdae21ec1a95cdc12cb6511a39f45e610e09b329
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031786"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Non diminuire la visibilità di membri ereditati

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un metodo privato in un tipo unsealed ha una firma identica a un metodo pubblico dichiarato in un tipo di base. Il metodo privato non è finale.

## <a name="rule-description"></a>Descrizione della regola

Non modificare il modificatore di accesso per i membri ereditati. La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo. Se il membro viene reso privato e il tipo è non bloccato, tipi che ereditano possa chiamare l'implementazione di pubblico ultimo del metodo nella gerarchia di ereditarietà. Se è necessario modificare il modificatore di accesso, il metodo deve essere contrassegnato come finale o il relativo tipo deve essere sealed per impedire che il metodo da sottoporre a override.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare l'accesso per essere non privata. In alternativa, se supporta il linguaggio di programmazione, è possibile rendere il metodo finale.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo che viola la regola.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]