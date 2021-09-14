---
description: IDiaFrameData::get_systemExceptionHandling recupera un flag che indica se la gestione delle eccezioni di sistema è in vigore.
title: IDiaFrameData::get_systemExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_systemExceptionHandling method
ms.assetid: e8df1972-913c-446c-9779-775575b0caa9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e6ac56cb23c47ee1378b8ae5eb1d2a50a1c30c50
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629814"
---
# <a name="idiaframedataget_systemexceptionhandling"></a>IDiaFrameData::get_systemExceptionHandling
Recupera un flag che indica se la gestione delle eccezioni di sistema è in vigore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce `TRUE` se la gestione delle eccezioni di sistema è in vigore; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 La gestione delle eccezioni di sistema è più comunemente nota come gestione delle eccezioni strutturata.

 Per determinare se la gestione delle eccezioni C++ è in vigore, chiamare il [metodo IDiaFrameData::get_cplusplusExceptionHandling.](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)

## <a name="see-also"></a>Vedi anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)
