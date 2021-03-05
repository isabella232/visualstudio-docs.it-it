---
description: 'Mantiene il contesto dello stack tra le chiamate del metodo IDiaFrameData:: Execute.'
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 87fb733057272773d7cead9ceadbfe20020baf58
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156860"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Mantiene il contesto dello stack tra le chiamate del metodo [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

## <a name="syntax"></a>Sintassi

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDiaStackWalkFrame` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera il valore di un registro.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Imposta il valore di un registro.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Legge la memoria dall'immagine.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Cerca nell'stack frame specificato l'indirizzo restituito della funzione più vicino.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Cerca nell'stack frame specificato un indirizzo restituito in corrispondenza o in prossimità dell'indirizzo specificato.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene utilizzata durante l'esecuzione del programma per leggere e scrivere i registri, nonché per accedere alla memoria e trovare gli indirizzi restituiti.

## <a name="notes-for-callers"></a>Note per i chiamanti
 L'applicazione client implementa questa interfaccia e passa un'istanza dell'interfaccia al metodo [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . La stessa istanza di questa interfaccia viene utilizzata nuovamente e per mantenere lo stato dei registri durante ogni chiamata del `execute` metodo. Il `execute` metodo usa inoltre questa interfaccia per determinare l'indirizzo mittente.

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
