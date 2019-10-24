---
title: IDiaFrameData::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4af060a4a0c36067a07a78166d1cf9cbc62e90e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743474"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
Recupera il tipo di frame specifico del compilatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un valore dall'enumerazione Enumerazione [StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) che indica il tipo di frame specifico del compilatore.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Enumerazione StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)