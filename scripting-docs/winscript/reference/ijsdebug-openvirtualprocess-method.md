---
title: 'Metodo IJsDebug:: OpenVirtualProcess | Microsoft Docs'
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
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577751"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>Metodo IJsDebug::OpenVirtualProcess
Metodo Factory utilizzato per creare un nuovo oggetto processo virtuale.  
  
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
 in ID del processo a cui connettersi il debugger.  
  
 `runtimeJsBaseAddress`  
 in Indirizzo di base in cui il runtime JavaScript è stato caricato nel processo di destinazione.  
  
 `pDataTarget`  
 in Interfaccia fornita dal debugger per eseguire una query per lo stato del processo.  
  
 `ppProcess`  
 out Nuovo oggetto processo di debug  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_JsDEBUG_MISMATCHED_RUNTIME se Jscript9diag e Jscript9 non corrispondono.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebug](../../winscript/reference/ijsdebug-interface.md)