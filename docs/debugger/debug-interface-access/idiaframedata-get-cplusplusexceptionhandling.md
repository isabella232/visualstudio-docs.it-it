---
description: Recupera un flag che indica se la gestione delle eccezioni C++ è in vigore.
title: IDiaFrameData::get_cplusplusExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_cplusplusExceptionHandling method
ms.assetid: 54ee9cde-ce8e-45f1-809c-6fbad800d850
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bf7887170df3d63335d213ca48cfb8f89d56c6f647c0a93d35baea02e0902487
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121326105"
---
# <a name="idiaframedataget_cplusplusexceptionhandling"></a>IDiaFrameData::get_cplusplusExceptionHandling
Recupera un flag che indica se la gestione delle eccezioni C++ è in vigore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_cplusplusExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se la gestione delle eccezioni C++ è in vigore; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Per determinare se la gestione strutturata delle eccezioni è in vigore (che è molto diversa dalla gestione delle eccezioni C++), chiamare il metodo [IDiaFrameData::get_systemExceptionHandling.](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)
