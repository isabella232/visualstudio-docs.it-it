---
title: 'CA2213: I campi Disposable devono essere eliminati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d89e714ceb0a6d0e3d99be05f6c6936622c035ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968029"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: I campi eliminabili devono essere eliminati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> dichiara i campi di tipi che implementano anche <xref:System.IDisposable>. Il <xref:System.IDisposable.Dispose%2A> metodo del campo non viene chiamata dal <xref:System.IDisposable.Dispose%2A> metodo del tipo dichiarante.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo è responsabile per l'eliminazione di tutte le risorse non gestite; Questa operazione viene eseguita implementando <xref:System.IDisposable>. Questa regola verifica se un tipo disposable `T` dichiara un campo `F` vale a dire un'istanza di un tipo disposable `FT`. Per ogni campo `F`, la regola tenta di individuare una chiamata a `FT.Dispose`. La regola cerca i metodi chiamati dalla `T.Dispose`e a un livello inferiore (i metodi chiamati dai metodi chiamati `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> nei campi di tipi che implementano <xref:System.IDisposable> se si è responsabili allocando e rilasciando le risorse non gestite contenute in un campo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se non si è responsabili per rilasciare le risorse contenute in un campo o se la chiamata a <xref:System.IDisposable.Dispose%2A> si verifica a un livello più profondo chiama rispetto ai controlli regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable> (`FT` nella precedente discussione riguardo).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeB` che violano questa regola dichiarando un campo `aFieldOfADisposableType` (`F` nella precedente discussione riguardo) come un tipo disposable (`TypeA`) e non chiamare <xref:System.IDisposable.Dispose%2A> sul campo. `TypeB` corrisponde a `T` nella precedente discussione.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable?displayProperty=fullName> [Criterio Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
