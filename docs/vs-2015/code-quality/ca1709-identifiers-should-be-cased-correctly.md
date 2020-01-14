---
title: 'CA1709: gli identificatori devono essere configurati correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c4da0414c9923a8ed7bb01456f38000433641522
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919225"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA1709: gli identificatori devono essere configurati correttamente](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly).

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Categoria|Microsoft.Naming|
|Modifica importante|Quando vengono generati gli assembly, gli spazi dei nomi, i tipi, i membri e i parametri.<br /><br /> Senza interruzioni: quando viene attivato su parametri di tipo generico.|

## <a name="cause"></a>Causa
 Il nome di un identificatore non viene inserito correttamente nel caso.

 \- oppure -

 Il nome di un identificatore contiene un acronimo di due lettere e la seconda lettera è minuscola.

 \- oppure -

 Il nome di un identificatore contiene un acronimo di tre o più lettere maiuscole.

## <a name="rule-description"></a>Descrizione della regola
 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

 Per convenzione, i nomi dei parametri utilizzano la combinazione Camel; lo spazio dei nomi, il tipo e i nomi dei membri utilizzano la convenzione Pascal. In un nome con distinzione tra maiuscole e minuscole, la prima lettera è minuscola e la prima lettera delle parole rimanenti nel nome è maiuscola. Esempi di nomi con case Camel sono "packetSniffer", "ioFile" e "fatalErrorCode". In un nome con maiuscole e minuscole Pascal la prima lettera è maiuscola e la prima lettera delle parole rimanenti nel nome è maiuscola. Esempi di nomi con case Pascal sono "PacketSniffer", "IOFile" e "FatalErrorCode".

 Questa regola suddivide il nome in parole basate sulla combinazione di maiuscole e minuscole e controlla le parole di due lettere rispetto a un elenco di parole comuni di due lettere, ad esempio "in" o "My". Se non viene trovata alcuna corrispondenza, si presuppone che la parola sia un acronimo. Inoltre, questa regola presuppone che abbia trovato un acronimo quando il nome contiene quattro lettere maiuscole in una riga o tre lettere maiuscole in una riga alla fine del nome.

 Per convenzione, gli acronimi di due lettere utilizzano lettere maiuscole e gli acronimi di tre o più caratteri utilizzano la combinazione di maiuscole e minuscole Pascal. Gli esempi seguenti usano questa convenzione di denominazione:' DB ',' CR ',' CPA ' è ECMA '. Negli esempi seguenti viene violata la convenzione:' io ',' XML ' è DoD ' e per i nomi non di parametri,' XP ' è CPL '.

 Il valore di ' ID ' è speciale in caso di violazione di questa regola. 'ID' non è un acronimo bensì l'abbreviazione di 'identification'.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare il nome in modo che sia inserito correttamente nel caso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile evitare di visualizzare questo avviso se si dispone di convenzioni di denominazione personalizzate oppure se l'identificatore rappresenta un nome appropriato, ad esempio, il nome di una società o una tecnologia.

 È anche possibile aggiungere termini specifici, abbreviazioni e acronimi a un dizionario personalizzato di analisi del codice. I termini specificati nel dizionario personalizzato non comporteranno violazioni di questa regola. Per altre informazioni, vedere [procedura: personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Regole correlate
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
