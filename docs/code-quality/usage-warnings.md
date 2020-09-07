---
title: avvisi di utilizzo
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd2f5919b0f48290ecc14cf71295e2af0bac4748
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509718"
---
# <a name="usage-warnings"></a>avvisi di utilizzo

Gli avvisi di utilizzo supportano il corretto utilizzo di .NET.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1801: Controllare i parametri non usati](../code-quality/ca1801.md)|Una firma di metodo include un parametro non utilizzato nel corpo del metodo.|
|[CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816.md)|Un metodo che costituisce un'implementazione di Dispose non chiama GC.SuppressFinalize oppure un metodo che non costituisce un'implementazione di Dispose chiama GC.SuppressFinalize oppure un metodo chiama GC.SuppressFinalize e passa un elemento diverso da this (Me in Visual Basic).|
|[CA2200: Eseguire il rethrow per mantenere i dettagli dello stack](../code-quality/ca2200.md)|Viene generata di nuovo un'eccezione, specificata in modo esplicito nell'istruzione throw. Se un'eccezione viene generata di nuovo tramite la specifica nell'istruzione throw, l'elenco di chiamate ai metodi tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso.|
|[CA2201: Non generare tipi di eccezione riservati](../code-quality/ca2201.md)|In questo modo è difficile rilevare ed eseguire il debug dell'errore originale.|
|[CA2202: Non eliminare gli oggetti più volte](../code-quality/ca2202.md)|Un'implementazione di metodo contiene percorsi del codice che potrebbero comportare più chiamate a System.IDisposable.Dispose o a un equivalente di Dispose (ad esempio un metodo Close() per alcuni tipi) sullo stesso oggetto.|
|[CA2207: Inizializzare i campi statici dei tipi di valore inline](../code-quality/ca2207.md)|Un tipo di valore dichiara un costruttore statico esplicito. Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.|
|[CA2208: Creare istanze di eccezioni di argomento correttamente](../code-quality/ca2208.md)|Viene effettuata una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione che corrisponde a o deriva da ArgumentException oppure viene passato un argomento stringa non corretto a un costruttore con parametri di un tipo di eccezione che corrisponde a o deriva da ArgumentException.|
|[CA2211: I campi non costanti non devono essere visibili](../code-quality/ca2211.md)|I campi statici che non sono costanti o di sola lettura non sono thread-safe. L'accesso a tale campo deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe.|
|[CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213.md)|Un tipo che implementa System.IDisposable dichiara i campi di tipi che implementano anch'essi IDisposable. Il metodo Dispose del campo non viene chiamato dal metodo Dispose del tipo dichiarante.|
|[CA2214: Non chiamare metodi sottoponibili a override nei costruttori](../code-quality/ca2214.md)|Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non sia stato eseguito.|
|[CA2215: I metodi Dispose devono chiamare Dispose della classe di base](../code-quality/ca2215.md)|Se un tipo eredita da un tipo eliminabile, deve chiamare il metodo Dispose del tipo di base dal proprio metodo Dispose.|
|[CA2216: I tipi eliminabili devono dichiarare un finalizzatore](../code-quality/ca2216.md)|Un tipo che implementa System. IDisposable e contiene campi che suggeriscono l'uso di risorse non gestite, non implementa un finalizzatore come descritto da Object. Finalize.|
|[CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217.md)|Un'enumerazione visibile esternamente è contrassegnata con FlagsAttribute e contiene uno o più valori che non sono potenze di due o una combinazione degli altri valori definiti nell'enumerazione.|
|[CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219.md)|Quando un'eccezione viene generata in una clausola finally o in una clausola fault, la nuova eccezione nasconde l'eccezione attiva. Quando un'eccezione viene generata in una clausola filter, il runtime rileva l'eccezione automaticamente. In questo modo è difficile rilevare ed eseguire il debug dell'errore originale.|
|[CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225.md)|È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato. Il membro alternativo denominato fornisce l'accesso alla stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.|
|[CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226.md)|Un tipo implementa l'operatore di uguaglianza o disuguaglianza e non implementa l'operatore opposto.|
|[CA2227: Le proprietà di raccolte devono essere in sola lettura](../code-quality/ca2227.md)|Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri.|
|[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229.md)|Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.|
|[CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231.md)|Un tipo di valore esegue l'override di `Object.Equals` , ma non implementa l'operatore di uguaglianza.|
|[CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread](../code-quality/ca2232.md)|STAThreadAttribute indica che il modello di threading COM per l'applicazione è un apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente.|
|[CA2233: Evitare l'overflow delle operazioni](../code-quality/ca2233.md)|Le operazioni aritmetiche non devono essere eseguite senza prima convalidare gli operandi, per assicurarsi che il risultato dell'operazione non sia compreso nell'intervallo dei valori possibili per i tipi di dati necessari.|
|[CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234.md)|Viene effettuata una chiamata a un metodo che dispone di un parametro di stringa il cui nome contiene "uri", "URI", "urn", "URN", "url" o "URL".  Il tipo dichiarante del metodo contiene un overload del metodo corrispondente con un parametro System.Uri.|
|[CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235.md)|Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.|
|[CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236.md)|Per correggere una violazione di questa regola, chiamare il costruttore di serializzazione o il metodo GetObjectData del tipo di base dal costruttore o dal metodo del tipo derivato corrispondente.|
|[CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237.md)|Per essere riconosciuti dal Common Language Runtime come serializzabile, i tipi devono essere contrassegnati con l'attributo SerializableAttribute anche se il tipo utilizza una routine di serializzazione personalizzata tramite l'implementazione dell'interfaccia ISerializable.|
|[CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238.md)|Un metodo che gestisce un evento di serializzazione non dispone della visibilità, del tipo restituito o della firma corretta.|
|[CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239.md)|Un tipo dispone di un campo contrassegnato con l'attributo System. Runtime. Serialization. OptionalFieldAttribute e il tipo non fornisce metodi di gestione degli eventi di deserializzazione.|
|[CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240.md)|Per correggere una violazione di questa regola, rendere visibile e sottoponibile a override il metodo GetObjectData e verificare che tutti i campi di istanza siano inclusi nel processo di serializzazione o contrassegnati in modo esplicito con l'attributo NonSerializedAttribute.|
|[CA2241: Specificare argomenti corretti ai metodi di formattazione](../code-quality/ca2241.md)|L'argomento di formato passato a System. String. Format non contiene un elemento di formato corrispondente a ogni argomento dell'oggetto o viceversa.|
|[CA2242: Testare i valori NaN in modo corretto](../code-quality/ca2242.md)|Questa espressione consente di testare un valore rispetto a Single.Nan o Double.Nan. Utilizzare Single.IsNan(Single) o Double.IsNan(Double) per testare il valore.|
|[CA2243: I valori letterali stringa di attributo devono essere analizzati correttamente](../code-quality/ca2243.md)|Il parametro valore letterale stringa di un attributo non viene analizzato correttamente per un URL, un GUID o una versione.|
|[CA2244: Non duplicare inizializzazioni di elementi indicizzati](../code-quality/ca2244.md)|Un inizializzatore di oggetto ha più di un inizializzatore di elemento indicizzato con lo stesso indice costante. Tutti tranne l'ultimo inizializzatore sono ridondanti.|
|[CA2245: Non assegnare una proprietà a se stessa](../code-quality/ca2245.md)|Una proprietà è stata assegnata per errore a se stessa.|
|[CA2246: Non assegnare un simbolo e il relativo membro nella stessa istruzione](../code-quality/ca2246.md)|Non è consigliabile assegnare un simbolo e il relativo membro, ovvero un campo o una proprietà, nella stessa istruzione. Non è chiaro se l'accesso ai membri fosse destinato a usare il valore precedente del simbolo prima dell'assegnazione o del nuovo valore dall'assegnazione in questa istruzione.|
|[CA2247: L'argomento passato al costruttore TaskCompletionSource deve essere l'enumerazione TaskCreationOptions invece dell'enumerazione TaskContinuationOptions](../code-quality/ca2246.md)|TaskCompletionSource dispone di costruttori che accettano TaskCreationOptions che controllano l'attività sottostante e i costruttori che accettano lo stato dell'oggetto archiviato nell'attività.  Se si passa accidentalmente un TaskContinuationOptions anziché un TaskCreationOptions, la chiamata tratta le opzioni come stato.|
|[CA2248: specificare l'argomento ' enum ' corretto per ' enum. HasFlag '](../code-quality/ca2248.md)|Il tipo enum passato come argomento alla chiamata al `HasFlag` metodo è diverso dal tipo enum chiamante.|
|[CA2249: Provare a usare String.Contains invece di String.IndexOf](../code-quality/ca2249.md)|Le chiamate a in `string.IndexOf` cui viene usato il risultato per verificare la presenza o l'assenza di una sottostringa possono essere sostituite da `string.Contains` .|
