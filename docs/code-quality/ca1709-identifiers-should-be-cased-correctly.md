---
title: 'CA1709: Gli identificatori devono essere digitati correttamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e954b3e3d346775d87cfcc8bb46bddca2b16056a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881727"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Gli identificatori devono essere digitati correttamente

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Category|Microsoft.Naming|
|Modifica importante|Interrompere l'esecuzione - quando è generato su assembly, spazi dei nomi, tipi, membri e parametri.<br /><br /> Non sostanziale - Quando viene attivato su parametri di tipo generico.|

## <a name="cause"></a>Causa
 Il nome di un identificatore non è maiuscole e minuscole.

 \- oppure -

 Il nome di un identificatore contiene un acronimo di due lettere e la seconda lettera è in minuscola.

 \- oppure -

 Il nome di un identificatore contiene l'acronimo di tre o più lettere maiuscole.

## <a name="rule-description"></a>Descrizione della regola
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. Questa coerenza consente di ridurre la curva di apprendimento che ha richiesto per le nuove librerie di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

 Per convenzione, i nomi dei parametri usano le iniziali maiuscole e minuscole e lo spazio dei nomi, il tipo e i nomi dei membri utilizzare la convenzione Pascal maiuscole e minuscole. Un nome di maiuscole/minuscole camel, la prima lettera è in lettere minuscola e la prima lettera di qualsiasi rimanenti parole nel nome è un carattere maiuscola. Sono esempi di nomi di maiuscole/minuscole camel `packetSniffer`, `ioFile`, e `fatalErrorCode`. Un nome, la convenzione Pascal, la prima lettera è un carattere maiuscola, e la prima lettera di qualsiasi rimanenti parole nel nome è un carattere maiuscola. Sono esempi di nomi di convenzione Pascal `PacketSniffer`, `IOFile`, e `FatalErrorCode`.

 Questa regola suddivide il nome in base alle maiuscole e minuscole di parole e controlla le parole di due lettere rispetto a un elenco di parole di due lettere comuni, ad esempio "In" o "My". Se non viene trovata una corrispondenza, la parola è considerata un acronimo. Inoltre, questa regola presuppone che è stata rilevata l'acronimo quando il nome contiene quattro lettere maiuscole in una riga o tre lettere maiuscole in una riga alla fine del nome.

 Per convenzione, gli acronimi di due lettere usano lettere maiuscole e gli acronimi di tre o più caratteri utilizzano la convenzione Pascal maiuscole e minuscole. Gli esempi seguenti usano questa convenzione di denominazione: 'DB', 'CR', 'Cpa' e 'Ecma'. Negli esempi seguenti non rispettano la convenzione: 'Io', 'XML' e 'DoD' e per i nomi non di parametro, "xp" e "cpl".

 'ID' è maiuscole/minuscole speciale per causare una violazione della regola. 'ID' non è un acronimo bensì l'abbreviazione di 'identification'.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare il nome in modo che viene maiuscole e minuscole.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare questo avviso se si dispone di proprie convenzioni di denominazione oppure se l'identificatore rappresenta un nome appropriato, ad esempio, il nome di una società o una tecnologia.

 È anche possibile aggiungere condizioni specifiche, le abbreviazioni e gli acronimi che a un dizionario personalizzato di analisi del codice. I termini specificati nel dizionario personalizzato non genererà le violazioni di questa regola. Per altre informazioni, vedere [Procedura: Personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Regole correlate
 [CA1708: Gli identificatori devono differenziarsi minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)