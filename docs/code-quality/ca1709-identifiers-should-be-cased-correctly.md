---
title: 'CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 864918b7ce394e9f096c6fa9dea9389957983177
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921769"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Category|Microsoft.Naming|
|Modifica importante|Quando vengono generati gli assembly, gli spazi dei nomi, i tipi, i membri e i parametri.<br /><br /> Senza interruzioni: quando viene attivato su parametri di tipo generico.|

## <a name="cause"></a>Causa

Il nome di un identificatore non viene inserito correttamente nel caso.

\- oppure -

Il nome di un identificatore contiene un acronimo di due lettere e la seconda lettera è minuscola.

\- oppure -

Il nome di un identificatore contiene un acronimo di tre o più lettere maiuscole.

## <a name="rule-description"></a>Descrizione della regola

Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. Questa coerenza riduce la curva di apprendimento necessaria per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente che dispone di competenze per lo sviluppo di codice gestito.

Per convenzione, i nomi di parametro utilizzano la combinazione di maiuscole e minuscole e i nomi di spazio dei nomi, tipi e membri utilizzano la convenzione Pascal In un nome con distinzione tra maiuscole e minuscole, la prima lettera è minuscola e la prima lettera delle parole rimanenti nel nome è maiuscola. Esempi di nomi con case Camel sono `packetSniffer`, `ioFile`e `fatalErrorCode`. In un nome con case Pascal la prima lettera è maiuscola e la prima lettera delle parole rimanenti nel nome è maiuscola. Esempi di nomi con case Pascal sono `PacketSniffer`, `IOFile`e `FatalErrorCode`.

Questa regola suddivide il nome in parole basate sulla combinazione di maiuscole e minuscole e controlla le parole di due lettere rispetto a un elenco di parole comuni di due lettere, ad esempio "in" o "My". Se non viene trovata alcuna corrispondenza, si presuppone che la parola sia un acronimo. Inoltre, questa regola presuppone che abbia trovato un acronimo quando il nome contiene quattro lettere maiuscole in una riga o tre lettere maiuscole in una riga alla fine del nome.

Per convenzione, gli acronimi di due lettere utilizzano lettere maiuscole e gli acronimi di tre o più caratteri utilizzano la combinazione di maiuscole e minuscole Pascal. Negli esempi seguenti viene utilizzata questa convenzione di denominazione: ' DB ',' CR ',' CPA ' è ECMA '. Negli esempi seguenti viene violata la convenzione: ' Io ',' XML ' è DoD ' e per i nomi non di parametro,' XP ' è CPL '.

Il valore di ' ID ' è speciale in caso di violazione di questa regola. 'ID' non è un acronimo bensì l'abbreviazione di 'identification'.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Modificare il nome in modo che sia inserito correttamente nel caso.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile evitare di visualizzare questo avviso se si dispone di convenzioni di denominazione personalizzate oppure se l'identificatore rappresenta un nome appropriato, ad esempio, il nome di una società o una tecnologia.

È anche possibile aggiungere termini specifici, abbreviazioni e acronimi a un dizionario personalizzato di analisi del codice. I termini specificati nel dizionario personalizzato non comporteranno violazioni di questa regola. Per altre informazioni, vedere [Procedura: Personalizzare il dizionario](../code-quality/how-to-customize-the-code-analysis-dictionary.md)di analisi del codice.

## <a name="related-rules"></a>Regole correlate

[CA1708 Gli identificatori devono differire più di case](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)