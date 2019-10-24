---
title: 'IDiaEnumDebugStreams:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 105a84b7c4a1b0a43f8f8008cffbebe7b6e23af5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744773"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreams** ppenum
);
```

#### <a name="parameters"></a>Parametri
 `ppenum`

out Restituisce un oggetto [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) che contiene un duplicato dell'enumeratore. I flussi non vengono duplicati, ma solo l'enumeratore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)