---
title: 'CA1014: contrassegnare gli assembly con CLSCompliantAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c6dc131a2bb5f0c54943213fbb42561a0c72d95c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545470"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Contrassegnare gli assembly con CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 A un assembly non è <xref:System.CLSCompliantAttribute?displayProperty=fullName> applicato l'attributo.

## <a name="rule-description"></a>Descrizione della regola
 In Common Language Specification (CLS) vengono definite limitazioni di denominazione, tipi di dati e regole che gli assembly devono rispettare per poter essere utilizzati tra diversi linguaggi di programmazione. Una progettazione efficace impone che tutti gli assembly indichino in modo esplicito la conformità a CLS con <xref:System.CLSCompliantAttribute> . Se l'attributo non è presente in un assembly, l'assembly non è conforme.

 Un assembly conforme a CLS può contenere tipi o membri di tipo non conformi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly. Anziché contrassegnare l'intero assembly come non conforme, è necessario determinare il tipo o i membri dei tipi non conformi e contrassegnare questi elementi come tali. Se possibile, è necessario fornire un'alternativa conforme a CLS per i membri non conformi in modo che i destinatari più ampi possano accedere a tutte le funzionalità dell'assembly.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Se non si desidera che l'assembly sia conforme, applicare l'attributo e impostarne il valore su `false` .

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un assembly a cui è <xref:System.CLSCompliantAttribute?displayProperty=fullName> applicato l'attributo che lo dichiara conforme a CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>[Indipendenza del linguaggio e componenti indipendenti dal linguaggio](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
