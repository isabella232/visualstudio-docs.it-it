---
title: 'CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b3e34bec0e199e1eb0b49a88517e9551b9b13cd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921633"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Il nome di un membro visibile esternamente corrisponde, in un confronto senza distinzione tra maiuscole e minuscole, il nome di uno dei relativi parametri.

## <a name="rule-description"></a>Descrizione della regola
Un nome di parametro deve comunicare il significato di un parametro e un nome di membro deve comunicare il significato di un membro. Le progettazioni in cui questi nomi coincidono sono rare. Assegnare a un parametro lo stesso nome del relativo membro non è intuitiva e rende più complesso l'utilizzo della libreria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Selezionare un nome di parametro che non corrisponda al nome del membro.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Per il nuovo sviluppo, non si verificano scenari noti in cui è necessario eliminare un avviso da questa regola. Per le librerie di spedizione, potrebbe essere necessario eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
[CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708 Gli identificatori devono differire più di case](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)