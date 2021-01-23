---
title: Rilocare file binari instrumentati | Microsoft Docs
description: Informazioni sul modo in cui i probe vengono inseriti nel file binario per misurare le prestazioni dell'applicazione durante la strumentazione.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ee94737f59f5c29aac47d686f68ade06131d0379
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720618"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Procedura: Rilocare file binari instrumentati

Durante la strumentazione, i probe vengono inseriti nel file binario per misurare le prestazioni dell'applicazione. Se si sceglie di rilocare il file binario instrumentato, una copia del file binario originale viene instrumentata e inserita nella posizione specificata. Questa opzione è utile se non si vuole che il profiler rinomini il file binario originale. Se il file binario non viene rilocato, la versione originale di tale file verrà sovrascritta.

## <a name="to-relocate-instrumented-binary"></a>Per rilocare il file binario instrumentato

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.

2. Nella **Pagine delle proprietà** fare clic sulle proprietà di **Binario** .

3. Selezionare la casella di controllo **Rilocare binari instrumentati** .

4. Specificare la posizione per il file binario instrumentato.

## <a name="see-also"></a>Vedere anche

[Configurare le sessioni](../profiling/configuring-performance-sessions.md) 
 di prestazioni [VSInstr](../profiling/vsinstr.md)
