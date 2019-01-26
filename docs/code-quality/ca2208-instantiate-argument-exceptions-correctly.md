---
title: 'CA2208: Creare istanze di eccezioni di argomento correttamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 8ef4e23f0200f17c0f6d59789538352d9e1676ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980180"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Creare istanze di eccezioni di argomento correttamente

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Cause possibili includono le situazioni seguenti:

- Viene eseguita una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione, o che deriva da <xref:System.ArgumentException>.

- Un argomento stringa non corretto viene passato a un costruttore con parametri di un tipo di eccezione, o che deriva da <xref:System.ArgumentException>.

## <a name="rule-description"></a>Descrizione della regola

Invece di chiamare il costruttore predefinito, chiamare uno degli overload del costruttore che consente a un messaggio di eccezione più significativo da fornire. Il messaggio di eccezione deve lo sviluppatore di destinazione e spiegano chiaramente la condizione di errore e su come risolvere o evitare l'eccezione.

Le firme dei costruttori della stringa una e due <xref:System.ArgumentException> e i tipi derivati non sono coerenti con il `message` e `paramName` parametri. Assicurarsi che questi costruttori vengono chiamati con gli argomenti stringa corretta. Le firme sono come segue:

 <xref:System.ArgumentException>(stringa `message`)

 <xref:System.ArgumentException>(string `message`, stringa `paramName`)

 <xref:System.ArgumentNullException>(stringa `paramName`)

 <xref:System.ArgumentNullException>(string `paramName`, stringa `message`)

 <xref:System.ArgumentOutOfRangeException>(stringa `paramName`)

 <xref:System.ArgumentOutOfRangeException>(string `paramName`, stringa `message`)

 <xref:System.DuplicateWaitObjectException>(stringa `parameterName`)

 <xref:System.DuplicateWaitObjectException>(string `parameterName`, stringa `message`)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare un costruttore che accetta un messaggio, un nome di parametro o entrambi e assicurarsi che gli argomenti sono appropriati per il tipo di <xref:System.ArgumentException> chiamato.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola solo se un costruttore con parametri viene chiamato con gli argomenti stringa corretta.

## <a name="example-1"></a>Esempio 1
 Nell'esempio seguente illustra un costruttore che crea un'istanza in modo non corretto di un'istanza del tipo di eccezione ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example-2"></a>Esempio 2
 Nell'esempio seguente consente di correggere la violazione precedente passando gli argomenti del costruttore.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]