---
description: Crea un enumeratore che contiene la stessa sequenza enumerata dell'enumeratore del flusso di dati di debug corrente.
title: IDiaEnumDebugStreamData::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Clone method
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 965fb81fec0964b5e682c21e03c67410b148eae0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044904"
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

[out] Restituisce un [oggetto IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) che contiene la sequenza duplicata dei record del flusso di dati di debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
