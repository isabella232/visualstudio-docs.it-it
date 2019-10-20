---
title: 'CA1009: dichiarare correttamente i gestori eventi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 261013ed844b6c5ba37c544c7745a77378c0c722
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668915"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Dichiarare correttamente i gestori eventi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un delegato che gestisce un evento pubblico o protetto non ha la firma, il tipo restituito o i nomi di parametro corretti.

## <a name="rule-description"></a>Descrizione della regola
 I metodi di gestione eventi accettano due parametri. Il primo è di tipo <xref:System.Object?displayProperty=fullName> ed è denominato ' sender '. Corrisponde all'oggetto che ha generato l'evento. Il secondo parametro è di tipo <xref:System.EventArgs?displayProperty=fullName> ed è denominato ' è. Questi sono i dati associati all'evento. Se, ad esempio, l'evento viene generato ogni volta che un file viene aperto, i dati dell'evento contengono in genere il nome del file.

 I metodi del gestore eventi non devono restituire un valore. Nel linguaggio C# di programmazione, questo è indicato dal tipo restituito `void`. Un gestore eventi può richiamare più metodi in più oggetti. Se i metodi possono restituire un valore, si verificheranno più valori restituiti per ogni evento e sarà disponibile solo il valore dell'ultimo metodo richiamato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere la firma, il tipo restituito o i nomi dei parametri del delegato. Per informazioni dettagliate, vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un delegato adatto per la gestione di eventi. I metodi che possono essere richiamati da questo gestore eventi sono conformi alla firma specificata nelle linee guida di progettazione. `AlarmEventHandler` è il nome del tipo del delegato. `AlarmEventArgs` deriva dalla classe di base per i dati dell'evento, <xref:System.EventArgs> e include i dati degli eventi di avviso.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2109: Controllare i gestori di eventi visibili](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [PENNINI: eventi e delegati](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
