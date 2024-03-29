---
description: Recupera l'ID del registro che contiene un puntatore di base alle variabili locali nello stack.
title: IDiaSymbol::get_localBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_localBasePointerRegisterId method
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: acc288ef526269700fbcdf6c699cdbcf06c10147
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628020"
---
# <a name="idiasymbolget_localbasepointerregisterid"></a>IDiaSymbol::get_localBasePointerRegisterId
Recupera l'ID del registro che contiene un puntatore di base alle variabili locali nello stack. Utilizzare quando [l'enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) è impostata su `SymTagFunction` .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_localBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'ID del registro che contiene un puntatore di base alle variabili locali nello stack.

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
