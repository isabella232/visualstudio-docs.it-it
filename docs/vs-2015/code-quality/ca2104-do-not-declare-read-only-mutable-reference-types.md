---
title: 'CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03bb90b11e994ce2f823deb7e2395afc6aee7e04
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966459"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Il modificatore di sola lettura ([readonly](http://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) in C# [ReadOnly](http://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) nelle [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], e [const](http://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) in C++) in un tipo di riferimento campo (puntatore in C++) impedisce il campo sostituito da una diversa istanza del tipo di riferimento. Il modificatore non impedisce, tuttavia, i dati dell'istanza del campo venga modificato tramite il tipo di riferimento.

 I campi di matrici di sola lettura sono esclusi da questa regola, ma invece causare una violazione del [CA2105: I campi di matrici non devono essere solo lettura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il modificatore di sola lettura o, se una modifica di rilievo è accettabile, sostituire il campo con un tipo non modificabile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il tipo di campo è modificabile.

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra una dichiarazione di campo che causa una violazione della regola.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
