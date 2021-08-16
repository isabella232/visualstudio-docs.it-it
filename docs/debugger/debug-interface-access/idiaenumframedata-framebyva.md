---
description: Restituisce un frame in base all'indirizzo virtuale (VA).
title: IDiaEnumFrameData::frameByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3a30585dcbd7f9b57ecb401bf76b8af3a00dbbe51287207a929c95be86e79b15
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380595"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Restituisce un frame in base all'indirizzo virtuale (VA).

## <a name="syntax"></a>Sintassi

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parametri
 virtualAddress

[in] Va del frame di interesse.

 frame

[out] Restituisce un [oggetto IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) che rappresenta il frame che contiene l'indirizzo fornito.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se nessun dato del frame corrisponde all'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
