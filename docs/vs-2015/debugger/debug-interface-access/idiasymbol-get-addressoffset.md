---
title: Get_addressoffset | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 810d9e90c5b1313db5714dfc476a99ceb50149ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518236"
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Get_addressoffset](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-addressoffset).  
  
Recupera la parte offset di un percorso di indirizzo. Utilizzare quando le [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostata su `LocIsStatic`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce la parte offset di un percorso di indirizzo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Per i membri statici che si trova in una DLL esterna, l'offset restituito da questo metodo può essere 0, poiché questo metodo si basa su come ottenere l'indirizzo virtuale del membro. Indirizzi virtuali sono validi solo se il [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metodo nella [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia è stata richiamata con un parametro diverso da zero che specifica l'indirizzo di caricamento della DLL.  
  
 Per ottenere la parte della sezione di un indirizzo, chiamare il [Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)   
 [Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



