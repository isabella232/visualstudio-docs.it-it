---
title: 'CA1009: Dichiarare correttamente i gestori di eventi | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f3764e7e7965fb9efe46a8404273de9adde4a34
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967748"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Dichiarare correttamente i gestori eventi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un delegato che gestisce un evento pubblico o protetto non avere la firma corretta, tipo restituito o i nomi dei parametri.

## <a name="rule-description"></a>Descrizione della regola
 I metodi di gestione eventi accettano due parametri. Il primo è di tipo <xref:System.Object?displayProperty=fullName> ed è denominato 'sender'. Corrisponde all'oggetto che ha generato l'evento. Il secondo parametro è di tipo <xref:System.EventArgs?displayProperty=fullName> ed è denominato 'e'. Questi sono i dati associati all'evento. Ad esempio, se l'evento viene generato ogni volta che viene aperto un file, i dati dell'evento contengano in genere il nome del file.

 Metodi del gestore eventi non devono restituire un valore. In C# programming language, ciò è indicato il tipo restituito `void`. Un gestore eventi può richiamare più metodi in più oggetti. Se i metodi sono stati consentiti per restituire un valore, si verificherà più valori restituiti per ogni evento e sarà disponibile solo il valore dell'ultimo metodo richiamato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere la firma, il tipo restituito o i nomi dei parametri del delegato. Per informazioni dettagliate, vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un delegato che è adatto per la gestione degli eventi. I metodi che possono essere richiamati da questo gestore dell'evento sono conformi alla firma specificata nelle linee guida di progettazione. `AlarmEventHandler` è il nome del tipo del delegato. `AlarmEventArgs` deriva dalla classe di base per i dati dell'evento <xref:System.EventArgs>, e contiene i dati degli eventi di allarme.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2109: Controllare i gestori di eventi visibili](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: Eventi e delegati](http://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
