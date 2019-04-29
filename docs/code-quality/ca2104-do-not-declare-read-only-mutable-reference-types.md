---
title: 'CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura'
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 40fdeefc2d664b80bb6e17c109349cb5912b0516
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545355"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Category|Microsoft.Security|
|Modifica importante|Non sostanziale|

> [!NOTE]
> Regola CA2104 è obsoleto e verrà rimossa in una versione futura di Visual Studio. Non verrà implementato come un [analizzatore](roslyn-analyzers-overview.md) a causa di analisi complesse necessarie per determinare l'immutabilità effettivo di un tipo.

## <a name="cause"></a>Causa

Un tipo visibile esternamente contiene un campo in sola lettura visibile esternamente che costituisce un tipo di riferimento modificabile.

## <a name="rule-description"></a>Descrizione della regola

Un tipo modificabile è un tipo i cui dati di istanza possono essere modificati. Il <xref:System.Text.StringBuilder?displayProperty=fullName> classe è un esempio di un tipo di riferimento modificabile. Contiene i membri che è possono modificare il valore di un'istanza della classe. Un esempio di un tipo di riferimento non modificabile è di <xref:System.String?displayProperty=fullName> classe. Dopo che è stata creata un'istanza, tale valore non può cambiare mai.

Il modificatore di sola lettura ([readonly](/dotnet/csharp/language-reference/keywords/readonly) in C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in Visual Basic, e [const](/cpp/cpp/const-cpp) in C++) in un tipo di riferimento campo (o un puntatore in C++) impedisce il campo da sostituita da una diversa istanza del tipo di riferimento. Il modificatore non impedisce, tuttavia, i dati dell'istanza del campo venga modificato tramite il tipo di riferimento.

Questa regola potrebbe inavvertitamente mostrano una violazione per un tipo che sia in realtà, non modificabile. In tal caso, è possibile eliminare l'avviso.

I campi di matrici di sola lettura sono esclusi da questa regola, ma invece causare una violazione del [CA2105: I campi di matrici non devono essere solo lettura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il modificatore di sola lettura o, se una modifica di rilievo è accettabile, sostituire il campo con un tipo non modificabile.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se il tipo di campo è modificabile.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata una dichiarazione di campo che causa una violazione della regola:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]