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
ms.openlocfilehash: 8fa572c3db3726bd1a8518990e1adfdba3c09269
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167410"
---
# <a name="fxcop-rule-port-status"></a>Stato della porta della regola FxCop

Se in precedenza è stata usata l'analisi statica del codice in Visual Studio, è possibile chiedersi quali di queste regole sono disponibili nell'implementazione corrente come [analizzatori FxCop](install-fxcop-analyzers.md). In questa pagina sono elencate le regole che vengono trasferite, nonché quelle che non sono state trasferite e se sono presenti piani per trasferirle.

## <a name="ported-rules"></a>Regole trasferite

La [pagina della documentazione generata automaticamente](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) nel repository Roslyn-Analyzers include l'elenco più aggiornato delle regole che sono state trasferite agli analizzatori FxCop. Questa pagina contiene anche informazioni aggiuntive, ad esempio se la regola è abilitata per impostazione predefinita e se è associata a una *correzione del codice*. Le[correzioni del codice](../ide/quick-actions.md) sono correzioni con un solo clic disponibili nel menu icona lampadina in Visual Studio.

A partire dalla data di questa pagina, l'elenco di regole FxCop che sono state trasferite agli [analizzatori FxCop](install-fxcop-analyzers.md) include:

ID regola | Titolo
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Non dichiarare membri statici su tipi generici
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | I tipi proprietari di campi Disposable devono essere Disposable
[CA1003](ca1003-use-generic-event-handler-instances.md) | Usare istanze di gestori eventi generici
[CA1008](ca1008-enums-should-have-zero-value.md) | Le enumerazioni devono avere valore zero
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Le raccolte devono implementare un'interfaccia generica
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | I tipi astratti non devono includere costruttori
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Contrassegnare gli assembly con CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Contrassegnare gli assembly con la versione dell'assembly
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Contrassegnare gli assembly con ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Contrassegnare gli attributi con AttributeUsageAttribute
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Definire le funzioni di accesso per gli argomenti degli attributi
[CA1021](ca1021.md) | Evitare parametri out
[CA1024](ca1024-use-properties-where-appropriate.md) | Usare proprietà dove appropriato
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Contrassegnare le enumerazioni con FlagsAttribute
[CA1028](ca1028-enum-storage-should-be-int32.md) | L'archiviazione enum deve essere Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Usare eventi dove appropriato
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Non rilevare tipi di eccezione generali
[CA1032](ca1032-implement-standard-exception-constructors.md) | Implementare costruttori di eccezioni standard
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | I metodi di interfaccia devono essere richiamabili dai tipi figlio
[CA1034](ca1034-nested-types-should-not-be-visible.md) | I tipi annidati non devono essere visibili
[CA1036](ca1036-override-methods-on-comparable-types.md) | Eseguire l'override di metodi su tipi confrontabili
[CA1040](ca1040-avoid-empty-interfaces.md) | Evitare l'uso di interfacce vuote
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Specificare una proprietà ObsoleteAttribute.Message
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | USA argomento di stringa o integrale per gli indicizzatori
[CA1044](ca1044-properties-should-not-be-write-only.md) | Le proprietà non devono essere in sola scrittura
[CA1050](ca1050-declare-types-in-namespaces.md) | Dichiarare i tipi negli spazi dei nomi
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Non dichiarare campi di istanza visibili
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | I tipi di segnaposto statici devono essere statici o NotInheritable
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | I tipi di segnaposto statici non devono avere costruttori (CA1053 fa parte di [CA1052](ca1052-static-holder-types-should-be-sealed.md) per gli analizzatori FxCop)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | I parametri URI non devono essere stringhe
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | I valori restituiti URI non devono essere stringhe
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Le proprietà URI non devono essere stringhe
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | I tipi non devono estendere tipi di base specifici
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Spostare pinvokes in una classe di metodi nativi
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Non nascondere i metodi di una classe base
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Convalidare gli argomenti di metodi pubblici
[CA1063](ca1063-implement-idisposable-correctly.md) | Implementare IDisposable correttamente
[CA1064](ca1064-exceptions-should-be-public.md) | Le eccezioni devono essere pubbliche
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Non generare eccezioni in posizioni non previste
Ca1066 | Il {0} tipo deve implementare\<IEquatable T> perché esegue l'override di Equals
CA1067 | Eseguire l'override di Object. Equals (Object)\<quando si implementa IEquatable T>
[CA1068](ca1068.md) | I parametri CancellationToken devono essere indicati per ultimi
Ca1200 | Evitare l'uso di tag cref con un prefisso
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Non passare valori letterali come parametri localizzati
[CA1304](ca1304-specify-cultureinfo.md) | Specificare CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Specificare IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Specificare StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normalizzare le stringhe in lettere maiuscole
[CA1309](ca1309-use-ordinal-stringcomparison.md) | USA confronto di stringhe ordinali
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | I P/Invoke non devono essere visibili
[CA1501](ca1501-avoid-excessive-inheritance.md) | Evitare ereditarietà eccessiva
[CA1502](ca1502-avoid-excessive-complexity.md) | Evitare complessità eccessiva
[CA1505](ca1505-avoid-unmaintainable-code.md) | Evitare codice non gestibile
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Evitare un numero eccessivo di accoppiamenti tra classi
[Ca1507](ca1507.md) | Usare NameOf per esprimere i nomi dei simboli
Ca1508 | Evitare codice condizionale non attivo
Ca1509 | Voce non valida nel file di specifica della regola della metrica del codice
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Gli identificatori non devono contenere caratteri di sottolineatura
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Gli identificatori devono contenere il suffisso corretto
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Gli identificatori non devono contenere un suffisso non corretto
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | Non usare nomi di tipo come prefisso nei valori di enumerazione
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Le enumerazioni con Flags devono avere nomi plurali
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Gli identificatori devono contenere il prefisso corretto
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Gli identificatori non devono corrispondere a parole chiave
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Solo le enumerazioni con FlagsAttribute devono avere nomi plurali
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | Identificatore contenente il nome del tipo
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | I nomi delle proprietà non devono corrispondere ai metodi get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | I nomi dei tipi non devono corrispondere agli spazi dei nomi
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | I nomi dei parametri devono corrispondere alla dichiarazione di base
[CA1801](ca1801.md) | Controllare i parametri non usati
[CA1802](ca1802.md) | Usare valori letterali laddove appropriato
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
[CA2000](ca2000.md) | Eliminare gli oggetti prima che siano esterni all'ambito
[CA2002](ca2002.md) | Non bloccare oggetti con identità debole
[Ca2007](ca2007.md) | Prendere in considerazione la chiamata a ConfigureAwait sull'attività attesa
Ca2008 | Non creare attività senza passare un oggetto TaskScheduler
Ca2009 | Non chiamare ToImmutableCollection su un valore non modificabile
CA2010 | Utilizzare sempre il valore restituito dai metodi contrassegnati con PreserveSigAttribute
[CA2100](ca2100.md) | Controllare la vulnerabilità della sicurezza nelle query SQL
[CA2101](ca2101.md) | Specificare il marshalling per gli argomenti di stringa P/Invoke
[CA2119](ca2119.md) | Impostare come sealed i metodi che soddisfano interfacce private
[CA2153](ca2153.md) | Non intercettare le eccezioni di stato danneggiate
[CA2200](ca2200.md) | Rethrow per conservare i dettagli dello stack.
[CA2201](ca2201.md) | Non generare tipi di eccezione riservati
[CA2207](ca2207.md) | Inizializzare i campi statici dei tipi di valore inline
[CA2208](ca2208.md) | Creare istanze di eccezioni di argomento correttamente
[CA2211](ca2211.md) | I campi non costanti non devono essere visibili
[CA2213](ca2213.md) | I campi eliminabili devono essere eliminati
[CA2214](ca2214.md) | Non chiamare metodi sottoponibili a override nei costruttori
[CA2216](ca2216.md) | I tipi eliminabili devono dichiarare un finalizzatore
[CA2217](ca2217.md) | Non contrassegnare le enumerazioni con FlagsAttribute
[CA2218](ca2218.md) | Eseguire l'override di GetHashCode all'override di Equals
[CA2219](ca2219.md) | Non generare eccezioni nelle clausole finally
[CA2224](ca2224.md) | Esegue l'override di Equals in un operatore di overload uguale a
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
CA2244 | Non duplicare le inizializzazioni di elementi indicizzati
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
CA3061 | Non aggiungere lo schema in base all'URL
[CA3075](ca3075.md) | Elaborazione DTD non sicura nel codice XML
[CA3076](ca3076.md) | Elaborazione di script XSLT non protetta.
[CA3077](ca3077.md) | Elaborazione non sicura in progettazione API, XmlDocument e XmlTextReader
[CA3147](ca3147.md) | Contrassegnare i gestori dei verbi con il token antifalsificazione Validate
[CA5350](ca5350.md) | Non usare algoritmi di crittografia vulnerabili
[CA5351](ca5351.md) | Non usare algoritmi di crittografia interrotti
CA5358 | Non usare modalità crittografia non sicure
CA5359 | Non disabilitare la convalida del certificato
CA5360 | Non chiamare metodi pericolosi nella deserializzazione
CA5361 | Non disabilitare l'uso di crittografia avanzata in SChannel
CA5362 | Non fare riferimento a self in una classe serializzabile
CA5363 | Non disabilitare la convalida delle richieste
CA5364 | Non usare protocolli di sicurezza deprecati
CA5365 | Non disabilitare il controllo delle intestazioni HTTP
CA5366 | Utilizzare XmlReader per il set di dati Read XML
CA5367 | Non serializzare i tipi con i campi puntatore
CA5368 | Imposta ViewStateUserKey per le classi derivate dalla pagina
CA5369 | Utilizzare XmlReader per la deserializzazione
CA5370 | Utilizzare XmlReader per la convalida del lettore
CA5371 | Utilizzare XmlReader per la lettura dello schema
CA5372 | Usare XmlReader per XPathDocument
CA5373 | Non usare la funzione di derivazione di chiave obsoleta
CA5374 | Non utilizzare XslTransform
CA5375 | Non usare la firma di accesso condiviso dell'account
CA5376 | Usare SharedAccessProtocol HttpsOnly
CA5377 | Usare i criteri di accesso a livello di contenitore
CA5378 | Non disabilitare ServicePointManagerSecurityProtocols
CA5379 | Non usare l'algoritmo della funzione di derivazione della chiave debole
Ca9999 | Versione analizzatore non corrispondente

## <a name="unported-rules"></a>Regole non portate

Il set di regole che non sono state trasferite agli [analizzatori FxCop](install-fxcop-analyzers.md) è costituito da regole che ancora non sono ancora state [trasferite](#rules-that-may-be-ported)e da quelle deprecate e [non verranno trasferite](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Regole che possono essere trasferite

Le seguenti regole di analisi legacy di FxCop non sono state ancora implementate come analizzatori, ma possono comunque essere. Questo problema può essere dovuto a un motivo tecnico di blocco o semplicemente alla priorità più bassa. Per ulteriori informazioni sullo stato di portabilità di ogni regola, fare clic sul collegamento nella colonna **problema di rilevamento** .

ID regola | Problema di rilevamento
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Regole deprecate

Le seguenti regole di analisi legacy FxCop sono deprecate e non verranno implementate come analizzatori. Per ulteriori informazioni, è possibile eseguire la ricerca in base all'ID regola, ad esempio **CA1009**, nella [pagina Roslyn-Analyzers GitHub issues](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701.md)
- [CA1702](ca1702.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([giustificazione](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>Vedere anche

- [Regole Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
