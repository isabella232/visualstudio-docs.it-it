---
description: Restituisce il numero di tag del puntatore del tasto di scelta rapida in una C++ AMP stub.
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0a7d072d4c3df5321ce07435a316221499b1dbc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113411"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Restituisce il numero di tag del puntatore del tasto di scelta rapida in una C++ AMP stub.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parametri
 `count`

[out] Puntatore a un oggetto che contiene il numero di tag del puntatore del tasto di scelta `DWORD` rapida in una C++ AMP stub.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su `IDiaSymbol` un'interfaccia che corrisponde a una funzione C++ AMP stub dell'acceleratore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
