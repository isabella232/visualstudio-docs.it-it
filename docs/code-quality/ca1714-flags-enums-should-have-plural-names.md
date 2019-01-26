---
title: 'CA1714: Le enumerazioni con Flags devono avere nomi plurali'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: eb6bcfb7684c27104801ec54839b3fc6598cc850
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971351"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Le enumerazioni con Flags devono avere nomi plurali

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un'enumerazione pubblica dispone di <xref:System.FlagsAttribute?displayProperty=fullName> e il nome non può finire in'.

## <a name="rule-description"></a>Descrizione della regola
 Tipi contrassegnati con <xref:System.FlagsAttribute> avere nomi plurali perché l'attributo indica che è possibile specificare più valori. Ad esempio, un'enumerazione che definisce i giorni della settimana potrebbe essere destinata all'uso in un'applicazione in cui è possibile specificare più giorni. Questa enumerazione deve avere il <xref:System.FlagsAttribute> e potrebbe essere denominata "Days". Un'enumerazione simile che consenta solo un singolo giorno specificare non include l'attributo e può essere chiamato 'Day'.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Cambiare il nome dell'enumerazione di una parola plurale oppure rimuovere il <xref:System.FlagsAttribute> attributo se non è possibile specificare più valori di enumerazione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare una violazione, se il nome è una parola plurale, ma non termina del '. Ad esempio, se l'enumerazione di più giorni che è stato descritto in precedenza erano denominata "DaysOfTheWeek", questa violerebbe la logica della regola, ma non lo scopo. Tali violazioni devono essere eliminate.

## <a name="related-rules"></a>Regole correlate
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Progettazione di enum](/dotnet/standard/design-guidelines/enum)