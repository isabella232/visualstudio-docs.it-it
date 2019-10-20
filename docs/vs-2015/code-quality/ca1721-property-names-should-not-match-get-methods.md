---
title: 'CA1721: i nomi delle proprietà non devono corrispondere ai metodi Get | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 366932c83328c6810e0103308db1c73a3e3076cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671613"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: I nomi delle proprietà non devono corrispondere ai metodi get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un membro pubblico o protetto inizia con "Get" e in caso contrario corrisponde al nome di una proprietà pubblica o protetta. Ad esempio, un tipo che contiene un metodo denominato ' GetColor ' e una proprietà denominata ' color ' viola questa regola.

## <a name="rule-description"></a>Descrizione della regola
 I metodi get e le proprietà devono avere nomi che distinguono chiaramente la relativa funzione.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce il tempo necessario per apprendere una nuova raccolta software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare il nome in modo che non corrisponda al nome di un metodo con prefisso "Get".

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

> [!NOTE]
> Questo avviso può essere escluso se il metodo Get è causato dall'implementazione dell'interfaccia IExtenderProvider.

## <a name="example"></a>Esempio
 L'esempio seguente contiene un metodo e una proprietà che violano questa regola.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)
