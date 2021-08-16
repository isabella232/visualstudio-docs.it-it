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
ms.openlocfilehash: 9ba4051e6538b1739914f5cd75660b3045d7f5e7387464682db6df8031f57b1d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380030"
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
Cerca l'indirizzo stack frame funzione più vicino nell'elenco specificato.

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

[out] Restituisce l'indirizzo mittente della funzione più vicino.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
