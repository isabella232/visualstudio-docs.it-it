---
title: IDiaSymbol::get_offset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f99a9cef4266be9a3373d20f09fca8c64e5a33b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839783"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera l'offset della posizione del simbolo. Utilizzare quando l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è `LocIsRegRel` o `LocIsBitField` .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce l'offset in byte della posizione del simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Commenti  
 L'offset è da un punto noto precedentemente determinato. Ad esempio, l'offset per un `LocIsBitField` tipo di posizione è in genere dall'inizio della classe che lo contiene.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|dia2. h|  
|Version:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
