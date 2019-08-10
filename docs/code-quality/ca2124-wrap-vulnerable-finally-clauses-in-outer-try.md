---
title: 'CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno'
ms.date: 11/04/2016
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
ms.openlocfilehash: c75c7c240f694b18caacefc0f9b1ee07f54faf36
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920797"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
Nelle versioni 1,0 e 1,1 del .NET Framework, un metodo pubblico o protetto `try` contiene un / `catch` / `finally` blocco. Il `finally` blocco sembra reimpostare lo stato di sicurezza e non è racchiuso in un `finally` blocco.

## <a name="rule-description"></a>Descrizione della regola
Questa regola individua `try` / i blocchi nel codice che ha come destinazione le versioni 1,0 e 1,1 del .NET Framework che potrebbero essere vulnerabili a filtri di eccezioni dannosi presenti nello stack di chiamate. `finally` Se si verificano operazioni sensibili come la rappresentazione nel blocco try e viene generata un'eccezione, il filtro può essere eseguito prima del `finally` blocco. Per l'esempio di rappresentazione, questo significa che il filtro verrebbe eseguito come utente rappresentato. I filtri sono attualmente implementabili solo in Visual Basic.

> [!NOTE]
> Nelle versioni 2,0 e successive del .NET Framework, il Runtime protegge `try` automaticamente un / `catch` /  `finally` blocco da filtri eccezioni dannosi, se la reimpostazione viene eseguita direttamente nel metodo che contiene il blocco Exception.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Posizionare l'oggetto di `try` cui è stato eseguito il wrapper / `finally` in un blocco try esterno. Vedere il secondo esempio riportato di seguito. In questo modo `finally` l'oggetto verrà forzato prima dell'esecuzione del codice del filtro.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudo-codice

### <a name="description"></a>DESCRIZIONE

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

Lo pseudo codice seguente mostra il modello che è possibile usare per proteggere il codice e soddisfare questa regola.

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