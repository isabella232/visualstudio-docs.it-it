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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305679"
---
# <a name="usage-warnings"></a>avvisi di utilizzo

Gli avvisi di utilizzo supportano il corretto utilizzo di .NET.

## <a name="in-this-section"></a>In questa sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1801: Controllare i parametri inutilizzati @ no__t-0|Una firma di metodo include un parametro non utilizzato nel corpo del metodo.|
|[CA1806: Non ignorare i risultati del metodo @ no__t-0|Un nuovo oggetto viene creato, ma non viene mai utilizzato oppure viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai utilizzata oppure un metodo COM o P/Invoke restituisce un HRESULT o un codice di errore che non viene mai utilizzato.|
|[CA1816: Chiamare GC. SuppressFinalize correttamente @ no__t-0|Un metodo che è un'implementazione di Dispose non chiama GC. SuppressFinalize; o un metodo che non è un'implementazione di Dispose chiama GC. SuppressFinalize; o un metodo chiama GC. SuppressFinalize e passa un valore diverso da this (Me in Visual Basic).|
|[CA2200: Rigenerazione per mantenere i dettagli dello stack @ no__t-0|Viene generata di nuovo un'eccezione, specificata in modo esplicito nell'istruzione throw. Se un'eccezione viene generata di nuovo tramite la specifica nell'istruzione throw, l'elenco di chiamate ai metodi tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso.|
|[CA2201: Non generare tipi di eccezione riservati @ no__t-0|In questo modo è difficile rilevare ed eseguire il debug dell'errore originale.|
|[CA2202: Non eliminare oggetti più volte @ no__t-0|Un'implementazione di metodo contiene percorsi del codice che potrebbero comportare più chiamate a System.IDisposable.Dispose o a un equivalente di Dispose (ad esempio un metodo Close() per alcuni tipi) sullo stesso oggetto.|
|[CA2204: I valori letterali devono essere digitati correttamente @ no__t-0|Una stringa letterale in un corpo del metodo contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.|
|[CA2205: Usare equivalenti gestiti dell'API Win32 @ no__t-0|È stato definito un metodo di platform invoke e è disponibile un metodo .NET con la funzionalità equivalente.|
|[CA2207: Inizializzare i campi statici del tipo di valore inline @ no__t-0|Un tipo di valore dichiara un costruttore statico esplicito. Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.|
|[CA2208: Creare istanze di eccezioni di argomento corrette @ no__t-0|Viene effettuata una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione che corrisponde a o deriva da ArgumentException oppure viene passato un argomento stringa non corretto a un costruttore con parametri di un tipo di eccezione che corrisponde a o deriva da ArgumentException.|
|[CA2211: I campi non costanti non devono essere visibili @ no__t-0|I campi statici che non sono costanti o di sola lettura non sono thread-safe. L'accesso a tale campo deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe.|
|[CA2212: Non contrassegnare i componenti serviti con WebMethod @ no__t-0|Un metodo in un tipo che eredita da System. EnterpriseServices. ServicedComponent è contrassegnato con System. Web. Services. WebMethodAttribute. Poiché WebMethodAttribute e un metodo ServicedComponent presentano comportamenti e requisiti di contesto e flusso di transazioni in conflitto tra loro, il comportamento del metodo non sarà corretto in determinati scenari.|
|[CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Un tipo che implementa System.IDisposable dichiara i campi di tipi che implementano anch'essi IDisposable. Il metodo Dispose del campo non viene chiamato dal metodo Dispose del tipo dichiarante.|
|[CA2214: Non chiamare metodi sottoponibili a override nei costruttori @ no__t-0|Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non sia stato eseguito.|
|[CA2215: I metodi Dispose devono chiamare la classe di base Dispose @ no__t-0|Se un tipo eredita da un tipo eliminabile, deve chiamare il metodo Dispose del tipo di base dal proprio metodo Dispose.|
|[CA2216: I tipi Disposable devono dichiarare Finalizer @ no__t-0|Un tipo che implementa System. IDisposable e contiene campi che suggeriscono l'uso di risorse non gestite, non implementa un finalizzatore come descritto da Object. Finalize.|
|[CA2217: Non contrassegnare le enumerazioni con FlagsAttribute @ no__t-0|Un'enumerazione visibile esternamente è contrassegnata con FlagsAttribute e contiene uno o più valori che non sono potenze di due o una combinazione degli altri valori definiti nell'enumerazione.|
|[CA2218: Eseguire l'override di GetHashCode all'override di Equals @ no__t-0|GetHashCode restituisce un valore, basato sull'istanza corrente, appropriato per algoritmi di hash e strutture dei dati come una tabella hash. Due oggetti dello stesso tipo e uguali devono restituire lo stesso codice hash.|
|[CA2219: Non generare eccezioni in clausole di eccezione @ no__t-0|Quando un'eccezione viene generata in una clausola finally o in una clausola fault, la nuova eccezione nasconde l'eccezione attiva. Quando un'eccezione viene generata in una clausola filter, il runtime rileva l'eccezione automaticamente. In questo modo è difficile rilevare ed eseguire il debug dell'errore originale.|
|[CA2220: I finalizzatori devono chiamare il finalizzatore della classe di base @ no__t-0|La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. A tale scopo, i tipi devono chiamare il metodo Finalize della classe di base nel proprio metodo Finalize.|
|[CA2221: I finalizzatori devono essere protetti @ no__t-0|I finalizzatori devono utilizzare il modificatore di accesso a livello di famiglia.|
|[CA2222: Non diminuire la visibilità del membro ereditato @ no__t-0|Non modificare il modificatore di accesso per i membri ereditati. La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo.|
|[CA2223: I membri devono essere diversi dal tipo restituito @ no__t-0|Nonostante Common Language Runtime consenta l'utilizzo di tipi restituiti per differenziare membri altrimenti identici, questa funzionalità non è inclusa nella specifica CLS (Common Language Specification) e non è una funzionalità comune dei linguaggi di programmazione .NET.|
|[CA2224: Eseguire l'override di Equals in overload operator uguale a @ no__t-0|Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue l'override di Object. Equals.|
|[CA2225: Gli overload degli operatori hanno alternative denominate @ no__t-0|È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato. Il membro alternativo denominato fornisce l'accesso alla stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.|
|[CA2226: Gli operatori devono avere Overload simmetrici @ no__t-0|Un tipo implementa l'operatore di uguaglianza o disuguaglianza e non implementa l'operatore opposto.|
|[CA2227: Le proprietà della raccolta devono essere di sola lettura @ no__t-0|Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri.|
|[CA2228: Non fornire formati di risorse non rilasciati @ no__t-0|I file di risorse compilati con le versioni non definitive di .NET potrebbero non essere utilizzabili dalle versioni supportate di .NET.|
|[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)|Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.|
|[CA2230: USA params per gli argomenti variabili @ no__t-0|Un tipo pubblico o protetto contiene un metodo pubblico o protetto che utilizza la convenzione di chiamata VarArgs anziché la parola chiave params.|
|[CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Un tipo di valore esegue l'override di `Object.Equals` ma non implementa l'operatore di uguaglianza.|
|[CA2232: Contrassegnare Windows Forms punti di ingresso con STAThread @ no__t-0|STAThreadAttribute indica che il modello di threading COM per l'applicazione è un apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente.|
|[CA2233: Le operazioni non devono essere overflow @ no__t-0|Le operazioni aritmetiche non devono essere eseguite senza prima convalidare gli operandi, per assicurarsi che il risultato dell'operazione non sia compreso nell'intervallo dei valori possibili per i tipi di dati necessari.|
|[CA2234: Passare oggetti System. Uri invece di stringhe @ no__t-0|Viene effettuata una chiamata a un metodo che dispone di un parametro di stringa il cui nome contiene "uri", "URI", "urn", "URN", "url" o "URL".  Il tipo dichiarante del metodo contiene un overload del metodo corrispondente con un parametro System.Uri.|
|[CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.|
|[CA2236: Chiamare metodi della classe di base su tipi ISerializable @ no__t-0|Per correggere una violazione di questa regola, chiamare il costruttore di serializzazione o il metodo GetObjectData del tipo di base dal costruttore o dal metodo del tipo derivato corrispondente.|
|[CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute @ no__t-0|Per essere riconosciuti dal Common Language Runtime come serializzabile, i tipi devono essere contrassegnati con l'attributo SerializableAttribute anche se il tipo utilizza una routine di serializzazione personalizzata tramite l'implementazione dell'interfaccia ISerializable.|
|[CA2238: Implementare correttamente i metodi di serializzazione @ no__t-0|Un metodo che gestisce un evento di serializzazione non dispone della visibilità, del tipo restituito o della firma corretta.|
|[CA2239: Fornire metodi di deserializzazione per i campi facoltativi @ no__t-0|Un tipo dispone di un campo contrassegnato con l'attributo System. Runtime. Serialization. OptionalFieldAttribute e il tipo non fornisce metodi di gestione degli eventi di deserializzazione.|
|[CA2240: Implementare ISerializable correttamente @ no__t-0|Per correggere una violazione di questa regola, rendere visibile e sottoponibile a override il metodo GetObjectData e verificare che tutti i campi di istanza siano inclusi nel processo di serializzazione o contrassegnati in modo esplicito con l'attributo NonSerializedAttribute.|
|[CA2241: Fornire argomenti corretti ai metodi di formattazione @ no__t-0|L'argomento di formato passato a System. String. Format non contiene un elemento di formato corrispondente a ogni argomento dell'oggetto o viceversa.|
|[CA2242: Test per NaN correttamente @ no__t-0|Questa espressione consente di testare un valore rispetto a Single.Nan o Double.Nan. Utilizzare Single.IsNan(Single) o Double.IsNan(Double) per testare il valore.|
|[CA2243: I valori letterali stringa di attributo devono essere analizzati correttamente @ no__t-0|Il parametro valore letterale stringa di un attributo non viene analizzato correttamente per un URL, un GUID o una versione.|