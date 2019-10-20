---
title: 'CA2213: i campi Disposable devono essere eliminati | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662891"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: I campi Disposable devono essere eliminati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> dichiara campi di tipo che implementano anche <xref:System.IDisposable>. Il metodo <xref:System.IDisposable.Dispose%2A> del campo non viene chiamato dal metodo <xref:System.IDisposable.Dispose%2A> del tipo dichiarante.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo è responsabile dell'eliminazione di tutte le risorse non gestite; Questa operazione viene eseguita implementando <xref:System.IDisposable>. Questa regola consente di verificare se un tipo Disposable `T` dichiara un campo `F` che è un'istanza di un tipo Disposable `FT`. Per ogni `F` di campo, la regola tenta di individuare una chiamata a `FT.Dispose`. La regola cerca i metodi chiamati da `T.Dispose` e un livello inferiore (i metodi chiamati dai metodi chiamati da `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> su campi di tipo che implementano <xref:System.IDisposable> se si è responsabili dell'allocazione e del rilascio delle risorse non gestite utilizzate dal campo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se non si è responsabili del rilascio della risorsa utilizzata dal campo o se la chiamata a <xref:System.IDisposable.Dispose%2A> si verifica a un livello di chiamata più profondo rispetto ai controlli della regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable> (`FT` nella discussione precedente).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeB` che viola questa regola dichiarando un campo `aFieldOfADisposableType` (`F` nella discussione precedente) come tipo Disposable (`TypeA`) e non chiamando <xref:System.IDisposable.Dispose%2A> sul campo. `TypeB` corrisponde a `T` nella discussione precedente.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Vedere anche
 [modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable?displayProperty=fullName>
