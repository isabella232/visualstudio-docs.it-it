---
title: 'CA1700: Non assegnare un nome ai &#39;valori enum riservati&#39;'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5171123827481c99bbc35c10b04aaf942a15fabb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234382"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Non assegnare un nome ai &#39;valori enum riservati&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Category|Microsoft.Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Il nome di un membro di enumerazione contiene la parola "reserved".

## <a name="rule-description"></a>Descrizione della regola

Questa regola presuppone che un membro di enumerazione con un nome che contiene la parola "reserved" non sia attualmente utilizzato, ma sia un segnaposto che dovrà essere rinominato o rimosso in una versione futura. La ridenominazione o rimozione di un membro è ritenuta una modifica sostanziale. Non è previsto che gli utenti ignorino un membro solo perché il nome contiene "riservato", né si può fare affidamento sugli utenti per leggere o rispettare la documentazione. Inoltre, poiché i membri riservati vengono visualizzati nei browser oggetti e negli ambienti di sviluppo integrato intelligenti, possono causare confusione sui membri effettivamente utilizzati.

Anziché utilizzare un membro riservato, aggiungere un nuovo membro all'enumerazione nella versione futura. Nella maggior parte dei casi l'aggiunta del nuovo membro non è una modifica di rilievo, purché l'aggiunta non provochi la modifica dei valori dei membri originali.

In un numero limitato di casi l'aggiunta di un membro è una modifica di rilievo anche quando i membri originali mantengono i valori originali. Principalmente, il nuovo membro non può essere restituito da percorsi di codice esistenti senza che i chiamanti `switch` che`Select` usano [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]un'istruzione (in) sul valore restituito che include l'intero elenco di membri e che generino un'eccezione nel case predefinito. Un problema secondario è che il codice client potrebbe non gestire la modifica del comportamento da metodi di reflection <xref:System.Enum.IsDefined%2A?displayProperty=fullName>quali. Di conseguenza, se il nuovo membro deve essere restituito da metodi esistenti o se si verifica un'incompatibilità dell'applicazione nota a causa di un utilizzo ribasso della reflection, l'unica soluzione che non causa interruzioni è:

1. Aggiungere una nuova enumerazione che contiene i membri originali e nuovi.

2. Contrassegnare l'enumerazione originale con <xref:System.ObsoleteAttribute?displayProperty=fullName> l'attributo.

   Seguire la stessa procedura per qualsiasi tipo o membro visibile esternamente che espone l'enumerazione originale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere o rinominare il membro.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola per un membro attualmente in uso o per le librerie in precedenza spedite.

## <a name="related-rules"></a>Regole correlate

[CA2217 Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712 Non anteporre i valori enum al nome del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028: L'archiviazione enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008 Le enumerazioni devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)