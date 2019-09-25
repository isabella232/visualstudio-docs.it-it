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
ms.openlocfilehash: 1838d7e57b841c932d95006d1ff33972dd7a1a1f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231601"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: I campi eliminabili devono essere eliminati

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> i campi dichiara di tipi che implementano <xref:System.IDisposable>anche. Il <xref:System.IDisposable.Dispose%2A> metodo del campo non viene chiamato <xref:System.IDisposable.Dispose%2A> dal metodo del tipo dichiarante.

## <a name="rule-description"></a>Descrizione della regola

Un tipo è responsabile dell'eliminazione di tutte le relative risorse non gestite. La regola CA2213 verifica se un tipo Disposable, <xref:System.IDisposable>ovvero uno che implementa `T` , dichiara un campo `F` che è un'istanza di un tipo `FT`Disposable. Per ogni campo `F` a cui viene assegnato un oggetto creato localmente all'interno dei metodi o degli inizializzatori del `T`tipo che lo contiene, la regola tenta di `FT.Dispose`individuare una chiamata a. La regola cerca i metodi chiamati da `T.Dispose` e un livello inferiore, ovvero i metodi chiamati dai metodi chiamati da. `T.Dispose`

> [!NOTE]
> A parte i [casi speciali](#special-cases), la regola CA2213 viene attivata solo per i campi a cui viene assegnato un oggetto Disposable creato localmente all'interno dei metodi e degli inizializzatori del tipo che lo contiene. Se l'oggetto viene creato o assegnato all'esterno del `T`tipo, la regola non viene attivata. In questo modo si riduce il rumore nei casi in cui il tipo che lo contiene non è responsabile dell'eliminazione dell'oggetto.

### <a name="special-cases"></a>Casi speciali

La regola CA2213 può anche essere attivata per i campi dei seguenti tipi anche se l'oggetto assegnato non viene creato localmente:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Il passaggio di un oggetto di uno di questi tipi a un costruttore e quindi l'assegnazione a un campo indica un *trasferimento di proprietà Dispose* al tipo appena costruito. Ovvero il tipo appena costruito è ora responsabile dell'eliminazione dell'oggetto. Se l'oggetto non viene eliminato, si verifica una violazione di CA2213.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> su campi di tipo che implementano. <xref:System.IDisposable>

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se:

- Il tipo contrassegnato non è responsabile del rilascio della risorsa utilizzata dal campo (ovvero, il tipo non dispone della *Proprietà Dispose*)
- La chiamata a <xref:System.IDisposable.Dispose%2A> viene eseguita a un livello di chiamata più profondo rispetto ai controlli della regola

## <a name="example"></a>Esempio

Il frammento di codice seguente `TypeA` Mostra un <xref:System.IDisposable>tipo che implementa.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Il frammento di codice seguente `TypeB` Mostra un tipo che viola la regola CA2213 dichiarando un campo `aFieldOfADisposableType` come tipo`TypeA`Disposable () e <xref:System.IDisposable.Dispose%2A> non chiamando sul campo.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

Per correggere la violazione, chiamare `Dispose()` il campo Disposable:

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable?displayProperty=fullName>
- [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)