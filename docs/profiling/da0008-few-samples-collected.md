---
title: DA0008 - Pochi campioni raccolti | Microsoft Docs
description: Durante l'esecuzione della profilatura sono stati raccolti solo alcuni campioni.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2b12813f7e0da051a0b6d96ac907638acf04517f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084337"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Numero ridotto di campioni raccolti

|Elemento|valore|
|-|-|
|ID regola|DA0008|
|Category|Uso degli strumenti di profilatura|
|Metodo di profilatura|campionamento|
|Message|È stato raccolto un numero ridotto di campioni. Si consiglia di eseguire il campionamento più a lungo o di aumentare la frequenza di campionamento per ottenere risultati più significativi.|
|Tipo regola|Informazioni|

## <a name="cause"></a>Causa
 Durante l'esecuzione della profilatura sono stati raccolti solo alcuni campioni.

## <a name="rule-description"></a>Descrizione della regola
 Quando viene usato il metodo di campionamento, è necessario raccogliere un numero di campioni statisticamente significativo per assicurarsi che i dati siano rappresentativi dell'effettivo comportamento del programma. Per ridurre al minimo gli errori di campionamento, provare a raccogliere almeno 1000 campioni di comportamento dell'esecuzione delle istruzioni del programma. Se non si raccoglie un numero sufficiente di campioni è possibile che l'analisi dei dati di profilatura porti a conclusioni fuorvianti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 È consigliabile profilare un'esecuzione più lunga dell'applicazione o usare una frequenza di campionamento più elevata per ottenere risultati significativi a livello statistico. Per informazioni su come modificare la frequenza di campionamento nell'IDE Visual Studio, vedere [Procedura: Scegliere gli eventi di campionamento.](../profiling/how-to-choose-sampling-events.md) Per altre informazioni sulla modifica della frequenza di campionamento quando si usa la riga di comando degli strumenti di profilatura, vedere [Timer](../profiling/timer.md) nel riferimento di [VSPerfCmd](../profiling/vsperfcmd.md).
