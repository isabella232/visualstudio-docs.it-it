---
title: 'CA2208: Creare istanze di eccezioni di argomento correttamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231641"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Creare istanze di eccezioni di argomento correttamente

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Tra le cause possibili sono incluse le situazioni seguenti:

- Viene eseguita una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione che è o deriva da <xref:System.ArgumentException>.

- Un argomento stringa errato viene passato a un costruttore con parametri di un tipo di eccezione che è o deriva da <xref:System.ArgumentException>.

## <a name="rule-description"></a>Descrizione della regola

Anziché chiamare il costruttore predefinito, chiamare uno degli overload del costruttore che consente di fornire un messaggio di eccezione più significativo. Il messaggio di eccezione deve avere come destinazione lo sviluppatore e spiegare chiaramente la condizione di errore e come correggere o evitare l'eccezione.

Le firme di uno e due costruttori di stringa di e <xref:System.ArgumentException> dei relativi tipi derivati non sono coerenti rispetto alla posizione `message` e `paramName` ai parametri. Assicurarsi che questi costruttori vengano chiamati con gli argomenti stringa corretti. Le firme sono le seguenti:

- <xref:System.ArgumentException>(stringa `message`)
- <xref:System.ArgumentException>(String `message`, String `paramName`)
- <xref:System.ArgumentNullException>(stringa `paramName`)
- <xref:System.ArgumentNullException>(String `paramName`, String `message`)
- <xref:System.ArgumentOutOfRangeException>(stringa `paramName`)
- <xref:System.ArgumentOutOfRangeException>(String `paramName`, String `message`)
- <xref:System.DuplicateWaitObjectException>(stringa `parameterName`)
- <xref:System.DuplicateWaitObjectException>(String `parameterName`, String `message`)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare un costruttore che accetta un messaggio, un nome di parametro o entrambi e verificare che gli argomenti siano appropriati per il tipo di <xref:System.ArgumentException> chiamata.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola solo se un costruttore con parametri viene chiamato con gli argomenti stringa corretti.

## <a name="example"></a>Esempio

Il codice seguente illustra un costruttore che crea erroneamente un'istanza di <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Il codice seguente corregge la violazione precedente cambiando gli argomenti del costruttore.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1507: Usare NameOf al posto della stringa](ca1507.md)