---
title: "Visualizzazione Puntatore all'istruzione: dati sui conflitti | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b27b185e659fc3a1f0adca4379896543a1eb87ea
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54834586"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Visualizzazione Puntatore all'istruzione: dati sui conflitti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella visualizzazione Puntatore all'istruzione dei dati sui conflitti sono elencati i dati per le istruzioni dell'assembly di cui è stata impedita l'esecuzione durante la profilatura.  
  
 La tabella seguente illustra i valori delle colonne nella visualizzazione Puntatore all'istruzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo blocco esclusivo**|Tempo di blocco in questa funzione.|  
|**% tempo blocco esclusivo**|Percentuale di tempo di blocco durante l'esecuzione dell'istruzione.|  
|**Conflitti esclusivi**|Numero di conflitti che si sono verificati durante l'esecuzione dell'istruzione.|  
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che si sono verificati durante l'esecuzione dell'istruzione.|  
|**Indirizzo funzione**|Indirizzo di memoria iniziale della funzione nel file binario caricato.|  
|**Nome funzione**|Nome della funzione contenente l'istruzione.|  
|**Indirizzo istruzione**|Indirizzo di memoria dell'istruzione nel file binario caricato.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Nome modulo**|Nome del modulo contenente l'istruzione.|  
|**Percorso modulo**|Percorso del modulo contenente l'istruzione.|  
|**ID processo**|ID di processo (PID) del processo profilato.|  
|**Nome processo**|Nome del processo.|  
|**Inizio carattere di origine**|Offset del carattere nella riga del file di origine in corrispondenza del quale inizia questa istruzione.|  
|**Fine carattere di origine**|Offset del carattere nella riga del file di origine in corrispondenza del quale termina questa istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Inizio riga di origine**|Numero di riga del file di origine dove inizia questa istruzione.|  
|**Fine riga di origine**|Numero di riga del file di origine dove termina questa istruzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view.md)   
 [Visualizzazione Puntatore all'istruzione - Campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view-sampling-data.md)
