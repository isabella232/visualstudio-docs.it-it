---
title: 'CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: c178558743ca69fb3b62eccaf8164e4b49167ad3
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547568"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi
|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un nome di tipo corrisponde a un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] spazi dei nomi in un confronto tra maiuscole e minuscole.

## <a name="rule-description"></a>Descrizione della regola
 I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. La violazione di questa regola può ridurre l'utilizzabilità della libreria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome di tipo che non corrispondono al nome di un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dello spazio dei nomi della libreria di classi.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Per i nuovi sviluppi, nessun noti verificarsi gli scenari in cui è necessario eliminare un avviso da questa regola. Prima di eliminare l'avviso, considerare attentamente come gli utenti della libreria potrebbero essere confusi dal nome corrispondente. Per le librerie, potrebbe essere necessario eliminare un avviso da questa regola.