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
ms.openlocfilehash: 9bf9ad425b703cbaa15378200260061304223607
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040177"
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
 [in] L'indice della voce della tabella nell'intervallo da 0 a `count`-1, dove `count` restituito dalle [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)(metodo).  
  
 `element`  
 [out] Restituisce un `IUnknown` oggetto che rappresenta la voce della tabella specificata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Una tabella rappresenta una raccolta di oggetti. A seconda di tali oggetti, il parametro di elemento può essere convertito all'interfaccia appropriata. Ad esempio, se una tabella contiene [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) oggetti, quindi il parametro di elemento può essere convertito nel `IDiaSegment` interfaccia.  
  
 È un approccio più comune per chiamare il `QueryInterface` metodo nella [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interfaccia per l'interfaccia dell'enumeratore appropriato e usare i metodi specifici dell'enumeratore per accedere al contenuto della tabella. Vedere le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaccia per un esempio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)