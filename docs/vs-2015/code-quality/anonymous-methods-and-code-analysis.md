---
title: Metodi anonimi e analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652217"
---
# <a name="anonymous-methods-and-code-analysis"></a>Metodi anonimi e analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *metodo anonimo* è un metodo senza nome. I metodi anonimi vengono usati più frequentemente per passare un blocco di codice come parametro del delegato.

 Questo argomento illustra il modo in cui l'analisi del codice gestisce gli avvisi e le metriche associati ai metodi anonimi.

## <a name="anonymous-methods-declared-in-a-member"></a>Metodi anonimi dichiarati in un membro
 Gli avvisi e le metriche per un metodo anonimo dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associati al membro che dichiara il metodo. Non sono associate al membro che chiama il metodo.

 Nella classe seguente, ad esempio, qualsiasi avviso rilevato nella dichiarazione di **anonymousMethod** deve essere generato in base a **Method1** e non **Method2**.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Metodi anonimi inline
 Gli avvisi e le metriche per un metodo anonimo dichiarato come assegnazione inline a un campo sono associati al costruttore. Se il campo viene dichiarato come `static` (`Shared` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), gli avvisi e le metriche sono associati al costruttore della classe; in caso contrario, vengono associati al costruttore di istanza.

 Nella classe seguente, ad esempio, eventuali avvisi presenti nella dichiarazione di **anonymousMethod1** verranno generati in base al costruttore predefinito generato in modo implicito della **classe**. Mentre quelli presenti in **anonymousMethod2** verranno applicati al costruttore della classe generata in modo implicito.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

 Una classe può contenere un metodo anonimo inline che assegna un valore a un campo che dispone di più costruttori. In questo caso, gli avvisi e le metriche sono associati a tutti i costruttori, a meno che il costruttore non venga concatenato a un altro costruttore nella stessa classe.

 Nella classe seguente, ad esempio, tutti gli avvisi presenti nella dichiarazione di **anonymousMethod** devono essere generati sulla classe **(int)** e sulla **classe (String)** ma non sulla classe ( **)** .

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

 Sebbene possa sembrare imprevisto, questo si verifica perché il compilatore restituisce un metodo univoco per ogni costruttore che non viene concatenato a un altro costruttore. A causa di questo comportamento, eventuali violazioni che si verificano in **anonymousMethod** devono essere evitate separatamente. Ciò significa anche che se viene introdotto un nuovo costruttore, gli avvisi che sono stati eliminati in precedenza rispetto alla **classe (int)** e alla **classe (stringa)** devono essere eliminati anche per il nuovo costruttore.

 È possibile risolvere questo problema in uno dei due modi seguenti. È possibile dichiarare **anonymousMethod** in un costruttore comune che tutti i costruttori concatenano. In alternativa, è possibile dichiararlo in un metodo di inizializzazione chiamato da tutti i costruttori.

## <a name="see-also"></a>Vedere anche
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
