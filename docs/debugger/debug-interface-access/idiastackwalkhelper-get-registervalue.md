---
description: IDiaStackWalkHelper::get_registerValue recupera il valore di un registro.
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5f5edbbe7e01e1b15f308687d58be0623521b1ce
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626838"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
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

[in] Valore [dell'enumerazione CV_HREG_e che](../../debugger/debug-interface-access/cv-hreg-e.md) specifica il registro da cui ottenere il valore.

 `pRetVal`

[out] Restituisce il valore corrente del registro.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Nonostante le dimensioni del `pRetVal` parametro , un'implementazione deve archiviare solo ciò che normalmente contiene il registro. Ad esempio, un registro a 8 bit contiene solo gli 8 bit più bassi del valore specificato. Questo valore a 8 bit viene espanso a 64 bit quando viene restituito da questo metodo.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
