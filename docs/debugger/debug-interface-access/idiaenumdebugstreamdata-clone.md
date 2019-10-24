---
title: 'IDiaEnumDebugStreamData:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Clone method
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468cc34453373df91898dce99fca01b8cb04b9fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744893"
---
# <a name="idiaenumdebugstreamdataclone"></a>IDiaEnumDebugStreamData::Clone
Crea un enumeratore che contiene la stessa sequenza enumerata dell'enumeratore corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreamData** ppenum
);
```

#### <a name="parameters"></a>Parametri
 ppenum

out Restituisce un oggetto [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) che contiene la sequenza duplicata di record del flusso di dati di debug.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)