---
title: Set di regole Regole estese delle linee guida di progettazione per codice gestito
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: aad09901de2017ae14b65ec6e79f3153557c4d81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587641"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Set di regole Regole estese delle linee guida di progettazione per codice gestito

Il set di regole delle linee guida per la progettazione estesa Microsoft espande le regole delle linee guida di progettazione di base per massimizzare i problemi di usabilità e gestibilità segnalati. Le linee guida per la denominazione hanno un'enfasi aggiuntiva. È consigliabile includere questo set di regole se il progetto include il codice della libreria o se si desidera applicare gli standard più elevati per la scrittura di codice facile da gestire.

Le regole delle linee guida di progettazione estese includono tutte le regole del set di regole di [base della Guida di progettazione](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) , che include le regole nel set di regole [consigliate gestite](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

Nella tabella seguente vengono descritte tutte le regole del set di regole delle linee guida di progettazione estese Microsoft.

|Regola|Descrizione|
|----------|-----------------|
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
|[CA1000](../code-quality/ca1000.md)|Non dichiarare membri statici su tipi generici|
|[CA1002](../code-quality/ca1002.md)|Non esporre elenchi generici|
|[CA1003](../code-quality/ca1003.md)|Usare istanze di gestori eventi generici|
|[CA1004](../code-quality/ca1004.md)|I metodi generici devono specificare parametri di tipo|
|[CA1005](../code-quality/ca1005.md)|Evitare un uso eccessivo di parametri nei tipi generici|
|[CA1006](../code-quality/ca1006.md)|Non annidare tipi generici nelle firme dei membri|
|[CA1007](../code-quality/ca1007.md)|Usare generics dove appropriato|
|[CA1008](../code-quality/ca1008.md)|Le enumerazioni devono avere valore zero|
|[CA1010](../code-quality/ca1010.md)|Le raccolte devono implementare un'interfaccia generica|
|[CA1011](../code-quality/ca1011.md)|Provare a passare tipi di base come parametri|
|[CA1012](../code-quality/ca1012.md)|I tipi astratti non devono includere costruttori|
|[CA1013](../code-quality/ca1013.md)|Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione|
|[CA1014](../code-quality/ca1014.md)|Contrassegnare gli assembly con CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017.md)|Contrassegnare gli assembly con ComVisibleAttribute|
|[CA1018](../code-quality/ca1018.md)|Contrassegnare gli attributi con AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019.md)|Definire le funzioni di accesso per gli argomenti degli attributi|
|[CA1023](../code-quality/ca1023.md)|Gli indicizzatori non devono essere multidimensionali|
|[CA1024](../code-quality/ca1024.md)|Usare proprietà dove appropriato|
|[CA1025](../code-quality/ca1025.md)|Sostituire gli argomenti ripetitivi con una matrice di parametri|
|[CA1026](../code-quality/ca1026.md)|Evitare l'uso di parametri predefiniti|
|[CA1027](../code-quality/ca1027.md)|Contrassegnare le enumerazioni con FlagsAttribute|
|[CA1028](../code-quality/ca1028.md)|Le risorse di archiviazione dell'enumerazione devono essere Int32|
|[CA1030](../code-quality/ca1030.md)|Usare eventi dove appropriato|
|[CA1031](../code-quality/ca1031.md)|Non rilevare tipi di eccezione generali|
|[CA1032](../code-quality/ca1032.md)|Implementare costruttori di eccezioni standard|
|[CA1034](../code-quality/ca1034.md)|I tipi annidati non devono essere visibili|
|[CA1035](../code-quality/ca1035.md)|Le implementazioni di ICollection hanno membri fortemente tipizzati|
|[CA1036](../code-quality/ca1036.md)|Eseguire l'override di metodi su tipi confrontabili|
|[CA1038](../code-quality/ca1038.md)|Gli enumeratori devono essere fortemente tipizzati|
|[CA1039](../code-quality/ca1039.md)|Gli elenchi sono fortemente tipizzati|
|[CA1041](../code-quality/ca1041.md)|Specificare una proprietà ObsoleteAttribute.Message|
|[CA1043](../code-quality/ca1043.md)|Usare un argomento di tipo stringa o integrale per gli indicizzatori|
|[CA1044](../code-quality/ca1044.md)|Le proprietà non devono essere in sola scrittura|
|[CA1046](../code-quality/ca1046.md)|Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento|
|[CA1047](../code-quality/ca1047.md)|Non dichiarare membri protected nei tipi sealed|
|[CA1048](../code-quality/ca1048.md)|Non dichiarare membri virtuali nei tipi sealed|
|[CA1050](../code-quality/ca1050.md)|Dichiarare i tipi negli spazi dei nomi|
|[CA1051](../code-quality/ca1051.md)|Non dichiarare campi di istanza visibili|
|[CA1052](../code-quality/ca1052.md)|I tipi che contengono membri statici devono essere sealed|
|[CA1053](../code-quality/ca1053.md)|I tipi che contengono membri statici non devono avere costruttori|
|[CA1054](../code-quality/ca1054.md)|I parametri URI non devono essere stringhe|
|[CA1055](../code-quality/ca1055.md)|I valori restituiti URI non devono essere stringhe|
|[CA1056](../code-quality/ca1056.md)|Le proprietà URI non devono essere stringhe|
|[CA1057](../code-quality/ca1057.md)|Gli overload URI dei valori di stringa chiamano gli overload System.Uri|
|[CA1058](../code-quality/ca1058.md)|I tipi non devono estendere tipi di base specifici|
|[CA1059](../code-quality/ca1059.md)|I membri non devono esporre tipi concreti specifici|
|[CA1064](../code-quality/ca1064.md)|Le eccezioni devono essere pubbliche|
|[CA1500](../code-quality/ca1500.md)|I nomi delle variabili non devono corrispondere ai nomi dei campi|
|[CA1502](../code-quality/ca1502.md)|Evitare complessità eccessiva|
|[CA1708](../code-quality/ca1708.md)|Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole|
|[CA1716](../code-quality/ca1716.md)|Gli identificatori non devono corrispondere a parole chiave|
|[CA1801](../code-quality/ca1801.md)|Controllare i parametri non usati|
|[CA1804](../code-quality/ca1804.md)|Rimuovere variabili locali non usate|
|[CA1809](../code-quality/ca1809.md)|Evitare un numero eccessivo di variabili locali|
|[CA1810](../code-quality/ca1810.md)|Inizializzare i campi statici del tipo di riferimento inline|
|[CA1811](../code-quality/ca1811.md)|Evitare il codice privato non chiamato|
|[CA1812](../code-quality/ca1812.md)|Evitare classi interne prive di istanze|
|[CA1813](../code-quality/ca1813.md)|Evitare attributi unsealed|
|[CA1814](../code-quality/ca1814.md)|Preferire matrici di matrici rispetto a matrici multidimensionali|
|[CA1815](../code-quality/ca1815.md)|Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore|
|[CA1819](../code-quality/ca1819.md)|Le proprietà non devono restituire matrici|
|[CA1820](../code-quality/ca1820.md)|Testare le stringhe vuote usando la lunghezza di stringa|
|[CA1822](../code-quality/ca1822.md)|Contrassegna i membri come statici|
|[CA1823](../code-quality/ca1823.md)|Evitare campi privati non usati|
|[CA2201](../code-quality/ca2201.md)|Non generare tipi di eccezione riservati|
|[CA2205](../code-quality/ca2205.md)|Usare equivalenti gestiti dell'API Win32|
|[CA2208](../code-quality/ca2208.md)|Creare istanze di eccezioni di argomento correttamente|
|[CA2211](../code-quality/ca2211.md)|I campi non costanti non devono essere visibili|
|[CA2217](../code-quality/ca2217.md)|Non contrassegnare le enumerazioni con FlagsAttribute|
|[CA2219](../code-quality/ca2219.md)|Non generare eccezioni in clausole di eccezione|
|[CA2221](../code-quality/ca2221.md)|I finalizzatori devono essere protetti|
|[CA2222](../code-quality/ca2222.md)|Non diminuire la visibilità di membri ereditati|
|[CA2223](../code-quality/ca2223.md)|La differenza tra membri non deve limitarsi al tipo restituito|
|[CA2224](../code-quality/ca2224.md)|Eseguire l'override di Equals all'overload dell'operatore "uguale a"|
|[CA2225](../code-quality/ca2225.md)|Gli overload degli operatori hanno alternative con nome|
|[CA2226](../code-quality/ca2226.md)|Gli operatori devono avere overload simmetrici|
|[CA2227](../code-quality/ca2227.md)|Le proprietà di raccolte devono essere in sola lettura|
|[CA2230](../code-quality/ca2230.md)|Usare params per argomenti variabili|
|[CA2234](../code-quality/ca2234.md)|Passare oggetti System.Uri invece di stringhe|
|[CA2239](../code-quality/ca2239.md)|Specificare metodi di deserializzazione per i campi facoltativi|
|[CA1020](../code-quality/ca1020.md)|Evitare l'uso di spazi dei nomi con un numero ridotto di tipi|
|[CA1021](../code-quality/ca1021.md)|Evitare parametri out|
|[CA1040](../code-quality/ca1040.md)|Evitare l'uso di interfacce vuote|
|[CA1045](../code-quality/ca1045.md)|Non passare i tipi per riferimento|
|[CA1062](../code-quality/ca1062.md)|Convalidare gli argomenti di metodi pubblici|
|[CA1501](../code-quality/ca1501.md)|Evitare ereditarietà eccessiva|
|[CA1504](../code-quality/ca1504.md)|Controllare i nomi dei campi fuorvianti|
|[CA1505](../code-quality/ca1505.md)|Evitare codice non gestibile|
|[CA1506](../code-quality/ca1506.md)|Evitare un numero eccessivo di accoppiamenti tra classi|
|[CA1700](../code-quality/ca1700.md)|Non denominare 'Reserved' i valori di enumerazione|
|[CA1701](../code-quality/ca1701.md)|Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole|
|[CA1702](../code-quality/ca1702.md)|Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole|
|[CA1703](../code-quality/ca1703.md)|Le stringhe di risorsa devono essere digitate correttamente|
|[CA1704](../code-quality/ca1704.md)|Gli identificatori devono essere digitati correttamente|
|[CA1707](../code-quality/ca1707.md)|Gli identificatori non devono contenere caratteri di sottolineatura|
|[CA1709](../code-quality/ca1709.md)|Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole|
|[CA1710](../code-quality/ca1710.md)|Gli identificatori devono contenere il suffisso corretto|
|[CA1711](../code-quality/ca1711.md)|Gli identificatori non devono contenere un suffisso non corretto|
|[CA1712](../code-quality/ca1712.md)|Non usare nomi di tipo come prefisso nei valori di enumerazione|
|[CA1713](../code-quality/ca1713.md)|Non usare il prefisso Before o After negli eventi|
|[CA1714](../code-quality/ca1714.md)|Le enumerazioni con Flags devono avere nomi plurali|
|[CA1715](../code-quality/ca1715.md)|Gli identificatori devono contenere il prefisso corretto|
|[CA1717](../code-quality/ca1717.md)|Solo le enumerazioni con FlagsAttribute devono avere nomi plurali|
|[CA1719](../code-quality/ca1719.md)|I nomi dei parametri non devono corrispondere ai nomi dei membri|
|[CA1720](../code-quality/ca1720.md)|Gli identificatori non devono contenere nomi di tipo|
|[CA1721](../code-quality/ca1721.md)|I nomi delle proprietà non devono corrispondere ai metodi get|
|[CA1722](../code-quality/ca1722.md)|Gli identificatori non devono contenere il prefisso non corretto|
|[CA1724](../code-quality/ca1724.md)|I nomi dei tipi non devono corrispondere agli spazi dei nomi|
|[CA1725](../code-quality/ca1725.md)|I nomi dei parametri devono corrispondere alla dichiarazione di base|
|[CA1726](../code-quality/ca1726.md)|Usare termini preferiti|
|[CA2204](../code-quality/ca2204.md)|I valori letterali devono essere digitati correttamente|
