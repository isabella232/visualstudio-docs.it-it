---
title: Stato della porta della regola FxCop
ms.date: 05/21/2019
description: Informazioni sulle regole di analisi del codice statiche che sono state portate agli analizzatori .NET in Visual Studio. Visualizzare le regole e le risorse di porting sugli aggiornamenti di porting.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: d9c64040e4ff5b3ca96ef4b49b749b2be73a6dc63a0fa9fd48f2201007de2dcd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420965"
---
# <a name="fxcop-rule-port-status"></a>Stato della porta della regola Fxcop

Se in precedenza è stata usata l'analisi statica del codice Visual Studio, ci si potrebbe chiedere quale di queste regole è disponibile nell'implementazione corrente come [analizzatori .NET.](install-net-analyzers.md) In questa pagina sono elencate le regole che sono state portate. Vedere [Regole non portate](fxcop-unported-rules.md) per quelle che non sono state portate e se sono presenti piani per il port.

## <a name="ported-rules"></a>Regole trasferite

La [pagina della](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) documentazione rigenerata automaticamente nel repo roslyn-analyzers include l'elenco più aggiornato delle regole che sono state portate agli analizzatori Roslyn. Tale pagina contiene anche informazioni aggiuntive, ad esempio se la regola è abilitata per impostazione predefinita e se è associata una correzione *del codice*. Le[correzioni di codice](../ide/quick-actions.md) sono correzioni con un solo clic disponibili nel menu dell'icona a forma di lampadina in Visual Studio.

Alla data in questa pagina, l'elenco delle regole FxCop che sono state portate agli [analizzatori .NET](install-net-analyzers.md) include:

ID regola | Titolo
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Non dichiarare membri statici su tipi generici
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | I tipi proprietari di campi Disposable devono essere Disposable
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Non esporre elenchi generici
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Usare istanze di gestori eventi generici
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Evitare un uso eccessivo di parametri nei tipi generici
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Le enumerazioni devono avere valore zero
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Le raccolte devono implementare un'interfaccia generica
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | I tipi astratti non devono includere costruttori
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Contrassegnare gli assembly con CLSCompliant
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Contrassegnare gli assembly con la versione dell'assembly
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Contrassegnare gli assembly con ComVisible
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Contrassegnare gli attributi con AttributeUsageAttribute
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Definire le funzioni di accesso per gli argomenti degli attributi
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | Evitare parametri out
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Usare proprietà dove appropriato
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Contrassegnare le enumerazioni con FlagsAttribute
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | Enum Archiviazione deve essere Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Usare eventi dove appropriato
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Non rilevare tipi di eccezione generali
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Implementare costruttori di eccezioni standard
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | I metodi di interfaccia devono essere richiamabili dai tipi figlio
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | I tipi annidati non devono essere visibili
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Eseguire l'override di metodi su tipi confrontabili
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Evitare l'uso di interfacce vuote
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | Specificare una proprietà ObsoleteAttribute.Message
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Usare un argomento integrale o stringa per gli indicizzatori
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Le proprietà non devono essere in sola scrittura
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Non passare i tipi per riferimento
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Non dichiarare membri protected nei tipi sealed
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Dichiarare i tipi negli spazi dei nomi
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Non dichiarare campi di istanza visibili
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | I tipi di titolari statici devono essere statici o NotInheritable
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | I tipi di titolari statici non devono avere costruttori (CA1053 fa parte di [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) per analizzatori .NET)
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | I parametri URI non devono essere stringhe
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | I valori restituiti uri non devono essere stringhe
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Le proprietà URI non devono essere stringhe
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | I tipi non devono estendere tipi di base specifici
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Spostare i pinvoke nella classe di metodi nativi
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Non nascondere i metodi di una classe base
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Convalidare gli argomenti di metodi pubblici
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Implementare correttamente IDisposable
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Le eccezioni devono essere pubbliche
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Non generare eccezioni in posizioni non previste
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | Il {0} tipo deve implementare IEquatable \<T> perché esegue l'override di Equals
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Eseguire l'override di Object.Equals(object) durante l'implementazione di IEquatable\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Non passare valori letterali come parametri localizzati
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | Specificare CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | Specificare IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Specificare StringComparison per maggiore chiarezza
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Normalizzare le stringhe in lettere maiuscole
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Usare il confronto ordinale tra stringhe
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | I P/Invoke non devono essere visibili
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Evitare ereditarietà eccessiva
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Evitare complessità eccessiva
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Evitare codice non gestibile
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Evitare un numero eccessivo di accoppiamenti tra classi
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Non denominare 'Reserved' i valori di enumerazione
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Gli identificatori non devono contenere caratteri di sottolineatura
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Gli identificatori devono contenere il suffisso corretto
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Gli identificatori non devono contenere un suffisso non corretto
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | Non usare nomi di tipo come prefisso nei valori di enumerazione
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Non usare il prefisso Before o After negli eventi
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Le enumerazioni con Flags devono avere nomi plurali
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Gli identificatori devono contenere il prefisso corretto
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Gli identificatori non devono corrispondere a parole chiave
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Solo le enumerazioni con FlagsAttribute devono avere nomi plurali
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | L'identificatore contiene il nome del tipo
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | I nomi delle proprietà non devono corrispondere ai metodi get
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | I nomi dei tipi non devono corrispondere a spazi dei nomi
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | I nomi dei parametri devono corrispondere alla dichiarazione di base
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Controllare i parametri non usati
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Usare i valori letterali dove appropriato
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Non inizializzare inutilmente
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | Non ignorare i risultati dei metodi
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Inizializzare i campi statici del tipo di riferimento inline
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Evitare classi interne prive di istanze
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Evitare attributi unsealed
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Preferire matrici di matrici rispetto a matrici multidimensionali
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | I metodi Dispose devono chiamare SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Le proprietà non devono restituire matrici
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Testare le stringhe vuote usando la lunghezza di stringa
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Rimuovere finalizzatori vuoti
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Contrassegna i membri come statici
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Evitare campi privati non usati
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Contrassegnare gli assembly con NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Evitare allocazioni di matrici di lunghezza zero.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Eliminare gli oggetti prima che siano esterni all'ambito
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Non bloccare oggetti con identità debole
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | Controllare la vulnerabilità della sicurezza nelle query SQL
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Specificare il marshalling per gli argomenti di stringa P/Invoke
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Controllare i gestori di eventi visibili
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Impostare come sealed i metodi che soddisfano interfacce private
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Non rilevare eccezioni di stato danneggiate
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Rigenerare per mantenere i dettagli dello stack.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Non generare tipi di eccezione riservati
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Inizializzare i campi statici dei tipi di valore inline
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Creare istanze di eccezioni di argomento correttamente
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | I campi non costanti non devono essere visibili
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | I campi eliminabili devono essere eliminati
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | Non chiamare metodi sottoponibili a override nei costruttori
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | I metodi Dispose devono chiamare Dispose della classe di base
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | I tipi eliminabili devono dichiarare un finalizzatore
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Non contrassegnare le enumerazioni con FlagsAttribute
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Non generare eccezioni nelle clausole finally
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Gli overload degli operatori hanno alternative con nome
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Gli operatori devono avere overload simmetrici
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Le proprietà di raccolte devono essere in sola lettura
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Implementare costruttori di serializzazione
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Operatore di overload uguale a in caso di override del tipo di valore Equals
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Passare oggetti URI di sistema anziché stringhe
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Contrassegnare tutti i campi non serializzabili
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | Contrassegnare i tipi ISerializable con Serializable
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Specificare argomenti corretti ai metodi di formattazione
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Testare i valori NaN in modo corretto
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | I valori letterali stringa di attributo devono essere analizzati correttamente
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | Non usare il deserializzatore non sicuro BinaryFormatter
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | Non chiamare BinaryFormatter.Deserialize senza aver prima impostato BinaryFormatter.Binder
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Assicurarsi che BinaryFormatter.Binder sia impostato prima di chiamare BinaryFormatter.Deserialize
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | Non usare il deserializzatore non sicuro LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | Non usare il deserializzatore non sicuro NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | Non eseguire la deserializzazione senza aver prima impostato NetDataContractSerializer.Binder
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Assicurarsi di impostare NetDataContractSerializer.Binder prima della deserializzazione
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | Non usare il deserializzatore non sicuro ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | Non eseguire la deserializzazione con JavaScriptSerializer usando un oggetto SimpleTypeResolver
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Verificare che l'oggetto JavaScriptSerializer non sia inizializzato con SimpleTypeResolver prima di eseguire la deserializzazione
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo SQL injection
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XSS
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo file path injection
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo diffusione di informazioni
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo LDAP injection
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo process command injection
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo reindirizzamento aperto
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XPath injection
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XML injection
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo XAML injection
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo DLL injection
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Esaminare il codice per verificare la presenza di vulnerabilità di tipo regex injection
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | Non aggiungere lo schema in base all'URL
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Elaborazione DTD non sicura nel codice XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Elaborazione di script XSLT non sicura.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Elaborazione non sicura in Progettazione API, XmlDocument e XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Contrassegnare i gestori di verbi con il token di convalida antiforgery
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | Non usare algoritmi di crittografia vulnerabili
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Non usare algoritmi di crittografia interrotti
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Non usare modalità crittografia non sicure
CA5359 | Non disabilitare la convalida del certificato
CA5360 | Non chiamare metodi pericolosi nella deserializzazione
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Non disabilitare l'uso SChannel della crittografia forte
CA5362 | Non fare riferimento a una classe serializzabile
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | Non disabilitare la convalida delle richieste
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Non usare protocolli di sicurezza deprecati
CA5365 | Non disabilitare il controllo delle intestazioni HTTP
CA5366 | Usare XmlReader per il dataset Read Xml
CA5367 | Non serializzare tipi con campi puntatore
CA5368 | Impostare ViewStateUserKey per le classi derivate dalla pagina
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Usare XmlReader per la deserializzazione
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Usare XmlReader per convalidare il lettore
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Usare XmlReader per la lettura dello schema
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | Usare XmlReader per XPathDocument
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Non usare la funzione di derivazione di chiave obsoleta
CA5374 | Non usare XslTransform
CA5375 | Non usare la firma di accesso condiviso dell'account
CA5376 | Usare SharedAccessProtocol HttpsOnly
CA5377 | Usare i criteri di accesso a livello di contenitore
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | Non disabilitare ServicePointManagerSecurityProtocols
CA5379 | Non usare l'algoritmo della funzione di derivazione della chiave debole
CA9999 | Mancata corrispondenza della versione dell'analizzatore

## <a name="see-also"></a>Vedi anche

- [Regole dell'analizzatore .NET](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
