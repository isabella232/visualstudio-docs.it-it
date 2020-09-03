---
title: 'IDiaEnumDebugStreamData:: get_name | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37cd52af7326454b0b684ad97f9cde088a8a5679
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468469"
---
# <a name="idiaenumdebugstreamdataget_name"></a>IDiaEnumDebugStreamData::get_name
Recupera il nome di un flusso di dati di debug.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_Name ( 
   BSTR * pRetVal
)
```

#### <a name="parameters"></a>Parametri
 pRetVal

out Restituisce il nome di un flusso di dati di debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)