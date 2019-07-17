---
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b26a638c1ac8bd808bae6fa78aaa3cc24dedede5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151965"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Riceve i callback dal simbolo DIA individuazione di routine, consentendo un'interfaccia utente segnalare lo stato di avanzamento del tentativo di percorso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 I metodi seguenti vengono esposte da questa interfaccia:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Chiamato quando è stata trovata una directory di debug nel file .exe.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Chiamato quando è stato aperto un file DBG candidato.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Chiamato quando è stato aperto un file con estensione pdb candidato.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Determina se query del Registro di sistema possono essere utilizzate per individuare i percorsi di ricerca simbolo.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Determina se l'accesso è consentito in un server di simboli per risolvere i simboli.|  
  
## <a name="remarks"></a>Note  
 L'applicazione client implementa questa interfaccia e fornisce un riferimento a esso nella chiamata ai [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).  
  
 Per altre restrizioni che possono essere imposti in un processo di caricamento, vedere la [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: DIA2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
