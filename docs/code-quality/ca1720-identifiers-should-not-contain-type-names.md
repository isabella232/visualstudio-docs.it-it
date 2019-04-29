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
ms.openlocfilehash: d0eb7cfeb2271b7ed01f59d4892987fb2ef72808
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546570"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Gli identificatori non devono contenere nomi di tipo

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Il nome di un parametro in un membro contiene il nome di un tipo di dati.

-oppure-

Il nome di un membro contiene un nome di tipo di dati specifico del linguaggio.

Per impostazione predefinita, questa regola cerca solo in membri visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

I nomi dei parametri e membri sono meglio utilizzati per comunicare il significato di to descriverne il tipo, il quale viene in genere fornito dagli strumenti di sviluppo. Per i nomi dei membri, se è necessario utilizzare un nome di tipo di dati, usare un nome indipendente dalla lingua anziché uno specifico del linguaggio. Ad esempio, invece del C# nome del tipo `int`, usare il nome del tipo dati indipendenti dal linguaggio `Int32`.

Ogni token discreti il nome del parametro o un membro viene confrontato con i seguenti nomi dei tipi di dati specifico del linguaggio in modo tra maiuscole e minuscole:

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

Inoltre, i nomi di parametro sono anche confrontati con i seguenti nomi dei tipi di dati indipendenti dal linguaggio in modo tra maiuscole e minuscole:

- Object
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
- Ptr
- Puntatore
- UInptr
- UPtr
- UPointer
- Single
- Double
- Decimale
- GUID

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

**Se viene generato con un parametro:**

Sostituire l'identificatore del tipo di dati del nome del parametro con un termine che meglio descrive il significato o un termine più generico, ad esempio 'value'.

**Se generato da un membro:**

Sostituire l'identificatore del tipo di dati specifico del linguaggio il nome del membro con un termine che meglio descrive il significato, un equivalente indipendente dal linguaggio o un termine più generico, ad esempio 'value'.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Uso occasionale di nomi di parametri e membri in base al tipo potrebbe essere appropriato. Tuttavia, per i nuovi sviluppi, nessun noti verificarsi gli scenari in cui si deve eliminare un avviso da questa regola. Per le librerie fornite in precedenza, potrebbe essere necessario eliminare un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1720.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regole correlate

- [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Gli identificatori devono differenziarsi minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)