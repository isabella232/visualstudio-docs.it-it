---
title: 'CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2bda5a9f5d569057455af9e31fb5d6852c9881e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815494"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 I nomi dei due tipi, membri, parametri o spazi dei nomi completi sono identici quando vengono convertiti in caratteri minuscoli.

## <a name="rule-description"></a>Descrizione della regola
 Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole. Ad esempio, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] è un diffuso linguaggio tra maiuscole e minuscole.

 Questa regola viene attivata su solo i membri visibili pubblicamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome che è univoco se confrontato con altri identificatori, in modo tra maiuscole e minuscole.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola. La libreria potrebbe non essere utilizzabile in tutte le lingue disponibili in .NET Framework.

## <a name="example-of-a-violation"></a>Esempio di violazione
 L'esempio seguente illustra una violazione della regola.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)