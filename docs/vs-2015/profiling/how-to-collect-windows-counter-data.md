---
title: 'Procedura: Raccogliere i dati dei contatori Windows | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f0ace1d920cdd4f2c503c608a1695b04c1251f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529588"
---
# <a name="how-to-collect-windows-counter-data"></a>Procedura: Raccogliere i dati dei contatori Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: raccogliere i dati dei contatori Windows](https://docs.microsoft.com/visualstudio/profiling/how-to-collect-windows-counter-data).  
  
I contatori Windows sono contatori di prestazioni del sistema che possono essere raccolti a intervalli prestabiliti durante la profilatura. Nella visualizzazione Contrassegni del rapporto degli strumenti di profilatura è presente una riga con etichetta **AutoMark** per ogni intervallo della raccolta. La riga contiene colonne che descrivono i valori dei contatori di prestazioni inclusi nell'intervallo specificato. Per limitare l'analisi a un periodo di tempo compreso tra due contrassegni particolari, selezionare i contrassegni, fare clic con il pulsante destro del mouse e quindi scegliere **Filtra per** ->  **Contrassegni** dal menu di scelta rapida.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
### <a name="to-collect-windows-counter-data"></a>Per raccogliere i dati dei contatori Windows  
  
1.  In Esplora prestazioni fare clic con il pulsante destro del mouse sulla sessione per cui si vogliono configurare i contatori Windows e scegliere **Proprietà**.  
  
2.  In **Pagine delle proprietà** fare clic su **Contatori Windows**.  
  
3.  Selezionare la casella di controllo **Raccogliere contatori Windows**.  
  
4.  Nella casella di testo **lntervallo di raccolta (msec)** digitare un intervallo di tempo.  
  
5.  Selezionare una categoria dall'elenco a discesa **Categoria contatori**.  
  
6.  Selezionare un'istanza dall'elenco a discesa **Istanza**.  
  
7.  Selezionare i contatori da usare quando si profila l'applicazione.  
  
8.  Fare clic su **Applica**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)   
 [Contatori CPU e Windows](../profiling/cpu-and-windows-counters.md)


