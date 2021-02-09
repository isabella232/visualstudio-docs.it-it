---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f45c212502a6f8cb065be536e5ecbb7e6b61d7b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854619"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Restituisce tutti i valori dei tag del puntatore dell'acceleratore che corrispondono a una funzione C++ AMP Stub dell'acceleratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametri
 `cnt`

in Dimensioni della matrice di output `pPointerTags` .

 `pcnt`

out Il numero di tag del puntatore acceleratore nella funzione C++ AMP Stub dell'acceleratore.

 `pPointerTags`

out `DWORD` Puntatore di matrice riempito con i valori dei tag del puntatore dell'acceleratore nella funzione C++ amp Stub dell'acceleratore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su un' `IDiaSymbol` interfaccia che corrisponde a una funzione dello stub di C++ amp Accelerator.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)