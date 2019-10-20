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
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660240"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Nelle versioni 1,0 e 1,1 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], un metodo pubblico o protetto contiene un `try` / `catch` / blocco `finally`. Il blocco `finally` sembra ripristinare lo stato di sicurezza e non è racchiuso in un blocco `finally`.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola consente di individuare `try` / blocchi `finally` nel codice destinato alle versioni 1,0 e 1,1 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che potrebbero essere vulnerabili a filtri di eccezioni dannosi presenti nello stack di chiamate. Se si verificano operazioni sensibili come la rappresentazione nel blocco try e viene generata un'eccezione, il filtro può essere eseguito prima del blocco `finally`. Per l'esempio di rappresentazione, questo significa che il filtro verrebbe eseguito come utente rappresentato. I filtri sono attualmente implementabili solo in Visual Basic.

> [!WARNING]
> Nelle versioni 2,0 e successive del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], il Runtime protegge automaticamente un `try` / `catch` /  `finally` da filtri eccezioni dannosi, se la reimpostazione viene eseguita direttamente all'interno del metodo che contiene il blocco di eccezioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Inserire il `try` di cui è stato eseguito il incapsulamento / `finally` in un blocco try esterno. Vedere il secondo esempio riportato di seguito. In questo modo si impone l'esecuzione di `finally` prima di filtrare il codice.

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
