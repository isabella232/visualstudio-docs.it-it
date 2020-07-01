---
title: 'CA2104: non dichiarare tipi di riferimento modificabili in sola lettura | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521043"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Category|Microsoft.Security|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene un campo in sola lettura visibile esternamente che costituisce un tipo di riferimento modificabile.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo modificabile è un tipo i cui dati di istanza possono essere modificati. La <xref:System.Text.StringBuilder?displayProperty=fullName> classe è un esempio di un tipo di riferimento modificabile. Contiene membri che possono modificare il valore di un'istanza della classe. Un esempio di tipo di riferimento non modificabile è la <xref:System.String?displayProperty=fullName> classe. Una volta creata un'istanza, il relativo valore non può mai essere modificato.

 Il modificatore di sola lettura ([ReadOnly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) in C#, [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) in c++) in un campo di tipo riferimento (puntatore in c++) impedisce che il campo venga sostituito da un'istanza diversa del tipo di riferimento. Tuttavia, il modificatore non impedisce che i dati dell'istanza del campo vengano modificati tramite il tipo di riferimento.

 I campi di matrice di sola lettura sono esenti da questa regola, ma causano una violazione dei [campi CA2105: Array non devono essere di sola lettura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il modificatore di sola lettura o, se è accettabile una modifica di rilievo, sostituire il campo con un tipo non modificabile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il tipo di campo non è modificabile.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una dichiarazione di campo che causa la violazione di questa regola.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
