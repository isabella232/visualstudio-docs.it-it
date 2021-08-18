---
description: Recupera un elemento dati del frame tramite un indice.
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 943d67c89d3ec8334dce585575db63fbb7291a42
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113720"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Recupera un elemento dati del frame tramite un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Parametri
 index

[in] Indice [dell'oggetto IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) da recuperare. L'indice è compreso nell'intervallo da 0 a -1, dove viene restituito dal `count` `count` metodo [IDiaEnumFrameData::get_Count.](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)

 section

[out] Restituisce un [oggetto IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) che rappresenta l'elemento dati del frame desiderato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
