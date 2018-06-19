---
title: 'CA1714: Le enumerazioni con Flags devono avere nomi plurali'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e00c0e7eaf3b88588f0914d78a23db40082d63f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915731"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Le enumerazioni con Flags devono avere nomi plurali
|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un'enumerazione pubblica dispone di <xref:System.FlagsAttribute?displayProperty=fullName> e il nome non termina in'.

## <a name="rule-description"></a>Descrizione della regola
 Tipi contrassegnati con <xref:System.FlagsAttribute> sono assegnati nomi plurali perché tale attributo indica che è possibile specificare più di un valore. Ad esempio, un'enumerazione che definisce i giorni della settimana potrebbe essere deve essere utilizzato in un'applicazione in cui è possibile specificare più giorni. Questa enumerazione dovrà contenere il <xref:System.FlagsAttribute> e potrebbe essere denominata "Days". Un'enumerazione simile che consente un solo giorno specificare l'attributo non è necessario e potrebbe essere chiamato 'Day'.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Specificare il nome dell'enumerazione di una parola plurale o rimuovere il <xref:System.FlagsAttribute> attributo se non è possibile specificare più valori di enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile se il nome è una parola plurale ma non termina con l'esclusione di una violazione del '. L'enumerazione di più giorni descritto in precedenza erano denominata "DaysOfTheWeek", ad esempio, verrebbe violata la logica della regola, ma non lo scopo. Tali violazioni devono essere escluse.

## <a name="related-rules"></a>Regole correlate
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName> [Progettazione di enum](/dotnet/standard/design-guidelines/enum)