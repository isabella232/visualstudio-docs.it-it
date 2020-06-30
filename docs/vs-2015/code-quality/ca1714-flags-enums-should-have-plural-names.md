---
title: 'CA1714: le enumerazioni con Flags devono avere nomi plurali | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 74e93a9644f365120117bd247d2ea8b9d43608cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548187"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Le enumerazioni con Flags devono avere nomi plurali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un'enumerazione pubblica ha <xref:System.FlagsAttribute?displayProperty=fullName> e il nome non termina con ' s'.

## <a name="rule-description"></a>Descrizione della regola
 I tipi contrassegnati con <xref:System.FlagsAttribute> hanno nomi plurali perché l'attributo indica che è possibile specificare più di un valore. Ad esempio, un'enumerazione che definisce i giorni della settimana può essere usata in un'applicazione in cui è possibile specificare più giorni. Questa enumerazione deve avere <xref:System.FlagsAttribute> e potrebbe essere chiamata ' Days '. Un'enumerazione simile che consente di specificare solo un singolo giorno non avrà l'attributo e potrebbe essere chiamata ' Day '.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rendere il nome dell'enumerazione una parola plurale oppure rimuovere l' <xref:System.FlagsAttribute> attributo se non devono essere specificati contemporaneamente più valori di enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile evitare una violazione se il nome è una parola plurale ma non termina con ' s'. Se, ad esempio, l'enumerazione di più giorni descritta in precedenza era denominata ' DaysOfTheWeek ', ciò violerebbe la logica della regola, ma non l'intento. Tali violazioni devono essere evitate.

## <a name="related-rules"></a>Regole correlate
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName>[Progettazione enum](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
