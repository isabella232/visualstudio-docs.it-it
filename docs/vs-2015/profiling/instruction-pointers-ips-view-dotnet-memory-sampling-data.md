---
title: "Visualizzazione dei puntatori all'istruzione (IP, Instruction Pointer): dati di campionamento di memoria .NET | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd06bc09114785c4359d05e3cda70c3ce7646c9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804247"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Visualizzazione dei puntatori all'istruzione (IP, Instruction Pointer): dati di campionamento di memoria .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione IP dei dati di profilatura sull'allocazione di memoria .NET raccolti tramite il metodo di campionamento elenca le istruzioni dell'assembly che hanno allocato memoria durante l'esecuzione della profilatura. Le colonne della visualizzazione elencano inoltre le dimensioni e il numero delle allocazioni.  
  
 Vengono elencati solo valori esclusivi.  
  
|Colonna|Description|  
|------------|-----------------|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**Nome modulo**|Nome del modulo contenente l'istruzione.|  
|**Percorso modulo**|Percorso del modulo contenente l'istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Nome funzione**|Nome della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Indirizzo funzione**|Indirizzo iniziale della funzione.|  
|**Inizio riga di origine**|Numero di riga iniziale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Fine riga di origine**|Numero di riga finale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Inizio carattere di origine**|Offset del carattere iniziale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Fine carattere di origine**|Offset del carattere finale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Indirizzo istruzione**|Indirizzo dell'istruzione.|  
|**Allocazioni esclusive**|Numero totale di oggetti creati dall'istruzione.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che sono stati allocati dall'istruzione.|  
|**Byte esclusivi**|Numero di byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati dall'istruzione.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati dall'istruzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view-sampling-data.md)
