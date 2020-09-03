---
title: 'CA1816: chiamare GC. SuppressFinalize correttamente | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 532478a8d6ed6b88347d196b4a74b6f19a38ef85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546770"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Chiamare GC.SuppressFinalize correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. Utilizzo|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

- Un metodo che rappresenta un'implementazione di non <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Metodo che non è un'implementazione delle <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamate a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Un metodo chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> e passa un valore diverso da this (me in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo consente agli utenti di rilasciare le risorse in qualsiasi momento prima che l'oggetto diventi disponibile per Garbage Collection. Se <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> viene chiamato il metodo, vengono liberate le risorse dell'oggetto. Questa operazione rende superflua la finalizzazione. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> deve chiamare in <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> modo che il Garbage Collector non chiami il finalizzatore dell'oggetto.

 Per impedire che i tipi derivati con finalizzatori debbano implementare nuovamente [System. IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) e per chiamarlo, i tipi non sealed senza finalizzatori devono comunque chiamare <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola:

 Se il metodo è un'implementazione di <xref:System.IDisposable.Dispose%2A> , aggiungere una chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 Se il metodo non è un'implementazione di <xref:System.IDisposable.Dispose%2A> , rimuovere la chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> o spostarla nell'implementazione del tipo <xref:System.IDisposable.Dispose%2A> .

 Modificare tutte le chiamate a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per passare questo (me in Visual Basic).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo se si intende utilizzare <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per controllare la durata di altri oggetti. Non eliminare un avviso da questa regola se un'implementazione di non <xref:System.IDisposable.Dispose%2A> chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> . In questa situazione, la mancata eliminazione della finalizzazione comporta un peggioramento delle prestazioni e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che chiama erroneamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che chiama correttamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2215: I metodi Dispose devono chiamare Dispose della classe di base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: I tipi eliminabili devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vedere anche
 [Modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
