---
title: Set di regole Regole estese delle linee guida di progettazione per codice gestito
ms.date: 11/04/2016
description: Informazioni sul set di regole delle linee guida di progettazione estese in Visual Studio, in particolare sull'usabilità e sulla manutenibilità. Vedere le descrizioni delle regole.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: d284dec49e0973f2781f00f178fa193b52797085
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632028"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Set di regole Regole estese delle linee guida di progettazione per codice gestito

Il set di regole Microsoft Extended Design Guideline Rules si espande in base alle regole delle linee guida di progettazione di base per ottimizzare i problemi di usabilità e manutenibilità segnalati. Viene posta particolare attenzione alle linee guida per la denominazione. È consigliabile includere questo set di regole se il progetto include codice di libreria o se si vogliono applicare gli standard più elevati per la scrittura di codice facile da gestire.

Le regole delle linee guida per la progettazione estese includono tutte le regole del set di regole Basic [Design Guideline Rules,](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) che include le regole nel set di regole [managed recommended rules.](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

Nella tabella seguente vengono descritte tutte le regole del set di regole Microsoft Extended Design Guideline Rules.

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
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Non dichiarare membri statici su tipi generici|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Non esporre elenchi generici|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Usare istanze di gestori eventi generici|
|[CA1004](../code-quality/ca1004.md)|I metodi generici devono specificare parametri di tipo|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Evitare un uso eccessivo di parametri nei tipi generici|
|[CA1006](../code-quality/ca1006.md)|Non annidare tipi generici nelle firme dei membri|
|[CA1007](../code-quality/ca1007.md)|Usare generics dove appropriato|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Le enumerazioni devono avere valore zero|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Le raccolte devono implementare un'interfaccia generica|
|[CA1011](../code-quality/ca1011.md)|Provare a passare tipi di base come parametri|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|I tipi astratti non devono includere costruttori|
|[CA1013](../code-quality/ca1013.md)|Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Contrassegnare gli assembly con CLSCompliantAttribute|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Contrassegnare gli assembly con ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Contrassegnare gli attributi con AttributeUsageAttribute|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Definire le funzioni di accesso per gli argomenti degli attributi|
|[CA1023](../code-quality/ca1023.md)|Gli indicizzatori non devono essere multidimensionali|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Usare proprietà dove appropriato|
|[CA1025](../code-quality/ca1025.md)|Sostituire gli argomenti ripetitivi con una matrice di parametri|
|[CA1026](../code-quality/ca1026.md)|Evitare l'uso di parametri predefiniti|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Contrassegnare le enumerazioni con FlagsAttribute|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|Le risorse di archiviazione dell'enumerazione devono essere Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Usare eventi dove appropriato|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Non rilevare tipi di eccezione generali|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementare costruttori di eccezioni standard|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|I tipi annidati non devono essere visibili|
|[CA1035](../code-quality/ca1035.md)|Le implementazioni di ICollection hanno membri fortemente tipizzati|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Eseguire l'override di metodi su tipi confrontabili|
|[CA1038](../code-quality/ca1038.md)|Gli enumeratori devono essere fortemente tipizzati|
|[CA1039](../code-quality/ca1039.md)|Gli elenchi sono fortemente tipizzati|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|Specificare una proprietà ObsoleteAttribute.Message|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Usare un argomento di tipo stringa o integrale per gli indicizzatori|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Le proprietà non devono essere in sola scrittura|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Non dichiarare membri protected nei tipi sealed|
|[CA1048](../code-quality/ca1048.md)|Non dichiarare membri virtuali nei tipi sealed|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Dichiarare i tipi negli spazi dei nomi|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Non dichiarare campi di istanza visibili|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|I tipi che contengono membri statici devono essere sealed|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|I tipi che contengono membri statici non devono avere costruttori|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|I parametri URI non devono essere stringhe|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|I valori restituiti URI non devono essere stringhe|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Le proprietà URI non devono essere stringhe|
|[CA1057](../code-quality/ca1057.md)|Gli overload URI dei valori di stringa chiamano gli overload System.Uri|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|I tipi non devono estendere tipi di base specifici|
|[CA1059](../code-quality/ca1059.md)|I membri non devono esporre tipi concreti specifici|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Le eccezioni devono essere pubbliche|
|[CA1500](../code-quality/ca1500.md)|I nomi delle variabili non devono corrispondere ai nomi dei campi|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Evitare complessità eccessiva|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Gli identificatori non devono corrispondere a parole chiave|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Controllare i parametri non usati|
|[CA1804](../code-quality/ca1804.md)|Rimuovere variabili locali non usate|
|[CA1809](../code-quality/ca1809.md)|Evitare un numero eccessivo di variabili locali|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Inizializzare i campi statici del tipo di riferimento inline|
|[CA1811](../code-quality/ca1811.md)|Evitare il codice privato non chiamato|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Evitare classi interne prive di istanze|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Evitare attributi unsealed|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Preferire matrici di matrici rispetto a matrici multidimensionali|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Le proprietà non devono restituire matrici|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testare le stringhe vuote usando la lunghezza di stringa|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Contrassegna i membri come statici|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Evitare campi privati non usati|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Non generare tipi di eccezione riservati|
|[CA2205](../code-quality/ca2205.md)|Usare equivalenti gestiti dell'API Win32|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Creare istanze di eccezioni di argomento correttamente|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|I campi non costanti non devono essere visibili|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Non contrassegnare le enumerazioni con FlagsAttribute|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Non generare eccezioni in clausole di eccezione|
|[CA2221](../code-quality/ca2221.md)|I finalizzatori devono essere protetti|
|[CA2222](../code-quality/ca2222.md)|Non diminuire la visibilità di membri ereditati|
|[CA2223](../code-quality/ca2223.md)|La differenza tra membri non deve limitarsi al tipo restituito|
|[CA2224](../code-quality/ca2224.md)|Eseguire l'override di Equals all'overload dell'operatore "uguale a"|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Gli overload degli operatori hanno alternative con nome|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Gli operatori devono avere overload simmetrici|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Le proprietà di raccolte devono essere in sola lettura|
|[CA2230](../code-quality/ca2230.md)|Usare params per argomenti variabili|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Passare oggetti System.Uri invece di stringhe|
|[CA2239](../code-quality/ca2239.md)|Specificare metodi di deserializzazione per i campi facoltativi|
|[CA1020](../code-quality/ca1020.md)|Evitare l'uso di spazi dei nomi con un numero ridotto di tipi|
|[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021)|Evitare parametri out|
|[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040)|Evitare l'uso di interfacce vuote|
|[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045)|Non passare i tipi per riferimento|
|[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062)|Convalidare gli argomenti di metodi pubblici|
|[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)|Evitare ereditarietà eccessiva|
|[CA1504](../code-quality/ca1504.md)|Controllare i nomi dei campi fuorvianti|
|[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)|Evitare codice non gestibile|
|[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)|Evitare un numero eccessivo di accoppiamenti tra classi|
|[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700)|Non denominare 'Reserved' i valori di enumerazione|
|[CA1701](../code-quality/ca1701.md)|Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole|
|[CA1702](../code-quality/ca1702.md)|Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole|
|[CA1703](../code-quality/ca1703.md)|Le stringhe di risorsa devono essere digitate correttamente|
|[CA1704](../code-quality/ca1704.md)|Gli identificatori devono essere digitati correttamente|
|[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707)|Gli identificatori non devono contenere caratteri di sottolineatura|
|[CA1709](../code-quality/ca1709.md)|Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole|
|[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)|Gli identificatori devono contenere il suffisso corretto|
|[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711)|Gli identificatori non devono contenere un suffisso non corretto|
|[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712)|Non usare nomi di tipo come prefisso nei valori di enumerazione|
|[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713)|Non usare il prefisso Before o After negli eventi|
|[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714)|Le enumerazioni con Flags devono avere nomi plurali|
|[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715)|Gli identificatori devono contenere il prefisso corretto|
|[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717)|Solo le enumerazioni con FlagsAttribute devono avere nomi plurali|
|[CA1719](../code-quality/ca1719.md)|I nomi dei parametri non devono corrispondere ai nomi dei membri|
|[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720)|Gli identificatori non devono contenere nomi di tipo|
|[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721)|I nomi delle proprietà non devono corrispondere ai metodi get|
|[CA1722](../code-quality/ca1722.md)|Gli identificatori non devono contenere il prefisso non corretto|
|[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724)|I nomi dei tipi non devono corrispondere agli spazi dei nomi|
|[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725)|I nomi dei parametri devono corrispondere alla dichiarazione di base|
|[CA1726](../code-quality/ca1726.md)|Usare termini preferiti|
|[CA2204](../code-quality/ca2204.md)|I valori letterali devono essere digitati correttamente|
