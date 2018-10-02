---
title: 'Procedura: Creare un report di confronto del profiler da un prompt dei comandi | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb31a79af25fbe66112efd6be0aacd9b3c3820d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525792"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Procedura: creare un rapporto di confronto del profiler da un prompt dei comandi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: creare un Report di confronto del Profiler da un prompt dei comandi](https://docs.microsoft.com/visualstudio/profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt).  
  
È possibile generare un report degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che confronta i dati sulle prestazioni di due file di dati di profilatura (con estensione vsp o vsps). Nel rapporto vengono mostrate le differenze, le regressioni delle prestazioni e i miglioramenti riscontrati da una sessione di profilatura a altra. I valori nel report presentano il delta o la modifica rispetto alla linea di base del primo file specificato. Il delta è calcolato determinando la differenza tra il valore precedente, che è il valore della linea di base, e il valore risultante dalla nuova analisi. I confronti tra i dati del profiler possono essere basati su funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione e tipi.  
  
 Per elencare gli identificatori dei campi e delle categorie di confronto, digitare la riga di comando seguente:  
  
 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*  
  
 Usare la sintassi seguente per creare il report di confronto:  
  
 **VSPerfReport /diff**  `VspFileName1` *VspFileName2* [**/**`Options`]  
  
 È possibile aggiungere le opzioni contenute nella tabella seguente alla riga di comando **VSPerfReport /diff**.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**DiffThreshold:**[*Value*]|Ignorare la differenza se al di sotto di questo valore di soglia in percentuale. Inoltre, i nuovi dati con valori al di sotto della soglia non verranno visualizzati.|  
|**DiffTable:** *TableName*|Usare questa tabella per confrontare i file. Per impostazione predefinita, viene usata la tabella delle funzioni. Specificare l'identificatore elencato in **VSPerfReport /querydifftables**.|  
|**DiffColumn:** *ColumnName*|Usare questa colonna per confrontare i valori. Per impostazione predefinita, viene usata la colonna percentuale campioni esclusivi. Specificare l'identificatore elencato in **VSPerfReport /querydifftables**.|



