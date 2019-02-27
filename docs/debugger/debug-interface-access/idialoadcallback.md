---
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 353e7dcbe1bcc44b9e8b7e9c7c417913ef07be35
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618874"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Riceve i callback dal simbolo DIA individuazione di routine, consentendo un'interfaccia utente segnalare lo stato di avanzamento del tentativo di percorso.

## <a name="syntax"></a>Sintassi

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 I metodi seguenti vengono esposte da questa interfaccia:

|Metodo|Description|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Chiamato quando è stata trovata una directory di debug nel file .exe.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Chiamato quando è stato aperto un file DBG candidato.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Chiamato quando è stato aperto un file con estensione pdb candidato.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Determina se query del Registro di sistema possono essere utilizzate per individuare i percorsi di ricerca simbolo.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Determina se l'accesso è consentito in un server di simboli per risolvere i simboli.|

## <a name="remarks"></a>Osservazioni
 L'applicazione client implementa questa interfaccia e fornisce un riferimento a esso nella chiamata ai [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).

 Per altre restrizioni che possono essere imposti in un processo di caricamento, vedere la [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: MSDIA80

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)