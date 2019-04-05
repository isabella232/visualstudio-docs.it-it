---
title: 'CA1014: Contrassegnare gli assembly con CLSCompliantAttribute | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 617f409eef099b78debacfe09c68a7f516cf7050
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58963944"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Contrassegnare gli assembly con CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un assembly non dispone di <xref:System.CLSCompliantAttribute?displayProperty=fullName> applicato l'attributo.

## <a name="rule-description"></a>Descrizione della regola
 In Common Language Specification (CLS) vengono definite limitazioni di denominazione, tipi di dati e regole che gli assembly devono rispettare per poter essere utilizzati tra diversi linguaggi di programmazione. Una buona progettazione impone che tutti gli assembly indicano in modo esplicito la conformità a CLS con <xref:System.CLSCompliantAttribute>. Se l'attributo non è presente in un assembly, l'assembly non è conforme.

 È possibile che un assembly conforme a CLS contengono i tipi o membri non conformi di tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly. Invece di contrassegnare l'intero assembly come non conforme, è necessario determinare quale tipo o i membri dei tipi non conformi e contrassegnarli come tali. Se possibile, è necessario fornire un'alternativa conforme a CLS per i membri non conformi in modo che un vasto pubblico possa accedere tutte le funzionalità dell'assembly.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Se si preferisce che non l'assembly come conforme, applicare l'attributo e impostarne il valore su `false`.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un assembly avente il <xref:System.CLSCompliantAttribute?displayProperty=fullName> attributo applicato che lo dichiara conforme a CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
