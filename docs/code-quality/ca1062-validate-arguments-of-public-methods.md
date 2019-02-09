---
title: 'CA1062: Convalidare gli argomenti di metodi pubblici'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 274b01a67974db08d9ec016a18ec115bcfac2452
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907971"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Convalidare gli argomenti di metodi pubblici

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Category|Microsoft.Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un metodo visibile esternamente dereferenziato in uno dei relativi argomenti di riferimento senza verificare se è specificata nell'argomento `null` (`Nothing` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola

Tutti gli argomenti di riferimento che vengono passati a metodi visibili esternamente devono essere confrontati con `null`. Se appropriato, generare una <xref:System.ArgumentNullException> quando l'argomento è `null`.

Se un metodo può essere chiamato da un assembly sconosciuto perché è dichiarato come pubblico o protetto, è necessario convalidare tutti i parametri del metodo. Se il metodo è progettato per essere chiamato solo da assembly noti, è necessario rendere il metodo interno e applicare il <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributo all'assembly che contiene il metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, convalidare ogni argomento di riferimento su `null`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se si è certi che il parametro dereferenziato sia stato convalidato da un'altra chiamata al metodo della funzione, è possibile eliminare un avviso da questa regola.

## <a name="example"></a>Esempio

L'esempio seguente illustra un metodo che viola la regola e un metodo che soddisfa la regola.

 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Esempio

I costruttori di copia che consentono di popolare i campi o proprietà che sono oggetti di riferimento possono anche violare la regola di CA1062. La violazione si verifica perché l'oggetto copiato che viene passato al costruttore di copia potrebbe essere `null` (`Nothing` in Visual Basic). Per correggere la violazione, usare un metodo statico (Shared in Visual Basic) per verificare che l'oggetto copiato non è null.

Nell'esempio seguente `Person` esempio di classe, il `other` oggetto passato per il `Person` costruttore di copia potrebbe essere `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Esempio

Di seguito rivisti `Person` esempio, il `other` oggetto passato al costruttore di copia viene dapprima controllata dei valori null nel `PassThroughNonNull` (metodo).

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```