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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 384aab56a17faa4ada1ff99fc43f13032d18db3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121201"
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

[in] Indice della voce di tabella nell'intervallo compreso tra 0 e -1, dove viene restituito dal metodo `count` `count` [IDiaTable::get_Count.](../../debugger/debug-interface-access/idiatable-get-count.md)

 `element`

[out] Restituisce un `IUnknown` oggetto che rappresenta la voce di tabella specificata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Una tabella rappresenta una raccolta di oggetti . A seconda di questi oggetti, è possibile eseguire il cast del parametro dell'elemento all'interfaccia appropriata. Ad esempio, se una tabella contiene [oggetti IDiaSegment,](../../debugger/debug-interface-access/idiasegment.md) è possibile eseguire il cast del parametro dell'elemento all'interfaccia `IDiaSegment` .

 È un approccio più comune chiamare il metodo `QueryInterface` nell'interfaccia [IDiaTable](../../debugger/debug-interface-access/idiatable.md) per l'interfaccia dell'enumeratore appropriata e usare i metodi specifici dell'enumeratore per accedere al contenuto della tabella. Per un [esempio, vedere l'interfaccia IDiaEnumInjectedSources.](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

## <a name="see-also"></a>Vedi anche
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
