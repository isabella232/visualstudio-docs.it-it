---
title: IDiaStackWalkFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5d1010cf9231e4777c8aef8de4a71d23937974e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741508"
---
# <a name="idiastackwalkframeget_registervalue"></a>IDiaStackWalkFrame::get_registerValue
Recupera il valore di un registro.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `index`

in Valore dell'enumerazione di [enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) che specifica il registro per il quale ottenere il valore.

 `pRetVal`

out Restituisce il valore corrente del registro.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)