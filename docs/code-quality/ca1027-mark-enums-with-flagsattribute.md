---
title: 'CA1027: Contrassegnare le enumerazioni con FlagsAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44973d1bb1cc7ddf16ca72635dd8b6543174fb0e
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867601"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Contrassegnare le enumerazioni con FlagsAttribute

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

I valori dell'enumerazione siano potenze di due o sono combinazioni di altri valori definiti nell'enumerazione, e il <xref:System.FlagsAttribute?displayProperty=fullName> attributo non è presente. Per ridurre i falsi positivi, questa regola non segnala una violazione per enumerazioni associate a valori contigui.

Per impostazione predefinita, questa regola cerca solo in enumerazioni pubbliche, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Applicare <xref:System.FlagsAttribute> a un'enumerazione quando le relative costanti denominate possono essere combinate. Si consideri, ad esempio, un'enumerazione dei giorni della settimana in un'applicazione che tiene traccia delle risorse del giorno in cui sono disponibili. Se la disponibilità di ogni risorsa viene codificata utilizzando l'enumerazione con <xref:System.FlagsAttribute> present, qualsiasi combinazione di giorni può essere rappresentato. Senza l'attributo può essere rappresentato un solo giorno della settimana.

Per i campi che archiviano le enumerazioni combinable, singoli valori di enumerazione sono considerati come gruppi di bit del campo. Di conseguenza, questi campi sono talvolta detti *campi di bit*. Per combinare i valori di enumerazione per l'archiviazione in un campo di bit, usare gli operatori booleani condizionali. Per testare un campo di bit per determinare se è presente un valore di enumerazione specifico, usare gli operatori logici booleani. Per un campo di bit archiviare e recuperare valori di enumerazione correttamente, ogni valore definito nell'enumerazione deve essere una potenza di due. In caso contrario, gli operatori logici booleani non sarà in grado di estrarre i singoli valori di enumerazione che sono archiviati nel campo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere <xref:System.FlagsAttribute> all'enumerazione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare un avviso da questa regola se non si desidera valori di enumerazione da combinabili.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1027.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio riportato di seguito `DaysEnumNeedsFlags` è un'enumerazione che soddisfi i requisiti per l'uso di <xref:System.FlagsAttribute> ma non è presente. Il `ColorEnumShouldNotHaveFlag` enumerazione non dispone di valori che sono potenze di due, ma specifica in modo non corretto <xref:System.FlagsAttribute>. Questa condizione viola regola [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.FlagsAttribute?displayProperty=fullName>