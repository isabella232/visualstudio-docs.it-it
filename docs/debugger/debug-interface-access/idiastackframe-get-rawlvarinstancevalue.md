---
description: Questo metodo recupera il valore della variabile locale specificata come byte non elaborati.
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 065e15ccbaa714a46eb388c2550e6e1db45558f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074660"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Questo metodo recupera il valore della variabile locale specificata come byte non elaborati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Parametri
 `pInstance`

[in] Oggetto `IDiaLVarInstance` che rappresenta un'istanza della variabile locale per cui ottenere il valore.

 `cbDataMax`

[in] Numero massimo di byte nel buffer a cui punta `pbData` . Può essere un massimo di 8 byte ( `sizeof(ULONGLONG)` ).

 `pcbData`

[out] Restituisce il numero effettivo di byte archiviati nel buffer.

 `pbData`

[out] Buffer da riempire con i dati. Non può essere `NULL`.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
