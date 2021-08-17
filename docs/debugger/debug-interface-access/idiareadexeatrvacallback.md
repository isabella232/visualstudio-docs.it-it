---
description: Consente a un'applicazione client di fornire byte di un file eseguibile come specificato da un indirizzo virtuale relativo.
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ca3261998ae754b637c8adb412850676cb93532f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044502"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Consente a un'applicazione client di fornire byte di un file eseguibile come specificato da un indirizzo virtuale relativo.

## <a name="syntax"></a>Sintassi

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDiaReadExeAtRVACallback` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Legge il numero specificato di byte a partire dall'indirizzo virtuale relativo specificato dal file eseguibile.|

## <a name="remarks"></a>Commenti
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile usando un indirizzo virtuale relativo nel file del file eseguibile. Per usare un offset di file assoluto, implementare [l'interfaccia IDiaReadExeAtOffsetCallback.](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questo metodo viene implementato dall'applicazione client e passato al metodo [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) come metodo alternativo per la lettura del file.

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
