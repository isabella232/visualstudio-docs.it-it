---
title: 'CA1810: Inizializzare i campi statici del tipo di riferimento inline'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1fca9742a4fe5e778c0b172adad7996dcad58ca4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796871"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inizializzare i campi statici del tipo di riferimento inline

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo di riferimento dichiara un costruttore statico esplicito.

## <a name="rule-description"></a>Descrizione della regola
 Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT (Just-In-Time) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato. L'inizializzazione statica viene attivato quando si accede a qualsiasi membro statico o quando viene creata un'istanza del tipo. Tuttavia, l'inizializzazione statica non viene generato se si dichiara una variabile di tipo ma non usarla, che può essere importante se l'inizializzazione viene modificato lo stato globale.

 Quando tutti i dati statici vengono inizializzati inline e un costruttore statico esplicito non è dichiarato, i compilatori Microsoft intermediate language (MSIL) aggiungono il `beforefieldinit` flag e un costruttore statico implicito, che consente di inizializzare i dati statici, al tipo di codice MSIL definizione. Quando il compilatore JIT rileva il `beforefieldinit` flag, la maggior parte dei casi non vengono aggiunti i controlli dei costruttori statici. L'inizializzazione statica è sicuramente eseguita in un momento prima di tutti i campi statici sono accessibili, ma non prima che venga richiamato un costruttore di istanza o metodo statico. Si noti che l'inizializzazione statica può verificarsi in qualsiasi momento dopo la dichiarazione di una variabile del tipo.

 I controlli dei costruttori statici possono ridurre le prestazioni. Spesso un costruttore statico viene usato solo per inizializzare i campi statici, in cui i casi è necessario solo assicurarsi che l'inizializzazione statica si verifica prima del primo accesso di un campo statico. Il `beforefieldinit` comportamento è appropriato per questi e molti altri tipi. È solo inappropriata quando l'inizializzazione statica influisce sullo stato globale e viene soddisfatta una delle operazioni seguenti:

- L'effetto sullo stato globale è dispendiosa e non è obbligatorio se non viene utilizzato il tipo.

- Gli effetti di stato globale sono accessibili senza accesso a tutti i campi statici del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se le prestazioni non rappresentano un problema. o se le modifiche di stato globale che sono causate da inizializzazione statica sono costose o devono essere garantito che si verifichi prima viene chiamato un metodo statico del tipo o viene creata un'istanza del tipo.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo, `StaticConstructor`, che viola la regola e un tipo, `NoStaticConstructor`, che sostituisce il costruttore statico con inizializzazione inline per soddisfare la regola.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Si noti l'aggiunta del `beforefieldinit` flag nella definizione di codice MSIL per il `NoStaticConstructor` classe.

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>Regole correlate

- [CA2207: Inizializzare i campi statici del tipo di valore inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)