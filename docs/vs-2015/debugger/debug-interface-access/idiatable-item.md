---
title: Idiatable | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d1ebea7d657683d4174784a92ca2213851dcae9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816736"
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
 [in] L'indice della voce della tabella nell'intervallo da 0 a `count`-1, dove `count` restituito dalle [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)(metodo).  
  
 `element`  
 [out] Restituisce un `IUnknown` oggetto che rappresenta la voce della tabella specificata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Una tabella rappresenta una raccolta di oggetti. A seconda di tali oggetti, il parametro di elemento può essere convertito all'interfaccia appropriata. Ad esempio, se una tabella contiene [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) oggetti, quindi il parametro di elemento può essere convertito nel `IDiaSegment` interfaccia.  
  
 È un approccio più comune per chiamare il `QueryInterface` metodo nella [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interfaccia per l'interfaccia dell'enumeratore appropriato e usare i metodi specifici dell'enumeratore per accedere al contenuto della tabella. Vedere le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaccia per un esempio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



