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
ms.openlocfilehash: a59346cb70269d4d2b405279fc9ea5573a879b1e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547015"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Non chiamare metodi sottoponibili a override nei costruttori

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Il costruttore di un tipo non sealed chiama un metodo virtuale definito nella relativa classe.

## <a name="rule-description"></a>Descrizione della regola

Quando viene chiamato un metodo virtuale, il tipo effettivo che esegue il metodo non viene selezionato fino alla fase di esecuzione. Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non sia stato eseguito.

> [!NOTE]
> L'implementazione dell'analisi legacy di questa regola ha un messaggio di diagnostica diverso**di "\[nome Costruttore] contiene una catena di chiamate che genera una chiamata a un metodo virtuale definito dalla classe. Esaminare lo stack di chiamate seguente per le conseguenze**impreviste ". L'implementazione degli [analizzatori FxCop](install-fxcop-analyzers.md) di questa regola presenta un messaggio di diagnostica di "non**chiamare metodi sottoponibili a override nei costruttori**".

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, non chiamare i metodi virtuali di un tipo all'interno dei costruttori del tipo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. Il costruttore deve essere riprogettato per eliminare la chiamata al metodo virtuale.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato l'effetto della violazione di questa regola. L'applicazione di test crea un'istanza `DerivedType`di, che determina l'esecuzione del`BadlyConstructedType`costruttore della classe di base (). `BadlyConstructedType`il costruttore di ' s chiama erroneamente il `DoSomething`metodo virtuale. Come illustrato nell'output, `DerivedType.DoSomething()` viene eseguito prima `DerivedType`dell'esecuzione del costruttore.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Questo esempio produce il seguente output:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```