---
title: DA0011-CompareTo costoso | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 58c94e5a24eab1c638397d7b1391596e503207fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520666"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Funzione CompareTo dispendiosa

|Elemento|valore|
|-|-|
|ID regola|DA0011|
|Category|Uso di .NET Framework|
|Metodi di profilatura|campionamento<br /><br /> Memoria .NET|
|Message|Le funzioni CompareTo dovrebbero essere semplici e non allocare memoria. Se possibile, ridurre la complessità della funzione CompareTo.|
|Tipo regola|Avviso|

## <a name="cause"></a>Causa
 Il metodo CompareTo del tipo è dispendioso o alloca memoria.

## <a name="rule-description"></a>Descrizione della regola
 I metodi CompareTo dovrebbero essere efficienti e non allocare memoria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Ridurre la complessità del metodo CompareTo.
