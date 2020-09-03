---
title: 'CA1032: implementare costruttori di eccezioni standard | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542285"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementare costruttori di eccezioni standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo estende <xref:System.Exception?displayProperty=fullName> e non dichiara tutti i costruttori richiesti.

## <a name="rule-description"></a>Descrizione della regola
 I tipi di eccezione devono implementare i costruttori seguenti:

- public NewException ()

- public NewException (String)

- public NewException (stringa, eccezione)

- NewException protected o private (SerializationInfo, StreamingContext)

  Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni. Il costruttore con la firma, ad esempio, `NewException(string, Exception)` viene utilizzato per creare eccezioni causate da altre eccezioni. Senza questo costruttore non è possibile creare e generare un'istanza dell'eccezione personalizzata che contiene un'eccezione interna (annidata), ovvero il codice gestito che deve essere eseguita in una situazione di questo tipo. I primi tre costruttori di eccezioni sono pubblici per convenzione. Il quarto costruttore è protetto in classi non sealed e privato in classi sealed. Per altre informazioni, vedere [CA2229: implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere i costruttori mancanti all'eccezione e verificare che dispongano dell'accessibilità corretta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la violazione è causata dall'uso di un livello di accesso diverso per i costruttori pubblici.

## <a name="example"></a>Esempio
 Nell'esempio seguente è contenuto un tipo di eccezione che viola questa regola e un tipo di eccezione implementato correttamente.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
