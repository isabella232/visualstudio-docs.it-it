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
ms.openlocfilehash: 377906675d70a712f8ca72b0b6e4d8a6864c1fbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533237"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Convalidare gli argomenti di metodi pubblici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Category|Microsoft. Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo visibile esternamente consente di dereferenziare uno degli argomenti di riferimento senza verificare se tale argomento è `null` ( `Nothing` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 Tutti gli argomenti di riferimento passati a metodi visibili esternamente devono essere controllati `null` . Se appropriato, generare un' <xref:System.ArgumentNullException> eccezione quando l'argomento è `null` .

 Se un metodo può essere chiamato da un assembly sconosciuto perché è dichiarato pubblico o protetto, è necessario convalidare tutti i parametri del metodo. Se il metodo è progettato per essere chiamato solo da assembly noti, è necessario rendere il metodo interno e applicare l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributo all'assembly che contiene il metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, convalidare ogni argomento di riferimento rispetto a `null` .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si è certi che il parametro dereferenziato è stato convalidato da un'altra chiamata al metodo nella funzione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola la regola e un metodo che soddisfa la regola.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Esempio
 In [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] questa regola non rileva che i parametri vengono passati a un altro metodo che esegue la convalida.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Esempio
 I costruttori di copia che popolano i campi o le proprietà che sono oggetti di riferimento possono violare anche la regola CA1062. La violazione si verifica perché l'oggetto copiato passato al costruttore di copia potrebbe essere `null` ( `Nothing` in Visual Basic). Per risolvere la violazione, usare un metodo statico (Shared in Visual Basic) per verificare che l'oggetto copiato non sia null.

 Nell'esempio di `Person` classe seguente, l' `other` oggetto passato al `Person` costruttore di copia potrebbe essere `null` .

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
 Nell'esempio riportato di seguito `Person` , l' `other` oggetto passato al costruttore di copia viene prima verificato il valore null nel `PassThroughNonNull` metodo.

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
