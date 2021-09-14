---
description: Consente a un'applicazione client di fornire byte di un file eseguibile come specificato dalla posizione del file.
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9d8ca962425742304a215512abd10b7aed755feb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629502"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Consente a un'applicazione client di fornire byte di un file eseguibile come specificato dalla posizione del file.

## <a name="syntax"></a>Sintassi

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDiaReadExeAtOffsetCallback` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.|

## <a name="remarks"></a>Commenti
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile usando un offset assoluto nel file eseguibile. Per usare un indirizzo virtuale relativo, implementare [l'interfaccia IDiaReadExeAtRVACallback.](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questo metodo viene implementato dall'applicazione client e passato al metodo [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) come metodo alternativo per la lettura del file.

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
