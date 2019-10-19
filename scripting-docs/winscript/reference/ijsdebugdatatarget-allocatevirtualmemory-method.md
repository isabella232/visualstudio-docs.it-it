---
title: 'Metodo metodo ijsdebugdatatarget:: AllocateVirtualMemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577648"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Metodo IJsDebugDataTarget::AllocateVirtualMemory
Riserva e/o conferma un'area di memoria nello spazio degli indirizzi virtuale del processo di destinazione.  
  
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
 in Indirizzo all'interno del processo di destinazione in cui deve essere eseguito il commit o la riserva della memoria. Questo valore è in genere zero, nel qual caso il sistema sceglie un indirizzo.  
  
 `size`  
 in Dimensioni dell'area di memoria da allocare, in byte. Il sistema verrà arrotondato automaticamente al limite della pagina successiva.  
  
 `allocationType`  
 in Indica il tipo di allocazione da eseguire. Si tratta in genere &#124; di MEM_COMMIT MEM_RESERVE (0x3000) che riserva ed Esegui il commit di un'allocazione in un unico passaggio.  
  
 `pageProtection`  
 in Protezione della memoria per l'area di pagine da allocare. Se è in corso il commit delle pagine, è possibile specificare una delle costanti di protezione della memoria (ad esempio, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 out Indirizzo di base dell'area di pagine allocata.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 La funzione Inizializza la memoria allocata a zero, a meno che non venga usato MEM_RESET. Per ulteriori informazioni, vedere l'API Win32 VirtualAlloc.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)