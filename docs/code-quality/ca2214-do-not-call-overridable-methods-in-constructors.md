---
title: 'CA2214: Non chiamare metodi sottoponibili a override nei costruttori'
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e05e6925085b27de3001c8ff62d8a3c6e69a88f
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401318"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Non chiamare metodi sottoponibili a override nei costruttori

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Il costruttore di un tipo unsealed chiama un metodo virtuale definito nella relativa classe.

## <a name="rule-description"></a>Descrizione della regola

Quando viene chiamato un metodo virtuale, il tipo effettivo che esegue il metodo non è selezionato fino alla fase di esecuzione. Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non è stata eseguita.

> [!NOTE]
> L'implementazione di analisi binaria di questa regola presenta un messaggio di diagnostica diverso di " **\[nome costruttore] contiene una catena di chiamate che comporta una chiamata a un metodo virtuale definito dalla classe. Esaminare lo stack di chiamate seguente per conseguenze impreviste**". Il [analizzatori FxCop](install-fxcop-analyzers.md) implementazione di questa regola presenta un messaggio di diagnostica di "**non chiamare metodi sottoponibili a override nei costruttori**".

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, non chiamare metodi virtuali del tipo dall'interno di costruttori del tipo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola. Il costruttore deve essere riprogettato per eliminare la chiamata al metodo virtuale.

## <a name="example"></a>Esempio

L'esempio seguente illustra l'effetto della violazione di questa regola. L'applicazione di test viene creata un'istanza di `DerivedType`, in modo che la classe di base (`BadlyConstructedType`) costruttore per l'esecuzione. `BadlyConstructedType`del costruttore chiama in modo non corretto del metodo virtuale `DoSomething`. Come illustrato nell'output, `DerivedType.DoSomething()` vengono eseguiti prima `DerivedType`dell'esecuzione del costruttore.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Questo esempio produce il seguente output:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```