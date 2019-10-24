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
ms.openlocfilehash: 0ca58a206fec15bb8a9ae7f68a278a4530be47d8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743031"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Riceve i callback dalla procedura di individuazione dei simboli DIA, consentendo in tal modo a un'interfaccia utente di segnalare lo stato di avanzamento del tentativo del percorso.

## <a name="syntax"></a>Sintassi

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia espone i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Chiamato quando viene trovata una directory di debug nel file con estensione exe.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Chiamato quando è stato aperto un file. dbg candidato.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Chiamato quando è stato aperto un file con estensione PDB candidato.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Determina se è possibile utilizzare le query del registro di sistema per individuare i percorsi di ricerca dei simboli.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Determina se è consentito l'accesso a un server di simboli per la risoluzione dei simboli.|

## <a name="remarks"></a>Note
 L'applicazione client implementa questa interfaccia e fornisce un riferimento a tale interfaccia nella chiamata al metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

 Per ulteriori restrizioni che possono essere imposte in un processo di caricamento, vedere l'interfaccia [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: Msdia80. dll

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)