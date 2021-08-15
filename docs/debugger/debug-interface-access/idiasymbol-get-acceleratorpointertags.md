---
description: Restituisce tutti i valori dei tag del puntatore del tasto di scelta rapida che corrispondono a C++ AMP funzione stub dell'acceleratore.
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2620b47cdf732ea849d4e644e1fa621363c77a9ce4cfb77f0f97104c3233a710
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379982"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Restituisce tutti i valori dei tag del puntatore del tasto di scelta rapida che corrispondono a C++ AMP funzione stub dell'acceleratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametri
 `cnt`

[in] Dimensioni della matrice di output `pPointerTags` .

 `pcnt`

[out] Numero di tag puntatore del tasto di scelta rapida nella C++ AMP stub dell'acceleratore.

 `pPointerTags`

[out] Puntatore a matrice compilato con i valori del tag del puntatore del tasto di scelta rapida nella C++ AMP `DWORD` stub dell'acceleratore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su `IDiaSymbol` un'interfaccia che corrisponde a una funzione C++ AMP stub dell'acceleratore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
