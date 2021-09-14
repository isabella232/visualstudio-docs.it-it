---
title: Set di regole base di correttezza per codice gestito
ms.date: 11/04/2016
description: Informazioni sul set di regole di base delle regole di correttezza in Visual Studio, in particolare sugli errori logici e sugli errori comuni delle API del framework. Vedere le descrizioni delle regole.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 02c7b660c6aba7f25e631a14146582f08c3d5117
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632982"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Set di regole base di correttezza per codice gestito

Il set di regole Basic Correctness Rules (Regole di correttezza di base) è in particolare in particolare sugli errori logici e sugli errori comuni nell'utilizzo delle API del framework. Le regole di correttezza di base includono le regole nel set [di regole gestite consigliate.](managed-recommended-rules-rule-set-for-managed-code.md)

Nella tabella seguente vengono descritte tutte le regole del set di regole Microsoft Basic Correctness Rules.

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
