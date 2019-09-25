---
title: 'CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7203f7f287ebb5b71ecad6e6ad4a861d63e5cf08
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234224"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft.Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

I nomi di due tipi, membri, parametri o spazi dei nomi completi sono identici quando vengono convertiti in caratteri minuscoli.

Per impostazione predefinita, questa regola esamina solo i tipi, i membri e gli spazi dei nomi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole. Ad esempio, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] è un linguaggio molto diffuso senza distinzione tra maiuscole e minuscole.

Questa regola viene attivata solo sui membri visibili pubblicamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Consente di selezionare un nome univoco quando viene confrontato con altri identificatori senza distinzione tra maiuscole e minuscole.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. La libreria potrebbe non essere utilizzabile in tutte le lingue disponibili in .NET.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1708.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Esempio di violazione

Nell'esempio seguente viene illustrata una violazione di questa regola.

[!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)