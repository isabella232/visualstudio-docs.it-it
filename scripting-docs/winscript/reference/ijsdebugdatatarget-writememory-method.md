---
title: 'Metodo metodo ijsdebugdatatarget:: WriteMemory | Microsoft Docs'
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
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572411"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>Metodo IJsDebugDataTarget::WriteMemory
Esegue la lettura della memoria del processo di destinazione.  
  
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
 in Indirizzo di base da cui scrivere la memoria del processo di destinazione.  
  
 `pMemory`  
 in Dati da scrivere nello spazio degli indirizzi del processo specificato.  
  
 `size`  
 in Numero di byte da scrivere nel processo.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Prima del trasferimento dei dati, il sistema verifica che tutti i dati dell'indirizzo di base e della memoria della dimensione specificata siano accessibili per l'accesso in scrittura. se non è accessibile, la funzione genera un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)