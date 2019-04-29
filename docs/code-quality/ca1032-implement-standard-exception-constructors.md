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
ms.openlocfilehash: 7baf13eb9125b273ad8fb1265a65eb7b053238a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779124"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementare costruttori di eccezioni standard

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Estende un tipo <xref:System.Exception?displayProperty=fullName> ma non si dichiara tutti i costruttori necessari.

## <a name="rule-description"></a>Descrizione della regola

Tipi di eccezione devono implementare i tre costruttori seguenti:

- NewException() pubblico

- NewException(string) pubblico

- pubblica NewException (string, eccezione)

Inoltre, se si esegue l'analisi statica del codice di FxCop legacy come anziché [analizzatori basati su Roslyn FxCop](../code-quality/roslyn-analyzers-overview.md), l'assenza di un quarto costruttore genera anche una violazione:

- NewException protetti o privati (SerializationInfo, StreamingContext)

Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni. Ad esempio, il costruttore con la firma `NewException(string, Exception)` viene usato per creare le eccezioni sono causate da altri tipi di eccezioni. Senza questo costruttore, è possibile creare e generare un'istanza di eccezione personalizzata contenente un'eccezione (annidata) interna, è necessario eseguire l'operazione per il codice gestito in tale situazione.

I primi tre costruttori di eccezioni sono pubblici per convenzione. Il quarto costruttore è protetto nelle classi unsealed e private in classi sealed. Per altre informazioni, vedere [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere i costruttori mancanti per l'eccezione e assicurarsi che abbiano l'accessibilità corretto.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola quando la violazione è causata dall'utilizzo di un livello di accesso diversi per i costruttori pubblici. Inoltre, è possibile eliminare l'avviso per il `NewException(SerializationInfo, StreamingContext)` costruttore se si sta creando una libreria di classi portabile (PCL).

## <a name="example"></a>Esempio

Nell'esempio seguente contiene un tipo di eccezione che violano questa regola e un tipo di eccezione che viene implementato in modo corretto.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Vedere anche

[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)