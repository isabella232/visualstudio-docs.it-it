---
title: 'CA1504: Controllare i nomi dei campi fuorvianti'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa997ad5afb77df126cd0824d574884bef828ab6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443997"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Controllare i nomi dei campi fuorvianti

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Category|Microsoft. gestibilità|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Il nome di un campo di istanza inizia con "s_" o il nome di un campo `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) inizia con "m_".

## <a name="rule-description"></a>Descrizione della regola
I nomi di campo che iniziano con "s_" sono associati a dati statici da molti utenti. Analogamente, i nomi di campo che iniziano con "m_" sono associati ai dati dell'istanza (membro). Per il codice più facile da gestire, i nomi devono seguire le convenzioni di uso generale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rinominare il campo utilizzando il prefisso appropriato. In alternativa, fare in modo che il campo accetti il suffisso corrente aggiungendo o rimuovendo il modificatore `static`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.
