---
title: 'Metodo ijsdebugdatatarget:: FreeVirtualMemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583041"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Metodo IJsDebugDataTarget::FreeVirtualMemory
Rilascia e/o libera un'area di memoria nello spazio degli indirizzi virtuali del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] Indirizzi all'interno del processo di destinazione in cui deve essere liberata la memoria.  
  
 `size`  
 [in] Numero di byte da liberare. Per rilasciare un'area di memoria, questo valore deve essere zero.  
  
 `freeType`  
 [in] Indica il tipo di operazione gratuita da eseguire. Si tratta in genere è MEM_RELEASE (0x8000), che rilascia l'area specificata di pagine. Al termine dell'operazione, le pagine sono in stato libero. MEM_DECOMMIT (0x4000) può essere usato invece per liberare le pagine senza rilasciarle.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Per altre informazioni, vedere l'API Win32 VirtualFree.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)