---
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df32012a100d36c8d288b6b988b9498ff4afd3b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832555"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Consente a un'applicazione client fornire i byte di un file eseguibile come specificato dalla posizione del file.

## <a name="syntax"></a>Sintassi

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDiaReadExeAtOffsetCallback`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.|

## <a name="remarks"></a>Note
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile con un offset assoluto nel file dell'eseguibile. Per usare un indirizzo virtuale relativo, implementare il [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questo metodo è implementato dall'applicazione client e passato per la [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo come metodo alternativo per la lettura del file.

## <a name="requirements"></a>Requisiti
 Intestazione: DIA2.h

 Libreria: diaguids.lib

 DLL: MSDIA80

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)