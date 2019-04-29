---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c86a0e995e3336bc217bcc9ad0e7ce28a6434478
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832513"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Consente a un'applicazione client fornire i byte di un file eseguibile come specificato da un indirizzo virtuale relativo.

## <a name="syntax"></a>Sintassi

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDiaReadExeAtRVACallback`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Legge il numero specificato di byte a partire specificato indirizzo virtuale relativo (RVA) dal file eseguibile.|

## <a name="remarks"></a>Note
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile usando un indirizzo virtuale relativo nel file dell'eseguibile. Per utilizzare un offset di file assoluto, implementare il [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questo metodo è implementato dall'applicazione client e passato per la [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo come metodo alternativo per la lettura del file.

## <a name="requirements"></a>Requisiti
 Intestazione: DIA2.h

 Libreria: diaguids.lib

 DLL: MSDIA80

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)