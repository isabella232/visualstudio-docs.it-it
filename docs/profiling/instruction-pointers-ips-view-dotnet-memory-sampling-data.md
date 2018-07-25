---
title: "Visualizzazione dei puntatori all'istruzione (IP, Instruction Pointer): dati di campionamento di memoria .NET | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3b3d0d0334ed8073a125d8b2c435f8e5d58299d4
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844872"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Visualizzazione dei puntatori all'istruzione: dati di campionamento di memoria .NET
La visualizzazione IP dei dati di profilatura sull'allocazione di memoria .NET raccolti tramite il metodo di campionamento elenca le istruzioni dell'assembly che hanno allocato memoria durante l'esecuzione della profilatura. Le colonne della visualizzazione elencano inoltre le dimensioni e il numero delle allocazioni.  
  
 Vengono elencati solo valori esclusivi.  
  
|Colonna|Descrizione|  
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