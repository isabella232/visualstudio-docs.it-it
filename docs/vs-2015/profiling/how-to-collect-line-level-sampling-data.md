---
title: 'Procedura: Raccogliere i dati di campionamento a livello di riga | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd57893476ba7654a37fc44d1681adc3264f92b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527981"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Procedura: Raccogliere i dati di campionamento a livello di riga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: raccogliere dati di campionamento a livello di riga](https://docs.microsoft.com/visualstudio/profiling/how-to-collect-line-level-sampling-data).  
  
Il campionamento a livello di riga è una capacità del profiler che consente di determinare il punto del codice di una funzione che richiede un uso intensivo del processore, ad esempio una funzione con esempi esclusivi elevati, in cui il processore impiega la maggior parte del tempo.  
  
## <a name="overview"></a>Panoramica  
 Nel campionamento a livello di riga il profiler analizza lo stack di chiamate del programma a intervalli prestabiliti e aggrega i risultati ottenuti. Questi risultati mostrano le istruzioni che il processore stava eseguendo quando i campioni sono stati prelevati. I dati raccolti sui campioni esclusivi vengono quindi analizzati per identificare le righe del codice e il puntatore all'istruzione (IP).  
  
 Il campionamento a livello di riga può essere usato per il codice gestito così come per quello nativo. I rapporti di prestazioni che consentono di visualizzare questi dati includono la visualizzazione Righe e la visualizzazione Moduli.  
  
 Le informazioni di inizio/fine carattere non sono disponibili per il codice nativo. Per le istruzioni su più righe, per il codice nativo non sono disponibili le informazioni di inizio riga, ma solo quelle di fine riga.  
  
### <a name="available-data"></a>Dati disponibili  
 I dati del campionamento a livello di riga disponibili includono le informazioni seguenti:  
  
-   Nome funzione.  
  
-   Indirizzo funzione.  
  
-   Inizio riga: numero di riga del codice di campionamento.  
  
-   Fine riga: numero di riga di fine del codice sorgente. Generalmente corrisponde al valore di "Inizio riga" ad eccezione di quando una singola istruzione del programma si estende su più righe del codice sorgente.  
  
-   Inizio carattere: colonna iniziale del campione di aggregazione. Generalmente questo valore è 0 ad eccezione di quando una singola riga contiene più istruzioni del programma.  
  
-   Fine carattere: colonna finale del campione di aggregazione.  
  
-   IP: indirizzo in cui è stato prelevato il campione di aggregazione (solo visualizzazione IP).  
  
 Nella visualizzazione **Moduli**, se una funzione presenta statistiche a livello di riga, le statistiche vengono annidate in ogni funzione. Vengono inoltre visualizzate le statistiche a livello di IP annidate in ogni riga.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Disattivare il campionamento a livello di riga per il codice gestito  
 Per impostazione predefinita, il campionamento a livello di riga è attivato. È possibile disattivare la raccolta di dati a livello di riga per il codice gestito in uno dei seguenti modi:  
  
-   Prima della profilatura, digitare **VSPerfCLREnv /samplelineoff**. Questa operazione ha effetto sulle applicazioni e sui servizi.  
  
     oppure  
  
-   Quando si avvia un'applicazione, digitare **VSPerfCmd /lineoff \<altri argomenti>**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)


