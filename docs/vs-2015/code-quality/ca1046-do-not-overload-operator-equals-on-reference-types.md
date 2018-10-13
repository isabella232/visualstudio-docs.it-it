---
title: "CA1046: Non l'overload dell'operatore di uguaglianza sui tipi di riferimento | Microsoft Docs"
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
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 05c58c3b136c52ace4e683c3d42d0d6417ff4a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183405"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo di riferimento pubblica pubblica o annidata esegue l'overload dell'operatore di uguaglianza.

## <a name="rule-description"></a>Descrizione della regola
 Per i tipi di riferimento, l'implementazione predefinita dell'operatore di uguaglianza è quasi sempre corretta. Per impostazione predefinita, i due riferimenti sono uguali solo se puntano allo stesso oggetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'implementazione dell'operatore di uguaglianza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando il tipo di riferimento si comporta come un tipo di valore predefinito. Se è significativo per eseguire operazioni di addizione o sottrazione nelle istanze del tipo, è probabilmente corretta implementare l'operatore di uguaglianza e sopprimere la violazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato il comportamento predefinito quando si confrontano due riferimenti.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Esempio
 La seguente applicazione confronta alcuni riferimenti.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Questo esempio produce il seguente output:

 **un = nuovo (2,2) e b = nuovo (2,2) sono uguali? No**
**c e un oggetto sono uguali? Sì**
**b e a sono = =? No**
**c e sono = =? Sì**
## <a name="related-rules"></a>Regole correlate
 [CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Operatori di uguaglianza](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



