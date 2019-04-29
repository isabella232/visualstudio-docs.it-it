---
title: 'Metodo ijsdebugdatatarget:: WriteMemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 622de16cc5f755c5d69059a0e0f28d881121861c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558177"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>Metodo IJsDebugDataTarget::WriteMemory
Legge la memoria del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] L'indirizzo di base da cui scrivere nella memoria del processo di destinazione.  
  
 `pMemory`  
 [in] I dati da scrivere nello spazio degli indirizzi del processo specificato.  
  
 `size`  
 [in] Il numero di byte da scrivere nel processo.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Prima che si verifichi il trasferimento dei dati, il sistema verifica che tutti i dati nell'indirizzo di base e la memoria della dimensione specificata è accessibile per l'accesso in scrittura e se non è accessibile, la funzione genera un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)