---
title: 'CA2201: Non generare tipi di eccezione riservati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9db603567cb73827546bc488bf57aba641d97054
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946002"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Non generare tipi di eccezione riservati

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un metodo genera un tipo di eccezione che è troppo generico o che è riservato dal runtime.

## <a name="rule-description"></a>Descrizione della regola

I seguenti tipi di eccezione sono troppo generici per fornire informazioni sufficienti per l'utente:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

I seguenti tipi di eccezione sono riservati e devono essere generati solo da common language runtime:

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

**Non generare eccezioni generali**

Se si genera un tipo di eccezione generali, ad esempio <xref:System.Exception> o <xref:System.SystemException> in una libreria o framework, saranno costretti a intercettare tutte le eccezioni, incluse le eccezioni sconosciute che non si conosce la modalità di gestione.

Al contrario, generare un tipo più derivato che esiste già nel framework, o creare un proprio tipo che deriva da <xref:System.Exception>.

**Generare eccezioni specifiche**

Nella tabella seguente vengono illustrati parametri e le eccezioni da generare quando si convalida il parametro, tra cui il parametro del valore nella funzione di accesso set di una proprietà:

|Descrizione dei parametri|Eccezione|
|---------------------------|---------------|
|`null` Riferimento|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Compreso nell'intervallo consentito di valori (ad esempio un indice per una raccolta o elenco)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Non è valido `enum` valore|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Contiene un formato che non soddisfa le specifiche di parametri di un metodo (ad esempio la stringa di formato per `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|In caso contrario, non è valido|<xref:System.ArgumentException?displayProperty=fullName>|

Quando un'operazione non è valida per lo stato corrente di un oggetto generare <xref:System.InvalidOperationException?displayProperty=fullName>

Generata quando viene eseguita un'operazione su un oggetto che è stato eliminato <xref:System.ObjectDisposedException?displayProperty=fullName>

Quando un'operazione non è supportata (ad esempio in un stato eseguito l'override **oggetto Stream. Write** in un Stream aperto per la lettura) throw <xref:System.NotSupportedException?displayProperty=fullName>

Quando una conversione comporterebbe un overflow (ad esempio un overload dell'operatore di cast espliciti) generare <xref:System.OverflowException?displayProperty=fullName>

Per tutti gli altri casi, è consigliabile creare un proprio tipo che deriva da <xref:System.Exception> e generarlo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il tipo dell'eccezione generata in un tipo specifico che non è uno dei tipi riservati.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate

- [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)