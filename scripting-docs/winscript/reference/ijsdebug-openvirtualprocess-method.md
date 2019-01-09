---
title: 'Metodo ijsdebug:: OpenVirtualProcess | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093990"
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