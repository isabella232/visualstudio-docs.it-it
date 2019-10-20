---
title: 'CA1724: i nomi dei tipi non devono corrispondere agli spazi dei nomi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671589"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un nome di tipo corrisponde a uno spazio dei nomi di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] in un confronto senza distinzione tra maiuscole e minuscole.

## <a name="rule-description"></a>Descrizione della regola
 I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. La violazione di questa regola può ridurre l'utilizzabilità della libreria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Consente di selezionare il nome di un tipo che non corrisponde al nome di uno spazio dei nomi della libreria di classi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per il nuovo sviluppo, non si verificano scenari noti in cui è necessario eliminare un avviso da questa regola. Prima di disattivare l'avviso, valutare attentamente il modo in cui gli utenti della libreria potrebbero essere confusi con il nome corrispondente. Per le librerie di spedizione, potrebbe essere necessario eliminare un avviso da questa regola.
