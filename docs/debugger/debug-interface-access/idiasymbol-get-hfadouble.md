---
description: Recupera un flag che specifica se un tipo definito dall'utente (UDT) contiene dati di aggregazione a virgola mobile (HFA) omogenei di tipo double.
title: IDiaSymbol::get_hfaDouble | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hfaDouble method
ms.assetid: efc247b9-c16e-4fa3-89b0-901caf7b74c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1f38d004deab394abff83fd24d8a871c8e40b9f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052253"
---
# <a name="idiasymbolget_hfadouble"></a>IDiaSymbol::get_hfaDouble
Recupera un flag che specifica se un tipo definito dall'utente (UDT) contiene dati di aggregazione a virgola mobile (HFA) omogenei di tipo double.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hfaDouble( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se il tipo definito dall'utente contiene dati HFA di tipo double; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
