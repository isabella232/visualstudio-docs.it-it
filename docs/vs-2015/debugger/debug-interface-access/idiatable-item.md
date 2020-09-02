---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574801"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un riferimento alla voce specificata nella tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
## <a name="remarks"></a>Osservazioni  
 Una tabella rappresenta una raccolta di oggetti. A seconda di tali oggetti, è possibile eseguire il cast del parametro dell'elemento all'interfaccia appropriata. Se, ad esempio, una tabella contiene oggetti [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , è possibile eseguire il cast del parametro dell'elemento all' `IDiaSegment` interfaccia.  
  
 Si tratta di un approccio più comune per chiamare il `QueryInterface` metodo nell'interfaccia [IDiaTable](../../debugger/debug-interface-access/idiatable.md) per l'interfaccia dell'enumeratore appropriata e usare i metodi specifici dell'enumeratore per accedere al contenuto della tabella. Per un esempio, vedere l'interfaccia [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
