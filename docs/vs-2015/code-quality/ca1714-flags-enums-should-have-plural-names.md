---
title: 'CA1714: Le enumerazioni con Flags devono avere nomi plurali | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cbc6019b3ead7d65ad4b9cdb7e389cd4d22d75e1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235144"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Le enumerazioni con Flags devono avere nomi plurali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare una violazione, se il nome è una parola plurale, ma non termina del '. Ad esempio, se l'enumerazione di più giorni che è stato descritto in precedenza erano denominata "DaysOfTheWeek", questa violerebbe la logica della regola, ma non lo scopo. Le violazioni di questo tipo devono essere escluse.

## <a name="related-rules"></a>Regole correlate
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName> [Progettazione di enum](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)



