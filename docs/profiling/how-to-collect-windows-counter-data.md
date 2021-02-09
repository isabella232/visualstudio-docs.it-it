---
title: Raccogliere i dati dei contatori Windows | Microsoft Docs
description: I contatori di Windows vengono usati nella profilatura della strumentazione. Informazioni su come raccogliere i dati dei contatori di Windows e su come limitare l'analisi a un singolo intervallo di raccolta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f1e8f38ee9cb63dfe5a79f0b410e957b4cefaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886210"
---
# <a name="how-to-collect-windows-counter-data"></a>Procedura: Raccogliere i dati dei contatori Windows

I contatori Windows sono contatori di prestazioni del sistema che possono essere raccolti a intervalli prestabiliti durante la profilatura. Nella visualizzazione Contrassegni del rapporto degli strumenti di profilatura è presente una riga con etichetta **AutoMark** per ogni intervallo della raccolta. La riga contiene colonne che descrivono i valori dei contatori di prestazioni inclusi nell'intervallo specificato. Per limitare l'analisi a un periodo di tempo compreso tra due contrassegni particolari, selezionare i contrassegni, fare clic con il pulsante destro del mouse e quindi scegliere **Filtra per**  >  **Contrassegni** dal menu di scelta rapida.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Per raccogliere i dati dei contatori Windows

1. In Esplora prestazioni fare clic con il pulsante destro del mouse sulla sessione per cui si vogliono configurare i contatori Windows e scegliere **Proprietà**.

2. In **Pagine delle proprietà** fare clic su **Contatori Windows**.

3. Selezionare la casella di controllo **Raccogliere contatori Windows**.

4. Nella casella di testo **lntervallo di raccolta (msec)** digitare un intervallo di tempo.

5. Selezionare una categoria dall'elenco a discesa **Categoria contatori**.

6. Selezionare un'istanza dall'elenco a discesa **Istanza**.

7. Selezionare i contatori da usare quando si profila l'applicazione.

8. Fare clic su **Applica.**

## <a name="see-also"></a>Vedi anche

[Configurare le sessioni](../profiling/configuring-performance-sessions.md) 
 di prestazioni Proprietà della sessione di [prestazioni](../profiling/performance-session-properties.md) 
 [Contatori CPU e Windows](../profiling/cpu-and-windows-counters.md)
