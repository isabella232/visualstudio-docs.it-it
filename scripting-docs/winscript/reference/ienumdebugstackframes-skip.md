---
title: IEnumDebugStackFrames::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28821d90bc27d23d51db00e871807a2ccef885b7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097513"
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
Ignora un determinato numero di segmenti in una sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Numero di segmenti nella sequenza di enumerazione da ignorare.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo ignora un determinato numero di segmenti in una sequenza di enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)