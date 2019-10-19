---
title: 'IDebugStackFrameSnifferEx:: EnumStackFramesEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576700"
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
 in Limite inferiore degli indirizzi per l'enumerazione degli stack frame.  
  
 `ppedsf`  
 out Enumeratore degli stack frame per il thread corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 L'enumeratore stack frame restituisce i frame che iniziano nella parte superiore dello stack, con il frame di cui è stato effettuato il push più di recente. L'enumeratore contiene solo stack frame con indirizzi maggiori o uguali a `dwSpMin`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)