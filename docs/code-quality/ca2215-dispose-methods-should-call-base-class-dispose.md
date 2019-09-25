---
title: 'CA2215: I metodi Dispose devono chiamare Dispose della classe di base'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468b63ca554ea126bbd621a2502e54540e6ed068
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231275"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: I metodi Dispose devono chiamare Dispose della classe di base

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> eredita da un tipo che implementa <xref:System.IDisposable>anche. Il <xref:System.IDisposable.Dispose%2A> metodo del tipo che eredita non chiama il <xref:System.IDisposable.Dispose%2A> metodo del tipo padre.

## <a name="rule-description"></a>Descrizione della regola
Se un tipo eredita da un tipo eliminabile, deve chiamare il <xref:System.IDisposable.Dispose%2A> metodo del tipo di base dall'interno del <xref:System.IDisposable.Dispose%2A> relativo metodo. La chiamata del metodo Dispose del tipo di base garantisce che tutte le risorse create dal tipo di base vengano rilasciate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, chiamare `base`.<xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A> nel metodo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se la chiamata a `base`.<xref:System.IDisposable.Dispose%2A> si verifica a un livello di chiamata più profondo rispetto alla verifica della regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un `TypeA` tipo che <xref:System.IDisposable>implementa.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un `TypeB` tipo che eredita dal `TypeA` tipo e chiama correttamente <xref:System.IDisposable.Dispose%2A> il relativo metodo.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable?displayProperty=fullName>
- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)