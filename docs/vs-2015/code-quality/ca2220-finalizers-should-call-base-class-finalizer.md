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
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540660"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: I finalizzatori devono chiamare il finalizzatore della classe di base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che esegue l'override <xref:System.Object.Finalize%2A?displayProperty=fullName> di non chiama il <xref:System.Object.Finalize%2A> metodo nella relativa classe di base.

## <a name="rule-description"></a>Descrizione della regola
 La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. Per garantire questo problema, i tipi devono chiamare il <xref:System.Object.Finalize%2A> metodo della classe di base dall'interno del rispettivo <xref:System.Object.Finalize%2A> metodo. Il compilatore C# aggiunge automaticamente la chiamata al finalizzatore della classe di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare il metodo del tipo <xref:System.Object.Finalize%2A> di base dal <xref:System.Object.Finalize%2A> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Alcuni compilatori destinati a Common Language Runtime inseriscono una chiamata al finalizzatore del tipo di base nel linguaggio MSIL (Microsoft Intermediate Language). Se viene segnalato un avviso da questa regola, il compilatore non inserisce la chiamata ed è necessario aggiungerla al codice.

## <a name="example"></a>Esempio
 Nell'esempio di Visual Basic seguente viene illustrato un tipo `TypeB` che chiama correttamente il <xref:System.Object.Finalize%2A> metodo nella relativa classe di base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
