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
ms.openlocfilehash: 3d47b39208fce297fd058d6976b9fa7d7593cb9a
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867151"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Usare un argomento di tipo stringa o integrale per gli indicizzatori

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo contiene un indicizzatore che usa un tipo di indice diverso da <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, o <xref:System.String?displayProperty=fullName>.

Per impostazione predefinita, questa regola considerati solo i tipi pubblici e protetti, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Gli indicizzatori, ovvero, le proprietà indicizzate, devono utilizzare tipi integer o stringa per l'indice. Questi tipi vengono generalmente usati per indicizzare strutture di dati e aumentano l'usabilità della libreria. Usare il <xref:System.Object> tipo deve essere limitato ai casi in cui non è possibile specificare il tipo specifico di tipo integer o stringa in fase di progettazione. Se la struttura richiede altri tipi per l'indice, verificare che il tipo rappresenta un archivio dati logici. Se non rappresenta un archivio dati logici, utilizzare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare l'indice in un tipo integer o stringa o usare un metodo invece l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare un avviso da questa regola solo dopo aver considerato con attenzione la necessità per l'indicizzatore non standard.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1043.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra un indicizzatore che usa un <xref:System.Int32> indice.

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1023: Gli indicizzatori non devono essere multidimensionali](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)