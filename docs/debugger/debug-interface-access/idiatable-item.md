---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738720"
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

in Indice della voce della tabella nell'intervallo compreso tra 0 e `count`-1, dove `count` viene restituito dal metodo [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

out Restituisce un `IUnknown` oggetto che rappresenta la voce di tabella specificata.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Una tabella rappresenta una raccolta di oggetti. A seconda di tali oggetti, è possibile eseguire il cast del parametro dell'elemento all'interfaccia appropriata. Se, ad esempio, una tabella contiene oggetti [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , è possibile eseguire il cast del parametro dell'elemento all'interfaccia `IDiaSegment`.

 Si tratta di un approccio più comune per chiamare il metodo `QueryInterface` nell'interfaccia [IDiaTable](../../debugger/debug-interface-access/idiatable.md) per l'interfaccia dell'enumeratore appropriata e usare i metodi specifici dell'enumeratore per accedere al contenuto della tabella. Per un esempio, vedere l'interfaccia [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

## <a name="see-also"></a>Vedere anche
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)