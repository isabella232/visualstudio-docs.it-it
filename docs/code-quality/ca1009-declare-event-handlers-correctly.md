---
title: 'CA1009: Dichiarare correttamente i gestori eventi'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c3c5d2df6be4fef281d91794b5b71bfa0c3e653f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779675"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Dichiarare correttamente i gestori eventi

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

 Metodi del gestore eventi non devono restituire un valore. In c# programming language, ciò è indicato il tipo restituito `void`. Un gestore eventi può richiamare più metodi in più oggetti. Se i metodi sono stati consentiti per restituire un valore, si verificherà più valori restituiti per ogni evento e sarà disponibile solo il valore dell'ultimo metodo richiamato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere la firma, il tipo restituito o i nomi dei parametri del delegato. Per informazioni dettagliate, vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un delegato che è adatto per la gestione degli eventi. I metodi che possono essere richiamati da questo gestore dell'evento sono conformi alla firma specificata nelle linee guida di progettazione. `AlarmEventHandler` è il nome del tipo del delegato. `AlarmEventArgs` deriva dalla classe di base per i dati dell'evento <xref:System.EventArgs>, e contiene i dati degli eventi di allarme.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA2109: Controllare i gestori di eventi visibili](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [La gestione e generazione di eventi](/dotnet/standard/events/index)