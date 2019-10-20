---
title: 'CA2220: i finalizzatori devono chiamare il finalizzatore della classe di base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663583"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: I finalizzatori devono chiamare il finalizzatore della classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che esegue l'override di <xref:System.Object.Finalize%2A?displayProperty=fullName> non chiama il metodo <xref:System.Object.Finalize%2A> nella relativa classe di base.

## <a name="rule-description"></a>Descrizione della regola
 La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. Per garantire questo problema, i tipi devono chiamare la classe di base <xref:System.Object.Finalize%2A> metodo dall'interno del proprio <xref:System.Object.Finalize%2A> metodo. Il C# compilatore aggiunge automaticamente la chiamata al finalizzatore della classe di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare il metodo <xref:System.Object.Finalize%2A> del tipo di base dal metodo <xref:System.Object.Finalize%2A>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Alcuni compilatori destinati a Common Language Runtime inseriscono una chiamata al finalizzatore del tipo di base nel linguaggio MSIL (Microsoft Intermediate Language). Se viene segnalato un avviso da questa regola, il compilatore non inserisce la chiamata ed è necessario aggiungerla al codice.

## <a name="example"></a>Esempio
 Nell'esempio di Visual Basic seguente viene illustrato un tipo `TypeB` che chiama correttamente il metodo <xref:System.Object.Finalize%2A> nella relativa classe di base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Criterio Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
