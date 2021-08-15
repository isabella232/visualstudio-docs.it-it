---
title: Set di regole minime native
ms.date: 11/04/2016
description: Informazioni sul set di regole native per le regole minime in Visual Studio. Vedere le descrizioni delle regole per la sicurezza, l'affidabilità e altri problemi critici nel codice nativo.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: de4d23633de1c511e75d55b41e7b5f7f0d2568f187619227c4dd6479232783ab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348572"
---
# <a name="native-minimum-rules-rule-set"></a>Set di regole minime native

Le regole minime native di Microsoft sono incentrate sui problemi più critici del codice nativo, inclusi potenziali problemi di sicurezza e arresti anomali dell'applicazione.

Includere questo set di regole in qualsiasi set di regole personalizzato creato per i progetti nativi.

|Regola|Descrizione|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Utilizzo di memoria non inizializzata|
|[C6011](/cpp/code-quality/c6011)|Dereferenziazione del puntatore Null|
|[C6029](/cpp/code-quality/c6029)|Utilizzo del valore non verificato|
|[C6053](/cpp/code-quality/c6053)|Terminazione zero da chiamata|
|[C6059](/cpp/code-quality/c6059)|Concatenazione non valida|
|[C6063](/cpp/code-quality/c6063)|Argomento stringa mancante per formattare la funzione|
|[C6064](/cpp/code-quality/c6064)|Argomento Integer mancante per formattare la funzione|
|[C6066](/cpp/code-quality/c6066)|Argomento puntatore mancante per formattare la funzione|
|[C6067](/cpp/code-quality/c6067)|Argomento puntatore stringa mancante per formattare la funzione|
|[C6101](/cpp/code-quality/c6101)|Restituzione di memoria non inizializzata|
|[C6200](/cpp/code-quality/c6200)|L'indice supera il limite massimo del buffer|
|[C6201](/cpp/code-quality/c6201)|L'indice supera il limite massimo del buffer di stack|
|[C6270](/cpp/code-quality/c6270)|Argomento Float mancante per formattare la funzione|
|[C6271](/cpp/code-quality/c6271)|Argomento aggiuntivo per formattare la funzione|
|[C6272](/cpp/code-quality/c6272)|Argomento non Float per formattare la funzione|
|[C6273](/cpp/code-quality/c6273)|Argomento non Integer per formattare la funzione|
|[C6274](/cpp/code-quality/c6274)|Argomento non Character per formattare la funzione|
|[C6276](/cpp/code-quality/c6276)|Cast stringa non valido|
|[C6277](/cpp/code-quality/c6277)|Chiamata CreateProcess non valida|
|[C6284](/cpp/code-quality/c6284)|Argomento di oggetto non valido per formattare la funzione|
|[C6290](/cpp/code-quality/c6290)|Precedenza Logical-Not Bitwise-And|
|[C6291](/cpp/code-quality/c6291)|Precedenza Logical-Not Bitwise-Or|
|[C6302](/cpp/code-quality/c6302)|Argomento stringa di caratteri non valido per formattare la funzione|
|[C6303](/cpp/code-quality/c6303)|Argomento stringa di caratteri wide non valido per formattare la funzione|
|[C6305](/cpp/code-quality/c6305)|Uso dimensione e conteggio non corrispondente|
|[C6306](/cpp/code-quality/c6306)|Chiamata di funzione dell'argomento variabile non corretto|
|[C6328](/cpp/code-quality/c6328)|Tipo argomento potenzialmente non corrispondente|
|[C6385](/cpp/code-quality/c6385)|Overrun di lettura|
|[C6386](/cpp/code-quality/c6386)|Overrun di scrittura|
|[C6387](/cpp/code-quality/c6387)|Valore parametro non valido|
|[C6500](/cpp/code-quality/c6500)|Proprietà attributo non valido|
|[C6501](/cpp/code-quality/c6501)|Conflitto valori di proprietà attributo|
|[C6503](/cpp/code-quality/c6503)|I riferimenti non possono essere Null|
|[C6504](/cpp/code-quality/c6504)|Null su non puntatore|
|[C6505](/cpp/code-quality/c6505)|MustCheck su nullo|
|[C6506](/cpp/code-quality/c6506)|Dimensioni buffer su non puntatore o matrice|
|[C6508](/cpp/code-quality/c6508)|Accesso in scrittura a costante|
|[C6509](/cpp/code-quality/c6509)|Restituzione utilizzati in precondizione|
|[C6510](/cpp/code-quality/c6510)|Null terminato su non puntatore|
|[C6511](/cpp/code-quality/c6511)|MustCheck deve essere Yes o No|
|[C6513](/cpp/code-quality/c6513)|Dimensioni elemento senza dimensione buffer|
|[C6514](/cpp/code-quality/c6514)|Le dimensioni del buffer superano le dimensioni della matrice|
|[C6515](/cpp/code-quality/c6515)|Dimensioni buffer su non puntatore|
|[C6516](/cpp/code-quality/c6516)|Nessuna proprietà su attributo|
|[C6517](/cpp/code-quality/c6517)|Dimensioni valide su buffer non leggibile|
|[C6518](/cpp/code-quality/c6518)|Dimensioni scrivibili su buffer non scrivibile|
|[C6522](/cpp/code-quality/c6522)|Tipo stringa dimensioni non valida|
|[C6525](/cpp/code-quality/c6525)|Percorso irraggiungibile stringa dimensioni non valida|
|[C6527](/cpp/code-quality/c6527)|Annotazione non valida: la proprietà 'NeedsRelease' non può essere utilizzata con valori di tipo void|
|[C6530](/cpp/code-quality/c6530)|Stile stringa formato non riconosciuto|
|[C6540](/cpp/code-quality/c6540)|L'utilizzo delle annotazioni di attributo in questa funzione invalida tutte le relative annotazioni __declspec|
|[C6551](/cpp/code-quality/c6551)|Specifica di dimensione non valida: espressione non analizzabile|
|[C6552](/cpp/code-quality/c6552)|Deref= o Notref= non valido: espressione non analizzabile|
|[C6701](/cpp/code-quality/c6701)|Il valore non è un valore Yes/No/Maybe valido|
|[C6702](/cpp/code-quality/c6702)|Il valore non è un valore stringa|
|[C6703](/cpp/code-quality/c6703)|Il valore non è un numero|
|[C6704](/cpp/code-quality/c6704)|Errore imprevisto dell'espressione dell'annotazione|
|[C6705](/cpp/code-quality/c6705)|Numero previsto di argomenti per l'annotazione non corrispondente al numero effettivo di argomenti per l'annotazione|
|[C6706](/cpp/code-quality/c6706)|Errore di annotazione imprevisto per l'annotazione|
|[C26450](/cpp/code-quality/C26450)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](/cpp/code-quality/C26451)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](/cpp/code-quality/C26452)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](/cpp/code-quality/C26453)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](/cpp/code-quality/C26454)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](/cpp/code-quality/C26495)|MEMBER_UNINIT|
|[C28021](/cpp/code-quality/c28021)|Il parametro annotato deve essere un puntatore|
|[C28182](/cpp/code-quality/c28182)|Deferenziazione del puntatore NULL. Il puntatore contiene lo stesso valore NULL contenuto in un altro puntatore.|
|[C28202](/cpp/code-quality/c28202)|Riferimento non valido a membro non statico|
|[C28203](/cpp/code-quality/c28203)|Riferimento ambiguo al membro di classe.|
|[C28205](/cpp/code-quality/c28205)|\_Esito \_ positivo o In caso di errore usato in un contesto non \_ \_ \_ valido|
|[C28206](/cpp/code-quality/c28206)|L'operando sinistro punta a uno struct. Utilizzare '->'|
|[C28207](/cpp/code-quality/c28207)|L'operando sinistro è uno struct. Utilizzare '.'|
|[C28210](/cpp/code-quality/c28210)|Impossibile definire le annotazioni per il contesto __On_failure in un precontesto esplicito|
|[C28211](/cpp/code-quality/c28211)|Previsto nome contesto statico per SAL_context|
|[C28212](/cpp/code-quality/c28212)|Prevista espressione del puntatore per l'annotazione|
|[C28213](/cpp/code-quality/c28213)|\_ \_ L'annotazione Use decl \_ annotations \_ deve essere usata per fare riferimento, senza modifiche, a una dichiarazione precedente.|
|[C28214](/cpp/code-quality/c28214)|I nomi di parametro di attributo devono essere p1...p9|
|[C28215](/cpp/code-quality/c28215)|Impossibile applicare typefix a un parametro che già dispone di un typefix|
|[C28216](/cpp/code-quality/c28216)|L'annotazione checkReturn si applica soltanto a postcondizioni per il parametro di funzione specifico.|
|[C28217](/cpp/code-quality/c28217)|Per la funzione, il numero di parametri per l'annotazione non corrisponde a quello trovato nel file|
|[C28218](/cpp/code-quality/c28218)|Per il parametro della funzione, il parametro dell'annotazione non corrisponde a quello trovato nel file|
|[C28219](/cpp/code-quality/c28219)|Membro di enumerazione previsto per l'annotazione del parametro nell'annotazione|
|[C28220](/cpp/code-quality/c28220)|Espressione integer prevista per l'annotazione del parametro nell'annotazione|
|[C28221](/cpp/code-quality/c28221)|Prevista espressione di tipo String per il parametro nell'annotazione|
|[C28222](/cpp/code-quality/c28222)|Previsto __yes, \__no o \__maybe per l'annotazione|
|[C28223](/cpp/code-quality/c28223)|Token o identificatore previsto mancante per l'annotazione, parametro|
|[C28224](/cpp/code-quality/c28224)|L'annotazione richiede parametri|
|[C28225](/cpp/code-quality/c28225)|Numero non corretto di parametri necessari nell'annotazione|
|[C28226](/cpp/code-quality/c28226)|L'annotazione non può essere anche PrimOp nella dichiarazione corrente|
|[C28227](/cpp/code-quality/c28227)|L'annotazione non può essere anche PrimOp nella dichiarazione precedente|
|[C28228](/cpp/code-quality/c28228)|Parametro di annotazione: Impossibile utilizzare il tipo nelle annotazioni|
|[C28229](/cpp/code-quality/c28229)|L'annotazione non supporta parametri|
|[C28230](/cpp/code-quality/c28230)|Il tipo di parametro non ha membro.|
|[C28231](/cpp/code-quality/c28231)|L'annotazione è valida solo in una matrice|
|[C28232](/cpp/code-quality/c28232)|Pre, post o deref non applicato ad alcuna annotazione|
|[C28233](/cpp/code-quality/c28233)|Pre, post o deref applicato a un blocco|
|[C28234](/cpp/code-quality/c28234)|L'espressione __At non si applica alla funzione corrente|
|[C28235](/cpp/code-quality/c28235)|La funzione non può fungere autonomamente da annotazione|
|[C28236](/cpp/code-quality/c28236)|Impossibile utilizzare l'annotazione in un'espressione|
|[C28237](/cpp/code-quality/c28237)|L'annotazione nel parametro non è più supportata|
|[C28238](/cpp/code-quality/c28238)|L'annotazione nel parametro presenta più di un valore, stringValue e longValue. Utilizzare paramn=xxx|
|[C28239](/cpp/code-quality/c28239)|L'annotazione nel parametro presenta sia stringValue, o longValue, che paramn=xxx. Utilizzare solo paramn=xxx|
|[C28240](/cpp/code-quality/c28240)|L'annotazione nel parametro presenta param2 ma nessun param1|
|[C28241](/cpp/code-quality/c28241)|Annotazione per la funzione nel parametro non riconosciuta|
|[C28243](/cpp/code-quality/c28243)|L'annotazione per la funzione nel parametro richiede più dereferenziazioni di quante ne siano consentite dal tipo annotato effettivo|
|[C28245](/cpp/code-quality/c28245)|L'annotazione per la funzione annota 'this' in una funzione non membro|
|[C28246](/cpp/code-quality/c28246)|Nell'annotazione per la funzione, il parametro non corrisponde al tipo del parametro|
|[C28250](/cpp/code-quality/c28250)|Annotazione incoerente per la funzione: errore dell'istanza precedente.|
|[C28251](/cpp/code-quality/c28251)|Annotazione incoerente per la funzione: errore dell'istanza.|
|[C28252](/cpp/code-quality/c28252)|Annotazione incoerente per la funzione: il parametro presenta altre annotazioni su questa istanza.|
|[C28253](/cpp/code-quality/c28253)|Annotazione incoerente per la funzione: il parametro presenta altre annotazioni su questa istanza.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<>() non è supportato nelle annotazioni|
|[C28262](/cpp/code-quality/c28262)|Errore di sintassi dell'annotazione rilevato nella funzione per l'annotazione|
|[C28263](/cpp/code-quality/c28263)|Errore di sintassi nell'annotazione condizionale rilevato nell'oggetto annotazione intrinseco|
|[C28267](/cpp/code-quality/c28267)|Errore di sintassi dell'annotazione rilevato nella funzione per l'annotazione.|
|[C28272](/cpp/code-quality/c28272)|L'annotazione per la funzione, parametro, durante l'analisi non è coerente con la dichiarazione della funzione|
|[C28273](/cpp/code-quality/c28273)|Per la funzione, le informazioni non sono coerenti con la dichiarazione della funzione|
|[C28275](/cpp/code-quality/c28275)|Il parametro per \_ il valore macro è \_ \_ Null|
|[C28279](/cpp/code-quality/c28279)|Per il simbolo è stato trovato un 'begin' senza il corrispondente 'end'|
|[C28280](/cpp/code-quality/c28280)|Per il simbolo, è stato trovato un 'end' senza un 'begin' corrispondente|
|[C28282](/cpp/code-quality/c28282)|Le stringhe di formato devono essere nelle precondizioni|
|[C28285](/cpp/code-quality/c28285)|Per la funzione, errore di sintassi nel parametro|
|[C28286](/cpp/code-quality/c28286)|Per la funzione, errore di sintassi vicino alla fine|
|[C28287](/cpp/code-quality/c28287)|Per la funzione, errore di sintassi nell'annotazione \_At\_() (nome parametro non riconosciuto)|
|[C28288](/cpp/code-quality/c28288)|Per la funzione, errore di sintassi nell'annotazione \_At\_() (nome parametro non valido)|
|[C28289](/cpp/code-quality/c28289)|Per la funzione: ReadableTo o WritableTo non disponeva di limit-spec come parametro|
|[C28290](/cpp/code-quality/c28290)|L'annotazione per la funzione contiene un numero di riferimenti esterni maggiore del numero di parametri effettivi|
|[C28291](/cpp/code-quality/c28291)|Il post null/notnull al livello deref 0 è privo di significato per la funzione.|
|[C28300](/cpp/code-quality/c28300)|Operandi dell'espressione di tipi incompatibili per l'operatore|
|[C28301](/cpp/code-quality/c28301)|Nessuna annotazione per la prima dichiarazione di funzione.|
|[C28302](/cpp/code-quality/c28302)|Operatore \_Deref\_ aggiuntivo rilevato nell'annotazione.|
|[C28303](/cpp/code-quality/c28303)|Operatore \_Deref\_ ambiguo trovato nell'annotazione.|
|[C28304](/cpp/code-quality/c28304)|Operatore \_Notref\_ non correttamente posizionato applicato al token.|
|[C28305](/cpp/code-quality/c28305)|È stato individuato un errore durante l'analisi di un token.|
|[C28350](/cpp/code-quality/c28350)|L'annotazione descrive una situazione non applicabile in modo condizionale.|
|[C28351](/cpp/code-quality/c28351)|L'annotazione descrive la posizione nella condizione in cui non è possibile utilizzare un valore dinamico (variabile).|