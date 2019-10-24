---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741629"
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

in Oggetto `IDiaLVarInstance` che rappresenta un'istanza della variabile locale per la quale ottenere il valore.

 `cbDataMax`

in Numero massimo di byte nel buffer a cui punta `pbData`. Può essere costituito da un massimo di 8 byte (`sizeof(ULONGLONG)`).

 `pcbData`

out Restituisce il numero effettivo di byte archiviati nel buffer.

 `pbData`

out Buffer da compilare con i dati. Non può essere `NULL`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)