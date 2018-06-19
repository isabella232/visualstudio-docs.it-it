---
title: 'CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ce7e5de528e8b0c0a6f128fa9f7d68c1b9f385c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919804"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base
|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Categoria|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> eredita da un tipo che implementa anche <xref:System.IDisposable>. Il <xref:System.IDisposable.Dispose%2A> non chiamata al metodo del tipo che ereditano il <xref:System.IDisposable.Dispose%2A> metodo del tipo padre.

## <a name="rule-description"></a>Descrizione della regola
 Se un tipo eredita da un tipo eliminabile, deve chiamare il <xref:System.IDisposable.Dispose%2A> metodo del tipo di base dall'interno del proprio <xref:System.IDisposable.Dispose%2A> metodo. La chiamata al metodo del tipo di base Dispose garantisce che tutte le risorse create dal tipo di base vengono rilasciate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare `base`.<xref:System.IDisposable.Dispose%2A> nel <xref:System.IDisposable.Dispose%2A> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile escludere un avviso da questa regola se la chiamata a `base`.<xref:System.IDisposable.Dispose%2A> si verifica a un livello più profondo chiamante rispetto a quanto controllato dalla regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeB` che eredita dal tipo `TypeA` e chiama correttamente la <xref:System.IDisposable.Dispose%2A> metodo.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable?displayProperty=fullName> [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)