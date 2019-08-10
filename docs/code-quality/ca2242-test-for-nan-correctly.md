---
title: 'CA2242: Testare i valori NaN in modo corretto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8912cb6eeec8009364936a42d572f4f3d83fae5e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919911"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testare i valori NaN in modo corretto

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
Un'espressione testa un valore rispetto <xref:System.Single.NaN?displayProperty=fullName> a <xref:System.Double.NaN?displayProperty=fullName>o.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Double.NaN?displayProperty=fullName>, che rappresenta not-a-Number, viene restituito quando un'operazione aritmetica non è definita. Qualsiasi espressione che verifica l'uguaglianza tra un valore <xref:System.Double.NaN?displayProperty=fullName> e restituisce `false`sempre. Qualsiasi espressione che verifica la disuguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce `true`sempre.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola e determinare accuratamente se un valore rappresenta <xref:System.Double.NaN?displayProperty=fullName>, utilizzare <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> per verificare il valore.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrate due espressioni che testano erroneamente un <xref:System.Double.NaN?displayProperty=fullName> valore in e un'espressione che <xref:System.Double.IsNaN%2A?displayProperty=fullName> utilizza correttamente per verificare il valore.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]