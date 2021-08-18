---
description: IDiaStackWalkFrame::searchForReturnAddress cerca l'indirizzo mittente della funzione stack frame specificato.
title: IDiaStackWalkFrame::searchForReturnAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddress method
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0a6781c93bd76f0eaee54f3d134b34a147b57182
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074588"
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
Cerca l'indirizzo stack frame specificato per l'indirizzo restituito della funzione più vicino.

## <a name="syntax"></a>Sintassi

```C++
HRESULT searchForReturnAddress ( 
   IDiaFrameData* frame,
   ULONGLONG*     returnAddress
);
```

#### <a name="parameters"></a>Parametri
 `frame`

[in] Oggetto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) che rappresenta l'oggetto stack frame.

 `returnAddress`

[out] Restituisce l'indirizzo restituito della funzione più vicina.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
