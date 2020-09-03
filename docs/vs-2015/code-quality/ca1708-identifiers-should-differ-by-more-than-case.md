---
title: 'CA1708: gli identificatori devono differire più del case | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 22a33c852b941b4c7e7398416aa1e74e69ff1786
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544040"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 I nomi di due tipi, membri, parametri o spazi dei nomi completi sono identici quando vengono convertiti in caratteri minuscoli.

## <a name="rule-description"></a>Descrizione della regola
 Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole. Ad esempio, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] è un linguaggio molto diffuso senza distinzione tra maiuscole e minuscole.

 Questa regola viene attivata solo sui membri visibili pubblicamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Consente di selezionare un nome univoco quando viene confrontato con altri identificatori senza distinzione tra maiuscole e minuscole.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. La libreria potrebbe non essere utilizzabile in tutte le lingue disponibili nell' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="example-of-a-violation"></a>Esempio di violazione
 Nell'esempio seguente viene illustrata una violazione di questa regola.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
