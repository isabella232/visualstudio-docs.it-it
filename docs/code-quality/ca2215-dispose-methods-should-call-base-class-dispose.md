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
ms.openlocfilehash: 203fc14097e0c6d2fbdaee1689deffdfe814eb63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541897"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: I metodi Dispose devono chiamare Dispose della classe di base

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> eredita da un tipo che implementa anche <xref:System.IDisposable>. Il <xref:System.IDisposable.Dispose%2A> non esegue il metodo del tipo che ereditano il <xref:System.IDisposable.Dispose%2A> metodo del tipo padre.

## <a name="rule-description"></a>Descrizione della regola
 Se un tipo eredita da un tipo eliminabile, deve chiamare il <xref:System.IDisposable.Dispose%2A> metodo del tipo di base dall'interno del proprio <xref:System.IDisposable.Dispose%2A> (metodo). La chiamata al metodo di tipo di base Dispose assicura che vengano rilasciate tutte le risorse create tramite il tipo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare `base`.<xref:System.IDisposable.Dispose%2A> nel <xref:System.IDisposable.Dispose%2A> (metodo).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se la chiamata a `base`.<xref:System.IDisposable.Dispose%2A> si verifica a un livello più profondo chiama rispetto ai controlli regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeB` che eredita dal tipo `TypeA` e chiama correttamente relativo <xref:System.IDisposable.Dispose%2A> (metodo).

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable?displayProperty=fullName>
- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)