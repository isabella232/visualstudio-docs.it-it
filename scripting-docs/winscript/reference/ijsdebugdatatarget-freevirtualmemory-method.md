---
title: 'Metodo metodo ijsdebugdatatarget:: FreeVirtualMemory | Microsoft Docs'
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
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577612"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Metodo IJsDebugDataTarget::FreeVirtualMemory
Rilascia e/o Elimina un commit di un'area di memoria nello spazio degli indirizzi virtuali del processo di destinazione.  
  
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
 in Indirizzo nel processo di destinazione in cui la memoria deve essere liberata.  
  
 `size`  
 in Numero di byte di cui eseguire il decommit. Per rilasciare un'area di memoria, questo valore deve essere zero.  
  
 `freeType`  
 in Indica il tipo di operazione gratuita da eseguire. Si tratta in genere di MEM_RELEASE (0x8000), che rilascia l'area di pagine specificata. Al termine dell'operazione, le pagine sono in stato libero. È invece possibile usare MEM_DECOMMIT (0x4000) per eseguire il commit delle pagine senza rilasciarle.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere l'API Win32 VirtualFree.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)