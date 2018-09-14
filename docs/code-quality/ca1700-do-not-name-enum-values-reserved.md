---
title: 'CA1700: Non denominare i valori di enumerazione &#39;riservato&#39;'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 485a1e18f1c1047b84fa186cfcae1fde4bebe1df
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549976"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Non denominare i valori di enumerazione &#39;riservato&#39;
|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un membro di enumerazione contiene la parola "riservato".

## <a name="rule-description"></a>Descrizione della regola
 Questa regola presuppone che un membro di enumerazione con un nome che contiene la parola "reserved" non sia attualmente utilizzato, ma sia un segnaposto che dovrà essere rinominato o rimosso in una versione futura. La ridenominazione o rimozione di un membro è ritenuta una modifica sostanziale. Non bisogna agli utenti di ignorare un membro solo perché il relativo nome contiene "riservato", né è possibile basarsi su agli utenti di leggere o rispettare la documentazione. Inoltre, poiché i membri riservati vengono visualizzati in ambienti di sviluppo integrati e visualizzatori oggetti, è possibile che confusione sui cui i membri effettivamente usati.

 Invece di usare un membro riservato a, aggiungere un nuovo membro di enumerazione nella versione futura. Nella maggior parte dei casi l'aggiunta del nuovo membro non è una modifica importante, purché l'aggiunta non determina i valori dei membri originali da modificare.

 In un numero limitato di casi l'aggiunta di un membro è una modifica importante anche quando i membri originali mantengono i valori originali. In primo luogo, il nuovo membro non può essere restituito da percorsi del codice esistente senza interrompere i chiamanti che usano un `switch` (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) sul valore restituito che include l'elenco dei membri intera e che genera un'eccezione istruzione il case predefinito. Un secondo problema è che il codice client potrebbe non gestirà la modifica del comportamento da metodi di reflection, ad esempio <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. Di conseguenza, se il nuovo membro deve essere restituito da metodi esistenti o si verifica un'incompatibilità tra applicazioni noti a causa di utilizzo della reflection ridotte, l'unica soluzione è a:

1.  Aggiungere una nuova enumerazione che contiene i membri originali e quelli nuovi.

2.  Contrassegnare l'enumerazione originale con la <xref:System.ObsoleteAttribute?displayProperty=fullName> attributo.

 Seguire la stessa procedura per i tipi visibili esternamente o i membri che espongono l'enumerazione originale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere o rinominare il membro.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola per un membro che è attualmente usato o per le librerie fornite in precedenza.

## <a name="related-rules"></a>Regole correlate
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: L'archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Gli enum devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)