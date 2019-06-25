---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
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
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827294"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Restituisce tutti i valori di tag puntatore tasti di scelta rapida che corrispondono a una funzione di stub di tasti di scelta rapida AMP C++.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametri
 `cnt`

[in] Le dimensioni della matrice di output `pPointerTags`.

 `pcnt`

[out] Il conteggio dei tag puntatore tasti di scelta rapida di C++ funzione di stub di tasti di scelta rapida AMP.

 `pPointerTags`

[out] Oggetto `DWORD` puntatore di una matrice che viene riempito con i valori di tag puntatore tasti di scelta rapida nel C++ funzione stub di tasti di scelta rapida AMP.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene chiamato su un `IDiaSymbol` interfaccia che corrisponde a una funzione di stub di tasti di scelta rapida AMP C++.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)