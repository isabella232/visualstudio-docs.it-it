---
title: 'CA2220: I finalizzatori devono chiamare il finalizzatore della classe base | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 09ff2edfce51125d41dc22964a9730545f311bef
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589189"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: I finalizzatori devono chiamare il finalizzatore della classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2220: i finalizzatori devono chiamare il finalizzatore della classe base](https://docs.microsoft.com/visualstudio/code-quality/ca2220-finalizers-should-call-base-class-finalizer).

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che esegue l'override <xref:System.Object.Finalize%2A?displayProperty=fullName> non chiama il <xref:System.Object.Finalize%2A> metodo nella classe base.

## <a name="rule-description"></a>Descrizione della regola
 La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. A tale scopo, i tipi devono chiamare la relativa classe base <xref:System.Object.Finalize%2A> metodo all'interno di proprie <xref:System.Object.Finalize%2A> (metodo). Il compilatore c# aggiunge automaticamente la chiamata al finalizzatore della classe base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare il tipo di base <xref:System.Object.Finalize%2A> metodo di <xref:System.Object.Finalize%2A> (metodo).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Alcuni compilatori destinati a common language runtime inserire una chiamata a finalizzatore del tipo di base in Microsoft intermediate language (MSIL). Se viene segnalato un avviso da questa regola, il compilatore di non inserire la chiamata e aggiungerla al codice.

## <a name="example"></a>Esempio
 Nell'esempio Visual Basic seguente viene illustrato un tipo `TypeB` che chiama correttamente la <xref:System.Object.Finalize%2A> metodo nella classe base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Criterio Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



