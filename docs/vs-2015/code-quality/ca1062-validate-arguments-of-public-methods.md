---
title: 'CA1062: convalidare gli argomenti dei metodi pubblici | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663650"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Convalidare gli argomenti di metodi pubblici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Category|Microsoft. Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo visibile esternamente consente di dereferenziare uno degli argomenti di riferimento senza verificare se tale argomento sia `null` (`Nothing` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 Tutti gli argomenti di riferimento passati a metodi visibili esternamente devono essere controllati `null`. Se appropriato, generare un <xref:System.ArgumentNullException> quando l'argomento è `null`.

 Se un metodo può essere chiamato da un assembly sconosciuto perché è dichiarato pubblico o protetto, è necessario convalidare tutti i parametri del metodo. Se il metodo è progettato per essere chiamato solo da assembly noti, è necessario rendere il metodo interno e applicare l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> all'assembly che contiene il metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, convalidare ogni argomento di riferimento rispetto a `null`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si è certi che il parametro dereferenziato è stato convalidato da un'altra chiamata al metodo nella funzione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola la regola e un metodo che soddisfa la regola.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Esempio
 In [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], questa regola non rileva che i parametri vengono passati a un altro metodo che esegue la convalida.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Esempio
 I costruttori di copia che popolano i campi o le proprietà che sono oggetti di riferimento possono violare anche la regola CA1062. La violazione si verifica perché l'oggetto copiato passato al costruttore di copia potrebbe essere `null` (`Nothing` in Visual Basic). Per risolvere la violazione, usare un metodo statico (Shared in Visual Basic) per verificare che l'oggetto copiato non sia null.

 Nell'esempio di classe `Person` seguente, l'oggetto `other` passato al costruttore di copia `Person` potrebbe essere `null`.

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
 Nell'esempio `Person` modificato riportato di seguito, l'oggetto `other` passato al costruttore di copia viene prima verificato il valore null nel metodo `PassThroughNonNull`.

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
