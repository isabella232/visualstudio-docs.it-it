---
title: IDiaEnumFrameData::frameByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbdb525034016981c1f9030e6bce1f9590c45591
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838324"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
Restituisce un frame in base all'indirizzo virtuale relativo (RVA).

## <a name="syntax"></a>Sintassi

```C++
HRESULT frameByRVA( 
   DWORD           relativeVirtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parametri
 relativeVirtualAddress

[in] RVA del frame di interesse.

 cornice

[out] Restituisce un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto che rappresenta la cornice che contiene l'indirizzo fornito.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se nessun frame di dati corrisponde all'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)