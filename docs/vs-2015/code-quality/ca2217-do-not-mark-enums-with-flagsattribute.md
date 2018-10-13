---
title: 'CA2217: Non contrassegnare le enumerazioni con FlagsAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e62e483a120e2c0feccf8c517d3e0bcd44ad9840
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265252"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Non contrassegnare le enumerazioni con FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un'enumerazione visibile esternamente è contrassegnata con <xref:System.FlagsAttribute> e ne ha uno o più valori che non sono potenze di due o una combinazione degli altri valori definiti nell'enumerazione.

## <a name="rule-description"></a>Descrizione della regola
 Un'enumerazione deve avere <xref:System.FlagsAttribute> presentare solo se ogni valore definito nell'enumerazione è una potenza di due o una combinazione di valori definiti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere <xref:System.FlagsAttribute> ricavato dall'enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'enumerazione, colore, che contiene il valore 3, che non corrisponde a una potenza di due, né una combinazione di uno qualsiasi dei valori definiti. L'enumerazione Color non deve essere contrassegnato con il <xref:System.FlagsAttribute>.

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cpp/FxCop.Usage.EnumNoFlags.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cs/FxCop.Usage.EnumNoFlags.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/vb/FxCop.Usage.EnumNoFlags.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'enumerazione, giorni, che soddisfa i requisiti per essere contrassegnata con lo System. FlagsAttribute.

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cpp/FxCop.Usage.EnumNoFlags2.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cs/FxCop.Usage.EnumNoFlags2.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/vb/FxCop.Usage.EnumNoFlags2.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName>



