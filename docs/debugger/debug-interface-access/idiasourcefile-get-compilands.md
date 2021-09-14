---
description: Recupera un enumeratore di compilandi con numeri di riga che fanno riferimento a questo file.
title: IDiaSourceFile::get_compilands | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 88afe3bbaaa9fb7f07822ffd8690c4f040bcd896
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629039"
---
# <a name="idiasourcefileget_compilands"></a>IDiaSourceFile::get_compilands
Recupera un enumeratore di compilandi con numeri di riga che fanno riferimento a questo file.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_compilands ( 
   IDiaEnumSymbols** ppRetVal
);
```

#### <a name="parameters"></a>Parametri
 `ppRetVal`

[out] Restituisce un [oggetto IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene un elenco di tutti i compilandi con numeri di riga che fanno riferimento a questo file.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
