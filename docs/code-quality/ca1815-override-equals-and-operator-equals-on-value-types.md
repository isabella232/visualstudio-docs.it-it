---
title: "CA1815: Eseguire l'override di Equals e dell'operatore \"uguale a\" sui tipi di valore"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c4cf84a292e11b20eb37bee562cd039096e56af
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873425"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un tipo di valore non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName> o non implementa l'operatore di uguaglianza (= =). Questa regola non verifica le enumerazioni.

Per impostazione predefinita, questa regola cerca solo tipi visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Per i tipi di valore, l'implementazione ereditata di <xref:System.Object.Equals%2A> Usa la libreria Reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti per confrontare o ordinare le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare <xref:System.Object.Equals%2A>. Se il linguaggio di programmazione in uso supporta l'overload degli operatori, è necessario specificare anche un'implementazione degli operatori di uguaglianza e disuguaglianza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.Equals%2A>. Se possibile, implementare l'operatore di uguaglianza.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se le istanze del tipo di valore non verranno confrontate tra loro.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1815.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (prestazioni). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Il codice seguente illustra una struttura (tipo di valore) che violano questa regola:

[!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

Il codice seguente consente di correggere la violazione precedente eseguendo l'override <xref:System.ValueType.Equals%2A?displayProperty=fullName> e l'implementazione degli operatori di uguaglianza (= =,! =):

[!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA2224: Override di equals all'overload dell'operatore è uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
- [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Object.Equals%2A?displayProperty=fullName>