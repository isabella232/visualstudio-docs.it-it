---
title: Set di regole estese di correttezza per codice gestito
ms.date: 11/04/2016
description: Informazioni sul set di regole di correttezza estesa in Visual Studio, utile per l'interoperabilità COM e le applicazioni per dispositivi mobili. Vedere le descrizioni delle regole.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: a664b01f5fec771f4891389d3ec807d2e4976797
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114173"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Set di regole estese di correttezza per codice gestito

Il set di regole Microsoft Extended Correctness Rules ottimizza la logica e gli errori di utilizzo del framework segnalati dall'analisi del codice. Particolare attenzione viene posta su scenari specifici, ad esempio l'interoperabilità COM e le applicazioni per dispositivi mobili. È consigliabile includere questo set di regole se uno di questi scenari si applica al progetto o per individuare altri problemi nel progetto.

Il set di regole di Microsoft Extended Correctness Rules include le regole incluse nel set di regole Regole di correttezza di base, che contiene le regole presenti nel set di regole regole consigliate [gestite.](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) [](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)

Nella tabella seguente vengono descritte tutte le regole del set di regole di Microsoft Extended Correctness Rules.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|I tipi proprietari di campi Disposable devono essere Disposable|
|[CA1009](../code-quality/ca1009.md)|Dichiarare correttamente i gestori eventi|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Contrassegnare gli assembly con AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|I metodi di interfaccia devono essere richiamabili dai tipi figlio|
|[CA1049](../code-quality/ca1049.md)|I tipi delle risorse native devono essere disposable|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Spostare P/Invoke nella classe NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Non nascondere i metodi di una classe base|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implementare IDisposable correttamente|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Non generare eccezioni in posizioni non previste|
|[CA1301](../code-quality/ca1301.md)|Evitare tasti di scelta rapida duplicati|
|[CA1400](../code-quality/ca1400.md)|I punti di ingresso P/Invoke devono esistere|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|I P/Invoke non devono essere visibili|
|[CA1403](../code-quality/ca1403.md)|I tipi layout automatici non devono essere visibili a COM|
|[CA1404](../code-quality/ca1404.md)|Chiamare GetLastError immediatamente dopo P/Invoke|
|[CA1405](../code-quality/ca1405.md)|I tipi di base del tipo visibile a COM devono essere visibili a COM|
|[CA1410](../code-quality/ca1410.md)|I metodi di registrazione COM devono corrispondere|
|[CA1415](../code-quality/ca1415.md)|Dichiarare correttamente i P/Invoke|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Rimuovere i finalizzatori vuoti|
|[CA1900](../code-quality/ca1900.md)|I campi dei tipi di valore devono essere portabili|
|[CA1901](../code-quality/ca1901.md)|Le dichiarazioni P/Invoke devono essere portabili|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Non bloccare oggetti con identità debole|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Controllare la vulnerabilità della sicurezza nelle query SQL|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Specificare il marshalling per gli argomenti di stringa P/Invoke|
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
|[CA2141](../code-quality/ca2141.md)|I metodi Transparent non devono soddisfare LinkDemands|
|[CA2146](../code-quality/ca2146.md)|I tipi devono essere Critical almeno come le interfacce e i tipi base relativi|
|[CA2147](../code-quality/ca2147.md)|I metodi Transparent non possono usare asserzioni di sicurezza|
|[CA2149](../code-quality/ca2149.md)|I metodi Transparent non devono effettuare chiamate nel codice nativo|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Eseguire il rethrow per mantenere i dettagli dello stack|
|[CA2202](../code-quality/ca2202.md)|Non eliminare gli oggetti più volte|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Inizializzare i campi statici dei tipi di valore inline|
|[CA2212](../code-quality/ca2212.md)|Non contrassegnare componenti serviti con WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|I campi eliminabili devono essere eliminati|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Non chiamare metodi sottoponibili a override nei costruttori|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|I tipi eliminabili devono dichiarare un finalizzatore|
|[CA2220](../code-quality/ca2220.md)|I finalizzatori devono chiamare il finalizzatore della classe di base|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implementare costruttori di serializzazione|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Contrassegnare i punti di ingresso del Windows Form con STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Contrassegnare tutti i campi non serializzabili|
|[CA2236](../code-quality/ca2236.md)|Chiamare metodi della classe di base su tipi ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Contrassegnare i tipi ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementare correttamente i metodi di serializzazione|
|[CA2240](../code-quality/ca2240.md)|Implementare ISerializable in modo corretto|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Specificare argomenti corretti ai metodi di formattazione|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Testare i valori NaN in modo corretto|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Le enumerazioni devono avere valore zero|
|[CA1013](../code-quality/ca1013.md)|Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Non passare valori letterali come parametri localizzati|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizzare le stringhe in lettere maiuscole|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|Non ignorare i risultati dei metodi|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|Chiamare GC.SuppressFinalize correttamente|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Le proprietà non devono restituire matrici|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testare le stringhe vuote usando la lunghezza di stringa|
|[CA1903](../code-quality/ca1903.md)|Usare solo API della versione di .NET Framework di destinazione|
|[CA2004](../code-quality/ca2004.md)|Rimuovere le chiamate a GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Usare SafeHandle per incapsulare le risorse native|
|[CA2102](../code-quality/ca2102.md)|Individuare le eccezioni non CLSCompliant nei gestori generali|
|[CA2104](../code-quality/ca2104.md)|Non dichiarare tipi di riferimento modificabili in sola lettura|
|[CA2105](../code-quality/ca2105.md)|I campi di matrici non devono essere di sola lettura|
|[CA2106](../code-quality/ca2106.md)|Asserzioni protette|
|[CA2115](../code-quality/ca2115.md)|Chiamare GC.KeepAlive durante l'uso di risorse native|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Impostare come sealed i metodi che soddisfano interfacce private|
|[CA2120](../code-quality/ca2120.md)|Proteggere i costruttori di serializzazione|
|[CA2121](../code-quality/ca2121.md)|I costruttori statici devono essere privati|
|[CA2130](../code-quality/ca2130.md)|Le costanti SecurityCritical devono essere Transparent|
|[CA2205](../code-quality/ca2205.md)|Usare equivalenti gestiti dell'API Win32|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|I metodi Dispose devono chiamare Dispose della classe di base|
|[CA2221](../code-quality/ca2221.md)|I finalizzatori devono essere protetti|
|[CA2222](../code-quality/ca2222.md)|Non diminuire la visibilità di membri ereditati|
|[CA2223](../code-quality/ca2223.md)|La differenza tra membri non deve limitarsi al tipo restituito|
|[CA2224](../code-quality/ca2224.md)|Eseguire l'override di Equals all'overload dell'operatore "uguale a"|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Gli operatori devono avere overload simmetrici|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Le proprietà di raccolte devono essere in sola lettura|
|[CA2239](../code-quality/ca2239.md)|Specificare metodi di deserializzazione per i campi facoltativi|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementare costruttori di eccezioni standard|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|I parametri URI non devono essere stringhe|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|I valori restituiti URI non devono essere stringhe|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Le proprietà URI non devono essere stringhe|
|[CA1057](../code-quality/ca1057.md)|Gli overload URI dei valori di stringa chiamano gli overload System.Uri|
|[CA1402](../code-quality/ca1402.md)|Evitare gli overload nelle interfacce visibili a COM|
|[CA1406](../code-quality/ca1406.md)|Evitare gli argomenti Int64 per i client Visual Basic 6|
|[CA1407](../code-quality/ca1407.md)|Evitare i membri statici nei tipi visibili a COM|
|[CA1408](../code-quality/ca1408.md)|Non usare AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409.md)|I tipi visibili a COM devono essere creabili|
|[CA1411](../code-quality/ca1411.md)|I metodi di registrazione COM non devono essere visibili|
|[CA1412](../code-quality/ca1412.md)|Contrassegnare le interfacce ComSource come IDispatch|
|[CA1413](../code-quality/ca1413.md)|Evitare i campi non pubblici nei tipi valore visibili a COM|
|[CA1414](../code-quality/ca1414.md)|Contrassegnare gli argomenti P/Invoke booleani con MarshalAs|
|[CA1600](../code-quality/ca1600.md)|Non impostare la priorità del processo su Inattivo|
|[CA1601](../code-quality/ca1601.md)|Non usare i timer che impediscono le modifiche allo stato di potenza|
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|Contrassegnare gli assembly con NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001.md)|Evitare le chiamate a metodi problematici|
|[CA2003](../code-quality/ca2003.md)|Non considerare i fiber come i thread|
|[CA2135](../code-quality/ca2135.md)|Gli assembly di livello 2 non devono contenere LinkDemand|
|[CA2136](../code-quality/ca2136.md)|I membri non devono avere annotazioni di trasparenza in conflitto|
|[CA2139](../code-quality/ca2139.md)|I metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142.md)|Il codice Transparent non deve essere protetto con LinkDemand|
|[CA2143](../code-quality/ca2143.md)|I metodi Transparent non devono usare SecurityDemand|
|[CA2144](../code-quality/ca2144.md)|Il codice Transparent non deve caricare assembly da matrici di byte|
|[CA2145](../code-quality/ca2145.md)|I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|I valori letterali devono essere digitati correttamente|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|I campi non costanti non devono essere visibili|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Non contrassegnare le enumerazioni con FlagsAttribute|
|[CA2218](../code-quality/ca2218.md)|Eseguire l'override di GetHashCode all'override di Equals|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Non generare eccezioni in clausole di eccezione|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Gli overload degli operatori hanno alternative con nome|
|[CA2228](../code-quality/ca2228.md)|Non specificare formati di risorse non rilasciati|
|[CA2230](../code-quality/ca2230.md)|Usare params per argomenti variabili|
|[CA2233](../code-quality/ca2233.md)|Evitare l'overflow delle operazioni|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Passare oggetti System.Uri invece di stringhe|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|I valori letterali stringa di attributo devono essere analizzati correttamente|
