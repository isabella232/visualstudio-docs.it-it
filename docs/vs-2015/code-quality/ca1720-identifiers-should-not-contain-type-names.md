---
title: 'CA1720: gli identificatori non devono contenere nomi di tipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34ebe4848bbbe49b9a67449795f0aea7d104af8b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671633"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Gli identificatori non devono contenere nomi di tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un parametro in un membro visibile esternamente contiene un nome di tipo di dati.

 oppure

 Il nome di un membro visibile esternamente contiene un nome di tipo di dati specifico del linguaggio.

## <a name="rule-description"></a>Descrizione della regola
 I nomi di parametri e membri sono più utilizzati per comunicare il significato rispetto alla descrizione del tipo, che dovrebbe essere fornito dagli strumenti di sviluppo. Per i nomi dei membri, se è necessario usare un nome di tipo di dati, usare un nome indipendente dal linguaggio anziché un nome specifico della lingua. Ad esempio, anziché il C# nome del tipo ' int ', utilizzare il nome del tipo di dati indipendente dal linguaggio, Int32.

 Ogni token discreto nel nome del parametro o del membro viene verificato rispetto ai nomi dei tipi di dati specifici del linguaggio seguenti, senza distinzione tra maiuscole e minuscole:

- Bool

- WChar

- Int8

- UInt8

- Short

- UShort

- Int

- UInt

- Integer

- UInteger

- Long

- ULong

- Senza segno

- Firmato

- Float

- Float32

- Float64

  Inoltre, i nomi di un parametro vengono controllati in base ai nomi dei tipi di dati indipendenti dal linguaggio seguenti, senza distinzione tra maiuscole e minuscole:

- Oggetto

- Obj

- Booleano

- Char

- Stringa

- SByte

- Byte

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- PTR

- Puntatore

- UInptr

- UPtr

- UPointer

- Single

- Double

- Decimale

- GUID

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 **Se generato in base a un parametro:**

 Sostituire l'identificatore del tipo di dati nel nome del parametro con un termine che ne descriva meglio il significato o un termine più generico, ad esempio ' value '.

 **Se attivato per un membro:**

 Sostituire l'identificatore del tipo di dati specifico del linguaggio nel nome del membro con un termine che ne descriva meglio il significato, un equivalente indipendente dal linguaggio o un termine più generico, ad esempio ' value '.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 L'utilizzo occasionale dei nomi di parametro e di membro basati sul tipo potrebbe essere appropriato. Per il nuovo sviluppo, tuttavia, non si verificano scenari noti in cui è necessario eliminare un avviso da questa regola. Per le librerie con spedizioni precedenti, potrebbe essere necessario eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
