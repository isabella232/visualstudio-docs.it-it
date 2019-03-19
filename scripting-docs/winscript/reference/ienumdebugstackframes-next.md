---
title: IEnumDebugStackFrames::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e4025af8cf0de76ff224bf5236ba7130d638deb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157334"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Recupera un determinato numero di segmenti nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di segmenti da recuperare.  
  
 `prgdsfd`  
 [out] Restituisce una matrice di `DebugStackFrameDescriptor` interfacce che rappresenta i segmenti in corso il recupero.  
  
 `pceltFetched`  
 [out] Il numero effettivo di segmenti recuperate dall'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera un determinato numero di segmenti nella sequenza di enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugStackFrames Interface](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [Struttura DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)