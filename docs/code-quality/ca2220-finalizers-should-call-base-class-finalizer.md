---
title: 'CA2220: I finalizzatori devono chiamare il finalizzatore della classe di base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231165"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: I finalizzatori devono chiamare il finalizzatore della classe di base

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo che esegue <xref:System.Object.Finalize%2A?displayProperty=fullName> l'override di non <xref:System.Object.Finalize%2A> chiama il metodo nella relativa classe di base.

## <a name="rule-description"></a>Descrizione della regola

La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. Per garantire questo problema, i tipi devono chiamare il <xref:System.Object.Finalize%2A> metodo della classe di base <xref:System.Object.Finalize%2A> dall'interno del rispettivo metodo. Il C# compilatore aggiunge automaticamente la chiamata al finalizzatore della classe di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare il <xref:System.Object.Finalize%2A> metodo del tipo <xref:System.Object.Finalize%2A> di base dal metodo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. Alcuni compilatori destinati a Common Language Runtime inseriscono una chiamata al finalizzatore del tipo di base nel linguaggio MSIL (Microsoft Intermediate Language). Se viene segnalato un avviso da questa regola, il compilatore non inserisce la chiamata ed è necessario aggiungerla al codice.

## <a name="example"></a>Esempio

Nell'esempio di Visual Basic seguente viene illustrato `TypeB` un tipo che chiama <xref:System.Object.Finalize%2A> correttamente il metodo nella relativa classe di base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)