---
title: 'CA1717: solo le enumerazioni FlagsAttribute devono avere nomi plurali | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0c378d419be0d964c27cfcbe523fbe3a33da97b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669089"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un'enumerazione visibile esternamente termina con una parola plurale e l'enumerazione non è contrassegnata con l'attributo <xref:System.FlagsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Le convenzioni di denominazione stabiliscono che un nome plurale per un'enumerazione indica che è possibile specificare contemporaneamente più di un valore dell'enumerazione. Il <xref:System.FlagsAttribute> indica ai compilatori che l'enumerazione deve essere trattata come un campo di bit che consente operazioni bit per bit sull'enumerazione.

 Se è possibile specificare un solo valore di un'enumerazione alla volta, il nome dell'enumerazione deve essere una parola singolare. Ad esempio, un'enumerazione che definisce i giorni della settimana può essere usata in un'applicazione in cui è possibile specificare più giorni. Questa enumerazione deve avere il <xref:System.FlagsAttribute> e potrebbe essere denominata ' Days '. Un'enumerazione simile che consente di specificare solo un singolo giorno non avrà l'attributo e potrebbe essere chiamata ' Day '.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce il tempo necessario per apprendere una nuova raccolta software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rendere il nome dell'enumerazione una parola singolare o aggiungere il <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso dalla regola se il nome termina con una parola singolare.

## <a name="related-rules"></a>Regole correlate
 [CA1714: Le enumerazioni con Flags devono avere nomi plurali](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 Progettazione di <xref:System.FlagsAttribute?displayProperty=fullName> [enum](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
