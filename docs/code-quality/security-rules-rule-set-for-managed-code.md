---
title: Set di regole di sicurezza per codice gestito
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b436ad097209b34efdec87061347c8786352679f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944540"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Set di regole di sicurezza per codice gestito
È necessario includere il Microsoft Security set di regole per ottimizzare il numero di potenziali problemi di sicurezza che vengono segnalati.

|Regola|Descrizione|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Controllare la vulnerabilità della sicurezza nelle query SQL|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Individuare le eccezioni non CLSCompliant nei gestori generali|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Controllare la sicurezza imperativa|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Non dichiarare tipi di riferimento modificabili in sola lettura|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|I campi di matrici non devono essere di sola lettura|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Asserzioni protette|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Controllare l'uso di Deny e PermitOnly|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Controllare la sicurezza dichiarativa sui tipi di valori|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Controllare i gestori di eventi visibili|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|I puntatori non devono essere visibili|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|I tipi protetti non devono esporre campi|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La sicurezza del metodo deve essere un superset del tipo|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Chiamare GC.KeepAlive durante l'uso di risorse native|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|I metodi APTCA devono chiamare solo metodi APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|I tipi APTCA devono estendere solo tipi di base APTCA|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Impostare come sealed i metodi che soddisfano interfacce private|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Proteggere i costruttori di serializzazione|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|I costruttori statici devono essere privati|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Non esporre in modo indiretto metodi con richieste di collegamento|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Eseguire il wrapping delle clausole finally vulnerabili in un try esterno|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Le costanti SecurityCritical devono essere Transparent|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|I tipi SecurityCritical possono non partecipare all'equivalenza del tipo|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|I delegati devono essere associati ai metodi con trasparenza consistente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|I metodi devono mantenere trasparenza consistente durante l'override dei metodi base|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Gli assembly di livello 2 non devono contenere LinkDemand|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|I membri non devono avere annotazioni di trasparenza in conflitto|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|I metodi Transparent devono contenere solo IL verificabile|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|I metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Il codice Transparent non deve far riferimento a elementi SecurityCritical|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|I metodi Transparent non devono soddisfare i LinkDemand|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Il codice Transparent non deve essere protetto con LinkDemand|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|I metodi Transparent non devono usare SecurityDemand|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Il codice Transparent non deve caricare assembly da matrici di byte|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|I tipi devono essere Critical almeno come le interfacce e i tipi base relativi|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|I metodi Transparent non possono usare asserzioni di sicurezza|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|I metodi Transparent non devono effettuare chiamate nel codice nativo|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Gli assembly devono avere nomi sicuri validi|