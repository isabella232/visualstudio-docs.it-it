---
title: 'CA2124: eseguire il wrapping delle clausole finally vulnerabili in un try esterno | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544300"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Nelle versioni 1,0 e 1,1 di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , un metodo pubblico o protetto contiene un `try` / `catch` / `finally` blocco. Il `finally` blocco sembra reimpostare lo stato di sicurezza e non è racchiuso in un `finally` blocco.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola individua `try` / `finally` i blocchi nel codice che ha come destinazione le versioni 1,0 e 1,1 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che potrebbero essere vulnerabili a filtri di eccezioni dannosi presenti nello stack di chiamate. Se si verificano operazioni sensibili come la rappresentazione nel blocco try e viene generata un'eccezione, il filtro può essere eseguito prima del `finally` blocco. Per l'esempio di rappresentazione, questo significa che il filtro verrebbe eseguito come utente rappresentato. I filtri sono attualmente implementabili solo in Visual Basic.

> [!WARNING]
> Nelle versioni 2,0 e successive di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , il Runtime protegge automaticamente un `try` / `catch` /  `finally` blocco da filtri eccezioni dannosi, se la reimpostazione viene eseguita direttamente all'interno del metodo che contiene il blocco di eccezioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Posizionare l'oggetto di cui è stato eseguito il wrapper `try` / `finally` in un blocco try esterno. Vedere il secondo esempio riportato di seguito. In questo modo l'oggetto verrà forzato `finally` prima dell'esecuzione del codice del filtro.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudocodice

### <a name="description"></a>Descrizione
 Lo pseudocodice seguente illustra il modello rilevato da questa regola.

### <a name="code"></a>Codice

```
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

## <a name="example"></a>Esempio
 Lo pseudo codice seguente mostra il modello che è possibile usare per proteggere il codice e soddisfare questa regola.

```
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
