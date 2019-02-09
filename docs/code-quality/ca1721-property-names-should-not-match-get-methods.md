---
title: 'CA1721: I nomi delle proprietà non devono corrispondere ai metodi get'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 88a56a37248112d377b47054ed815a4aa2629f9d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953932"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: I nomi delle proprietà non devono corrispondere ai metodi get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un membro pubblico o protetto inizia con 'Get' e in caso contrario, corrisponde al nome di una proprietà pubblica o protetta. Ad esempio, un tipo che contiene un metodo denominato "GetColor" e una proprietà denominata 'Color' viola questa regola.

## <a name="rule-description"></a>Descrizione della regola
 I metodi get e le proprietà devono avere nomi di distinguere chiaramente le relative funzioni.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. Questa coerenza consente di ridurre il tempo necessario per informazioni su una nuova libreria di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare il nome in modo che il nome di un metodo che ha il prefisso 'Get' non corrisponde.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

> [!NOTE]
> Questo avviso può essere escluso se il metodo Get è causato dall'implementazione IExtenderProvider (interfaccia).

## <a name="example"></a>Esempio
 L'esempio seguente contiene un metodo e proprietà che violano questa regola.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)