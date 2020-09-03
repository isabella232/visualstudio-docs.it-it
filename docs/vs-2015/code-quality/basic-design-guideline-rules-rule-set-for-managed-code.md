---
title: Set di regole delle linee guida di progettazione di base per codice gestito | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cefe4864db8455ba6712dc728b342f49b6c7d5d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655118"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Set di regole Regole base delle linee guida di progettazione per codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare il set di regole delle linee guida di progettazione di base Microsoft per concentrarsi sulla semplificazione della comprensione e dell'utilizzo del codice. È necessario includere questo set di regole se il progetto include codice della libreria o se si desidera applicare procedure consigliate per il codice di facile manutenzione.

 Le regole delle linee guida di progettazione di base includono tutte le regole del set di regole raccomandati minime Microsoft. Per un elenco delle regole minime, vedere [set di regole consigliate gestite per il codice gestito](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).

 Nella tabella seguente vengono descritte tutte le regole del set di regole Microsoft Basic Design Guideline Rules.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi Disposable devono essere Disposable|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Dichiarare correttamente i gestori eventi|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Contrassegnare gli assembly con AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|I metodi di interfaccia devono essere richiamabili dai tipi figlio|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|I tipi delle risorse native devono essere disposable|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Spostare P/Invoke nella classe NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Non nascondere i metodi di una classe base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementare IDisposable correttamente|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Non generare eccezioni in posizioni non previste|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitare tasti di scelta rapida duplicati|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|I punti di ingresso P/Invoke devono esistere|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|I P/Invoke non devono essere visibili|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|I tipi layout automatici non devono essere visibili a COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Chiamare GetLastError immediatamente dopo P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|I tipi di base del tipo visibile a COM devono essere visibili a COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|I metodi di registrazione COM devono corrispondere|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Dichiarare correttamente i P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|I campi dei tipi di valore devono essere portabili|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Le dichiarazioni P/Invoke devono essere portabili|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Non bloccare oggetti con identità debole|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Controllare la vulnerabilità della sicurezza nelle query SQL|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Specificare il marshalling per gli argomenti di stringa P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Controllare la sicurezza dichiarativa sui tipi di valori|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|I puntatori non devono essere visibili|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|I tipi protetti non devono esporre campi|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La sicurezza del metodo deve essere un superset del tipo|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|I metodi APTCA devono chiamare solo metodi APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|I tipi APTCA devono estendere solo tipi di base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Non esporre in modo indiretto metodi con richieste di collegamento|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Eseguire il wrapping delle clausole finally vulnerabili in un try esterno|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|I tipi SecurityCritical possono non partecipare all'equivalenza del tipo|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|I delegati devono essere associati ai metodi con trasparenza consistente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|I metodi devono mantenere trasparenza consistente durante l'override dei metodi base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|I metodi Transparent devono contenere solo IL verificabile|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Il codice Transparent non deve far riferimento a elementi SecurityCritical|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|I metodi Transparent non devono soddisfare I LinkDemand|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|I tipi devono essere Critical almeno come le interfacce e i tipi base relativi|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|I metodi Transparent non possono usare asserzioni di sicurezza|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|I metodi Transparent non devono effettuare chiamate nel codice nativo|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Eseguire il rethrow per mantenere i dettagli dello stack|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Non eliminare gli oggetti più volte|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inizializzare i campi statici dei tipi di valore inline|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Non contrassegnare componenti serviti con WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi eliminabili devono essere eliminati|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Non chiamare metodi sottoponibili a override nei costruttori|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|I tipi eliminabili devono dichiarare un finalizzatore|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|I finalizzatori devono chiamare il finalizzatore della classe di base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementare costruttori di serializzazione|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Contrassegnare i punti di ingresso del Windows Form con STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Contrassegnare tutti i campi non serializzabili|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Chiamare metodi della classe di base su tipi ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Contrassegnare i tipi ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementare correttamente i metodi di serializzazione|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementare ISerializable in modo corretto|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Specificare argomenti corretti ai metodi di formattazione|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testare i valori NaN in modo corretto|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Non dichiarare membri statici su tipi generici|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Non esporre elenchi generici|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Usare istanze di gestori eventi generici|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|I metodi generici devono specificare parametri di tipo|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Evitare un uso eccessivo di parametri nei tipi generici|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Non annidare tipi generici nelle firme dei membri|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Usare generics dove appropriato|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Le enumerazioni devono avere valore zero|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Le raccolte devono implementare un'interfaccia generica|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Provare a passare tipi di base come parametri|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|I tipi astratti non devono includere costruttori|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Contrassegnare gli assembly con CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Contrassegnare gli assembly con ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Contrassegnare gli attributi con AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Definire le funzioni di accesso per gli argomenti degli attributi|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Gli indicizzatori non devono essere multidimensionali|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Usare proprietà dove appropriato|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Sostituire gli argomenti ripetitivi con una matrice di parametri|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Evitare l'uso di parametri predefiniti|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Contrassegnare le enumerazioni con FlagsAttribute|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Le risorse di archiviazione dell'enumerazione devono essere Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Usare eventi dove appropriato|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Non rilevare tipi di eccezione generali|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementare costruttori di eccezioni standard|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|I tipi annidati non devono essere visibili|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Le implementazioni di ICollection hanno membri fortemente tipizzati|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Eseguire l'override di metodi su tipi confrontabili|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Gli enumeratori devono essere fortemente tipizzati|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Gli elenchi sono fortemente tipizzati|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Specificare una proprietà ObsoleteAttribute.Message|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Usare un argomento di tipo stringa o integrale per gli indicizzatori|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Le proprietà non devono essere in sola scrittura|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Non dichiarare membri protected nei tipi sealed|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Non dichiarare membri virtuali nei tipi sealed|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Dichiarare i tipi negli spazi dei nomi|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Non dichiarare campi di istanza visibili|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|I tipi che contengono membri statici devono essere sealed|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|I tipi che contengono membri statici non devono avere costruttori|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|I parametri URI non devono essere stringhe|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|I valori restituiti URI non devono essere stringhe|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Le proprietà URI non devono essere stringhe|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Gli overload URI dei valori di stringa chiamano gli overload System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|I tipi non devono estendere tipi di base specifici|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|I membri non devono esporre tipi concreti specifici|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Le eccezioni devono essere pubbliche|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|I nomi delle variabili non devono corrispondere ai nomi dei campi|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Evitare complessità eccessiva|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Gli identificatori non devono corrispondere a parole chiave|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Controllare i parametri non usati|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Rimuovere variabili locali non usate|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Evitare un numero eccessivo di variabili locali|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inizializzare i campi statici del tipo di riferimento inline|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Evitare il codice privato non chiamato|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Evitare classi interne prive di istanze|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Evitare attributi unsealed|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Preferire matrici di matrici rispetto a matrici multidimensionali|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Le proprietà non devono restituire matrici|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testare le stringhe vuote usando la lunghezza di stringa|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Contrassegna i membri come statici|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Evitare campi privati non usati|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Non generare tipi di eccezione riservati|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Usare equivalenti gestiti dell'API Win32|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Creare istanze di eccezioni di argomento correttamente|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|I campi non costanti non devono essere visibili|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Non contrassegnare le enumerazioni con FlagsAttribute|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Non generare eccezioni in clausole di eccezione|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|I finalizzatori devono essere protetti|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Non diminuire la visibilità di membri ereditati|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|La differenza tra membri non deve limitarsi al tipo restituito|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Eseguire l'override di Equals all'overload dell'operatore "uguale a"|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Gli overload degli operatori hanno alternative con nome|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Gli operatori devono avere overload simmetrici|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Le proprietà di raccolte devono essere in sola lettura|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Usare params per argomenti variabili|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Passare oggetti System.Uri invece di stringhe|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Specificare metodi di deserializzazione per i campi facoltativi|
