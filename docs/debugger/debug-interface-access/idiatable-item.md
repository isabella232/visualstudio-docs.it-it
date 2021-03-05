---
description: Recupera un riferimento alla voce specificata nella tabella.
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9693a1d16666dcb23f97d918807f9c2fea31c186
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161676"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Recupera un riferimento alla voce specificata nella tabella.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>Parametri
 `index`

in Indice della voce della tabella nell'intervallo compreso tra 0 `count` e-1, dove `count` viene restituito dal metodo [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

out Restituisce un `IUnknown` oggetto che rappresenta la voce di tabella specificata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Una tabella rappresenta una raccolta di oggetti. A seconda di tali oggetti, è possibile eseguire il cast del parametro dell'elemento all'interfaccia appropriata. Se, ad esempio, una tabella contiene oggetti [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , è possibile eseguire il cast del parametro dell'elemento all' `IDiaSegment` interfaccia.

 Si tratta di un approccio più comune per chiamare il `QueryInterface` metodo nell'interfaccia [IDiaTable](../../debugger/debug-interface-access/idiatable.md) per l'interfaccia dell'enumeratore appropriata e usare i metodi specifici dell'enumeratore per accedere al contenuto della tabella. Per un esempio, vedere l'interfaccia [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

## <a name="see-also"></a>Vedi anche
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
