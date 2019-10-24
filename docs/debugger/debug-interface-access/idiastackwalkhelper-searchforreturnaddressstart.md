---
title: IDiaStackWalkHelper::searchForReturnAddressStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0753cfe2d9ef8b08606185a5f57a3951f54e7de
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741339"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Cerca nell'stack frame specificato un indirizzo restituito in corrispondenza o in prossimità dell'indirizzo dello stack specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT searchForReturnAddressStart( 
   IDiaFrameData*  frame,
   ULONGLONG       startAddress,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Parametri
 `frame`

in Oggetto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) che rappresenta l'stack frame corrente.

 `startAddress`

in Indirizzo di memoria virtuale da cui iniziare la ricerca.

 `ReturnAddress`

out Restituisce l'indirizzo restituito della funzione più vicino per `startAddress`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)