---
title: IDiaSymbol::get_machineType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ea9f5762e265b2892a906060a430db03f7b7d67
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739841"
---
# <a name="idiasymbolget_machinetype"></a>IDiaSymbol::get_machineType
Recupera il tipo di CPU di destinazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_machineType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un valore dalle [costanti IMAGE_FILE_MACHINE_](/windows/desktop/SysInfo/image-file-machine-constants) che specifica il tipo di CPU di destinazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedere anche
- [Costanti IMAGE_FILE_MACHINE_](/windows/desktop/SysInfo/image-file-machine-constants) 
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)