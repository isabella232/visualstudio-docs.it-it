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
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534381"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: I metodi Dispose devono chiamare Dispose della classe di base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> eredita da un tipo che implementa anche <xref:System.IDisposable> . Il <xref:System.IDisposable.Dispose%2A> metodo del tipo che eredita non chiama il <xref:System.IDisposable.Dispose%2A> metodo del tipo padre.

## <a name="rule-description"></a>Descrizione della regola
 Se un tipo eredita da un tipo eliminabile, deve chiamare il <xref:System.IDisposable.Dispose%2A> metodo del tipo di base dall'interno del relativo <xref:System.IDisposable.Dispose%2A> metodo. La chiamata del metodo Dispose del tipo di base garantisce che tutte le risorse create dal tipo di base vengano rilasciate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare `base` .<xref:System.IDisposable.Dispose%2A> nel <xref:System.IDisposable.Dispose%2A> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la chiamata a `base` .<xref:System.IDisposable.Dispose%2A> si verifica a un livello di chiamata più profondo rispetto alla verifica della regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeB` che eredita dal tipo `TypeA` e chiama correttamente il relativo <xref:System.IDisposable.Dispose%2A> metodo.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable?displayProperty=fullName> [Modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
