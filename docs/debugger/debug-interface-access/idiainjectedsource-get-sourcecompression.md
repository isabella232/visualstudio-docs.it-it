---
description: Recupera l'indicatore della compressione di origine utilizzata.
title: IDiaInjectedSource::get_sourceCompression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e227b830f516077a2b168e0ecb7e3cbec09f7ea1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629748"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Recupera l'indicatore della compressione di origine utilizzata.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'indicatore della compressione di origine utilizzata. Il valore zero indica che non è stata usata alcuna compressione di origine.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Il valore restituito da questo metodo è specifico del compilatore utilizzato. Ad esempio, un compilatore potrebbe usare Run-Length codifica o la compressione in stile Huffman.

## <a name="see-also"></a>Vedi anche
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
