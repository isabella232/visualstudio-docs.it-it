---
title: 'CA1722: Gli identificatori non devono contenere il prefisso non corretto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c1d2aa6f0889216b39b891b042989f1c8c69692
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907763"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Gli identificatori non devono contenere il prefisso non corretto

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore ha un prefisso non corretto.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.

 I nomi di tipo non è un prefisso specifico e non devono essere preceduti da "C". Questa regola segnala le violazioni per i nomi dei tipi, ad esempio 'CMyClass' e non segnalare le violazioni per i nomi dei tipi, ad esempio "Cache".

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. Questa coerenza consente di ridurre la curva di apprendimento che ha richiesto per le nuove librerie di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il prefisso dall'identificatore.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)