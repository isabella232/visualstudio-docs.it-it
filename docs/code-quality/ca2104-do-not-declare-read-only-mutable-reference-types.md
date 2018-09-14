---
title: 'CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 80d40dd60b0a6b6e507b903fd7a6185c5419422e
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551691"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Category|Microsoft.Security|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene un campo in sola lettura visibile esternamente che costituisce un tipo di riferimento modificabile.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo modificabile è un tipo i cui dati di istanza possono essere modificati. Il <xref:System.Text.StringBuilder?displayProperty=fullName> classe è un esempio di un tipo di riferimento modificabile. Contiene i membri che è possono modificare il valore di un'istanza della classe. Un esempio di un tipo di riferimento non modificabile è di <xref:System.String?displayProperty=fullName> classe. Dopo che è stata creata un'istanza, tale valore non può cambiare mai.

 Il modificatore di sola lettura ([readonly](/dotnet/csharp/language-reference/keywords/readonly) in c# [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) nelle [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], e [const](/cpp/cpp/const-cpp) in C++) in un tipo di riferimento campo (puntatore in C++) impedisce il campo sostituito da una diversa istanza del tipo di riferimento. Il modificatore non impedisce, tuttavia, i dati dell'istanza del campo venga modificato tramite il tipo di riferimento.

 I campi di matrici di sola lettura sono esclusi da questa regola, ma invece causare una violazione del [CA2105: i campi di matrici non devono essere solo lettura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il modificatore di sola lettura o, se una modifica di rilievo è accettabile, sostituire il campo con un tipo non modificabile.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se il tipo di campo è modificabile.

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra una dichiarazione di campo che causa una violazione della regola.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]