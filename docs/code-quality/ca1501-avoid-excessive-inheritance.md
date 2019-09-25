---
title: 'CA1501: Evitare ereditarietà eccessiva'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 88464effce80b6957dc8945ad17f5a39b4f449c8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234513"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Evitare ereditarietà eccessiva

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Category|Microsoft.Maintainability|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà.

## <a name="rule-description"></a>Descrizione della regola

Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. Questa regola limita l'analisi alle gerarchie nello stesso modulo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, derivare il tipo da un tipo di base più basso nella gerarchia di ereditarietà o eliminare alcuni tipi di base intermedi.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola in modo sicuro. Tuttavia, il codice potrebbe essere più difficile da gestire. Si noti che, a seconda della visibilità dei tipi di base, la risoluzione delle violazioni di questa regola potrebbe creare modifiche di rilievo. La rimozione dei tipi di base pubblici, ad esempio, costituisce una modifica sostanziale.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo che viola la regola:

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]