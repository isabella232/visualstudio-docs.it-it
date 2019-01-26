---
title: 'CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6d1fa4152b0906db89efbb4df68356c58c60416
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996530"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome.

## <a name="rule-description"></a>Descrizione della regola
 Si consideri un tipo di base che implementa in modo esplicito un metodo di interfaccia pubblica. Un tipo che deriva dal tipo di base possa accedere al metodo di interfaccia ereditati solo tramite un riferimento all'istanza corrente (`this` in c#) che viene eseguito il cast all'interfaccia. Se il tipo derivato implementa nuovamente (esplicitamente) il metodo di interfaccia ereditati, l'implementazione di base non saranno più accessibili. La chiamata tramite il riferimento all'istanza corrente richiamerà l'implementazione derivata; In questo modo la ricorsione e un overflow dello stack finale.

 Questa regola non genera un report per un'implementazione esplicita di una violazione <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando visibile esternamente `Close()` o `System.IDisposable.Dispose(Boolean)` viene fornito il metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare un nuovo metodo che espone la stessa funzionalità ed è visibile ai tipi derivati oppure passare a un'implementazione non esplicita. Se una modifica di rilievo è accettabile, un'alternativa consiste nel rendere il tipo sealed.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se viene fornito con la stessa funzionalità, ma un nome diverso rispetto al metodo implementato in modo esplicito un metodo visibile esternamente.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ViolatingBase`, che viola la regola e un tipo, `FixedBase`, che mostra una correzione per la violazione.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Interfacce](/dotnet/csharp/programming-guide/interfaces/index)