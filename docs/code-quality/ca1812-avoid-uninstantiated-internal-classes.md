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
ms.openlocfilehash: def22bd4aee4f64b5e14f2bbe7978a0dfa061261
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841441"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitare classi interne prive di istanze

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un tipo interno (a livello di assembly) non viene mai creata un'istanza.

## <a name="rule-description"></a>Descrizione della regola

Questa regola cerca di individuare una chiamata a uno dei costruttori del tipo e segnala una violazione, se viene trovata alcuna chiamata.

I tipi seguenti non vengono analizzati da questa regola:

- Tipi valore

- Tipi astratti

- Enumerazioni

- Delegati

- Tipi di matrice emesso dal compilatore

- I tipi che non può essere inizializzata e che solo definiscono [ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) metodi.

Se si applica il <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> all'assembly che si sta analizzando, questa regola non contrassegna i tipi che sono contrassegnati come [ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) perché può essere un campo utilizzato da un assembly friend.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il tipo o aggiungere codice che lo usa. Se il tipo contiene solo `static` metodi, aggiungere uno dei seguenti per il tipo per impedire al compilatore di creazione di un costruttore di istanza pubblici predefinito:

- Un costruttore privato per i tipi destinate a .NET Framework versioni 1.0 e 1.1.

- Il `static` modificatore per C# che hanno come destinazione i tipi [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] o versione successiva.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola. Si consiglia di eliminare l'avviso nelle situazioni seguenti:

- La classe viene creata tramite i metodi di reflection con associazione tardiva, ad esempio <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- La classe viene creata automaticamente dal runtime o ASP.NET. Alcuni esempi di classi create automaticamente sono quelli che implementano <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> o <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- La classe viene passata come parametro di tipo con un [ `new` vincolo](/dotnet/csharp/language-reference/keywords/new-constraint). Nell'esempio seguente viene contrassegnato dalla regola CA1812:

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

- [CA1811: Evitare il codice privato](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Controllare i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)