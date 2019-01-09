---
title: IActiveScriptStats::GetStatEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 824546b64323f7fb88c4ec016f8420169afa665c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097331"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Restituisce una statistica di script personalizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guid`  
 [in] Specifica quale statistica da restituire. La semantica di statistiche corrisponde a un determinato GUID è interamente motore definito.  
  
 `pluHi`  
 [out] 32 bit alti di un intero senza segno a 64 bit che rappresenta la statistica.  
  
 `pluLo`  
 [out] 32 bit bassi di un intero senza segno a 64 bit che rappresenta la statistica.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente a un motore di script personalizzato restituire statistiche significative per un host personalizzato.  
  
> [!NOTE]
>  Questo metodo non è attualmente implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)