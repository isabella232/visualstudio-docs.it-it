---
title: 'CA1724: I nomi dei tipi non devono corrispondere gli spazi dei nomi | Microsoft Docs'
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
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5331a32db054b1cb3939bbfd3ba088ab5da33f96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903179"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un nome di tipo corrisponde a un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] spazi dei nomi in un confronto tra maiuscole e minuscole.

## <a name="rule-description"></a>Descrizione della regola
 I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. La violazione di questa regola può ridurre l'utilizzabilità della libreria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome di tipo che non corrispondono al nome di un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dello spazio dei nomi della libreria di classi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per i nuovi sviluppi, nessun noti verificarsi gli scenari in cui è necessario eliminare un avviso da questa regola. Prima di eliminare l'avviso, considerare attentamente come gli utenti della libreria potrebbero essere confusi dal nome corrispondente. Per le librerie, potrebbe essere necessario eliminare un avviso da questa regola.



