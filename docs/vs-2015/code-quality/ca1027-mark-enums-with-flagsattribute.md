---
title: 'CA1027: contrassegnare le enumerazioni con FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 774279dd05bd14c34df7f1d450f00599812d6a5b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544508"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Contrassegnare le enumerazioni con FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 I valori di un'enumerazione pubblica sono le potenze di due o sono combinazioni di altri valori definiti nell'enumerazione e l' <xref:System.FlagsAttribute?displayProperty=fullName> attributo non è presente. Per ridurre i falsi positivi, questa regola non segnala una violazione per le enumerazioni con valori contigui.

## <a name="rule-description"></a>Descrizione della regola
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Applicare <xref:System.FlagsAttribute> a un'enumerazione quando le costanti denominate possono essere combinate in modo significativo. Si consideri, ad esempio, un'enumerazione dei giorni della settimana in un'applicazione che tiene traccia delle risorse del giorno disponibili. Se la disponibilità di ogni risorsa è codificata usando l'enumerazione <xref:System.FlagsAttribute> presente, è possibile rappresentare qualsiasi combinazione di giorni. Senza l'attributo, è possibile rappresentare solo un giorno della settimana.

 Per i campi che archiviano enumerazioni combinabili, i singoli valori di enumerazione vengono considerati come gruppi di bit nel campo. Pertanto, tali campi vengono talvolta definiti campi di *bit*. Per combinare i valori di enumerazione per l'archiviazione in un campo di bit, usare gli operatori condizionali booleani. Per testare un campo di bit per determinare se è presente un valore di enumerazione specifico, usare gli operatori logici booleani. Affinché un campo di bit memorizzi e recuperi correttamente i valori di enumerazione combinati, ogni valore definito nell'enumerazione deve essere una potenza di due. A meno che non sia così, gli operatori logici booleani non saranno in grado di estrarre i singoli valori di enumerazione archiviati nel campo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere <xref:System.FlagsAttribute> all'enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se non si desidera che i valori di enumerazione siano combinabili.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `DaysEnumNeedsFlags` è un'enumerazione che soddisfa i requisiti per l'utilizzo di <xref:System.FlagsAttribute> , ma non lo dispone. L' `ColorEnumShouldNotHaveFlag` enumerazione non contiene valori che sono potenze di due, ma specifica in modo errato <xref:System.FlagsAttribute> . Questo viola la regola [CA2217: non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName>
