---
title: "CA2007: Non attendere direttamente un'attività"
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: bf3e13697f39f7d0f531549d4c018b9f42872596
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545228"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Non attendere direttamente un'attività

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un metodo asincrono [attende](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> direttamente.

## <a name="rule-description"></a>Descrizione della regola

Quando un metodo asincrono attende un <xref:System.Threading.Tasks.Task> direttamente, si verifica continuazione nello stesso thread che ha creato l'attività. Questo comportamento può essere dispendioso in termini di prestazioni e può causare un deadlock nel thread UI. Si consiglia di chiamare <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> per segnalare l'intenzione di continuazione.

Questa regola è stata introdotta con [analizzatori FxCop](install-fxcop-analyzers.md) e non esiste in "legacy" (analisi statica del codice) FxCop.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere le violazioni, chiamare <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> sull'attesa <xref:System.Threading.Tasks.Task>. È possibile passare `true` oppure `false` per il `continueOnCapturedContext` parametro.

- La chiamata `ConfigureAwait(true)` dell'attività ha lo stesso comportamento come chiamare in modo non esplicito <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. In modo esplicito chiamando questo metodo, si sta per consentire i lettori che si intende eseguire la continuazione nel contesto di sincronizzazione originali intenzionalmente.

- Chiamare `ConfigureAwait(false)` nell'attività per pianificare le continuazioni al pool di thread, evitando così un deadlock nel thread UI. Il passaggio `false` è uno strumento utile per le librerie di app-indipendenti.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare questo avviso se si sa che il consumer non è un'app (GUI) dell'interfaccia utente grafica o se il consumer non dispone di un <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Esempio

Il frammento di codice seguente genera l'avviso:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Per correggere la violazione, chiamare <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> sull'attesa <xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>Configurabilità

È possibile configurare se si desidera escludere i metodi asincroni che non restituiscono un valore da questa regola. Per escludere questi tipi di metodi, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

È anche possibile configurare quali tipi di assembly a cui applicare questa regola di output. In un file con estensione editorconfig nel progetto, ad esempio, per questa regola si applicano solo al codice che produce un'applicazione console o una libreria di collegamento dinamico (vale a dire, non un'interfaccia utente app), aggiungere la coppia chiave-valore seguente:

```
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Vedere anche

- [È consigliabile attende l'attività con configureawait (false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Installare gli analizzatori FxCop in Visual Studio](install-fxcop-analyzers.md)