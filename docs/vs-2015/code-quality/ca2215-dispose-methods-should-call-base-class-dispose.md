---
title: 'CA2215: i metodi Dispose devono chiamare Dispose della classe base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89f3705169fb9d28a1ec773671d460f00b98d892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662858"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> eredita da un tipo che implementa anche <xref:System.IDisposable>. Il metodo <xref:System.IDisposable.Dispose%2A> del tipo di ereditarietà non chiama il metodo <xref:System.IDisposable.Dispose%2A> del tipo padre.

## <a name="rule-description"></a>Descrizione della regola
 Se un tipo eredita da un tipo eliminabile, deve chiamare il metodo <xref:System.IDisposable.Dispose%2A> del tipo di base dall'interno del proprio <xref:System.IDisposable.Dispose%2A> metodo. La chiamata del metodo Dispose del tipo di base garantisce che tutte le risorse create dal tipo di base vengano rilasciate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare `base`. <xref:System.IDisposable.Dispose%2A> nel metodo <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la chiamata a `base`. <xref:System.IDisposable.Dispose%2A> si verifica a un livello di chiamata più profondo rispetto alla verifica della regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeB` che eredita dal tipo `TypeA` e chiama correttamente il relativo metodo di <xref:System.IDisposable.Dispose%2A>.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vedere anche
 [modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable?displayProperty=fullName>
