---
title: 'CA1812: Evitare classi interne prive di istanze'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233604"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitare classi interne prive di istanze

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft.Performance|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Non viene mai creata un'istanza di un tipo interno (a livello di assembly).

## <a name="rule-description"></a>Descrizione della regola

Questa regola tenta di individuare una chiamata a uno dei costruttori del tipo e segnala una violazione se non viene trovata alcuna chiamata.

I tipi seguenti non vengono esaminati da questa regola:

- Tipi valore

- Tipi astratti

- Enumerazioni

- Delegati

- Tipi di matrici emesse dal compilatore

- Tipi di cui non è possibile creare un'istanza e [`static`](/dotnet/csharp/language-reference/keywords/static) che definiscono solo i metodi ([ `Shared` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)).

Se si applica l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> oggetto all'assembly analizzato, questa regola non contrassegnerà i tipi contrassegnati come [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) perché un campo può essere utilizzato da un assembly Friend.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il tipo o aggiungere il codice che lo utilizza. Se il tipo contiene solo `static` metodi, aggiungere uno degli elementi seguenti al tipo per impedire al compilatore di emettere un costruttore di istanza pubblica predefinito:

- Modificatore `static` per C# i tipi che hanno come destinazione .NET Framework 2,0 o versione successiva.

- Un costruttore privato per i tipi destinati a .NET Framework versioni 1,0 e 1,1.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola in modo sicuro. Si consiglia di non visualizzare più questo avviso nelle situazioni seguenti:

- La classe viene creata tramite metodi di reflection ad associazione tardiva <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>, ad esempio.

- La classe viene creata automaticamente dalla fase di esecuzione o ASP.NET. Alcuni esempi di classi create automaticamente sono quelli che <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> implementano <xref:System.Web.IHttpHandler?displayProperty=fullName>o.

- La classe viene passata come parametro di tipo con un [ `new` vincolo](/dotnet/csharp/language-reference/keywords/new-constraint). L'esempio seguente verrà contrassegnato da Rule CA1812:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Regole correlate

- [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801 Verifica parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Rimuovi variabili locali non usate](../code-quality/ca1804-remove-unused-locals.md)