---
title: 'CA1721: I nomi di proprietà non devono corrispondere ai metodi get | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 78a87e13b7c97dbe3d6487a721b9b439892bae7f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589165"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: I nomi delle proprietà non devono corrispondere ai metodi get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1721: i nomi di proprietà non devono corrispondere ai metodi get](https://docs.microsoft.com/visualstudio/code-quality/ca1721-property-names-should-not-match-get-methods).

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

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce il tempo necessario per l'apprendimento di una nuova libreria di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare il nome in modo che il nome di un metodo che ha il prefisso 'Get' non corrisponde.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

> [!NOTE]
>  Questo avviso può essere escluso se il metodo Get è causato dall'implementazione IExtenderProvider (interfaccia).

## <a name="example"></a>Esempio
 L'esempio seguente contiene un metodo e proprietà che violano questa regola.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)


