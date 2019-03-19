---
title: 'Metodo ijsdebugdatatarget:: ReadMemory | Microsoft Docs'
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
ms.openlocfilehash: 705fff3bf2d4be78897c18c5a4c61bd74a8c2230
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147761"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>Metodo IJsDebugDataTarget::ReadMemory
Legge la memoria del processo di destinazione.  
  
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
 [in] L'indirizzo di base da cui leggere la memoria del processo di destinazione.  
  
 `flags`  
 [in] Flag che controllano il comportamento di ReadMemory.  
  
 `pBuffer`  
 [out] Un buffer che riceve il contenuto dallo spazio degli indirizzi del processo di destinazione. In caso di errore, il contenuto di questo buffer non è specificato.  
  
 `size`  
 [in] Il numero di byte da leggere dal processo.  
  
 `pBytesRead`  
 [out] Indica il numero di byte letti dal processo di destinazione. Se JsDebugAllowPartialRead non è specificato, se l'operazione riesce questo valore sarà sempre esattamente uguale alla dimensione di input. Se JsDebugAllowPartialRead viene specificato, in caso di esito positivo questo valore sarà maggiore di zero.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce S_OK sul completamento dell'operazione e codici di errore vengono utilizzati per eventuali errori. Restituisce E_JsDEBUG_INVALID_MEMORY_ADDRESS se l'indirizzo non è valido. Per ulteriori informazioni, vedere JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)