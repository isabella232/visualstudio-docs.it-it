---
title: 'Procedura: Rilocare file binari instrumentati | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: 96faf382145d7c4541f1fe66f872ad3622f64631
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539300"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Procedura: Rilocare file binari instrumentati

Durante la strumentazione, i probe vengono inseriti nel file binario per misurare le prestazioni dell'applicazione. Se si sceglie di rilocare il file binario instrumentato, una copia del file binario originale viene instrumentata e inserita nella posizione specificata. Questa opzione è utile se non si vuole che il profiler rinomini il file binario originale. Se il file binario non viene rilocato, la versione originale di tale file verrà sovrascritta.

## <a name="to-relocate-instrumented-binary"></a>Per rilocare il file binario instrumentato

1. In **Esplora prestazioni**fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.

2. Nella **Pagine delle proprietà**fare clic sulle proprietà di **Binario** .

3. Selezionare la casella di controllo **Rilocare binari instrumentati** .

4. Specificare la posizione per il file binario instrumentato.

## <a name="see-also"></a>Vedere anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
