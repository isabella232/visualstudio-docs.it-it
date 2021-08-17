---
title: DA0010 - GetHashCode | Microsoft Docs
description: Le chiamate al metodo GetHashCode del tipo rappresentano una percentuale significativa dei dati di profilatura o il metodo alloca memoria.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b32dba46e496e80c12b2fd351cc5dde0984d95b95ddd98492adb51ee9c52f1b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368799"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Funzione GetHashCode dispendiosa

|Elemento|valore|
|-|-|
|ID regola|DA0010|
|Category|Uso di .NET Framework|
|Metodi di profilatura|campionamento<br /><br /> Memoria .NET|
|Message|Le funzioni GetHashCode dovrebbero essere semplici e non allocare memoria. Se possibile, ridurre la complessità della funzione di codice hash.|
|Tipo di messaggio|Avviso|

## <a name="cause"></a>Causa
 Le chiamate al metodo GetHashCode del tipo rappresentano una percentuale significativa dei dati di profilatura o il metodo alloca memoria.

## <a name="rule-description"></a>Descrizione della regola
 Hash è una tecnica per individuare rapidamente un particolare elemento in una raccolta di grandi dimensioni. Poiché possono avere dimensioni grandi e devono supportare frequenze di accesso molto elevate, le tabelle hash devono essere efficienti. Per questa ragione, i metodi GetHashCode in .NET Framework non devono allocare memoria. L'allocazione di memoria aumenta il carico del Garbage Collector ed espone il metodo a possibili ritardi se diventa necessario eseguire l'operazione di Garbage Collection in seguito alla richiesta di allocazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Ridurre la complessità del metodo.
