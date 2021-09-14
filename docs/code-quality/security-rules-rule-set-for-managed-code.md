---
title: Set di regole di sicurezza per codice gestito
ms.date: 11/04/2016
description: Informazioni sul set di regole di sicurezza per Visual Studio'analisi del codice legacy. Vedere le descrizioni delle regole incentrate sui potenziali problemi di sicurezza.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 26aaec700d308e73249401e215fc1b1b93a87735
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631823"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Set di regole di sicurezza per codice gestito

Usare il set di regole di sicurezza Microsoft per l'analisi del codice legacy per ottimizzare il numero di potenziali problemi di sicurezza segnalati.

|Regola|Descrizione|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Controllare la vulnerabilità della sicurezza nelle query SQL|
|[CA2102](../code-quality/ca2102.md)|Individuare le eccezioni non CLSCompliant nei gestori generali|
|[CA2103](../code-quality/ca2103.md)|Controllare la sicurezza imperativa|
|[CA2104](../code-quality/ca2104.md)|Non dichiarare tipi di riferimento modificabili in sola lettura|
|[CA2105](../code-quality/ca2105.md)|I campi di matrici non devono essere di sola lettura|
|[CA2106](../code-quality/ca2106.md)|Asserzioni protette|
|[CA2107](../code-quality/ca2107.md)|Controllare l'uso di Deny e PermitOnly|
|[CA2108](../code-quality/ca2108.md)|Controllare la sicurezza dichiarativa sui tipi di valori|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|Controllare i gestori di eventi visibili|
|[CA2111](../code-quality/ca2111.md)|I puntatori non devono essere visibili|
|[CA2112](../code-quality/ca2112.md)|I tipi protetti non devono esporre campi|
|[CA2114](../code-quality/ca2114.md)|La sicurezza del metodo deve essere un superset del tipo|
|[CA2115](../code-quality/ca2115.md)|Chiamare GC.KeepAlive durante l'uso di risorse native|
|[CA2116](../code-quality/ca2116.md)|I metodi APTCA devono chiamare solo metodi APTCA|
|[CA2117](../code-quality/ca2117.md)|I tipi APTCA devono estendere solo tipi di base APTCA|
|[CA2118](../code-quality/ca2118.md)|Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Impostare come sealed i metodi che soddisfano interfacce private|
|[CA2120](../code-quality/ca2120.md)|Proteggere i costruttori di serializzazione|
|[CA2121](../code-quality/ca2121.md)|I costruttori statici devono essere privati|
|[CA2122](../code-quality/ca2122.md)|Non esporre in modo indiretto metodi con richieste di collegamento|
|[CA2123](../code-quality/ca2123.md)|Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base|
|[CA2124](../code-quality/ca2124.md)|Eseguire il wrapping delle clausole finally vulnerabili in un try esterno|
|[CA2126](../code-quality/ca2126.md)|Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà|
|[CA2130](../code-quality/ca2130.md)|Le costanti SecurityCritical devono essere Transparent|
|[CA2131](../code-quality/ca2131.md)|I tipi SecurityCritical possono non partecipare all'equivalenza del tipo|
|[CA2132](../code-quality/ca2132.md)|I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base|
|[CA2133](../code-quality/ca2133.md)|I delegati devono essere associati ai metodi con trasparenza consistente|
|[CA2134](../code-quality/ca2134.md)|I metodi devono mantenere trasparenza consistente durante l'override dei metodi base|
|[CA2135](../code-quality/ca2135.md)|Gli assembly di livello 2 non devono contenere LinkDemand|
|[CA2136](../code-quality/ca2136.md)|I membri non devono avere annotazioni di trasparenza in conflitto|
|[CA2137](../code-quality/ca2137.md)|I metodi Transparent devono contenere solo IL verificabile|
|[CA2138](../code-quality/ca2138.md)|I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139.md)|I metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140.md)|Il codice Transparent non deve far riferimento a elementi SecurityCritical|
|[CA2141](../code-quality/ca2141.md)|I metodi Transparent non devono soddisfare LinkDemands|
|[CA2142](../code-quality/ca2142.md)|Il codice Transparent non deve essere protetto con LinkDemand|
|[CA2143](../code-quality/ca2143.md)|I metodi Transparent non devono usare SecurityDemand|
|[CA2144](../code-quality/ca2144.md)|Il codice Transparent non deve caricare assembly da matrici di byte|
|[CA2145](../code-quality/ca2145.md)|I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146.md)|I tipi devono essere Critical almeno come le interfacce e i tipi base relativi|
|[CA2147](../code-quality/ca2147.md)|I metodi Transparent non possono usare asserzioni di sicurezza|
|[CA2149](../code-quality/ca2149.md)|I metodi Transparent non devono effettuare chiamate nel codice nativo|
|[CA2210](../code-quality/ca2210.md)|Gli assembly devono avere nomi sicuri validi|
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|Non usare il deserializzatore non sicuro BinaryFormatter|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|Non chiamare BinaryFormatter.Deserialize senza aver prima impostato BinaryFormatter.Binder|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|Assicurarsi che BinaryFormatter.Binder sia impostato prima di chiamare BinaryFormatter.Deserialize|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|Non usare il deserializzatore non sicuro LosFormatter|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|Non usare il deserializzatore non sicuro NetDataContractSerializer|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|Non eseguire la deserializzazione senza aver prima impostato NetDataContractSerializer.Binder|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|Assicurarsi di impostare NetDataContractSerializer.Binder prima della deserializzazione|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|Non usare il deserializzatore non sicuro ObjectStateFormatter|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|Non eseguire la deserializzazione con JavaScriptSerializer usando un oggetto SimpleTypeResolver|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|Verificare che l'oggetto JavaScriptSerializer non sia inizializzato con SimpleTypeResolver prima di eseguire la deserializzazione|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo SQL injection|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo XSS|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo file path injection|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo diffusione di informazioni|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo LDAP injection|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo process command injection|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo reindirizzamento aperto|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo XPath injection|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo XML injection|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo XAML injection|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo DLL injection|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|Esaminare il codice per verificare la presenza di vulnerabilità di tipo regex injection|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|Non usare modalità crittografia non sicure|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|Non impostare il certificato come hardcoded|