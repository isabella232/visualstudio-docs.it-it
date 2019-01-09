---
title: 'Metodo ienumjsstackframes:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1838d6494311502faf99d86c80e0a74ded4c6e5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092404"
---
# <a name="ienumjsstackframesnext-method"></a>Metodo IEnumJsStackFrames::Next
Ottiene il numero di frame specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cFrameCount`  
 [in] Il numero di frame da ottenere.  
  
 `pFrames`  
 [out] Matrice in cui archiviare i frame.  
  
 `pcFetched`  
 [out] Il numero di frame restituiti.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)