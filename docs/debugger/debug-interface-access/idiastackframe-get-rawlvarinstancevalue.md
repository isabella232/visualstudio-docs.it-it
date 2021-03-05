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
ms.workload:
- multiple
ms.openlocfilehash: dc7bc12fe8fd38fc02b6794b2026bce328d95511
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147443"
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

in `IDiaLVarInstance` Oggetto che rappresenta un'istanza della variabile locale per la quale ottenere il valore.

 `cbDataMax`

in Numero massimo di byte nel buffer a cui punta `pbData` . Può essere un massimo di 8 byte ( `sizeof(ULONGLONG)` ).

 `pcbData`

out Restituisce il numero effettivo di byte archiviati nel buffer.

 `pbData`

out Buffer da compilare con i dati. Non può essere `NULL`.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
