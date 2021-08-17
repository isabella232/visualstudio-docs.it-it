---
title: Confrontare i file di dati delle prestazioni | Microsoft Docs
description: Informazioni su come confrontare i risultati di due diversi file di dati del profiler (con estensione vsp o vsps) per individuare differenze, regressioni delle prestazioni e miglioramenti delle prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 59421f44a2b5d9d30285f9959ea22d090b6bddcc3d4777a29e0de1e4cf98483e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231171"
---
# <a name="how-to-compare-performance-data-files"></a>Procedura: Confrontare i file di dati delle prestazioni
È possibile confrontare i risultati di due diversi file di dati del profiler, con estensione *vsp* o *vsps*, creando un report o una visualizzazione di confronto "Diff". Il confronto indica le differenze, le regressioni relative alle prestazioni e i miglioramenti riscontrati da una sessione di profilatura all'altra.

 Il rapporto Diff presenta una visualizzazione tabella dei dati. La tabella contiene il delta o la modifica rispetto al valore di base. Questo valore viene calcolato determinando la differenza tra il valore precedente, il valore di base e il valore dei risultati della nuova analisi.

 I confronti tra i dati del profiler possono essere basati su funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione (IP) e tipi.

 È possibile impostare una soglia per ridurre il rumore ed escludere qualsiasi dato nella visualizzazione tabella delle righe che non sono state modificate in base una quantità specificata.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Per creare una visualizzazione file di confronto per un progetto in Esplora prestazioni

1. In **Esplora prestazioni** in **Report** selezionare il file di report con estensione *vsp* o *vsps* da usare come valore di base per il confronto.

2. Selezionare i file di report con estensione *vsp* o *vsps* da confrontare.

3. Fare clic con il pulsante destro del mouse su uno dei file selezionati e quindi fare clic su **Confronta rapporti**.

### <a name="to-compare-values"></a>Per confrontare i valori

1. Selezionare la scheda **Rapporto di confronto** nella finestra delle visualizzazioni dei rapporti.

2. Nell'elenco a discesa **Tabella** selezionare una delle funzioni o dei moduli da confrontare.

3. Nell'elenco a discesa **Colonna** selezionare il valore da confrontare.

4. (facoltativo) Digitare un valore per **Soglia**.

5. Fare clic su **Applica**.

### <a name="to-compare-report-files"></a>Per confrontare file di rapporto

1. Nel menu **Analizza** selezionare **Confronta rapporto di prestazioni**.

2. Nella finestra **Selezionare i file di analisi per il confronto** individuare e selezionare il file di analisi **File baseline** con estensione *vsp* o *vsps* e il **File di confronto** con estensione *vsp* o *vsps*.

3. Fare clic su **OK**.
