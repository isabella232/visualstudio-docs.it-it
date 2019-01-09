---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c34ce267113ae5576a8b3bdca9ac34d4abc00f7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086971"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Restituisce un enumeratore di stack frame per il thread corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwSpMin`  
 [in] Limite inferiore dell'indirizzo per enumerare gli stack frame.  
  
 `ppedsf`  
 [out] Enumeratore di stack frame per il thread corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 L'enumeratore di frame dello stack restituisce i frame partire dall'inizio dello stack, il frame di recentemente inserito. L'enumeratore contiene solo gli stack frame con indirizzi maggiori o uguale a `dwSpMin`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)