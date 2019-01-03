---
title: 'CA1724: I nomi dei tipi non devono corrispondere gli spazi dei nomi'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c28bf4af55e1c12045357a76e3488ff4083fcee5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848941"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: I nomi dei tipi non devono corrispondere gli spazi dei nomi

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un nome di tipo corrisponde a un nome di riferimento dello spazio dei nomi contenente uno o più tipi visibili esternamente. Il confronto di nome è tra maiuscole e minuscole.

## <a name="rule-description"></a>Descrizione della regola

I nomi dei tipi creati dall'utente non deve corrispondere i nomi degli spazi dei nomi di riferimento che hanno tipi visibili esternamente. Violazione di questa regola, è possibile ridurre l'utilizzabilità della libreria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Rinominare il tipo in modo che non corrisponde il nome di uno spazio dei nomi di cui viene fatto riferimento con tipi visibili esternamente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Per i nuovi sviluppi, nessun noti verificarsi gli scenari in cui è necessario eliminare un avviso da questa regola. Prima di eliminare l'avviso, considerare attentamente come gli utenti della libreria potrebbero essere confusi dal nome corrispondente. Per le librerie, potrebbe essere necessario eliminare un avviso da questa regola.