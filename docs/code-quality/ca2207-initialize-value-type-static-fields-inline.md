---
title: 'CA2207: Inizializzare i campi statici dei tipi di valore inline'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46f579b6776ffab6d0ed3b2e216e29d36d2065ee
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231697"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inizializzare i campi statici dei tipi di valore inline

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo di valore dichiara un costruttore statico esplicito.

## <a name="rule-description"></a>Descrizione della regola
Quando un tipo di valore viene dichiarato, viene sottoposto a un'inizializzazione predefinita in cui tutti i campi di tipo valore sono impostati su zero e tutti i campi di `null` tipo`Nothing` riferimento sono impostati su (in Visual Basic). Un costruttore statico esplicito è garantito solo per l'esecuzione prima che venga chiamato un costruttore di istanza o un membro statico del tipo. Pertanto, se il tipo viene creato senza chiamare un costruttore di istanza, non è garantita l'esecuzione del costruttore statico.

Se tutti i dati statici vengono inizializzati inline e non viene dichiarato alcun costruttore statico C# esplicito, i compilatori e Visual Basic aggiungono il `beforefieldinit` flag alla definizione della classe MSIL. I compilatori aggiungono anche un costruttore statico privato che contiene il codice di inizializzazione statico. È garantito che questo costruttore statico privato venga eseguito prima che venga eseguito l'accesso a qualsiasi campo statico del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando viene dichiarata e rimuovere il costruttore statico.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
[CA1810 Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)