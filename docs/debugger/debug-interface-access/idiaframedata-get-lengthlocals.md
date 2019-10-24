---
title: 'IDiaFrameData:: get_lengthLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthLocals method
ms.assetid: 51fe15c3-4cd6-4a06-8a41-a56502209762
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff67d3b7e9466451c7e7f79bf4137ec21f629e04
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743602"
---
# <a name="idiaframedataget_lengthlocals"></a>IDiaFrameData::get_lengthLocals
Recupera il numero di byte delle variabili locali di cui è stato effettuato il push nello stack.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lengthLocals ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di byte delle variabili locali.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Il valore restituito da questo metodo viene in genere usato nell'interpretazione di una stringa di programma (vedere il metodo [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) per la definizione di una stringa di programma).

## <a name="see-also"></a>Vedere anche
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)