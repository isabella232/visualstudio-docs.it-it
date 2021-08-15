---
description: IDiaStackWalkFrame::get_registerValue recupera il valore di un registro.
title: IDiaStackWalkFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2a6b5c2a79f69d5d84f60e08145a470e974d38ea8c233c1a9b65e3964fc608a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312084"
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

[in] Valore dell'enumerazione [CV_HREG_e che](../../debugger/debug-interface-access/cv-hreg-e.md) specifica il registro per cui ottenere il valore.

 `pRetVal`

[out] Restituisce il valore corrente del registro.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
