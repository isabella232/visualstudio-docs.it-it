---
title: 'Procedura: Confrontare i file di dati delle prestazioni | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 185494623e019ef666374bd46e52bca0d58738f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185942"
---
# <a name="how-to-compare-performance-data-files"></a>Procedura: Confrontare i file di dati delle prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile confrontare i risultati di due diversi file di dati del profiler (con estensione vsp o vsps) creando un rapporto o una visualizzazione di confronto ("Diff"). Il confronto indica le differenze, le regressioni relative alle prestazioni e i miglioramenti riscontrati da una sessione di profilatura all'altra.  
  
 Il rapporto Diff presenta una visualizzazione tabella dei dati. La tabella contiene il delta o la modifica rispetto al valore di base. Questo valore viene calcolato determinando la differenza tra il valore precedente, il valore di base e il valore dei risultati della nuova analisi.  
  
 I confronti tra i dati del profiler possono essere basati su funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione (IP) e tipi.  
  
 È possibile impostare una soglia per ridurre il rumore ed escludere qualsiasi dato nella visualizzazione tabella delle righe che non sono state modificate in base una quantità specificata.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Per creare una visualizzazione file di confronto per un progetto in Esplora prestazioni  
  
1. In **Esplora prestazioni**, in **report**, selezionare il file di report con estensione vsp o vsps che si desidera utilizzare come valori di base per il confronto.  
  
2. Selezionare i file di rapporto con estensione vsp o vsps da confrontare.  
  
3. Fare clic con il pulsante destro del mouse su uno dei file selezionati e quindi fare clic su **Confronta rapporti**.  
  
### <a name="to-compare-values"></a>Per confrontare i valori  
  
1. Selezionare la scheda **Rapporto di confronto** nella finestra delle visualizzazioni dei rapporti.  
  
2. Nell'elenco a discesa **Tabella** selezionare una delle funzioni o dei moduli da confrontare.  
  
3. Nell'elenco a discesa **Colonna** selezionare il valore da confrontare.  
  
4. (facoltativo) Digitare un valore per **Soglia**.  
  
5. Fare clic su **Apply**.  
  
### <a name="to-compare-report-files"></a>Per confrontare file di rapporto  
  
1. Nel menu **Analizza** selezionare **Confronta rapporto di prestazioni**.  
  
2. Nella finestra **selezionare i file di analisi per il confronto** individuare e selezionare il file di analisi dei **file di base** (con estensione vsp o vsps) e il **file di confronto** (con estensione vsp o vsps).  
  
3. Fare clic su **OK**.
