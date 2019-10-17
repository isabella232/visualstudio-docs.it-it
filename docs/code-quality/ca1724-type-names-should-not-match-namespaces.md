---
title: 'CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e5ab83a73da6035df985b93294f850b5a49248f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443442"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: i nomi dei tipi non devono corrispondere agli spazi dei nomi

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft. Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un nome di tipo corrisponde a un nome di spazio dei nomi a cui si fa riferimento con uno o più tipi visibili esternamente. Per il confronto dei nomi non viene fatta distinzione tra maiuscole e minuscole.

## <a name="rule-description"></a>Descrizione della regola

I nomi dei tipi creati dall'utente non devono corrispondere ai nomi degli spazi dei nomi a cui si fa riferimento con tipi visibili esternamente. La violazione di questa regola può ridurre l'usabilità della libreria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Rinominare il tipo in modo che non corrisponda al nome di uno spazio dei nomi a cui si fa riferimento con tipi visibili esternamente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Per il nuovo sviluppo, non si verificano scenari noti in cui è necessario eliminare un avviso da questa regola. Prima di disattivare l'avviso, valutare attentamente il modo in cui gli utenti della libreria potrebbero essere confusi con il nome corrispondente. Per le librerie di spedizione, potrebbe essere necessario eliminare un avviso da questa regola.
