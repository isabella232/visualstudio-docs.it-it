---
title: Regola di analisi codice CA2153 per le eccezioni stato danneggiato
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542157"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitare la gestione delle eccezioni stato danneggiato

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

[Danneggiato (CSE) le eccezioni di stato](https://msdn.microsoft.com/magazine/dd419661.aspx) indicano che la memoria del processo sono presenti danni. Se si prova a intercettare tali eccezioni, invece di lasciare che il processo venga arrestato in modo anomalo, può portare a vulnerabilità di sicurezza nel caso in cui un utente malintenzionato riesca a inserire un exploit nell'area della memoria danneggiata.

## <a name="rule-description"></a>Descrizione della regola

CSE indica che lo stato di un processo è stato danneggiato e non è stato recuperato dal sistema. Nello scenario di stato danneggiato, un gestore generale recupera l'eccezione solo se si contrassegna il metodo con il <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> attributo. Per impostazione predefinita, il [Common Language Runtime (CLR)](/dotnet/standard/clr) non richiama i gestori catch per le eccezioni CSE.

La più sicura consiste nel consentire al processo di arresto anomalo del sistema senza rilevare questi tipi di eccezioni. Anche la registrazione del codice, è possibile consentire agli utenti malintenzionati di sfruttare i bug al danneggiamento della memoria.

Questo avviso viene attivato quando le eccezioni CSE con un gestore generale che recupera tutte le eccezioni, ad esempio, `catch (System.Exception e)` o `catch` senza alcun parametro di eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per risolvere questo problema, effettuare una delle operazioni seguenti:

- Rimuovere l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Viene ripristinato il comportamento di runtime predefinito che prevede che le eccezioni CSE non vengano passate ai gestori catch.

- Rimuovere il gestore catch generale nella preferenza dei gestori che recuperano tipi di eccezione specifici. Ad esempio estensioni CSE, presupponendo che il codice del gestore possa gestirle in modo sicuro (raro).

- Generare di nuovo l'estensione lato client nel gestore catch che passa l'eccezione al chiamante e deve comportare l'arresto del processo in esecuzione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudocodice

### <a name="violation"></a>Violazione

Lo pseudocodice seguente illustra il modello rilevato da questa regola.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Soluzione 1: rimuovere l'attributo

Rimozione di <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo assicura che le eccezioni stato danneggiato non vengono gestite tramite il metodo.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Soluzione 2: rilevare eccezioni specifiche

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
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Soluzione 3: rethrow

Rigenera l'eccezione.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```