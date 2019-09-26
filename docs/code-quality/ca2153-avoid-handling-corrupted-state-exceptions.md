---
title: CA2153 della regola di analisi codice per le eccezioni di stato danneggiato
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0179a9609907adc07dc6d8a085eb9a2a0c38c065
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253231"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitare di gestire le eccezioni di stato danneggiate

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Le [eccezioni di stato danneggiate (CSES)](https://msdn.microsoft.com/magazine/dd419661.aspx) indicano che nel processo è presente un danneggiamento della memoria. Se si prova a intercettare tali eccezioni, invece di lasciare che il processo venga arrestato in modo anomalo, può portare a vulnerabilità di sicurezza nel caso in cui un utente malintenzionato riesca a inserire un exploit nell'area della memoria danneggiata.

## <a name="rule-description"></a>Descrizione della regola

CSE indica che lo stato di un processo è stato danneggiato e non è stato recuperato dal sistema. Nello scenario di stato danneggiato, un gestore generale rileva l'eccezione solo se si contrassegna il metodo con l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> attributo. Per impostazione predefinita, [Common Language Runtime (CLR)](/dotnet/standard/clr) non richiama i gestori catch per CSES.

L'opzione più sicura è consentire l'arresto anomalo del processo senza intercettare questi tipi di eccezioni. Anche il codice di registrazione può consentire agli utenti malintenzionati di sfruttare bug di danneggiamento della memoria.

Questo avviso viene attivato quando si intercettano CSES con un gestore generale che intercetta tutte le eccezioni, `catch (System.Exception e)` ad `catch` esempio, o senza il parametro Exception.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per risolvere il problema, eseguire una delle operazioni seguenti:

- Rimuovere l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Viene ripristinato il comportamento predefinito in fase di esecuzione in cui CSEs non vengono passati ai gestori catch.

- Rimuovere il gestore catch generale nella preferenza dei gestori che recuperano tipi di eccezione specifici. Questo può includere CSEs, supponendo che il codice del gestore sia in grado di gestirle in modo sicuro (rare).

- Rigenerare l'estensione lato client nel gestore catch, che passa l'eccezione al chiamante e dovrebbe causare l'interruzione del processo in esecuzione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudo-codice

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

La rimozione <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> dell'attributo garantisce che le eccezioni di stato danneggiate non vengano gestite dal metodo.

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

### <a name="solution-2---catch-specific-exceptions"></a>Soluzione 2: intercettare eccezioni specifiche

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

### <a name="solution-3---rethrow"></a>Soluzione 3-rigenerazione

Generare nuovamente l'eccezione.

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