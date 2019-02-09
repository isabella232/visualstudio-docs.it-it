---
title: 'CA1014: Contrassegnare gli assembly con CLSCompliantAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ea7c0d4b9c1d8edea3c2d96f04114db47f3b0d7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911000"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Contrassegnare gli assembly con CLSCompliantAttribute

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

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola. Se si preferisce che non l'assembly come conforme, applicare l'attributo e impostarne il valore su `false`.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un assembly avente il <xref:System.CLSCompliantAttribute?displayProperty=fullName> attributo applicato che lo dichiara conforme a CLS.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Vedere anche

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)