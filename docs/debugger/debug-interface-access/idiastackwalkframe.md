---
description: Mantiene il contesto dello stack tra le chiamate del metodo IDiaFrameData::execute.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 785766a8fb0de87b967ecebdae391a5167bca466
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121561"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Mantiene il contesto dello stack tra le chiamate del [metodo IDiaFrameData::execute.](../../debugger/debug-interface-access/idiaframedata-execute.md)

## <a name="syntax"></a>Sintassi

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDiaStackWalkFrame` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera il valore di un registro.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Imposta il valore di un registro.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Legge la memoria dall'immagine.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Cerca l'indirizzo stack frame specificato per l'indirizzo restituito della funzione più vicino.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Cerca l'indirizzo stack frame specificato in corrispondenza o vicino all'indirizzo specificato.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene usata durante l'esecuzione del programma per leggere e scrivere registri, nonché per accedere alla memoria e trovare gli indirizzi restituiti.

## <a name="notes-for-callers"></a>Note per i chiamanti
 L'applicazione client implementa questa interfaccia e passa un'istanza dell'interfaccia al [metodo IDiaFrameData::execute.](../../debugger/debug-interface-access/idiaframedata-execute.md) La stessa istanza di questa interfaccia viene usata di nuovo per mantenere lo stato dei registri durante ogni chiamata del `execute` metodo . Il `execute` metodo usa anche questa interfaccia per determinare l'indirizzo del mittente.

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
