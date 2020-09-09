---
title: Set di regole consigliate miste
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c29e27160b50a53995b7542680256bfd4e2d8f2
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600046"
---
# <a name="mixed-recommended-rules-rule-set"></a>Set di regole consigliate miste

Le regole consigliate di Microsoft sono incentrate sui problemi più comuni e critici nei progetti C++ che supportano Common Language Runtime, inclusi potenziali problemi di sicurezza, arresti anomali dell'applicazione e altri errori di logica e progettazione importanti. Questo set di regole include tutte le regole nel set di regole di [regole minime miste](mixed-minimum-rules-rule-set.md) .

Includere questo set di regole in tutti i set di regole personalizzati creati per i progetti C++ che supportano Common Language Runtime.

|Regola|Descrizione|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Utilizzo di memoria non inizializzata|
|[C6011](/cpp/code-quality/c6011)|Dereferenziazione del puntatore Null|
|[C6029](/cpp/code-quality/c6029)|Utilizzo del valore non verificato|
|[C6031](/cpp/code-quality/c6031)|Valore restituito ignorato|
|[C6053](/cpp/code-quality/c6053)|Terminazione zero da chiamata|
|[C6054](/cpp/code-quality/c6054)|Terminazione zero mancante|
|[C6059](/cpp/code-quality/c6059)|Concatenazione non valida|
|[C6063](/cpp/code-quality/c6063)|Argomento stringa mancante per formattare la funzione|
|[C6064](/cpp/code-quality/c6064)|Argomento Integer mancante per formattare la funzione|
|[C6066](/cpp/code-quality/c6066)|Argomento puntatore mancante per formattare la funzione|
|[C6067](/cpp/code-quality/c6067)|Argomento puntatore stringa mancante per formattare la funzione|
|[C6101](/cpp/code-quality/c6101)|Restituzione di memoria non inizializzata|
|[C6200](/cpp/code-quality/c6200)|L'indice supera il limite massimo del buffer|
|[C6201](/cpp/code-quality/c6201)|L'indice supera il limite massimo del buffer di stack|
|[C6214](/cpp/code-quality/c6214)|Cast di HRESULT a BOOL non valido|
|[C6215](/cpp/code-quality/c6215)|Cast di BOOL a HRESULT non valido|
|[C6216](/cpp/code-quality/c6216)|Cast compilato dal compilatore BOOL a HRESULT non valido|
|[C6217](/cpp/code-quality/c6217)|Test HRESULT non valido con NOT|
|[C6220](/cpp/code-quality/c6220)|Confronto HRESULT non valido a-1|
|[C6226](/cpp/code-quality/c6226)|Assegnazione HRESULT non valida a-1|
|[C6230](/cpp/code-quality/c6230)|Utilizzo HRESULT non valido come valore booleano|
|[C6235](/cpp/code-quality/c6235)|Costante diversa da zero con Logical-OR|
|[C6236](/cpp/code-quality/c6236)|Logical-OR con costante diversa da zero|
|[C6237](/cpp/code-quality/c6237)|Zero con and logico perde effetti collaterali|
|[C6242](/cpp/code-quality/c6242)|Rimozione locale forzata|
|[C6248](/cpp/code-quality/c6248)|Creazione di DACL null|
|[C6250](/cpp/code-quality/c6250)|Descrittori di indirizzo non rilasciati|
|[C6255](/cpp/code-quality/c6255)|Uso non protetto di alloca|
|[C6258](/cpp/code-quality/c6258)|Utilizzo del thread di terminazione|
|[C6259](/cpp/code-quality/c6259)|Codice inattivo nell'opzione con OR bit per bit limitato|
|[C6260](/cpp/code-quality/c6260)|Utilizzo aritmetico dei byte|
|[C6262](/cpp/code-quality/c6262)|Utilizzo eccessivo dello stack|
|[C6263](/cpp/code-quality/c6263)|Utilizzo di alloca in loop|
|[C6268](/cpp/code-quality/c6268)|Parentesi mancanti nel cast|
|[C6269](/cpp/code-quality/c6269)|Dereferenziazione del puntatore ignorata|
|[C6270](/cpp/code-quality/c6270)|Argomento Float mancante per formattare la funzione|
|[C6271](/cpp/code-quality/c6271)|Argomento aggiuntivo per formattare la funzione|
|[C6272](/cpp/code-quality/c6272)|Argomento non Float per formattare la funzione|
|[C6273](/cpp/code-quality/c6273)|Argomento non Integer per formattare la funzione|
|[C6274](/cpp/code-quality/c6274)|Argomento non Character per formattare la funzione|
|[C6276](/cpp/code-quality/c6276)|Cast stringa non valido|
|[C6277](/cpp/code-quality/c6277)|Chiamata CreateProcess non valida|
|[C6278](/cpp/code-quality/c6278)|Array-New Scalar-Delete non corrispondente|
|[C6279](/cpp/code-quality/c6279)|Scalar-new Array-Delete non corrispondente|
|[C6280](/cpp/code-quality/c6280)|Allocazione di memoria-deallocazione non corrispondente|
|[C6281](/cpp/code-quality/c6281)|Precedenza relazione bit per bit|
|[C6282](/cpp/code-quality/c6282)|L'assegnazione sostituisce il test|
|[C6283](/cpp/code-quality/c6283)|Array primitivo-nuovo scalare-eliminazione non corrispondente|
|[C6284](/cpp/code-quality/c6284)|Argomento di oggetto non valido per formattare la funzione|
|[C6285](/cpp/code-quality/c6285)|Logical-OR di costanti|
|[C6286](/cpp/code-quality/c6286)|Effetti collaterali logici diversi da zero|
|[C6287](/cpp/code-quality/c6287)|Test ridondante|
|[C6288](/cpp/code-quality/c6288)|Inclusione reciproca su Logical-and è false|
|[C6289](/cpp/code-quality/c6289)|Esclusione reciproca su OR logico true|
|[C6290](/cpp/code-quality/c6290)|Precedenza Logical-Not Bitwise-And|
|[C6291](/cpp/code-quality/c6291)|Precedenza Logical-Not Bitwise-Or|
|[C6292](/cpp/code-quality/c6292)|Conteggi cicli fino al massimo|
|[C6293](/cpp/code-quality/c6293)|Conteggio cicli inattivo dal minimo|
|[C6294](/cpp/code-quality/c6294)|Corpo del ciclo mai eseguito|
|[C6295](/cpp/code-quality/c6295)|Ciclo infinito|
|[C6296](/cpp/code-quality/c6296)|Ciclo eseguito una sola volta|
|[C6297](/cpp/code-quality/c6297)|Risultato del cast di spostamento a dimensioni maggiori|
|[C6299](/cpp/code-quality/c6299)|Confronto tra bit e Boolean|
|[C6302](/cpp/code-quality/c6302)|Argomento stringa di caratteri non valido per formattare la funzione|
|[C6303](/cpp/code-quality/c6303)|Argomento stringa di caratteri wide non valido per formattare la funzione|
|[C6305](/cpp/code-quality/c6305)|Uso dimensione e conteggio non corrispondente|
|[C6306](/cpp/code-quality/c6306)|Chiamata di funzione dell'argomento variabile non corretto|
|[C6306](/cpp/code-quality/c6308)|Perdita di realloc|
|[C6310](/cpp/code-quality/c6310)|Costante filtro eccezioni non valida|
|[C6312](/cpp/code-quality/c6312)|Ciclo di esecuzione dell'eccezione continua|
|[C6314](/cpp/code-quality/c6314)|Precedenza or bit per bit|
|[C6317](/cpp/code-quality/c6317)|Non complemento|
|[C6318](/cpp/code-quality/c6318)|Continua ricerca eccezione|
|[C6319](/cpp/code-quality/c6319)|Ignorato da virgola|
|[C6324](/cpp/code-quality/c6324)|Copia della stringa anziché confronto tra stringhe|
|[C6328](/cpp/code-quality/c6328)|Tipo argomento potenzialmente non corrispondente|
|[C6331](/cpp/code-quality/c6331)|Flag VirtualFree non validi|
|[C6332](/cpp/code-quality/c6332)|Parametro VirtualFree non valido|
|[C6333](/cpp/code-quality/c6333)|Dimensioni VirtualFree non valide|
|[C6335](/cpp/code-quality/c6335)|Handle di processo perdita|
|[C6381](/cpp/code-quality/c6381)|Informazioni di chiusura mancanti|
|[C6383](/cpp/code-quality/c6383)|Numero di byte del buffer di conteggio elementi|
|[C6384](/cpp/code-quality/c6384)|Divisione dimensioni puntatore|
|[C6385](/cpp/code-quality/c6385)|Overrun di lettura|
|[C6386](/cpp/code-quality/c6386)|Overrun di scrittura|
|[C6387](/cpp/code-quality/c6387)|Valore parametro non valido|
|[C6388](/cpp/code-quality/c6388)|Valore parametro non valido|
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
|[C6995](/cpp/code-quality/c6995)|Non è stato possibile salvare il file di log XML|
|[C26100](/cpp/code-quality/c26100)|Race condition|
|[C26101](/cpp/code-quality/c26101)|Impossibile utilizzare correttamente l'operazione Interlocked|
|[C26110](/cpp/code-quality/c26110)|Il chiamante non riesce a mantenere il blocco|
|[C26111](/cpp/code-quality/c26111)|Il chiamante non riesce a rilasciare il blocco|
|[C26112](/cpp/code-quality/c26112)|Il chiamante non può mantenere alcun blocco|
|[C26115](/cpp/code-quality/c26115)|Errore di rilascio del blocco|
|[C26116](/cpp/code-quality/c26116)|Impossibile acquisire o mantenere il blocco|
|[C26117](/cpp/code-quality/c26117)|Rilascio del blocco non mantenuto|
|[C26140](/cpp/code-quality/c26140)|Errore di annotazione di concorrenza SAL|
|[C28020](/cpp/code-quality/c28020)|L'espressione non è true in questa chiamata|
|[C28021](/cpp/code-quality/c28021)|Il parametro annotato deve essere un puntatore|
|[C28022](/cpp/code-quality/c28022)|Le classi di funzioni in questa funzione non corrispondono alle classi di funzioni nel typedef utilizzato per definirlo.|
|[C28023](/cpp/code-quality/c28023)|La funzione assegnata o passata deve avere un' \_ \_ \_ annotazione di classe di funzione per almeno una delle classi|
|[C28024](/cpp/code-quality/c28024)|Il puntatore a funzione assegnato è annotato con la classe Function, che non è contenuta nell'elenco delle classi di funzioni.|
|[C28039](/cpp/code-quality/c28039)|Il tipo di parametro effettivo deve corrispondere esattamente al tipo|
|[C28112](/cpp/code-quality/c28112)|Una variabile A cui si accede tramite una funzione Interlocked deve essere sempre accessibile tramite una funzione Interlocked.|
|[C28113](/cpp/code-quality/c28113)|Accesso a una variabile locale tramite una funzione Interlocked|
|[C28125](/cpp/code-quality/c28125)|La funzione deve essere chiamata dall'interno di un blocco try/except|
|[C28137](/cpp/code-quality/c28137)|L'argomento della variabile deve invece essere una costante (valore letterale)|
|[C28138](/cpp/code-quality/c28138)|L'argomento della costante deve essere variabile|
|[C28159](/cpp/code-quality/c28159)|Prendere in considerazione l'uso di un'altra funzione.|
|[C28160](/cpp/code-quality/c28160)|Error (annotazione)|
|[C28163](/cpp/code-quality/c28163)|La funzione non deve mai essere chiamata dall'interno di un blocco try/except|
|[C28164](/cpp/code-quality/c28164)|L'argomento viene passato a una funzione che prevede un puntatore a un oggetto (non un puntatore a un puntatore)|
|[C28182](/cpp/code-quality/c28182)|Deferenziazione del puntatore NULL. Il puntatore contiene lo stesso valore NULL contenuto in un altro puntatore.|
|[C28183](/cpp/code-quality/c28183)|L'argomento può essere un valore e è una copia del valore trovato nel puntatore|
|[C28193](/cpp/code-quality/c28193)|La variabile include un valore che deve essere esaminato|
|[C28196](/cpp/code-quality/c28196)|Il requisito non è soddisfatto. (L'espressione non restituisce true).|
|[C28202](/cpp/code-quality/c28202)|Riferimento non valido a membro non statico|
|[C28203](/cpp/code-quality/c28203)|Riferimento ambiguo al membro di classe.|
|[C28205](/cpp/code-quality/c28205)|\_Esito positivo \_ o \_ \_ negativo \_ utilizzato in un contesto non valido|
|[C28206](/cpp/code-quality/c28206)|L'operando sinistro punta a uno struct. Utilizzare '->'|
|[C28207](/cpp/code-quality/c28207)|L'operando sinistro è uno struct. Utilizzare '.'|
|[C28209](/cpp/code-quality/c28209)|La dichiarazione per il simbolo presenta una dichiarazione in conflitto|
|[C28210](/cpp/code-quality/c28210)|Impossibile definire le annotazioni per il contesto __On_failure in un precontesto esplicito|
|[C28211](/cpp/code-quality/c28211)|Previsto nome contesto statico per SAL_context|
|[C28212](/cpp/code-quality/c28212)|Prevista espressione del puntatore per l'annotazione|
|[C28213](/cpp/code-quality/c28213)|L' \_ \_ annotazione use decl Annotations \_ \_ deve essere utilizzata per fare riferimento, senza alcuna modifica, a una dichiarazione precedente.|
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
|[C28244](/cpp/code-quality/c28244)|L'annotazione per la funzione ha un parametro/annotazione esterna non analizzabile|
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
|[C28275](/cpp/code-quality/c28275)|Il parametro per \_ il \_ valore della macro \_ è null|
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
|[C28306](/cpp/code-quality/c28306)|L'annotazione sul parametro è obsoleti|
|[C28307](/cpp/code-quality/c28307)|L'annotazione sul parametro è obsoleti|
|[C28350](/cpp/code-quality/c28350)|L'annotazione descrive una situazione non applicabile in modo condizionale.|
|[C28351](/cpp/code-quality/c28351)|L'annotazione descrive la posizione nella condizione in cui non è possibile utilizzare un valore dinamico (variabile).|
|[CA1001](../code-quality/ca1001.md)|I tipi proprietari di campi Disposable devono essere Disposable|
|[CA1009](../code-quality/ca1009.md)|Dichiarare correttamente i gestori eventi|
|[CA1016](../code-quality/ca1016.md)|Contrassegnare gli assembly con AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|I metodi di interfaccia devono essere richiamabili dai tipi figlio|
|[CA1049](../code-quality/ca1049.md)|I tipi delle risorse native devono essere disposable|
|[CA1060](../code-quality/ca1060.md)|Spostare P/Invoke nella classe NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Non nascondere i metodi di una classe base|
|[CA1063](../code-quality/ca1063.md)|Implementare IDisposable correttamente|
|[CA1065](../code-quality/ca1065.md)|Non generare eccezioni in posizioni non previste|
|[CA1301](../code-quality/ca1301.md)|Evitare tasti di scelta rapida duplicati|
|[CA1400](../code-quality/ca1400.md)|I punti di ingresso P/Invoke devono esistere|
|[CA1401](../code-quality/ca1401.md)|I P/Invoke non devono essere visibili|
|[CA1403](../code-quality/ca1403.md)|I tipi layout automatici non devono essere visibili a COM|
|[CA1404](../code-quality/ca1404.md)|Chiamare GetLastError immediatamente dopo P/Invoke|
|[CA1405](../code-quality/ca1405.md)|I tipi di base del tipo visibile a COM devono essere visibili a COM|
|[CA1410](../code-quality/ca1410.md)|I metodi di registrazione COM devono corrispondere|
|[CA1415](../code-quality/ca1415.md)|Dichiarare correttamente i P/Invoke|
|[CA1821](../code-quality/ca1821.md)|Rimuovere i finalizzatori vuoti|
|[CA1900](../code-quality/ca1900.md)|I campi dei tipi di valore devono essere portabili|
|[CA1901](../code-quality/ca1901.md)|Le dichiarazioni P/Invoke devono essere portabili|
|[CA2002](../code-quality/ca2002.md)|Non bloccare oggetti con identità debole|
|[CA2100](../code-quality/ca2100.md)|Controllare la vulnerabilità della sicurezza nelle query SQL|
|[CA2101](../code-quality/ca2101.md)|Specificare il marshalling per gli argomenti di stringa P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Controllare la sicurezza dichiarativa sui tipi di valori|
|[CA2111](../code-quality/ca2111.md)|I puntatori non devono essere visibili|
|[CA2112](../code-quality/ca2112.md)|I tipi protetti non devono esporre campi|
|[CA2114](../code-quality/ca2114.md)|La sicurezza del metodo deve essere un superset del tipo|
|[CA2116](../code-quality/ca2116.md)|I metodi APTCA devono chiamare solo metodi APTCA|
|[CA2117](../code-quality/ca2117.md)|I tipi APTCA devono estendere solo tipi di base APTCA|
|[CA2122](../code-quality/ca2122.md)|Non esporre in modo indiretto metodi con richieste di collegamento|
|[CA2123](../code-quality/ca2123.md)|Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base|
|[CA2124](../code-quality/ca2124.md)|Eseguire il wrapping delle clausole finally vulnerabili in un try esterno|
|[CA2126](../code-quality/ca2126.md)|Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà|
|[CA2131](../code-quality/ca2131.md)|I tipi SecurityCritical possono non partecipare all'equivalenza del tipo|
|[CA2132](../code-quality/ca2132.md)|I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base|
|[CA2133](../code-quality/ca2133.md)|I delegati devono essere associati ai metodi con trasparenza consistente|
|[CA2134](../code-quality/ca2134.md)|I metodi devono mantenere trasparenza consistente durante l'override dei metodi base|
|[CA2137](../code-quality/ca2137.md)|I metodi Transparent devono contenere solo IL verificabile|
|[CA2138](../code-quality/ca2138.md)|I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Il codice Transparent non deve far riferimento a elementi SecurityCritical|
|[CA2141](../code-quality/ca2141.md)|I metodi Transparent non devono soddisfare I LinkDemand|
|[CA2146](../code-quality/ca2146.md)|I tipi devono essere Critical almeno come le interfacce e i tipi base relativi|
|[CA2147](../code-quality/ca2147.md)|I metodi Transparent non possono usare asserzioni di sicurezza|
|[CA2149](../code-quality/ca2149.md)|I metodi Transparent non devono effettuare chiamate nel codice nativo|
|[CA2200](../code-quality/ca2200.md)|Eseguire il rethrow per mantenere i dettagli dello stack|
|[CA2202](../code-quality/ca2202.md)|Non eliminare gli oggetti più volte|
|[CA2207](../code-quality/ca2207.md)|Inizializzare i campi statici dei tipi di valore inline|
|[CA2212](../code-quality/ca2212.md)|Non contrassegnare componenti serviti con WebMethod|
|[CA2213](../code-quality/ca2213.md)|I campi eliminabili devono essere eliminati|
|[CA2214](../code-quality/ca2214.md)|Non chiamare metodi sottoponibili a override nei costruttori|
|[CA2216](../code-quality/ca2216.md)|I tipi eliminabili devono dichiarare un finalizzatore|
|[CA2220](../code-quality/ca2220.md)|I finalizzatori devono chiamare il finalizzatore della classe di base|
|[CA2229](../code-quality/ca2229.md)|Implementare costruttori di serializzazione|
|[CA2231](../code-quality/ca2231.md)|Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Contrassegnare i punti di ingresso del Windows Form con STAThread|
|[CA2235](../code-quality/ca2235.md)|Contrassegnare tutti i campi non serializzabili|
|[CA2236](../code-quality/ca2236.md)|Chiamare metodi della classe di base su tipi ISerializable|
|[CA2237](../code-quality/ca2237.md)|Contrassegnare i tipi ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementare correttamente i metodi di serializzazione|
|[CA2240](../code-quality/ca2240.md)|Implementare ISerializable in modo corretto|
|[CA2241](../code-quality/ca2241.md)|Specificare argomenti corretti ai metodi di formattazione|
|[CA2242](../code-quality/ca2242.md)|Testare i valori NaN in modo corretto|