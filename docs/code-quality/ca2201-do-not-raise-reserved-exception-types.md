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
ms.openlocfilehash: 3d9b787a4e50f43867b5d9b4ec7a11aba03f8599
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231675"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Non generare tipi di eccezione riservati

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Category|Microsoft.Usage|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un metodo genera un tipo di eccezione troppo generale o che è riservato dal runtime.

## <a name="rule-description"></a>Descrizione della regola

I tipi di eccezione seguenti sono troppo generici per fornire informazioni sufficienti all'utente:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

I tipi di eccezione seguenti sono riservati e devono essere generati solo dal Common Language Runtime:

- <xref:System.AccessViolationException?displayProperty=fullName>

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SEHException?displayProperty=fullName>

- <xref:System.StackOverflowException?displayProperty=fullName>

**Non generare eccezioni generali**

Se si genera un tipo di eccezione generale, ad <xref:System.Exception> esempio <xref:System.SystemException> o in una libreria o in un Framework, impone ai consumer di intercettare tutte le eccezioni, incluse le eccezioni sconosciute che non sanno come gestire.

In alternativa, è possibile generare un tipo più derivato già esistente nel Framework oppure creare un tipo personalizzato che derivi da <xref:System.Exception>.

**Genera eccezioni specifiche**

La tabella seguente illustra i parametri e le eccezioni da generare quando si convalida il parametro, incluso il parametro value nella funzione di accesso set di una proprietà:

|Descrizione parametro|Eccezione|
|---------------------------|---------------|
|`null`riferimento|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Al di fuori dell'intervallo consentito di valori (ad esempio un indice per una raccolta o un elenco)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Valore `enum` non valido|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Contiene un formato che non soddisfa le specifiche dei parametri di un metodo (ad esempio la stringa di formato `ToString(String)`per)|<xref:System.FormatException?displayProperty=fullName>|
|Altrimenti non valido|<xref:System.ArgumentException?displayProperty=fullName>|

Quando un'operazione non è valida per lo stato corrente di un oggetto Throw<xref:System.InvalidOperationException?displayProperty=fullName>

Quando viene eseguita un'operazione su un oggetto che è stato eliminato da Throw<xref:System.ObjectDisposedException?displayProperty=fullName>

Quando un'operazione non è supportata (ad esempio in un flusso sottoposto a override **. scrivere** in un flusso aperto per la lettura) throw<xref:System.NotSupportedException?displayProperty=fullName>

Quando una conversione genera un overflow (ad esempio in un overload dell'operatore cast esplicito)<xref:System.OverflowException?displayProperty=fullName>

Per tutte le altre situazioni, è consigliabile creare un tipo personalizzato che deriva <xref:System.Exception> da e generarlo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il tipo dell'eccezione generata in un tipo specifico che non è uno dei tipi riservati.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate

- [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)
