---
title: 'CA1033: i metodi di interfaccia devono essere richiamabili dai tipi figlio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18629f8d5c63b652d6539db10c6e6dba5d621c24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542298"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome.

## <a name="rule-description"></a>Descrizione della regola
 Si consideri un tipo di base che implementa in modo esplicito un metodo di interfaccia pubblico. Un tipo che deriva dal tipo di base può accedere al metodo di interfaccia ereditato solo tramite un riferimento all'istanza corrente ( `this` in C#) di cui viene eseguito il cast all'interfaccia. Se il tipo derivato implementa di nuovo (in modo esplicito) il metodo di interfaccia ereditato, non è più possibile accedere all'implementazione di base. La chiamata tramite il riferimento all'istanza corrente richiamerà l'implementazione derivata; Questa operazione causa la ricorsione e un eventuale overflow dello stack.

 Questa regola non segnala una violazione per un'implementazione esplicita di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando `Close()` viene fornito un metodo o visibile esternamente `System.IDisposable.Dispose(Boolean)` .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare un nuovo metodo che espone la stessa funzionalità ed è visibile ai tipi derivati o alla modifica di un'implementazione non esplicita. Se una modifica di rilievo è accettabile, un'alternativa consiste nel rendere il tipo sealed.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se viene fornito un metodo visibile esternamente con la stessa funzionalità ma con un nome diverso rispetto al metodo implementato in modo esplicito.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ViolatingBase` , che viola la regola e un tipo, `FixedBase` , che mostra una correzione per la violazione.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Interfacce](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
