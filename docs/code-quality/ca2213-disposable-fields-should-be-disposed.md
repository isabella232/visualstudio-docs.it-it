---
title: 'CA2213: I campi eliminabili devono essere eliminati'
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805003"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: I campi eliminabili devono essere eliminati

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> dichiara i campi di tipi che implementano anche <xref:System.IDisposable>. Il <xref:System.IDisposable.Dispose%2A> metodo del campo non viene chiamata dal <xref:System.IDisposable.Dispose%2A> metodo del tipo dichiarante.

## <a name="rule-description"></a>Descrizione della regola

Un tipo è responsabile per l'eliminazione di tutte le relative risorse non gestite. Regola CA2213 controlla se un tipo disposable (vale a dire una che implementa <xref:System.IDisposable>) `T` dichiara un campo `F` che rappresenta un'istanza di un tipo disposable `FT`. Per ogni campo `F` che ha assegnato a un oggetto creato localmente all'interno di metodi o gli inizializzatori di tipo che lo contiene `T`, la regola tenta di individuare una chiamata a `FT.Dispose`. La regola cerca i metodi chiamati dalla `T.Dispose` e a un livello inferiore (vale a dire, i metodi chiamati dai metodi chiamati `T.Dispose`).

> [!NOTE]
> Diverso dal [casi speciali](#special-cases), regola CA2213 viene attivato solo per i campi che vengono assegnati a un oggetto eliminabile creato localmente all'interno di inizializzatori e i metodi del tipo contenitore. Se l'oggetto viene creato o assegnato di fuori di tipo `T`, la regola non viene generata. In questo modo si riduce il rumore nei casi in cui il tipo che lo contiene non è proprietario di responsabilità per l'eliminazione dell'oggetto.

### <a name="special-cases"></a>Casi speciali

Anche se l'oggetto che vengano loro assegnate non viene creato in locale, CA2213 regola possono inoltre attivare per i campi dei tipi seguenti:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Passaggio di un oggetto di uno di questi tipi per un costruttore e quindi assegnarlo a un campo indica un *dispose trasferimento della proprietà* per il tipo costruito. Vale a dire, il tipo costruito ora è responsabile dell'eliminazione dell'oggetto. Se non viene eliminato l'oggetto, si verifica una violazione di CA2213.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> nei campi di tipi che implementano <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se:

- Il tipo di flag non è responsabile per rilasciare le risorse contenute in un campo (vale a dire, il tipo non dispone *eliminare la proprietà*)
- La chiamata a <xref:System.IDisposable.Dispose%2A> si verifica a un livello più profondo chiama rispetto ai controlli regola

## <a name="example"></a>Esempio

Il frammento di codice seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Il frammento di codice seguente viene illustrato un tipo `TypeB` dichiarando un campo che viola la regola CA2213 `aFieldOfADisposableType` come un tipo disposable (`TypeA`) e non chiamando <xref:System.IDisposable.Dispose%2A> sul campo.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable?displayProperty=fullName>
- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)