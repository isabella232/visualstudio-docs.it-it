---
title: 'CA2242: eseguire il test per NaN correttamente | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0c832b7eb4a94506c5e15dfa5858bb9f6753912
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546263"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testare i valori NaN in modo corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un'espressione testa un valore rispetto a <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName> .

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Double.NaN?displayProperty=fullName>, che rappresenta not-a-Number, viene restituito quando un'operazione aritmetica non è definita. Qualsiasi espressione che verifica l'uguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `false` . Qualsiasi espressione che verifica la disuguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `true` .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola e determinare accuratamente se un valore rappresenta <xref:System.Double.NaN?displayProperty=fullName> , utilizzare <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> per verificare il valore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate due espressioni che testano erroneamente un valore <xref:System.Double.NaN?displayProperty=fullName> in e un'espressione che utilizza correttamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> per verificare il valore.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
