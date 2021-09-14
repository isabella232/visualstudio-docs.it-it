---
description: Riceve callback dalla procedura di individuazione dei simboli DIA, consentendo in tal modo a un'interfaccia utente di segnalare lo stato di avanzamento del tentativo di posizione.
title: Metodo IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9b5ef4523aa2b8acd098f8a9e46d5aa0009f9b37
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629615"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Riceve callback dalla procedura di individuazione dei simboli DIA, consentendo in tal modo a un'interfaccia utente di segnalare lo stato di avanzamento del tentativo di posizione.

## <a name="syntax"></a>Sintassi

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 I metodi seguenti vengono esposti da questa interfaccia:

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Chiamato quando è stata trovata una directory di debug nel file .exe.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Chiamato quando è stato aperto un file con estensione dbg candidato.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Chiamato quando viene aperto un file PDB candidato.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Determina se le query del Registro di sistema possono essere usate per individuare i percorsi di ricerca dei simboli.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Determina se è consentito l'accesso a un server di simboli per risolvere i simboli.|

## <a name="remarks"></a>Commenti
 L'applicazione client implementa questa interfaccia e vi fornisce un riferimento nella chiamata al [metodo IDiaDataSource::loadDataForExe.](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

 Per altre restrizioni che possono essere imposte a un processo di caricamento, vedere [l'interfaccia IDiaLoadCallback2.](../../debugger/debug-interface-access/idialoadcallback2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
