---
title: 'CA1715: Gli identificatori devono contenere il prefisso corretto'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b794eb7c7a258a843763b2c68902000031c17eb3
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873604"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Gli identificatori devono contenere il prefisso corretto

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Category|Microsoft.Naming|
|Modifica importante|Rilievo - quando viene attivato sulle interfacce.<br /><br /> Non sostanziale - Quando si è generato su parametri di tipo generico.|

## <a name="cause"></a>Causa

Il nome di un'interfaccia non inizia con una "I" maiuscola.

-oppure-

Il nome di un [parametro di tipo generico](/dotnet/csharp/programming-guide/generics/generic-type-parameters) su un tipo o metodo non inizia con una maiuscola l ' '.

Per impostazione predefinita, questa regola cerca solo in interfacce visibili esternamente, i tipi e metodi, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Per convenzione, i nomi di determinati elementi di programmazione iniziano con un prefisso specifico.

I nomi di interfaccia devono iniziare con una lettera maiuscola 'I' seguito da un'altra lettera maiuscola. Questa regola segnala le violazioni per i nomi di interfaccia, ad esempio "MyInterface" e "IsolatedInterface".

I nomi dei parametri di tipo generico deve iniziare con una ' T' ' e, facoltativamente, può essere seguita da un'altra lettera maiuscola. Questa regola segnala le violazioni per i nomi dei parametri di tipo generico, ad esempio "V" e 'Type'.

Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti del codice questa regola analizza. Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Parametri di tipo carattere singolo

È possibile configurare se utilizzare o meno escluderà i parametri di tipo carattere singolo da questa regola. Ad esempio, per specificare che questa regola *non deve* analizzare i parametri di tipo carattere singolo, aggiungere una delle seguenti coppie chiave-valore in un file con estensione editorconfig nel progetto:

```
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Questa regola viene attivata mai di un parametro di tipo denominato `T`, ad esempio, `Collection<T>`.

### <a name="api-surface"></a>Superficie dell'API

È possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1715.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Rinominare l'identificatore in modo che in modo corretto viene aggiunto come prefisso.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="interface-naming-example"></a>Esempio di denominazione di interfaccia

Il frammento di codice seguente illustra un'interfaccia denominata in modo non corretto:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

Il frammento di codice seguente consente di risolvere la violazione precedente anteponendo l'interfaccia 'I':

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Esempio di denominazione parametro di tipo

Il frammento di codice seguente mostra un parametro di tipo generico denominato in modo non corretto:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

Il seguente frammento di codice corretta la violazione precedente aggiungendo il parametro di tipo generico con l ' ':

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1722: Gli identificatori non devono contenere il prefisso non corretto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)