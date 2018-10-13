---
title: 'CA1708: Gli identificatori devono differenziare minuscole | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 07f4b9f9a69de3458bf0f7ea7dcb316e2e9a086a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187642"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 I nomi dei due tipi, membri, parametri o spazi dei nomi completi sono identici quando vengono convertiti in caratteri minuscoli.

## <a name="rule-description"></a>Descrizione della regola
 Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole. Ad esempio, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] è un diffuso linguaggio tra maiuscole e minuscole.

 Questa regola viene attivata su solo i membri visibili pubblicamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome che è univoco se confrontato con altri identificatori, in modo tra maiuscole e minuscole.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. La libreria potrebbe non essere utilizzabile in tutte le lingue disponibili nel [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="example-of-a-violation"></a>Esempio di violazione
 L'esempio seguente illustra una violazione della regola.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)



