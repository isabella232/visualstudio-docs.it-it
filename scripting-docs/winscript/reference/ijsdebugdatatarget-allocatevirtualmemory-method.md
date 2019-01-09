---
title: 'Metodo ijsdebugdatatarget:: Allocatevirtualmemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4eaf448e0be224f853674084a18f7aa2a6bd5ed7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086918"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Metodo IJsDebugDataTarget::AllocateVirtualMemory
Riserva e/o impegna un'area di memoria nello spazio degli indirizzi virtuali del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] L'indirizzo nel processo di destinazione in cui la memoria deve essere eseguito il commit o riservata. In genere, questo valore è uguale a zero, nel quale caso il sistema sceglie un indirizzo.  
  
 `size`  
 [in] Le dimensioni dell'area di memoria da allocare, in byte. Il sistema verrà automaticamente arrotondate per eccesso ai limiti della pagina successiva.  
  
 `allocationType`  
 [in] Indica il tipo di allocazione da eseguire. Si tratta in genere è MEM_COMMIT &#124; MEM_RESERVE (0x3000) che riserva e impegna un'allocazione in un unico passaggio.  
  
 `pageProtection`  
 [in] La protezione della memoria per l'area delle pagine da allocare. Se il commit di pagine, è possibile specificare qualsiasi una delle costanti di protezione dati di memoria (ad esempio PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Indirizzo di base dell'area allocata delle pagine.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 La funzione inizializza la memoria che assegna a zero, a meno che non sia utilizzato MEM_RESET. Per altre informazioni, vedere l'API Win32 VirtualAlloc.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)