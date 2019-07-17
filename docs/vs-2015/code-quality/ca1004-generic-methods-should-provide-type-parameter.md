---
title: 'CA1004: I metodi generici devono fornire parametri di tipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 458817ee19269735be181e08ed12ee1ecdee329f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182631"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: I metodi generici devono specificare parametri di tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 La firma di parametro di un metodo generico visibile esternamente non contiene tipi che corrispondono a tutti i parametri di tipo del metodo.

## <a name="rule-description"></a>Descrizione della regola
 Per inferenza si intende la procedura con cui viene determinato l'argomento di tipo di un metodo generico in base al tipo di argomento passato al metodo, piuttosto che in base alla specifica esplicita dell'argomento di tipo. Per consentire l'inferenza, la firma di parametro di un metodo generico deve includere un parametro dello stesso tipo del parametro di tipo relativo al metodo. In tal caso non è necessario specificare l'argomento tipo. Quando si usa l'inferenza per tutti i parametri di tipo, la sintassi per chiamare i metodi di istanza generici e non generici è identica. Ciò semplifica l'usabilità dei metodi generici.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la progettazione in modo che la firma di parametro contiene lo stesso tipo per ogni parametro di tipo del metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Che fornisce una sintassi facile da comprendere e usare generics riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata la sintassi per chiamare due metodi generici. L'argomento tipo per `InferredTypeArgument` viene dedotto e l'argomento tipo per `NotInferredTypeArgument` devono essere specificati esplicitamente.

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un numero eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare l'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)