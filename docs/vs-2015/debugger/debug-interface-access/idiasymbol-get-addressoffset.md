---
title: IDiaSymbol::get_addressOffset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49dde1739b5c595c9327a208e383e6de03300415
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966860"
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
|Version:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
