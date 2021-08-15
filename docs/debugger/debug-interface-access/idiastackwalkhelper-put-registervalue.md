---
description: IDiaStackWalkHelper::p ut_registerValue imposta il valore di un registro.
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7b4730b2998bbf2cdf6627ef7d749cd87d1eabe7281f3eb5e5892fc4af597ccd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121325913"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
Imposta il valore di un registro.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametri
 `index`

[in] Valore dell'enumerazione [CV_HREG_e che](../../debugger/debug-interface-access/cv-hreg-e.md) specifica il registro in cui scrivere.

 `NewVal`

[in] Nuovo valore del registro.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Nonostante le dimensioni del valore, un'implementazione deve archiviare solo ciò che normalmente contiene il registro. Ad esempio, un registro a 8 bit contenerebbe solo gli 8 bit più bassi del valore specificato.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
