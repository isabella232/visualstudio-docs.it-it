---
title: 'CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8773df5d309d72ef7e1a5298230b6cce63f23ee8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958836"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Nelle versioni 1.0 e 1.1 di .NET Framework, un metodo pubblico o protetto contiene un `try` / `catch` / `finally` blocco. Il `finally` blocco viene visualizzato per reimpostare lo stato di sicurezza e non è racchiuso un `finally` blocco.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola individua `try` / `finally` blocchi nel codice destinato alle versioni 1.0 e 1.1 di .NET Framework che potrebbero essere vulnerabili ai filtri eccezioni dannoso presenti nello stack di chiamate. Se vengono eseguite operazioni, ad esempio la rappresentazione nel blocco try e viene generata un'eccezione, il filtro può essere eseguito prima il `finally` blocco. Nell'esempio della rappresentazione, ciò significa che il filtro viene eseguito come utente rappresentato. I filtri sono attualmente è possibile implementare solo in Visual Basic.

> [!NOTE]
> Nelle versioni 2.0 e versioni successive di .NET Framework, il runtime protegge automaticamente un `try` / `catch` /  `finally` bloccare dai filtri eccezioni dannoso, se la reimpostazione si verifica direttamente all'interno del metodo che contiene il blocco di eccezioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Posizionare il wrapping `try` / `finally` in un blocco try esterno. Vedere il secondo esempio che segue. In tal modo il `finally` da eseguire prima del codice di filtro.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudocodice

### <a name="description"></a>Descrizione

Lo pseudocodice seguente illustra il modello rilevato da questa regola.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

Il pseudo-codice seguente viene illustrato il modello che è possibile usare per proteggere il codice e soddisfano questa regola.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```