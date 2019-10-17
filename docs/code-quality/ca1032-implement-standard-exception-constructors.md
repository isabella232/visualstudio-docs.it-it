---
title: 'CA1032: Implementare costruttori di eccezioni standard'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a73a615c08b538f4580a8d40765dcd7603722aa1
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446714"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementare costruttori di eccezioni standard

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft. Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo estende <xref:System.Exception?displayProperty=fullName> ma non dichiara tutti i costruttori richiesti.

## <a name="rule-description"></a>Descrizione della regola

I tipi di eccezione devono implementare i tre costruttori seguenti:

- public NewException ()

- public NewException (String)

- public NewException (stringa, eccezione)

Inoltre, se si esegue l'analisi FxCop legacy invece degli [analizzatori FxCop basati su .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md), anche l'assenza di un quarto costruttore genera una violazione:

- NewException protected o private (SerializationInfo, StreamingContext)

Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni. Il costruttore con la firma `NewException(string, Exception)`, ad esempio, viene utilizzato per creare eccezioni causate da altre eccezioni. Senza questo costruttore non è possibile creare e generare un'istanza dell'eccezione personalizzata che contiene un'eccezione interna (annidata), ovvero il codice gestito che deve essere eseguita in una situazione di questo tipo.

I primi tre costruttori di eccezioni sono pubblici per convenzione. Il quarto costruttore è protetto in classi non sealed e privato in classi sealed. Per altre informazioni, vedere [CA2229: implementare costruttori di serializzazione](../code-quality/ca2229.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere i costruttori mancanti all'eccezione e verificare che dispongano dell'accessibilità corretta.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola quando la violazione è causata dall'uso di un livello di accesso diverso per i costruttori pubblici. Inoltre, è possibile disattivare l'avviso per il costruttore `NewException(SerializationInfo, StreamingContext)` se si compila una libreria di classi portabile (PCL).

## <a name="example"></a>Esempio

Nell'esempio seguente è contenuto un tipo di eccezione che viola questa regola e un tipo di eccezione implementato correttamente.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Vedere anche

[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229.md)
