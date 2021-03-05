---
description: Restituisce il numero di tag del puntatore acceleratore in una funzione stub C++ AMP.
title: 'IDiaSymbol:: get_numberOfAcceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d428ea0a4837d8a1ddf79e6749d852279bb1c115
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155929"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Restituisce il numero di tag del puntatore acceleratore in una funzione stub C++ AMP.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parametri
 `count`

out Puntatore a un oggetto `DWORD` che include il numero di tag del puntatore dell'acceleratore in una funzione stub C++ amp.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su un' `IDiaSymbol` interfaccia che corrisponde a una funzione dello stub di C++ amp Accelerator.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
