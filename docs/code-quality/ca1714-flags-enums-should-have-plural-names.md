---
title: 'CA1714: Le enumerazioni con Flags devono avere nomi plurali'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a1532b67fdaeb2a44663db77cfc8a1056004e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546173"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Le enumerazioni con Flags devono avere nomi plurali

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

È un'enumerazione di <xref:System.FlagsAttribute?displayProperty=fullName> e il nome non può finire in'.

Per impostazione predefinita, questa regola solo esamina le enumerazioni visibile esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Tipi contrassegnati con <xref:System.FlagsAttribute> avere nomi plurali perché l'attributo indica che è possibile specificare più valori. Ad esempio, un'enumerazione che definisce i giorni della settimana potrebbe essere destinata all'uso in un'applicazione in cui è possibile specificare più giorni. Questa enumerazione deve avere il <xref:System.FlagsAttribute> e potrebbe essere denominata "Days". Un'enumerazione simile che consenta solo un singolo giorno specificare non include l'attributo e può essere chiamato 'Day'.

Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Cambiare il nome dell'enumerazione di una parola plurale oppure rimuovere il <xref:System.FlagsAttribute> attributo se non è possibile specificare più valori di enumerazione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare una violazione, se il nome è una parola plurale, ma non termina del '. Ad esempio, se l'enumerazione di più giorni che è stato descritto in precedenza erano denominata "DaysOfTheWeek", questa violerebbe la logica della regola, ma non lo scopo. Tali violazioni devono essere eliminate.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1714.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regole correlate

- [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Progettazione di enum](/dotnet/standard/design-guidelines/enum)