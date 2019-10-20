---
title: 'CA2201: non generare tipi di eccezione riservati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a550226a5ea1edb3b30e317be6b5682f4c204d52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667368"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Non generare tipi di eccezione riservati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Category|Microsoft. Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo genera un tipo di eccezione troppo generale o che è riservato dal runtime.

## <a name="rule-description"></a>Descrizione della regola
 I tipi di eccezione seguenti sono troppo generici per fornire informazioni sufficienti all'utente:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  I tipi di eccezione seguenti sono riservati e devono essere generati solo dal Common Language Runtime:

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **Non generare eccezioni generali**

  Se si genera un tipo di eccezione generale, ad esempio <xref:System.Exception> o <xref:System.SystemException> in una libreria o in un Framework, impone agli utenti di intercettare tutte le eccezioni, incluse le eccezioni sconosciute che non sanno come gestire.

  In alternativa, è possibile generare un tipo più derivato già esistente nel Framework oppure creare un tipo personalizzato che derivi da <xref:System.Exception>.

  **Genera eccezioni specifiche**

  La tabella seguente illustra i parametri e le eccezioni da generare quando si convalida il parametro, incluso il parametro value nella funzione di accesso set di una proprietà:

|Descrizione parametro|Eccezione|
|---------------------------|---------------|
|riferimento `null`|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Al di fuori dell'intervallo consentito di valori (ad esempio un indice per una raccolta o un elenco)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Valore di `enum` non valido|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Contiene un formato che non soddisfa le specifiche dei parametri di un metodo (ad esempio la stringa di formato per `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|Altrimenti non valido|<xref:System.ArgumentException?displayProperty=fullName>|

 Quando un'operazione non è valida per lo stato corrente di un oggetto Throw <xref:System.InvalidOperationException?displayProperty=fullName>

 Quando viene eseguita un'operazione su un oggetto che è stato eliminato Throw <xref:System.ObjectDisposedException?displayProperty=fullName>

 Quando un'operazione non è supportata (ad esempio in un flusso sottoposto a override **. Write** in un flusso aperto per la lettura) genera <xref:System.NotSupportedException?displayProperty=fullName>

 Quando una conversione genera un overflow, ad esempio in un overload dell'operatore cast esplicito, genera <xref:System.OverflowException?displayProperty=fullName>

 Per tutte le altre situazioni, provare a creare un tipo personalizzato che deriva da <xref:System.Exception> e generarlo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il tipo dell'eccezione generata in un tipo specifico che non è uno dei tipi riservati.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)
