---
title: 'Metodo metodo ijsdebugdatatarget:: ReadMemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572429"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>Metodo IJsDebugDataTarget::ReadMemory
Esegue la lettura della memoria del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 in Indirizzo di base da cui leggere la memoria del processo di destinazione.  
  
 `flags`  
 in Flag che controllano il comportamento di ReadMemory.  
  
 `pBuffer`  
 out Buffer che riceve il contenuto dallo spazio degli indirizzi del processo di destinazione. In caso di errore, il contenuto di questo buffer non è specificato.  
  
 `size`  
 in Numero di byte da leggere dal processo.  
  
 `pBytesRead`  
 out Indica il numero di byte letti dal processo di destinazione. Se JsDebugAllowPartialRead è chiaro, in caso di esito positivo questo valore sarà sempre esattamente uguale alla dimensione di input. Se viene specificato JsDebugAllowPartialRead, in caso di esito positivo, questo valore sarà maggiore di zero.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce S_OK in caso di esito positivo e i codici di errore vengono utilizzati per qualsiasi errore. Restituisce E_JsDEBUG_INVALID_MEMORY_ADDRESS se l'indirizzo non è valido. Per ulteriori informazioni, vedere JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)