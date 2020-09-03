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
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534576"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: I campi eliminabili devono essere eliminati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che implementa i <xref:System.IDisposable?displayProperty=fullName> campi dichiara di tipi che implementano anche <xref:System.IDisposable> . Il <xref:System.IDisposable.Dispose%2A> metodo del campo non viene chiamato dal <xref:System.IDisposable.Dispose%2A> metodo del tipo dichiarante.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo è responsabile dell'eliminazione di tutte le risorse non gestite; Questa operazione viene eseguita tramite l'implementazione di <xref:System.IDisposable> . Questa regola consente di controllare se un tipo Disposable `T` dichiara un campo `F` che è un'istanza di un tipo Disposable `FT` . Per ogni campo `F` , la regola tenta di individuare una chiamata a `FT.Dispose` . La regola cerca i metodi chiamati da `T.Dispose` e un livello inferiore, ovvero i metodi chiamati dai metodi chiamati da `FT.Dispose` .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> su campi di tipo che implementano <xref:System.IDisposable> se si è responsabili dell'allocazione e del rilascio delle risorse non gestite utilizzate dal campo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se non si è responsabili del rilascio della risorsa utilizzata dal campo o se la chiamata a <xref:System.IDisposable.Dispose%2A> viene eseguita a un livello di chiamata più profondo rispetto ai controlli della regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable> ( `FT` nella discussione precedente).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo `TypeB` che viola questa regola dichiarando un campo `aFieldOfADisposableType` ( `F` nella discussione precedente) come tipo Disposable ( `TypeA` ) e non chiamando <xref:System.IDisposable.Dispose%2A> sul campo. `TypeB` corrisponde a `T` nella discussione precedente.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable?displayProperty=fullName> [Modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
