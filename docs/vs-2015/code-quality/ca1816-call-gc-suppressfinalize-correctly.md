---
title: 'CA1816: Chiamare GC. SuppressFinalize correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 50375390b3a09ec18fcccd45e4eaee7e9fe102e2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094788"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Chiamare GC.SuppressFinalize correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. Utilizzo|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

- Un metodo che è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Un metodo che non è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamate <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Chiama un metodo <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> e passa un valore diverso da this (Me in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo consente agli utenti di rilasciare le risorse in qualsiasi momento prima dell'oggetto di essere disponibili per l'operazione di garbage collection. Se il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> viene chiamato il metodo, libera le risorse dell'oggetto. In questo modo la finalizzazione non necessaria. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> deve chiamare <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> in modo che il garbage collector non chiama il finalizzatore dell'oggetto.

 Per evitare che i tipi con i finalizzatori derivati di dover implementare nuovamente ([System. IDisposable]<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) e per la chiamata, i tipi unsealed senza i finalizzatori devono chiamare ancora <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola:

 Se il metodo è un'implementazione di <xref:System.IDisposable.Dispose%2A>, aggiungere una chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Se il metodo non è un'implementazione di <xref:System.IDisposable.Dispose%2A>, rimuovere la chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> o spostarlo nel tipo <xref:System.IDisposable.Dispose%2A> implementazione.

 Modificare tutte le chiamate a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> passare this (Me in Visual Basic).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola solo se si utilizza deliberatamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per controllare la durata di altri oggetti. Non eliminare un avviso da questa regola se un'implementazione di <xref:System.IDisposable.Dispose%2A> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. In questo caso, riesce a eliminare la finalizzazione comporta una riduzione delle prestazioni e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che erroneamente chiamate <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che correttamente le chiamate <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2215: I metodi Dispose devono chiamare dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vedere anche
 [Criterio Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
