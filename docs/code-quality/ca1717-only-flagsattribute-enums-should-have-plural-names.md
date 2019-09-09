---
title: 'CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d760802422773b3713fa7ea08ce0ce7a191f418
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547125"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Il nome di un'enumerazione termina con una parola plurale e l'enumerazione non è contrassegnata <xref:System.FlagsAttribute?displayProperty=fullName> con l'attributo.

Per impostazione predefinita, questa regola esamina solo le enumerazioni visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Le convenzioni di denominazione stabiliscono che un nome plurale per un'enumerazione indica che è possibile specificare contemporaneamente più di un valore dell'enumerazione. <xref:System.FlagsAttribute> Indica ai compilatori che l'enumerazione deve essere trattata come un campo di bit che consente operazioni bit per bit sull'enumerazione.

Se è possibile specificare un solo valore di un'enumerazione alla volta, il nome dell'enumerazione deve essere una parola singolare. Ad esempio, un'enumerazione che definisce i giorni della settimana può essere usata in un'applicazione in cui è possibile specificare più giorni. Questa enumerazione deve avere <xref:System.FlagsAttribute> e potrebbe essere chiamata ' Days '. Un'enumerazione simile che consente di specificare solo un singolo giorno non avrà l'attributo e potrebbe essere chiamata ' Day '.

Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce il tempo necessario per apprendere una nuova raccolta software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Rendere il nome dell'enumerazione una parola singolare o aggiungere <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso dalla regola se il nome termina con una parola singolare.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1717.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regole correlate

- [CA1714 I flag enum devono avere nomi plurali](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Progettazione enum](/dotnet/standard/design-guidelines/enum)