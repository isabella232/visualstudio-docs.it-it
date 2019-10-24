---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741108"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Restituisce tutti i valori dei tag del puntatore dell'acceleratore che corrispondono a una C++ funzione dello stub amp Accelerator.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametri
 `cnt`

in Dimensioni della matrice di output `pPointerTags`.

 `pcnt`

out Numero di tag del puntatore dell'acceleratore C++ nella funzione dello stub amp Accelerator.

 `pPointerTags`

out Puntatore di matrice `DWORD` riempito con i valori dei tag del puntatore dell'acceleratore C++ nella funzione dello stub dell'acceleratore amp.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene chiamato su un'interfaccia `IDiaSymbol` che corrisponde a una C++ funzione dello stub amp Accelerator.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)