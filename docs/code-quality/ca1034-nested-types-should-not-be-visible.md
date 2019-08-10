---
title: 'CA1034: I tipi annidati non devono essere visibili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a086ad80bd13fb18f866769db34d72cae3e67496
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922869"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: I tipi annidati non devono essere visibili

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo visibile esternamente contiene una dichiarazione di tipo visibile esternamente. Le enumerazioni annidate e i tipi protetti sono esenti da questa regola.

## <a name="rule-description"></a>Descrizione della regola
Un tipo annidato è un tipo dichiarato all'interno dell'ambito di un altro tipo. I tipi annidati sono utili per incapsulare i dettagli di implementazione privata del tipo che lo contiene. I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente.

Non usare tipi annidati visibili esternamente per il raggruppamento logico o per evitare conflitti di nomi; usare invece gli spazi dei nomi.

I tipi annidati includono la nozione di accessibilità dei membri, che alcuni programmatori non conoscono chiaramente.

I tipi protetti possono essere utilizzati nelle sottoclassi e nei tipi annidati in scenari di personalizzazione avanzati.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Se non si desidera che il tipo annidato sia visibile esternamente, modificare l'accessibilità del tipo. In caso contrario, rimuovere il tipo annidato dall'elemento padre. Se lo scopo dell'annidamento consiste nel categorizzare il tipo annidato, usare uno spazio dei nomi per creare la gerarchia.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola la regola.

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]