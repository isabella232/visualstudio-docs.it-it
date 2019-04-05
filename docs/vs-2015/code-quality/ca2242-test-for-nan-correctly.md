---
title: 'CA2242: Testare i valori NaN in modo corretto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a98ce3d213c5d9ae85bb5132a0a44e50112037
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954703"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testare i valori NaN in modo corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un valore rispetto a test di un'espressione <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Double.NaN?displayProperty=fullName>, che rappresenta non un numero, viene generato quando un'operazione aritmetica è definita. Qualsiasi espressione che consente di verificare l'uguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `false`. Qualsiasi espressione che consente di verificare la disuguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione della regola e determinare se un valore rappresenta con precisione <xref:System.Double.NaN?displayProperty=fullName>, usare <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due espressioni che testano erroneamente un valore rispetto <xref:System.Double.NaN?displayProperty=fullName> e un'espressione che utilizza correttamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
