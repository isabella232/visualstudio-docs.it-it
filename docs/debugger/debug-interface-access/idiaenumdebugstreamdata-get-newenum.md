---
title: IDiaEnumDebugStreamData::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get__NewEnum method
ms.assetid: 023b3e31-0fc9-478d-88e8-af2ce762f322
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17d82c09f3be60db5a51c952c7fb4476baba36cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468462"
---
# <a name="idiaenumdebugstreamdataget__newenum"></a>IDiaEnumDebugStreamData::get__NewEnum
Recupera la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione dell'enumeratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

out Restituisce l' `IUnknown` interfaccia che rappresenta la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione dell'enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)