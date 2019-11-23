---
title: 'IEnumDebugStackFrames:: Next | Microsoft Docs'
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
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575554"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Recupera un numero specificato di segmenti nella sequenza di enumerazione.  
  
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
 in Numero di segmenti da recuperare.  
  
 `prgdsfd`  
 out Restituisce una matrice di interfacce di `DebugStackFrameDescriptor` che rappresenta i segmenti da recuperare.  
  
 `pceltFetched`  
 out Numero effettivo di segmenti recuperati dall'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera un numero specificato di segmenti nella sequenza di enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [Struttura DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)