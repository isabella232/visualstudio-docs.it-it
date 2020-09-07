---
title: Stato della porta della regola FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508366"
---
# <a name="fxcop-rule-port-status"></a>Stato della porta della regola FxCop

Se in precedenza è stata usata l'analisi statica del codice in Visual Studio, è possibile chiedersi quali di queste regole sono disponibili nell'implementazione corrente come [analizzatori FxCop](install-fxcop-analyzers.md). In questa pagina sono elencate le regole che sono state trasferite. Vedere [regole non portate](fxcop-unported-rules.md) per quelle che non sono state trasferite e se sono presenti piani per la loro porta.

## <a name="ported-rules"></a>Regole trasferite

La [pagina della documentazione generata automaticamente](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) nel repository Roslyn-Analyzers include l'elenco più aggiornato delle regole che sono state trasferite agli analizzatori FxCop. Questa pagina contiene anche informazioni aggiuntive, ad esempio se la regola è abilitata per impostazione predefinita e se è associata a una *correzione del codice*. Le[correzioni del codice](../ide/quick-actions.md) sono correzioni con un solo clic disponibili nel menu icona lampadina in Visual Studio.

A partire dalla data di questa pagina, l'elenco di regole FxCop che sono state trasferite agli [analizzatori FxCop](install-fxcop-analyzers.md) include:

ID regola | Titolo
--------|---------
[CA1000](ca1000.md) | Non dichiarare membri statici su tipi generici
[CA1001](ca1001.md) | I tipi proprietari di campi Disposable devono essere Disposable
[CA1002](ca1002.md) | Non esporre elenchi generici
[CA1003](ca1003.md) | Usare istanze di gestori eventi generici
[CA1005](ca1005.md) | Evitare un uso eccessivo di parametri nei tipi generici
[CA1008](ca1008.md) | Le enumerazioni devono avere valore zero
[CA1010](ca1010.md) | Le raccolte devono implementare un'interfaccia generica
[CA1012](ca1012.md) | I tipi astratti non devono includere costruttori
[CA1014](ca1014.md) | Contrassegnare gli assembly con CLSCompliant
[CA1016](ca1016.md) | Contrassegnare gli assembly con la versione dell'assembly
[CA1017](ca1017.md) | Contrassegnare gli assembly con ComVisible
[CA1018](ca1018.md) | Contrassegnare gli attributi con AttributeUsageAttribute
[CA1019](ca1019.md) | Definire le funzioni di accesso per gli argomenti degli attributi
[CA1021](ca1021.md) | Evitare parametri out
[CA1024](ca1024.md) | Usare proprietà dove appropriato
[CA1027](ca1027.md) | Contrassegnare le enumerazioni con FlagsAttribute
[CA1028](ca1028.md) | L'archiviazione enum deve essere Int32
[CA1030](ca1030.md) | Usare eventi dove appropriato
[CA1031](ca1031.md) | Non rilevare tipi di eccezione generali
[CA1032](ca1032.md) | Implementare costruttori di eccezioni standard
[CA1033](ca1033.md) | I metodi di interfaccia devono essere richiamabili dai tipi figlio
[CA1034](ca1034.md) | I tipi annidati non devono essere visibili
[CA1036](ca1036.md) | Eseguire l'override di metodi su tipi confrontabili
[CA1040](ca1040.md) | Evitare l'uso di interfacce vuote
[CA1041](ca1041.md) | Specificare una proprietà ObsoleteAttribute.Message
[CA1043](ca1043.md) | USA argomento di stringa o integrale per gli indicizzatori
[CA1044](ca1044.md) | Le proprietà non devono essere in sola scrittura
[CA1045](ca1045.md) | Non passare i tipi per riferimento
[CA1046](ca1046.md) | Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento
[CA1047](ca1047.md) | Non dichiarare membri protected nei tipi sealed
[CA1050](ca1050.md) | Dichiarare i tipi negli spazi dei nomi
[CA1051](ca1051.md) | Non dichiarare campi di istanza visibili
[CA1052](ca1052.md) | I tipi di segnaposto statici devono essere statici o NotInheritable
[CA1053](ca1053.md) | I tipi di segnaposto statici non devono avere costruttori (CA1053 fa parte di [CA1052](ca1052.md) per gli analizzatori FxCop)
[CA1054](ca1054.md) | I parametri URI non devono essere stringhe
[CA1055](ca1055.md) | I valori restituiti URI non devono essere stringhe
[CA1056](ca1056.md) | Le proprietà URI non devono essere stringhe
[CA1058](ca1058.md) | I tipi non devono estendere tipi di base specifici
[CA1060](ca1060.md) | Spostare pinvokes in una classe di metodi nativi
[CA1061](ca1061.md) | Non nascondere i metodi di una classe base
[CA1062](ca1062.md) | Convalidare gli argomenti di metodi pubblici
[CA1063](ca1063.md) | Implementare IDisposable correttamente
[CA1064](ca1064.md) | Le eccezioni devono essere pubbliche
[CA1065](ca1065.md) | Non generare eccezioni in posizioni non previste
[Ca1066](ca1066.md) | Il tipo {0} deve implementare IEquatable \<T> perché esegue l'override di Equals
[CA1067](ca1067.md) | Eseguire l'override di Object. Equals (Object) quando si implementa IEquatable\<T>
[CA1303](ca1303.md) | Non passare valori letterali come parametri localizzati
[CA1304](ca1304.md) | Specificare CultureInfo
[CA1305](ca1305.md) | Specificare IFormatProvider
[CA1307](ca1307.md) | Specificare StringComparison per maggiore chiarezza
[CA1308](ca1308.md) | Normalizzare le stringhe in lettere maiuscole
[CA1309](ca1309.md) | USA confronto di stringhe ordinali
[CA1401](ca1401.md) | I P/Invoke non devono essere visibili
[CA1501](ca1501.md) | Evitare ereditarietà eccessiva
[CA1502](ca1502.md) | Evitare complessità eccessiva
[CA1505](ca1505.md) | Evitare codice non gestibile
[CA1506](ca1506.md) | Evitare un numero eccessivo di accoppiamenti tra classi
[CA1700](ca1700.md) | Non denominare 'Reserved' i valori di enumerazione
[CA1707](ca1707.md) | Gli identificatori non devono contenere caratteri di sottolineatura
[CA1708](ca1708.md) | Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole
[CA1710](ca1710.md) | Gli identificatori devono contenere il suffisso corretto
[CA1711](ca1711.md) | Gli identificatori non devono contenere un suffisso non corretto
[CA1712](ca1712.md) | Non usare nomi di tipo come prefisso nei valori di enumerazione
[CA1713](ca1713.md) | Non usare il prefisso Before o After negli eventi
[CA1714](ca1714.md) | Le enumerazioni con Flags devono avere nomi plurali
[CA1715](ca1715.md) | Gli identificatori devono contenere il prefisso corretto
[CA1716](ca1716.md) | Gli identificatori non devono corrispondere a parole chiave
[CA1717](ca1717.md) | Solo le enumerazioni con FlagsAttribute devono avere nomi plurali
[CA1720](ca1720.md) | Identificatore contenente il nome del tipo
[CA1721](ca1721.md) | I nomi delle proprietà non devono corrispondere ai metodi get
[CA1724](ca1724.md) | I nomi dei tipi non devono corrispondere agli spazi dei nomi
[CA1725](ca1725.md) | I nomi dei parametri devono corrispondere alla dichiarazione di base
[CA1801](ca1801.md) | Controllare i parametri non usati
[CA1802](ca1802.md) | Usare valori letterali laddove appropriato
[CA1805](ca1805.md) | Non inizializzare inutilmente
[CA1806](ca1806.md) | Non ignorare i risultati dei metodi
[CA1810](ca1810.md) | Inizializzare i campi statici del tipo di riferimento inline
[CA1812](ca1812.md) | Evitare classi interne prive di istanze
[CA1813](ca1813.md) | Evitare attributi unsealed
[CA1814](ca1814.md) | Preferire matrici di matrici rispetto a matrici multidimensionali
[CA1815](ca1815.md) | Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore
[CA1816](ca1816.md) | I metodi Dispose devono chiamare SuppressFinalize
[CA1819](ca1819.md) | Le proprietà non devono restituire matrici
[CA1820](ca1820.md) | Testare le stringhe vuote usando la lunghezza di stringa
[CA1821](ca1821.md) | Rimuovi finalizzatori vuoti
[CA1822](ca1822.md) | Contrassegna i membri come statici
[CA1823](ca1823.md) | Evitare campi privati non usati
[CA1824](ca1824.md) | Contrassegnare gli assembly con NeutralResourcesLanguageAttribute
[Ca1825](ca1825.md) | Evitare allocazioni di matrici di lunghezza zero.
[CA2000](ca2000.md) | Eliminare gli oggetti prima che siano esterni all'ambito
[CA2002](ca2002.md) | Non bloccare oggetti con identità debole
[CA2100](ca2100.md) | Controllare la vulnerabilità della sicurezza nelle query SQL
[CA2101](ca2101.md) | Specificare il marshalling per gli argomenti di stringa P/Invoke
[CA2109](ca2109.md) | Controllare i gestori di eventi visibili
[CA2119](ca2119.md) | Impostare come sealed i metodi che soddisfano interfacce private
[CA2153](ca2153.md) | Non intercettare le eccezioni di stato danneggiate
[CA2200](ca2200.md) | Rethrow per conservare i dettagli dello stack.
[CA2201](ca2201.md) | Non generare tipi di eccezione riservati
[CA2207](ca2207.md) | Inizializzare i campi statici dei tipi di valore inline
[CA2208](ca2208.md) | Creare istanze di eccezioni di argomento correttamente
[CA2211](ca2211.md) | I campi non costanti non devono essere visibili
[CA2213](ca2213.md) | I campi eliminabili devono essere eliminati
[CA2214](ca2214.md) | Non chiamare metodi sottoponibili a override nei costruttori
[CA2215](ca2215.md) | I metodi Dispose devono chiamare Dispose della classe di base
[CA2216](ca2216.md) | I tipi eliminabili devono dichiarare un finalizzatore
[CA2217](ca2217.md) | Non contrassegnare le enumerazioni con FlagsAttribute
[CA2219](ca2219.md) | Non generare eccezioni nelle clausole finally
[CA2225](ca2225.md) | Gli overload degli operatori hanno alternative con nome
[CA2226](ca2226.md) | Gli operatori devono avere overload simmetrici
[CA2227](ca2227.md) | Le proprietà di raccolte devono essere in sola lettura
[CA2229](ca2229.md) | Implementare costruttori di serializzazione
[CA2231](ca2231.md) | L'operatore di overload è uguale al tipo di valore uguale a
[CA2234](ca2234.md) | Passa oggetti URI di sistema anziché stringhe
[CA2235](ca2235.md) | Contrassegnare tutti i campi non serializzabili
[CA2237](ca2237.md) | Contrassegnare i tipi ISerializable con Serializable
[CA2241](ca2241.md) | Specificare argomenti corretti ai metodi di formattazione
[CA2242](ca2242.md) | Testare i valori NaN in modo corretto
[CA2243](ca2243.md) | I valori letterali stringa di attributo devono essere analizzati correttamente
[Ca2300](ca2300.md) | Non usare il deserializzatore non sicuro BinaryFormatter
[CA2301](ca2301.md) | Non chiamare BinaryFormatter.Deserialize senza aver prima impostato BinaryFormatter.Binder
[CA2302](ca2302.md) | Assicurarsi che BinaryFormatter.Binder sia impostato prima di chiamare BinaryFormatter.Deserialize
[CA2305](ca2305.md) | Non usare il deserializzatore non sicuro LosFormatter
[CA2310](ca2310.md) | Non usare il deserializzatore non sicuro NetDataContractSerializer
[CA2311](ca2311.md) | Non eseguire la deserializzazione senza aver prima impostato NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Assicurarsi di impostare NetDataContractSerializer.Binder prima della deserializzazione
[CA2315](ca2315.md) | Non usare il deserializzatore non sicuro ObjectStateFormatter
[CA2321](ca2321.md) | Non eseguire la deserializzazione con JavaScriptSerializer usando un oggetto SimpleTypeResolver
[CA2322](ca2322.md) | Verificare che l'oggetto JavaScriptSerializer non sia inizializzato con SimpleTypeResolver prima di eseguire la deserializzazione
[CA3001](ca3001.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo SQL injection
[CA3002](ca3002.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XSS
[Ca3003](ca3003.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo file path injection
[Ca3004](ca3004.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo diffusione di informazioni
[CA3005](ca3005.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo LDAP injection
[CA3006](ca3006.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo process command injection
[CA3007](ca3007.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo reindirizzamento aperto
[CA3008](ca3008.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XPath injection
[CA3009](ca3009.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XML injection
[CA3010](ca3010.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XAML injection
[CA3011](ca3011.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo DLL injection
[CA3012](ca3012.md) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo regex injection
[CA3061](ca3061.md) | Non aggiungere lo schema in base all'URL
[CA3075](ca3075.md) | Elaborazione DTD non sicura nel codice XML
[CA3076](ca3076.md) | Elaborazione di script XSLT non protetta.
[CA3077](ca3077.md) | Elaborazione non sicura in progettazione API, XmlDocument e XmlTextReader
[CA3147](ca3147.md) | Contrassegnare i gestori dei verbi con il token antifalsificazione Validate
[CA5350](ca5350.md) | Non usare algoritmi di crittografia vulnerabili
[CA5351](ca5351.md) | Non usare algoritmi di crittografia interrotti
[CA5358](ca5358.md) | Non usare modalità crittografia non sicure
CA5359 | Non disabilitare la convalida del certificato
CA5360 | Non chiamare metodi pericolosi nella deserializzazione
[CA5361](ca5361.md) | Non disabilitare l'uso di crittografia avanzata in SChannel
CA5362 | Non fare riferimento a self in una classe serializzabile
[CA5363](ca5363.md) | Non disabilitare la convalida delle richieste
[CA5364](ca5364.md) | Non usare protocolli di sicurezza deprecati
CA5365 | Non disabilitare il controllo delle intestazioni HTTP
CA5366 | Utilizzare XmlReader per il set di dati Read XML
CA5367 | Non serializzare i tipi con i campi puntatore
CA5368 | Imposta ViewStateUserKey per le classi derivate dalla pagina
[CA5369](ca5369.md) | Utilizzare XmlReader per la deserializzazione
[CA5370](ca5370.md) | Utilizzare XmlReader per la convalida del lettore
[CA5371](ca5371.md) | Utilizzare XmlReader per la lettura dello schema
[CA5372](ca5372.md) | Usare XmlReader per XPathDocument
[CA5373](ca5373.md) | Non usare la funzione di derivazione di chiave obsoleta
CA5374 | Non utilizzare XslTransform
CA5375 | Non usare la firma di accesso condiviso dell'account
CA5376 | Usare SharedAccessProtocol HttpsOnly
CA5377 | Usare i criteri di accesso a livello di contenitore
[CA5378](ca5378.md) | Non disabilitare ServicePointManagerSecurityProtocols
CA5379 | Non usare l'algoritmo della funzione di derivazione della chiave debole
Ca9999 | Versione analizzatore non corrispondente

## <a name="see-also"></a>Vedere anche

- [Regole Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
