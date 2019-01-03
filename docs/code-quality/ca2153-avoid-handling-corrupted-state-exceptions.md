---
title: 'CA2153: Evitare la gestione delle eccezioni in stato danneggiato'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6b789a4580c3787a4504d730e694308341657eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821860"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitare la gestione delle eccezioni in stato danneggiato

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Le[eccezioni in stato danneggiato (CSE, Corrupted State Exception)](https://msdn.microsoft.com/magazine/dd419661.aspx) indicano che sono presenti danni nella memoria del processo. Se si prova a intercettare tali eccezioni, invece di lasciare che il processo venga arrestato in modo anomalo, può portare a vulnerabilità di sicurezza nel caso in cui un utente malintenzionato riesca a inserire un exploit nell'area della memoria danneggiata.

## <a name="rule-description"></a>Descrizione della regola

CSE indica che lo stato di un processo è stato danneggiato e non è stato recuperato dal sistema. Nello scenario di stato danneggiato, un gestore generale recupera l'eccezione solo se si contrassegna il metodo con l'attributo `HandleProcessCorruptedStateExceptions` appropriato. Per impostazione predefinita, [Common Language Runtime (CLR)](/dotnet/standard/clr) non richiama i gestori catch per le eccezioni CSE.

Consentire l'arresto anomalo del processo senza tentare il recupero di queste eccezioni è l'opzione più sicura, sebbene anche la registrazione del codice possa consentire agli utenti malintenzionati di sfruttare i bug associati al danneggiamento della memoria.

Questo avviso viene attivato quando si recuperano le eccezioni CSE con un gestore generale che recupera tutte le eccezioni, ad esempio catch(exception) o catch(no exception specification).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per risolvere questo problema, effettuare una delle operazioni seguenti:

- Rimuovere l'attributo `HandleProcessCorruptedStateExceptions`. Viene ripristinato il comportamento di runtime predefinito che prevede che le eccezioni CSE non vengano passate ai gestori catch.

- Rimuovere il gestore catch generale nella preferenza dei gestori che recuperano tipi di eccezione specifici. Ad esempio estensioni CSE, presupponendo che il codice del gestore possa gestirle in modo sicuro (raro).

- Generare di nuovo l'estensione lato client nel gestore catch che assicura l'eccezione viene passata al chiamante e che il processo in esecuzione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudocodice

### <a name="violation"></a>Violazione

Lo pseudocodice seguente illustra il modello rilevato da questa regola.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Soluzione 1

La rimozione dell'attributo HandleProcessCorruptedExceptions assicura che le eccezioni non verranno gestite.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Soluzione 2

Rimuovere il gestore catch generale e recuperare solo tipi specifici di eccezioni.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Soluzione 3

Rigenera l'eccezione.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```