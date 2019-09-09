---
title: 'CA1043: Usare un argomento di tipo stringa o integrale per gli indicizzatori'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: aeec6e202ccb7f3075b04d29bdef7d171ae545f7
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547682"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Usare un argomento di tipo stringa o integrale per gli indicizzatori

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo contiene un indicizzatore che usa un tipo di indice diverso <xref:System.Int32?displayProperty=fullName>da <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, o <xref:System.String?displayProperty=fullName>.

Per impostazione predefinita, questa regola esamina solo i tipi pubblici e protetti, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare tipi Integer o stringa per l'indice. Questi tipi vengono in genere utilizzati per l'indicizzazione di strutture di dati e aumentano l'usabilità della libreria. L' <xref:System.Object> uso del tipo deve essere limitato ai casi in cui non è possibile specificare il tipo di stringa o Integer specifico in fase di progettazione. Se la progettazione richiede altri tipi per l'indice, riconsiderare se il tipo rappresenta un archivio dati logico. Se non rappresenta un archivio dati logico, utilizzare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare l'indice in un tipo Integer o stringa oppure utilizzare un metodo anziché l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola solo dopo aver valutato attentamente la necessità dell'indicizzatore non standard.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1043.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un indicizzatore che utilizza <xref:System.Int32> un indice.

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1023: Gli indicizzatori non devono essere multidimensionali](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024: Usare le proprietà laddove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)