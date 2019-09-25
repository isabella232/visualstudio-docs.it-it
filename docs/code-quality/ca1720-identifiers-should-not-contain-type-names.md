---
title: 'CA1720: Gli identificatori non devono contenere nomi di tipo'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2677c2ef5342b795bb684f3ab06bc7cf5195cf7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233891"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Gli identificatori non devono contenere nomi di tipo

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Il nome di un parametro in un membro contiene un nome di tipo di dati.

-oppure-

Il nome di un membro contiene un nome di tipo di dati specifico del linguaggio.

Per impostazione predefinita, questa regola esamina solo i membri visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

I nomi di parametri e membri sono più utilizzati per comunicare il significato rispetto alla descrizione del tipo, che dovrebbe essere fornito dagli strumenti di sviluppo. Per i nomi dei membri, se è necessario usare un nome di tipo di dati, usare un nome indipendente dal linguaggio anziché un nome specifico della lingua. Ad esempio, anziché il C# nome `int`del tipo, utilizzare il nome del tipo di `Int32`dati indipendente dal linguaggio.

Ogni token discreto nel nome del parametro o del membro viene verificato rispetto ai nomi dei tipi di dati specifici del linguaggio seguenti in modo non sensibile alla distinzione tra maiuscole e minuscole:

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

Inoltre, i nomi di un parametro vengono controllati in base ai nomi dei tipi di dati indipendenti dal linguaggio seguenti senza distinzione tra maiuscole e minuscole:

- Object
- obj
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

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

L'utilizzo occasionale dei nomi di parametro e di membro basati sul tipo potrebbe essere appropriato. Per il nuovo sviluppo, tuttavia, non si verificano scenari noti in cui è necessario eliminare un avviso da questa regola. Per le librerie fornite in precedenza, potrebbe essere necessario eliminare un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regole correlate

- [CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 Gli identificatori devono differire più di case](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719 I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)