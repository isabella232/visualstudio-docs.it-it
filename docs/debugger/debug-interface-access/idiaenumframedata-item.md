---
title: 'IDiaEnumFrameData:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c15f395e7f4aa576c5f69b0f1c61f37ca808fb6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744605"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Recupera un elemento dati di frame per mezzo di un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Parametri
 indice

in Indice dell'oggetto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` viene restituito dal metodo [IDiaEnumFrameData:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .

 section

out Restituisce un oggetto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) che rappresenta l'elemento dati del frame desiderato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)