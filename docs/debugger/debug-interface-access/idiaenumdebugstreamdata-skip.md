---
description: Ignora un numero specificato di record in una sequenza enumerata.
title: IDiaEnumDebugStreamData::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6275c370e7eb7569555fd72af25a6244ba87af7f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630420"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
Ignora un numero specificato di record in una sequenza enumerata.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di record da ignorare nella sequenza enumerata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce ; in caso contrario, restituisce se `S_OK` non sono presenti altri record da `S_FALSE` ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
