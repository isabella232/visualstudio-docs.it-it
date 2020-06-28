---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e32450e355d757081efaf66e7c5abaf179e7fd95
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467022"
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

out Restituisce l'indicatore della compressione di origine utilizzata. Un valore pari a zero indica che non è stata utilizzata alcuna compressione di origine.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Il valore restituito da questo metodo è specifico del compilatore utilizzato. Ad esempio, un compilatore può usare la codifica di lunghezza di esecuzione o la compressione di tipo Huffman.

## <a name="see-also"></a>Vedi anche
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)