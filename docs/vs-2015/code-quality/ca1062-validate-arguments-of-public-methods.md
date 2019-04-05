---
title: 'CA1062: Convalidare gli argomenti di metodi pubblici | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 13ea687ea9ca68693af7e2aa5c22881a36207d2e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965434"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Convalidare gli argomenti di metodi pubblici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Se si è certi che il parametro dereferenziato sia stato convalidato da un'altra chiamata al metodo della funzione, è possibile eliminare un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un metodo che viola la regola e un metodo che soddisfa la regola.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Esempio
 In [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], questa regola consente di rilevare che i parametri vengono passati a un altro metodo che esegue la convalida.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Esempio
 I costruttori di copia che consentono di popolare i campi o proprietà che sono oggetti di riferimento possono anche violare la regola di CA1062. La violazione si verifica perché l'oggetto copiato che viene passato al costruttore di copia potrebbe essere `null` (`Nothing` in Visual Basic). Per correggere la violazione, usare un metodo statico (Shared in Visual Basic) per verificare che l'oggetto copiato non è null.

 Nell'esempio seguente `Person` esempio di classe, il `other` oggetto passato per il `Person` costruttore di copia potrebbe essere `null`.

```

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

```
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
