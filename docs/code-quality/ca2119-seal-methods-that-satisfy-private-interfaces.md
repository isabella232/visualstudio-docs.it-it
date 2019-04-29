---
title: 'CA2119: Impostare come sealed i metodi che soddisfano interfacce private'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4c019e98e7f1311b6521dff563cb8e7bb0a2356e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62544018"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Impostare come sealed i metodi che soddisfano interfacce private

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico ereditabile fornisce un'implementazione di metodo sottoponibile a override di un `internal` (`Friend` in Visual Basic) dell'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 I metodi di interfaccia avere accessibilità pubblica, non può essere modificato dal tipo di implementazione. Un'interfaccia interna consente di creare un contratto che non può essere implementato all'esterno dell'assembly che definisce l'interfaccia. Un tipo pubblico che implementa un metodo di un'interfaccia interna usando le `virtual` (`Overridable` in Visual Basic) modificatore consente al metodo da sottoporre a override da un tipo derivato è all'esterno dell'assembly. Se un secondo tipo nell'assembly di definizione viene chiamato il metodo e prevede un contratto solo interni, comportamento può essere compromessi quando, invece, viene eseguito il metodo sottoposto a override nell'assembly esterno. In questo modo viene creata una vulnerabilità di sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impedire il metodo da sottoporre a override all'esterno dell'assembly usando uno dei seguenti:

- Impostare il tipo dichiarante `sealed` (`NotInheritable` in Visual Basic).

- Modificare l'accessibilità per il tipo dichiarante `internal` (`Friend` in Visual Basic).

- Rimuovere tutti i costruttori pubblici dal tipo dichiarante.

- Implementare il metodo senza usare il `virtual` modificatore.

- Implementare il metodo in modo esplicito.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se, dopo un attento esame, nessun problema di sicurezza che potrebbero essere sfruttabile se viene eseguito l'override di metodo all'esterno dell'assembly.

## <a name="example-1"></a>Esempio 1
 Nell'esempio seguente viene illustrato un tipo, `BaseImplementation`, che violano questa regola.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Esempio 2
 Nell'esempio seguente sfrutta l'implementazione del metodo virtuale dell'esempio precedente.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Vedere anche

- [Interfacce](/dotnet/csharp/programming-guide/interfaces/index)
- [Interfacce](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)