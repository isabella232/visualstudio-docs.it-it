---
title: 'Metodo ijsdebug:: OpenVirtualProcess | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583594"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>Metodo IJsDebug::OpenVirtualProcess
Metodo factory utilizzato per creare un nuovo oggetto processo virtuale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `processId`  
 [in] Id del processo per connettere il debugger.  
  
 `runtimeJsBaseAddress`  
 [in] L'indirizzo di base in corrispondenza del quale il runtime di JavaScript è caricato nel processo di destinazione.  
  
 `pDataTarget`  
 [in] Interfaccia fornita per eseguire query sullo stato del processo del debugger.  
  
 `ppProcess`  
 [out] Nuovo oggetto processo di debug  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_JsDEBUG_MISMATCHED_RUNTIME se Jscript9diag e Jscript9 non corrispondono.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebug](../../winscript/reference/ijsdebug-interface.md)