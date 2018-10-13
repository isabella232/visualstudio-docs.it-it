---
title: 'CA2216: I tipi Disposable devono dichiarare un finalizzatore | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a3724e883146cd382369026cd02432f6b8f0e5a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238615"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: I tipi Disposable devono dichiarare un finalizzatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName>e include campi che suggeriscono l'utilizzo delle risorse non gestite, non implementa un finalizzatore, come descritto dalla <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Una violazione di questa regola viene segnalata se il tipo disposable contiene i campi dei tipi seguenti:

-   <xref:System.IntPtr?displayProperty=fullName>

-   <xref:System.UIntPtr?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare un finalizzatore che chiama il <xref:System.IDisposable.Dispose%2A> (metodo).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il tipo non implementa <xref:System.IDisposable> allo scopo di rilasciare le risorse non gestite.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2115: Chiamare GC.KeepAlive durante l'uso di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: I tipi delle risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Criterio Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



