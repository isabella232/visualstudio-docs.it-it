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
ms.openlocfilehash: 92b74bcf587492155445c500252ea10773a5978b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547809"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Contrassegnare le enumerazioni con FlagsAttribute

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft.Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa

I valori di un'enumerazione sono potenze di due o sono combinazioni di altri valori definiti nell'enumerazione e l' <xref:System.FlagsAttribute?displayProperty=fullName> attributo non è presente. Per ridurre i falsi positivi, questa regola non segnala una violazione per le enumerazioni con valori contigui.

Per impostazione predefinita, questa regola esamina solo le enumerazioni pubbliche, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Applicare <xref:System.FlagsAttribute> a un'enumerazione quando le costanti denominate possono essere combinate in modo significativo. Si consideri, ad esempio, un'enumerazione dei giorni della settimana in un'applicazione che tiene traccia delle risorse del giorno disponibili. Se la disponibilità di ogni risorsa è codificata usando l'enumerazione <xref:System.FlagsAttribute> presente, è possibile rappresentare qualsiasi combinazione di giorni. Senza l'attributo, è possibile rappresentare solo un giorno della settimana.

Per i campi che archiviano enumerazioni combinabili, i singoli valori di enumerazione vengono considerati come gruppi di bit nel campo. Pertanto, tali campi vengono talvolta definiti campi di *bit*. Per combinare i valori di enumerazione per l'archiviazione in un campo di bit, usare gli operatori condizionali booleani. Per testare un campo di bit per determinare se è presente un valore di enumerazione specifico, usare gli operatori logici booleani. Affinché un campo di bit memorizzi e recuperi correttamente i valori di enumerazione combinati, ogni valore definito nell'enumerazione deve essere una potenza di due. A meno che non sia così, gli operatori logici booleani non saranno in grado di estrarre i singoli valori di enumerazione archiviati nel campo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere <xref:System.FlagsAttribute> all'enumerazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola se non si desidera che i valori di enumerazione siano combinabili.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente, `DaysEnumNeedsFlags` è un'enumerazione che soddisfa i requisiti per l'utilizzo <xref:System.FlagsAttribute> di ma non lo è. L' `ColorEnumShouldNotHaveFlag` enumerazione non contiene valori che sono potenze di due, ma specifica <xref:System.FlagsAttribute>in modo errato. Questo viola la regola [CA2217: Non contrassegnare le enumerazioni con](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)FlagsAttribute.

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA2217 Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.FlagsAttribute?displayProperty=fullName>